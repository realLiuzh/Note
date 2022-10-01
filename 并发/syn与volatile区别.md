# syn与volatile区别

- volatile不需要加锁，比syn更轻量级，不会阻塞线程。
- syn可以保证可见性与原子性。v只能保证可见性，不能保证原子性。
- volatile标记的变量不会被编译器优化。syn锁住的变量可能被编译器优化。
- volatile只能用在变量上。
