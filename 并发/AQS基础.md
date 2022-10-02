# AQS基础

AQS同步队列器，是构建锁和其它同步组件的基础框架，降低了实现一个可靠自定义同步组件的门槛。

使用方法：

- 子类继承同步器并实现其抽象方法来管理同步状态。

- AQS通过一个int变量state来表示同步状态
- AQS通过一个FIFO队列来完成阻塞线程的排队工作

如果说我要自定义一把锁：

自己实现lock、unlock肯定是困难的。

那么可以使用AQS框架，把难以实现的方法代理到Sync上面去。

因为有了AQS框架的帮助，实现那些比较复杂的功能就简单很多。

![3B05F25CA643FCC38AB666E6CAFA7DDE.jpg](https://cdn.nlark.com/yuque/0/2022/jpeg/2388408/1664692301003-9cbf5975-f44b-4c2b-9ef4-0eb16bfb8c90.jpeg?x-oss-process=image%2Fresize%2Cw_750%2Climit_0)