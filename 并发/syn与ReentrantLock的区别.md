# syn与ReentrantLock的区别

- syn是依赖于jvm实现的，reLock是基于AQS实现的。
- reLock提供了额外功能
  - 尝试非阻塞的获取锁。syn会阻塞；reLock会返回false
  - 超时获取锁。超时返回false
  - 可中断地获取锁。syn会被阻塞，阻塞时不能响应中断。reLock可以响应其它线程的中断并抛出异常。
  - 除此之外，reLock还可以设置为公平锁/非公平锁。