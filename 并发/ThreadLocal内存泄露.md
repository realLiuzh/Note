# ThreadLocal内存泄露

ThreadLocalMap中的key是ThreadLocal对象，但不完全是。

是ThreadLocal的弱引用。

为什么呢？

考虑在方法内创建一个ThreadLocal对象。

在该对象没有逃逸出去的情况下，当方法执行完，该对象应该被认定为垃圾了。

如果ThreadLocalMap为强引用，该对象永远不会被GC掉。除非线程结束。

所以把key设置为弱引用，下次GC会把只有弱引用的Key回收掉。

Entry的Key为null，当get()、set()或者remove()调用时，ThreadLocalMap会清除掉key为null的Entry。

完成相应内存的shi'f