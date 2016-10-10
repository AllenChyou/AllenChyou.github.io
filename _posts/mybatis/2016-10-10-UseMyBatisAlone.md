---
layout: post
title: "MyBatis单独使用TestDemo"
categories: mybatis
description: 不整合Spring的MyBatis使用
tags: mybatis Java MySQL ORM
---

* content
{:toc}


### 事前准备

- MySQL数据库配置OK

- 数据库逆向生成ORM代码OK

### 准备数据

- 新建sql文件保存数据库的结构

```
-- ----------------------------
-- file: schema.sql
-- ----------------------------
DROP DATABASE IF EXISTS `zzj_users`;
CREATE DATABASE  IF NOT EXISTS `zzj_users` /*!40100 DEFAULT CHARACTER SET utf8 */;
USE `zzj_users`;
SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for user
-- ----------------------------
DROP TABLE IF EXISTS `user`;
CREATE TABLE `user` (
  `user_id` int(11) unsigned NOT NULL COMMENT '用户ID',
  `user_name` varchar(32) NOT NULL DEFAULT '' COMMENT '用户名称',
  PRIMARY KEY (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

### 