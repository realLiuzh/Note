# changebuffer是否总是可以提高性能

change buffer只能用于普通索引。

merge是真正进行数据更新的操作，change buffer的作用就是将记录的更新动作缓存下来。

所以在一个数据页做merge之前，change buffer记录的变更越多，收益越大。

- 对于写多读少的业务来说，比如日志类、账单类的系统。页面写完后马上访问的概率比较小，此时change buffer的效果就很好
- 如果是那种写完之后马上会做查询的业务，即使满足了条件，将更新记录在change buffer上，但由于马上要访问这个数据，会立即触发merge过程。这样随机IO的次数不会减少，反而增加了merge的代价。这里change buffer起到了副作用。