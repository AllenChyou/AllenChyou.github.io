---
layout: post
title: MySQL表基本操作
categories: MySQL
description: MySQL表层面的操作
tags: MySQL
---

* content
{:toc}

## MySQL数据表基本操作
表是数据库存储数据的基本单位，一个表包含若干字段。表操作包括表的创建，修改和删除


### 创建表的方法
创建表的语法

```SQL
CREATE TABLE 表名字 ( 属性名字 数据类型 [完整性约束条件],
  属性名字 数据类型 [完整性约束条件],
  ...
  );
```
  表名字是表的名称，属性名是表中的字段名称，完整性约束条件是字段的某些约束。

EX: CREATE TABLE example0( id INT, name VARCHAR(20), sex BOOLEAN);

### 表的完整性约束条件
- 主键 PRIMARY KEY 是表的一个特殊字段，表中的每一条信息进行唯一标识。
- 外键 FOREIGN KEY 表的一个特殊字段，是其他某一张表的主键。
- 非空约束 NOT NULL 属性不能为空的约束。
- UNIQUE 表示这个字段是唯一的。
- AUTO_INCREMENT 属性自动增加
- DEFAULT 设定属性的默认值

### 查看表结构的方法
语法: DESCRIBE 表名字;

可以使用缩写 DESC

查看表的详细结构的方法 $ SHOW CREATE TABLE 表名字;
   看到的是详细的创建表语句的信息。


### 修改表的方法


- 修改表名字 $ ALTER TABLE 原来的表名字 RENAME [TO] 新的表名字;
- 修改表中字段的类型 $ ALTER TABLE 表名字 MODIFY 字段名字 新的类型;
- 修改字段名字和字段类型 $ ALTER TABLE 表名字 CHANGE 旧的字段名字 新的字段名字 新的字段数据类型;
- 增加字段

```SQL
$ ALTER TABLE 表名字 ADD 属性名字 数据类型 [完整性约束条件] [FIRST| AFTER 属性名字];
```
其中前面的属性名字是新增加的字段，后面的属性名字表示要插入的位置，FIRST表示增加到最前面，AFTER表示增加到那个属性的后面，默认来讲是增加到所有字段的最后。

- 删除字段 $ ALTER TABLE 表名字 DROP 属性名字;
- 修改字段的排列

```SQL
$ ALTER TABLE 表名字 MODIFY 属性名字1 数据类型 FIRST|AFTER 属性名字2;
```

### 删除表的方法
- 删除没有被关联的普通表 $ DROP TABLE 表名字;
- 被其他表所关联的父表没有那么好删除，需要在其他表中删除外键才能顺利删除。

temp ended 有关索引，触发器，视图等概念，之后再来补足
