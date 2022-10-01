# 持久化策略-AOF

避免因为进程结束而造成的数据丢失问题，在下次启动时候利用之前持久化的文件实现数据恢复。

# AOF

将每次写命令记录到日志文件中，重启时重新执行aof文件中的命令来恢复数据。

使用AOF要开启 `appendonly yes`，默认关闭。

## 流程

<img src="https://cdn.nlark.com/yuque/0/2022/png/2388408/1662605560185-ac83e685-84a9-44a1-9987-f50c3905b634.png" alt="img" style="zoom:67%;" />

### 文件同步

![img](https://cdn.nlark.com/yuque/0/2022/png/2388408/1662605657437-3d8c8008-d46f-4cc7-8593-7da73ef302ee.png)

- always：每次写入都要同步到AOF文件，性能差
- no：性能高，但是数据安全性差
- everysec：默认，性能和安全性兼顾。最多丢失1s数据

### 重写机制

解决AOF文件过大的问题，加快AOF加载的速度。

为什么能变小呢？过时数据、命令合并

#### 触发方式

手动触发： bgrewriteaof命令。  

自动触发： 据auto-aof-rewrite-min-size和auto-aof-rewrite-percentage参数确定自动触发时机。  

#### 流程

<img src="https://cdn.nlark.com/yuque/0/2022/png/2388408/1662606142911-c3f9d491-b97a-4afd-853e-7e49484b072b.png" alt="img" style="zoom:80%;" />

1. 先判断是否正在执行 bgsave/bgrewriteaof的子进程。
   1. bgrewriteaof：直接返回
   2. bgsave：等bgsave执行完成后再执行

2. 父进程执行fork操作创建子进程，此时父进程阻塞。
3. 父进程fork后，可以响应其他命令。**Redis的所有写命令依然写入AOF缓冲区，并同步到硬盘，保证原有AOF机制的正确。**
4. 同时，Redis也会把命令写入AOF重写缓冲区中，防止新AOF文件丢失这部分数据。即bgrewriteaof重写期间Redis的写命令同时追加到aof_buf和aof_rewirte_buf两个缓冲区。
5. 子进程完成AOF重写后会给父进程发送一个信号，将AOF重写缓冲区中的内容写入到新的AOF文件中。
6. 重写完成后使用新aof文件替换掉旧的aof文件。

