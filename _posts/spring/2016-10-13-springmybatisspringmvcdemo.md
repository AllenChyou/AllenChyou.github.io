---
layout: post
title: "Spring MyBatis SpringMVC 框架基本整合"
categories: spring
excerpt: 
tags: spring mybatis springmvc webservice Java 后端
---

* content
{:toc}

Spring框架整合第三弹；
使用SSM框架搭建最基本的web service




### 基本问题

- 如何做一个最基本的 web service

- SSM框架怎么整合使用？最小集合的基本使用？

### 事前准备

- 本地的MySQL服务创建配置OK

### 具体手顺

#### 项目创建

- 使用maven进行构建，创建新项目，使用模板webapp

- 项目Github地址：[ssmdemo](https://github.com/AllenChyou/ssmdemo)

#### 数据准备

- 创建数据库表结构

    文件：src/main/resources/sql/schema.sql

#### DAO代码生成

- 使用mybatis-generator根据数据库生成代码

    文件：src/main/resources/generatorConfig.xml

- 添加生成代码用的maven插件

- 生成之后的目录结构

![](http://ww4.sinaimg.cn/large/8d6a2535gw1f8qpzx3t9ij208u0e2wfw.jpg)

#### 编辑MyBatis配置文件

- 文件：src/main/resources/mybatis-config.xml

#### 添加pom.xml中的依赖

- 文件：pom.xml

- 依赖包括mybatis相关和spring相关包

- maven-jetty-plugin插件是项目运行的web容器

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.zzj</groupId>
    <artifactId>ssmdemo</artifactId>
    <packaging>war</packaging>
    <version>1.0-SNAPSHOT</version>
    <name>ssmdemo Maven Webapp</name>
    <url>http://maven.apache.org</url>
    <properties>
        <spring.version>4.2.4.RELEASE</spring.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.4.0</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.38</version>
        </dependency>
        <!-- mybatis/spring包 -->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>1.3.0</version>
        </dependency>
        <!-- spring核心包 -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-web</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-oxm</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-tx</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context-support</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>3.1.0</version>
        </dependency>
    </dependencies>
    <build>
        <finalName>ssmdemo</finalName>
        <plugins>
            <plugin>
                <groupId>org.mybatis.generator</groupId>
                <artifactId>mybatis-generator-maven-plugin</artifactId>
                <version>1.3.5</version>
                <configuration>
                    <verbose>true</verbose>
                    <overwrite>true</overwrite>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

#### 配置web.xml文件

- 容器根据这个文件加载context文件

#### 编辑ssmdemo-dispatcher-servlet.xml文件

- 这个文件的名字是固定的，项目名称-dispatcher-servlet.xml

#### 构建UserService接口和实现

- UserService接口

- UserServiceImpl实现

#### 构建Controller

- UserController实现

### 小结

- 最最基本的SSM搭建，只是跑通了，web service起来了

- 有待完善的点

    - 只有查询方法，CRUD的添加有待完成

    - 数据交互没有JSON格式化，只是文本



