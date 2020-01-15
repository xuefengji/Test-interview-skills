# mysql数据库及性能相关

1、mysql中索引作用

加快表的查询速度

+ 什么是索引：是对数据库表中一列或多列的值进行排序的一种结构，使用索引可快速访问数据库表中的特定信息
+ 索引分类：
+ 索引创建的目的：加快检索表中数据的速度，也就是查询数据的速度
+ 索引不是越多越好：索引过多创建，会带来数据的写入的代价过高，即减慢数据写入速度

2、如何分析一条查询SQL的效率

3、MySQL的常用存储引擎有什么？区别是什么？

MyISAM引擎：

![MyISAM](./MyISAM.png)

索引工作原理：

![MyISAM索引](E:\个人文档\个人文档\个人\个人学习\测试\Test-interview-skills\MyISAM索引.png)



InnoDB引擎：

![InnoDB](./InnoDB.png)

索引工作原理：

![InnoDB索引](E:\个人文档\个人文档\个人\个人学习\测试\Test-interview-skills\InnoDB索引.png)