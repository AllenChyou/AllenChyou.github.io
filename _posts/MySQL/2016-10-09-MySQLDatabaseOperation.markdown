---
layout: post
title: MySQL数据库DB基本操作
categories: MySQL
description: MySQL数据库层面的操作
tags: MySQL
---

* content
{:toc}

## MySQL数据库基本操作

### 操作数据库（数据库的创建与删除，显示现存的数据库）

创建数据库SQL语句 $ CREATE DATABASE [数据库名字];

显示已经存在的数据库名字列表 $ SHOW DATABASES;

删除已经存在的数据库 $DROP DATABASE [数据库名字];

### 数据库存储引擎

存储引擎是MySQL的特点，决定数据库中的表用不同的方式来存储

显示所有的存储引擎 $ SHOW ENGINES;
