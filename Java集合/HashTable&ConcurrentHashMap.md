# HashTable&ConcurrentHashMap

- HashTable与ConcurrentHashMap都是线程安全的集合
- key值都不能为null
- HashTable并发度低，整个HashTable使用一把锁，同一时刻只能有一个线程操作它
- ConcurrentHashMap
  - 1.8之前，使用的是Segment+数组+链表/红黑树。每个Segment对于一把锁，如果多个线程访问不同的Segment，则不会造成冲突。1.8之前ConcurrentHashMap的并发度是Segment的个数。
  - 1.8及以后，将数组的每个头节点作为锁，如果多个线程访问的头节点不同，则不会冲突。此时的并发度为数组的容量。