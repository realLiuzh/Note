# MySQL三大范式

简介：范式是数据库设计所要求的设计规范。满足范式可以减少数据的冗余度，增强数据的一致性。

# 1NF

数据库表中的每一列都是不可分割的基本数据项。

# 2NF

满足1NF，每一条记录的非主属性完全依赖于候选键。

候选键：能够唯一标识出一条数据的一个属性或者最小属性组。

主键：从候选键中选出一个作为主键

主属性：候选码中的一个属性

例如，在选课关系表(学号，课程号，成绩，学分)，关键字为组合关键字(学号，课程号)，但由于非主属性学分仅依赖于课程号，对关键字(学号，课程号)只是部分依赖，而不是完全依赖，因此此种方式会导致数据冗余以及更新异常等问题。

# 3NF

满足2NF，非主属性不存在传递依赖关系。

| 学号（主键） | 姓名 | 性别 | 年级 | 专业             | 班主任姓名 | 班主任性别 | 班主任年龄 |
| ------------ | ---- | ---- | ---- | ---------------- | ---------- | ---------- | ---------- |
| 202001       | 张三 | 男   | 大一 | 计算机科学与技术 | 老张       | 男         | 33         |
| 202002       | 李四 | 男   | 大二 | 网络工程         | 老李       | 男         | 34         |
| 202003       | 王舞 | 女   | 大三 | 软件工程         | 老王       | 男         | 35         |

例如，在上表中，班主任姓名依赖于班主任姓名，班主任姓名依赖于主键。