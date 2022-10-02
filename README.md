# Note

<p align="center">
  <a href="https://github.com">
  <img src="https://img.shields.io/badge/MySQL-github-blue.svg" alt="github"></a>
   <a href="https://github.com">
  <img src="https://img.shields.io/badge/Redis-github-black.svg" alt="github"></a>
   <a href="https://github.com">
  <img src="https://img.shields.io/badge/JVM-github-green.svg" alt="github"></a>
   <a href="https://github.com">
  <img src="https://img.shields.io/badge/并发-github-red.svg" alt="github"></a>
   <a href="https://github.com">
  <img src="https://img.shields.io/badge/Linux-github-white.svg" alt="github"></a>
</p>


**目录 Catalogue：**

- [计算机网络](#计算机网络) 

- [MySQL](#MySQL)
- [Redis](#Redis)
- [JVM](#JVM)
- [Java集合](#Java集合)
- [Java并发](#Java并发)
- [设计模式](#设计模式)
- [Spring](./Spring/Aop思想.md)
- [Linux](#Linux)
- [其它](#其它)
- [反馈与改进](#反馈及改进)
- [参与贡献](#参与贡献)

# 计算机网络

- [TCP可靠传输](./计算机网络/TCP可靠传输.md)
- [TCP三握四挥](./计算机网络/TCP三握四挥.md)
- [浏览器输入URL后的过程](./计算机网络/浏览器输入URL后的过程.md)
- [DNS过程](./计算机网络/DNS过程.md)
- [http长连接](./计算机网络/http长连接.md)

# MySQL

- [InnoDB与MyISAM的区别](./MySQL/InnoDB与MyISAM的区别.md)
- [主键自增继续编or重新编](./MySQL/主键自增继续编or重新编.md)
- [MySQL优化手段](./MySQL/MySQL优化手段.md)
- [MySQL三大范式](./MySQL/MySQL三大范式.md)
- [唯一列用普通索引还是唯一索引](./MySQL/唯一列用普通索引还是唯一索引.md)
- [redolog与changebuffer的区别](./MySQL/redolog与changebuffer的区别.md)
- [changebuffer是否总是可以提高性能](./MySQL/changebuffer是否总是可以提高性能.md)
- [索引优化手段](./MySQL/索引优化手段.md)
- [索引为什么最好是自增的](./MySQL/索引为什么最好是自增的.md)

# Redis

- [缓存穿透、缓存击穿与缓存雪崩](./Redis/缓存穿透、缓存击穿与缓存雪崩.md)
- [键过期策略](./Redis/键过期策略.md)
- [内存淘汰策略](./Redis/内存淘汰策略.md)
- [持久化策略-RDB](./Redis/持久化策略-RDB.md)
- [持久化策略-AOF](./Redis/持久化策略-AOF.md)
- [重启过程](./Redis/重启过程.md)

# JVM

- [对象的四种引用](./JVM/对象的四种引用.md)
- [JVM内存分布](./JVM/JVM内存分布.md)
- [JVM为什么要分代GC](./JVM/JVM为什么要分代GC.md)
- [标记整理比标记复制慢](./JVM/标记整理比标记复制慢.md)
- [新生代与老年代GC算法的选择](./JVM/新生代与老年代GC算法的选择)
- [三种GC算法的优劣](./JVM/三种GC算法的优劣.md)
- [对象分配过程](./JVM/对象分配过程.m)
- [堆内存细究](./JVM/堆内存细究.md)
- [对象晋升到老年代](./JVM/对象晋升到老年代.md)
- [GCROOTS](./JVM/GCROOTS.md)
- [双亲委派机制是什么](./JVM/双亲委派机制是什么.md)
- [如何打破双亲委派](./JVM/如何打破双亲委派.md)
- [CMS的特点](./JVM/CMS的特点.md)
- [CMS过程](./JVM/CMS过程.md)
- [G1特点](./JVM/G1特点.md)
- [跨代引用](./JVM/跨代引用.md)
- [G1过程](./JVM/G1过程.md)
- [JVM参数](./JVM/JVM参数.md)
- [类加载机制](./JVM/类加载机制.md)

# Java集合

- [各种Map的区别](./Java集合/各种Map的区别.md)
- [ArrayList&LinkedList](./Java集合/ArrayList&LinkedList.md)
- [HashMap.put()](./Java集合/HashMapput().md)
- [HashMap扩容时机](./Java集合/HashMap扩容时机.md)
- [HashMap树化时机](./Java集合/HashMap树化时机.md)
- [HashMap1.8的优化](./Java集合/HashMap1.8的优化.md)
- [ArrayList扩容机制](./Java集合/ArrayList扩容机制.md)
- [HashMap为什么要引入红黑树](./Java集合/HashMap为什么要引入红黑树.md)
- [HashMap为什么不一开始就树化](./Java集合/HashMap为什么不一开始就树化.md)
- [HashMap树化阈值为什么是8](./Java集合/HashMap树化阈值为什么是8.md)
- [HashMap树退化时机](./Java集合/HashMap树退化时机)
- [HashMap索引](./Java集合/HashMap索引.md)
- [HashMap桶的容量为何为2的n次方幂](./Java集合/HashMap桶的容量为何为2的n次方幂)
- [HashMap扩容因子的设计](./Java集合/HashMap扩容因子的设计.md)
- [HashMap并发问题1.8](./Java集合/HashMap并发问题1.8.md)
- [HashMap并发问题1.7](./Java集合/HashMap并发问题1.7.md)
- [HashTable&ConcurrentHashMap](./Java集合/HashTable&ConcurrentHashMap.md)
- [ConcurrentHashMap1.7](./Java集合/ConcurrentHashMap1.7.md)

# Java并发

- [6种线程状态](./并发/6种线程状态.md)
- [同步异步阻塞非阻塞](./并发/同步异步阻塞非阻塞.md)
- [保证线程安全的方式](./JVM/保证线程安全的方式.md)
- [为什么需要Java内存模型](./并发/为什么需要Java内存模型.md)
- [Happends-Before](./并发/Happends-Before.md)
- [线程池参数](./并发/线程池参数)
- [线程池阻塞队列](./并发/线程池阻塞队列.md)
- [线程池拒绝策略](./并发/线程池拒绝策略.md)
- [线程池创建方法](./并发/线程池创建方法.md)
- [线程池生命周期](./并发/线程池生命周期.md)
- [线程池执行流程](./并发/线程池执行流程.md)
- [线程池参数设置](./并发/线程池参数设置.md)
- [线程安全的集合](./并发/线程安全的集合.md)
- [synchronized原理](./并发/synchronized原理.md)
- [synchronized优化](./并发/synchronized优化.md)
- [volatile](./并发/volatile.md)
- [syn与volatile区别](./并发/syn与volatile区别.md)
- [syn与lock的区别](./并发/syn与lock的区别.md)
- [syn与ReentrantLock的区别](./并发/syn与ReentrantLock的区别.md)
- [AQS基础](./并发/AQS基础)
- [偏向锁](./并发/偏向锁.md)
- [轻量级锁](./并发/轻量级锁.md)
- [锁对比](./并发/锁对比.md)
- [CAS](./并发/CAS.md)
- [ABA](./并发/ABA.md)
- [ThreadLocal](./并发/ThreadLocal.md)
- [ThreadLocal内存泄露](./并发/ThreadLocal内存泄露.md)

# 设计模式

- [单例模式](./设计模式/单例模式.md)

# Spring

- [Aop思想](./Spring/Aop思想.md)
- [autowired&resource](./Spring/autowired&resource.md)
- [IOC思想](./Spring/IOC思想.md)

# Linux

- [Linux常见命令](./Linux/Linux常见命令.md)

# 其它

- [反射代理](./其它/反射代理.md)
- [为什么重写equals()时要重写hashcode()](./其它/为什么重写equals()时要重写hashcode().md)
- [静态代理与动态代理](./其它/静态代理与动态代理.md)
- [红黑树特点](./其它/红黑树特点.)
- [序列化与反序列化](./其它/序列化与反序列化.md)
- [冷门问题合集](./其它/冷门问题合集.md)

# 笔记问题

- 啰嗦😥。无法”正确的、一针见血的“的指出问题所在

# 反馈及改进

😙😙欢迎提出`issues`，看到就会回馈。并且将您添加到项目贡献者列表中。

# 参与贡献

> 手动打字难免会有错别字，如果在学习过程中发现了错别字或者需要补充及修正的知识点。
>
> 欢迎及时修正本项目，让我们一起为开源做贡献！

具体步骤如下:

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request，填写必要信息
5. 等待审核即可，通过之后会邮件通知您
