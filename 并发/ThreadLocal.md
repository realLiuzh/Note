# ThreadLocal

如果创建了一个ThreadLocal变量，那么访问这个变量时，每个线程都有一个独立的、自己的本地值。

## 原理

Thread类里有一个threadLocals变量。

```java
public class Thread implements Runnable {
    //......
    //与此线程有关的ThreadLocal值。由ThreadLocal类维护
    ThreadLocal.ThreadLocalMap threadLocals = null;
    
}
```

ThreadLocal的set()方法：

```java
public void set(T value) {
    //获取当前请求的线程    
    Thread t = Thread.currentThread();
    //取出 Thread 类内部的 threadLocals 变量(哈希表结构)
    ThreadLocalMap map = getMap(t);
    if (map != null)
        // 将需要存储的值放入到这个哈希表中
        map.set(this, value);
    else
        createMap(t, value);
}
ThreadLocalMap getMap(Thread t) {
    return t.threadLocals;
}
```

- 每个Thread种都有一个ThreadLocalMap
- ThreadLocalMap种存储以ThreadLocal为key，Obejct为value的键值对

![ThreadLocal 数据结构](https://guide-blog-images.oss-cn-shenzhen.aliyuncs.com/github/javaguide/java/concurrent/threadlocal-data-structure.png)























