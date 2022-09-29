# TCP可靠传输

- 校验和
- 序列号与确认应答机制
- 重传机制
- 流量控制
- 拥塞控制

# 校验和
TCP 将计算首部和数据的检验和。

作用是检测数据在传输过程中的变化。

如果接受端的检验和有差错，TCP 将丢弃这个报文段并且不确认收到此报文段。

# 序列号与确认应答机制

1. 序列号是指该报文段的第一个字节的序号，一个字节占一个序号。
2. 确认应答机制就是接收方收到TCP报文段后就会返回一个确认应答消息。
# 重传机制
## 超时重传
在发送数据时，设定一个定时器，当超过指定的时间后，没有收到对方的 ACK 报文，就会重发该数据。

数据包丢失和确认应答丢失都会引起超时重传。

**RTT(往返时间)即数据从网络的一端传送到另一端所需的时间的两倍。**![](https://cdn.nlark.com/yuque/0/2022/webp/2388408/1662728441222-2ef2b783-4fcf-4bfa-8c54-e7d2081c77a2.webp#clientId=u459df086-2385-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u0f0001cf&margin=%5Bobject%20Object%5D&originHeight=804&originWidth=921&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ube9b4553-54b5-4c47-acfc-6a9a218a40b&title=)

**显然，超时重传时间 RTO 的值应该略大于 RTT **。而RTT是一个动态变化的值，所以RTO也是一个动态变化的值。

如果超时重发的数据，再次超时又需要重传的时候，**超时重传时间就会加倍。**

超时触发重传的缺点：超时周期可能相对较长，效率低。


## 快速重传
TCP 还有另外一种快速重传机制，它不以时间为驱动，而是以数据驱动重传。

快速重传是接收方每当收到一个失序报文段时，就向发送方发送一个重复ACK，指明下一个期待的字节的序号。

当接受方收到三个**相同的**冗余ACK时，**就会认为该报文丢失**重传该报文段。 <img src="https://cdn.nlark.com/yuque/0/2022/webp/2388408/1662728770834-52e432e3-bb0a-41b3-a4a7-5978e3e74442.webp#clientId=u459df086-2385-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=uaf2386a7&margin=%5Bobject%20Object%5D&originHeight=1089&originWidth=790&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u89fa8d8c-4469-4a83-8c86-b2ddc8f6c81&title=" style="zoom:50%;" /><br />思考这里为什么会回复ACK6？滑动窗口吧


## 滑动窗口
窗口大小就是指**无需等待确认应答，而可以连续发送数据的区域**。

窗口的实现实际上是操作系统开辟的一个缓冲区。发送方在等待确认应答报文返回之前，必须在缓冲区中保留已发送的数据。

如果在规定时间间隔内收到确认应答报文，就可以将数据从缓冲区中清除。

**ACK丢失也不一定会重传。**

若有 ACK 丢失，可以通过下一个确认应答进行确认。这个模式就叫**累计确认**或者**累计应答**。

例如：ACK 300 即使丢失了，只要发送方收到了 ACK 400 的确认应答，就意味着 400 之前的所有数据「接收方」都收到了。<img src="https://cdn.nlark.com/yuque/0/2022/webp/2388408/1662728999222-944766dc-7d1f-4fce-959f-40255215651a.webp#clientId=u459df086-2385-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u87dadef2&margin=%5Bobject%20Object%5D&originHeight=886&originWidth=912&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u36b8630c-d563-4a49-9e3d-455d705ded5&title=" style="zoom:67%;" /><br />**发送方的滑动窗口**

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1662559636397-f59e9f79-e732-4655-a62a-8b30f475cac9.png?x-oss-process=image%2Fresize%2Cw_750%2Climit_0&date=1664450282157)

> 面试题：TCP 是一个包发送出去并得到确认后，才可以发送下一个包，还是无需等待确认就可以发送下一个包？看滑动窗口吧

**接收方的滑动窗口**

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1662559714175-0fb35530-07c1-45da-a495-a37cec2e700e.png?x-oss-process=image%2Fresize%2Cw_750%2Climit_0&date=1664450282158)

# 流量控制
**目的：**流量控制就是控制发送方发送速率，保证接收方来得及接收，**防止分组丢失**。

**实现**：TCP流量控制的方法就是滑动窗口机制。

接收端会在发送 ACK 报文时，会填入自己的接收窗口大小填入TCP头部的字段中。

发送方会根据接收到的 ACK 报文中的窗口大小的值改变自己的发送速度。

**死锁：**为了避免流量控制引发的死锁，每当发送者收到一个零窗口的应答后就启动一个计时器。

时间一到便主动发送报文询问接收者的窗口大小。

若接收者仍然返回零窗口，则重置该计时器继续等待；若窗口不为0，此时重置发送窗口后开始发送。

# 拥塞控制
**流量控制与拥塞控制的区别：**

- 流量控制是控制发送者的发送速度从而使接收者来得及接收，防止分组丢失的。
- 拥塞控制是**网络发生拥塞时，为了防止更多的数据注入到网络中，降低网络的拥塞程度的一种手段。**

**如何判断网络拥塞**

只要触发了超时重传机制，就认为网络中出现了拥塞。

**拥塞控制的实现-拥塞窗口**

拥塞窗口 cwnd是发送方维护的一个的变量。它会根据网络的拥塞程度动态变化，网络中没有拥塞，cwnd就会变大，反之就会减小。

加入了拥塞窗口的概念后，此时发送窗口的值是swnd = min(cwnd, rwnd)。

## 拥塞控制算法
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1662565485256-fcdb54c3-04ec-4a5f-99a9-db7b3d89725a.png?date=1664450282339)
### 慢开始
一点一点开始提高数据发送量。<br />规则：

- cwnd初始值为1，每经过一个传播轮次(RTT)，cwnd就会加倍。
- 当cwnd大于等于慢启动门限(ssthresh)时，就会使用拥塞避免算法。
### 拥塞避免算法
规则：每经过一个传播轮次(RTT)，cwnd增加1。
### 发生拥塞
无论是慢开始阶段还是拥塞避免，只要出现了网络拥塞（**触发超时重传机制**），慢开始轮限 sshresh 和 拥塞窗口大小 cwnd 的值会发生变化（乘法减小）：

- ssthresh 设为 cwnd/2
- cwnd 重置为 1
- 然后重新开始执行慢开始算法
### 快重传与快恢复

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1662565645217-20e547a6-33c3-4b29-82bd-3614d24a1e04.png?date=1664450282340)

> 发送方知道只有个别报文段丢失而不是网络拥塞时，不启动慢开始算法，而是执行快恢复算法。

- 将门限值设为cwnd/2
- 将cwnd设为更新过后的门限值
- 执行拥塞避免算法

