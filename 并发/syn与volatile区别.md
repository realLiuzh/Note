# syn与volatile区别

- volatile不需要加锁，比syn更轻量级，不会阻塞线程。
- syn可以保证可见性与原子性。v只能保证可见性。
