# HashMap并发问题1.7

1.7下的HashMap会有数据错乱和扩容死链的问题。

数据错乱和1.8同理

扩容死链的原因是1.7头插法，发生在两个线程对HashMap扩容时。

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1664633215132-4969990d-2c03-4bf3-960d-76088ee444b0.png?x-oss-process=image%2Fresize%2Cw_647%2Climit_0)

抽象派.....