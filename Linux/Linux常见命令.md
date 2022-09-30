# Linux常见命令

## 上个命令的最后一个参数

Esc+.

## 网络

- ip addr。查看网卡以及ip信息。
- netstat -tnulp。查看端口占用情况。

## CPU和内存占用

- top。显示各个进程CPU和内存的占用率。

## 查看日志

- 固定场景下：cat -n log | grep "key"
- 实时场景下：tail -fn 100 test.log 

## 查看文件信息

- stat [file name]。显示文件大小和修改时间

## 删除命令的最后一个单词

ctrl+w
