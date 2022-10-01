# syn与lock的区别

- Lock提供了许多额外的功能：
  - 尝试非阻塞的获取锁。syn会阻塞；lock会返回false
  - 超时获取锁。超时返回false
  - 可中断地获取锁。syn会被阻塞，阻塞时不能响应中断。Lock可以响应其它线程的中断并抛出异常。
- Lock可以提高多个线程的效率（ReadWriteLock 实现读写分离）