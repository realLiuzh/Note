# TCP长连接

TCP长连接解决了：在长时间未通信的情况下，如何得知对方还活着？

在一段时间t内如果tcp连接都不活跃，开启保活功能的一端会向对端发送一个保活探测报文。

- 若对端对端收到探测报文并进行响应。则证明TCP连接正常，重置保活时间计数器。
- 若无法收到响应。那么在一定时间t后，将继续发送探测报文。直到达到**上限**。这时会被认为不可达，TCP连接会被中断。