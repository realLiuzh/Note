# 持久化策略-RDB

避免因为进程结束而造成的数据丢失问题，在下次启动时候利用之前持久化的文件实现数据恢复。

# RDB快照

将进程数据生成快照保存到硬盘。

## 流程

<img src="https://cdn.nlark.com/yuque/0/2022/png/2388408/1662605171569-da992c54-f8be-4dd7-bc8c-4cced0557f54.png" alt="img" style="zoom:67%;" />

# 特点

优点：redis加载rdb恢复数据的速度快于aof，所以比较适合备份和全量复制

缺点：没法做到实时持久化。因为bgsave要fork操作创建子进程，频繁执行成本高。

