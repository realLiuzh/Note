# HashMap为什么要引入红黑树

其实扩容和树化都是为了解决 **链表过长导致查询效率变低**的问题。

- 扩容时会对元素重新进行哈希计算。有机会减小链表长度。

- 极端情况下，**有大量元素二次哈希的值总是相同的**，这导致扩容并不能减小链表长度。

  所以引入红黑树来应对这种情况。