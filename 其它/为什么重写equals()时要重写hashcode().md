# 为什么重写equals()时要重写hashcode()

1. 设计hashcode()的目的是为了提高哈希容器的效率。
2. equals()是两个对象相等的充要条件，hashcode()是必要条件。
3. 重写equals()如果不重写hashcode()，可能会出现两个equals()相等的对象加入到HashSet容器中的情况。

