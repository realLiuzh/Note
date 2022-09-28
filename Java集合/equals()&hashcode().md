# equals()&hashcode()

为什么重写equals()时要重写hashcode()？

首先我们要明确：equals()用来判断对象是否相等，hashcode()的作用主要是在哈希容器中提高判断对象是否相等的效率。

为什么这么说呢？具体原因百度吧。

哈希容器判断对象是否相等的方法是，先hashcode()再equals()

如果你只重写了equals，那么有可能造成这样的情况：两个相同的自定义对象同时被放到hashset中了。这就导致了equals()相等的两个对象被放到set容器中的错误现象。

重写hashcode()时是否要重写equals()呢？我觉得没必要，因为hashcode()起到的是辅助作用。

总结：只重写equals()而不重写hashcode()会引起语义上的错误。

