# redo log与change buffer的区别

redo log与change buffer这的不同之处在于优化了**整个变更流程的不同阶段**。

一个简单的变更流程：

1. 从磁盘读取待变更的数据页，读取到内存页中
2. 对数据进行修改
3. 将变更后的数据写入到磁盘中

- change buffer 优化了(1)，避免了随机读磁盘IO

- redo log优化了(3)，将随机写磁盘优化成顺序写磁盘（确保crash-safe）

change buffer不一定会用到，redo log会一直用到。

有无用到change buffer，对redo log的区别在于：用到了change buffer，在redo log中记录的是new change buffer信息，而不是物理变更。

redo log主要节省的是随机写磁盘的消耗(转成顺序写)，而change buffer主要节省的是随机读磁盘的IO消耗。

