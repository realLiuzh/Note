# HashMap树退化时机

- 如果扩容后，树的元素小于等于6，红黑树会退化为链表。
- 移除元素时，如果移除之前，root.left.left或者root.right有一个为空，会退化为链表