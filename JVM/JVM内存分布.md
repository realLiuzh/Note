# JVM内存分布

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2388408/1664181955617-5b2d6bc6-ebe7-4c7b-8013-7673c03ac7f4.png)

# 方法区

- 方法区是线程共享的。
- jdk1.8之前方法区由永久代实现，使用的是JVM内存；jdk1.8及以后方法区由元数据区实现，使用的是本地内存。
- 方法区中存储了：类型信息、静态变量、属性信息、方法信息和运行时常量池。

# 堆

- 堆的内部结构划分（方法区在逻辑上被认为是堆的一部分）：![img](https://cdn.nlark.com/yuque/0/2022/png/2388408/1664185642486-8355be69-e381-4651-85a5-360d2d49daff.png)

  
