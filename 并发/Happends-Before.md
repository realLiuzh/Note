# Happends-Before

JMM为程序中所有的操作定义的一种偏序关系。

如果操作B想要看到操作A的结果，那么A和B之间必须满足Happends-Before关系。否则JVM可以对它们进行任意的重排序。