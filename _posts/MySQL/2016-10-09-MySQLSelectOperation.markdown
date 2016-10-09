---
layout: post
title: MySQL表查询操作
categories: MySQL
description: MySQL查询表中内容的操作
tags: MySQL
---

* content
{:toc}

# SQL查询语句


## 查询数据（从数据库中获取需要的数据）


#### 查询语句的基本语法

使用SELECT进行基本查询

```
SELECT 属性列表 FROM 表名字和视图列表
  [WHERE 条件表达式1]
  [GROUP BY 属性名1 [HAVING 条件表达式2]]
  [ORDER BY 属性名2 [ASC|DESC]]
```
属性列表表示需要查询的字段名字，表和视图是指定查询的地方，可以有多个。条件表达式1表示查询的条件；
属性名1表示按照这个字段进行分组；条件表达式2表示满足条件的数据才能输出；
属性名2表示根据这个字段进行查询；后面的是排序方式，升序降序；

- EX: 省略后面的条件之类的就会默认输出全部数据

```
SELECT num,name,age,sex,homeaddr FROM employee;
```
- EX: 包含条件和排序的查询

```
SELECT num,d_id,name,age,sex,homeaddr
  FROM employee
  WHERE age<26
  ORDER BY d_id DESC;
```

#### 在单表上查询数据

- 查询所有字段

使用 \* 查询所有字段

```
SELECT * FROM employee;
```


- 查询指定字段

```SQL
SELECT num,name,sex,homeaddr FROM employee;
```
将会显示的就是指定字段的数据，并且按照字段顺序出现，只要改变字段顺序就可以改变显示顺序。

- 查询指定的行

指定查询的筛选条件WHERE

```SQL
SELECT * FROM employee WHERE d_id=1001;
```


###### 查询条件
@. 比较运算符号，等于；大于小于；不等于；大于等于，小于等于；不大于，不小于；

@. 指定范围， BETWEEN AND, NOT BETWEEN AND

为查询指定取值的范围

```SQL
SELECT * FROM employee WHERE age BETWEEN 15 AND 25;
SELECT * FROM employee WHERE age NOT BETWEEN 15 AND 25;
```
@. 指定集合， IN, NOT IN

```SQL
SELECT * FROM employee WHERE d_id IN( 1001, 1004 );
SELECT * FROM employee WHERE name NOT IN( '张三', '李四' );
```

@. 匹配字符， LIKE, NOT LIKE

匹配字符串的语法规则： [NOT] LIKE '字符串'

字符串可以使用单引号包含或者双引号包含，可以使完整的字符串也可以包含百分号或者下划线作为通配符

% 可以匹配任意长度的字符串
_ 表示单个字符

```SQL
SELECT * FROM employee WHERE name LIKE 'Aric';
SELECT * FROM employee WHERE hoemaddr LIKE '北京%';
SELECT * FROM employee WHERE name LIKE 'Ar_c';
SELECT * FROM employee WHERE name NOT LIKE 'Aric';
```

在字符串中没有通配符存在的情况下，LIKE可以使用等于号=来替换。

@. 是否为空值， IS NULL, IS NOT NULL

```SQL
SELECT * FROM work WHERE info IS NULL;
SELECT * FROM work WHERE info IS NOT NULL;
```
这里的IS和IS NOT是一个整体，不可以使用等于和不等于来替换。

- 多条件查询 AND, OR

AND连接多个需要同时满足的条件

```SQL
SELECT * FROM employee WHERE
  d_id=1001 AND sex LIKE '男';
SELECT * FROM employee WHERE
  d_id=1001 AND age<26 AND sex LIKE '男';
```
OR连接只需要满足其中一个条件的状况

```SQL
SELECT * FROM employee WHERE
  d_id=1001 OR sex LIKE '男';
SELECT * FROM employee WHERE
  num IN (1,2,3) OR age BETWEEN 24 AND 25
  OR homeaddr LIKE '北京％';
```

- 查询结果不重复

没有设定UNIQUE约束的字段，有可能会出现重复的情况，在语句中可以使用DISTINCT来消除重复的状况
```SQL
SELECT DISTINCT 属性名字 FROM 表名字;
SELECT DISTINCT d_id FROM employee;
```

- 给查询结果排序

升序的结果排序和降序结果排序
```SQL
SELECT * FROM employee ORDER BY age ASC;
SELECT * FROM employee ORDER BY age DESC;
```

- 分组查询

分组查询的语法

```SQL
GROUP BY 属性名字 [HAVING 条件表达式][WITH ROLLUP]
```
GROUP BY [详细用法](http://allenchyou.github.io/jekyll/update/2016/03/27/welcome-to-jekyll.html)


- 用LIMIT限制查询结果

#### 使用聚合函数查询数据


#### 多表上联合查询 连接查询


#### 子查询


#### 合并查询结果


#### 为表和字段取别名


#### 使用正则表达式查询
