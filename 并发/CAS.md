# CAS

首先，CAS是一种**乐观锁思想**的实现。

CAS是**原子操作**

CAS的**解决办法**是：需要A、B、C三个参数，如果A==B，就把A修改为C。

- A是内存值
- B是旧的预期值
- C是要修改成的新值。

```java
public final int incrementAndGet() {
    for (;;) {
        int current = get();
        int next = current + 1;
        if (compareAndSet(current, next))
            return next;
    }
}
```

