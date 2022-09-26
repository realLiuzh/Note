# 各种Map的区别

# HashMap与TreeMap的区别

1. HashMap底层是数组加链表/红黑树，时间复杂度为O(1)；TreeMap底层是红黑树，时间复杂度为O(n)。
2. HashMap存放的元素是无序的；TreeMap存放的元素是按照key大小排列的。

# HashMap与HashTable的区别

1. HashMap是线程不安全的；HashTable是线程安全的。
2. HashMap支持key-value为null；HashTable不支持。

