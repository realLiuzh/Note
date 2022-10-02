# ConcurrentHashMap1.7

我们知道ConcurrentHashMap在1.7版本底层实现是Segment+数组+链表/红黑树。

Segment到底是个啥？

它其实是个数组：

- 数组的长度就是并发度
- 每个数组的元素是HashMap的元素
- 并发度一旦确定就不再改变