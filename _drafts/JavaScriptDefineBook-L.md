---
layout: post
title: "JavaScript权威指南 读书笔记-L"
categories: javascript
description: JavaScript权威指南读书笔记
tags: javascript
---

* content
{:toc}

全书的第二编：客户端JavaScript

第19章：jQuery类库





### 19 jQuery类库

主要是由于浏览器之间严重的不兼容性，导致客户端的API复杂得很，js必须使用框架和类库，简化操作，隐藏差异，于是出现了jQuery

**jQuery能做什么**

在文档中轻松找到想要的元素并且操作，添加内容，编辑属性和css样式，定义事件处理程序，执行动画。

方法会尽可能返回对象本身，这样子链式调用就可以了

#### 19.1 jQuery基础

全局方法jquery()，这个方法使用太频繁，有个别名就是美元符号$，这是核心查询方法

```
var divs = $("div");
```

##### 19.1.1 jQuery()函数

##### 19.1.2 查询与查询结果

#### 19.2 jQuery的getter和setter

##### 19.2.1 获取和设置HTML属性

```
$("form").attr("action");
```

##### 19.2.2 获取和设置CSS属性

```
$("h1").css("font-weight");
```

##### 19.2.3 获取和设置CSS类

```
$("h1").addClass("h1lite");
```

##### 19.2.4 获取和设置HTML表单值

##### 19.2.5 设置和获取元素内容

##### 19.2.6 获取和设置元素的位置高宽

##### 19.2.7 获取和设置元素数据

#### 19.3 修改文档结构

html()和text()方法可以用来设置元素内容

##### 19.3.1 插入和替换元素

![](http://ww4.sinaimg.cn/large/8d6a2535gw1f9clitmg3aj20m8066gmt.jpg)

##### 19.3.2 复制元素

##### 19.3.3 包装元素

##### 19.3.4 删除元素

#### 19.4 使用jQuery处理事件

##### 19.4.1 事件处理程序的简单注册

简单的事件注册方法，可用于常用的每一一个浏览器事件，比如给单价注册一个事件处理程序

```
$("p").click(function() { $(this).css("background-color", "gray"); });
```

下面是jQuery定义的简单事件处理程序注册的方法

![](http://ww4.sinaimg.cn/large/8d6a2535gw1f9cln9u25pj20g503rgm6.jpg)

##### 19.4.2 jQuery事件处理程序

##### 19.4.3 jQuery事件对象

通过定义自己的Event对象来隐藏浏览器之间的实现差异

对象的属性和方法

![](http://ww4.sinaimg.cn/large/8d6a2535gw1f9clpe2yxlj20hj04hgm7.jpg)

![](http://ww1.sinaimg.cn/large/8d6a2535gw1f9clq020fkj20hg01kdft.jpg)

![](http://ww3.sinaimg.cn/large/8d6a2535gw1f9clqbbgccj20g501xmxe.jpg)

##### 19.4.4 事件处理程序的高级注册

使用bind方法来为命名的事件类型绑定处理程序

```
$('p').bind('click', f);
```


##### 19.4.5 注销事件处理程序

bind来绑定之后，可以使用unbind来解绑

##### 19.4.6 触发事件

##### 19.4.7 自定义事件

##### 19.4.8 实时事件

#### 19.5 动画效果

##### 19.5.1 简单动画

fadeIn，fadeOut，fadeTo

show，hide，toggle

slideDown，slideUp，slideToggle

##### 19.5.2 自定义动画

##### 19.5.3 动画的取消，延迟和队列

#### 19.6 jQuery中的Ajax

##### 19.6.1 load()方法
 load是jQuery中最简单的，传入一个url，异步加载url的内容，然后将内容插入元素中，替换原有内容

 ```
setInterval(function() { $('status').load("status_report.html"); }, 60000);
 ```

##### 19.6.2 Ajax工具函数

 - jQuery.getScript() 异步加载js文件，执行完成后调用
 - jQuery.getJson() 获取文本，然后特殊处理一下

##### 19.6.3 jQuery.ajax()函数

所有的ajax工具最后都会调用ajax函数，这是整个类库中最复杂的函数

```
jQuery.ajax({
  type: "GET",
  url: url,
  data: null,
  dataType: "script",
  success: callback
  });
```

##### 19.6.4 Ajax事件

#### 19.7 工具函数

jQuery.browser 提供浏览器相关的信息

jQuery.contains()

#### 19.8 jQuery选择器和选取方法

##### 19.8.1 jQuery选择器

##### 19.8.2 选取方法

#### 19.9 jQuery的插件扩展

#### 19.10 jQuery UI类库

### 20 客户端存储

存储形式：

- Web存储，H5的API
- cookie
- IE user data
- 离线Web应用
- Web数据库
- 文件西戎

#### 20.1 localStorage和sessionStorage

##### 20.1.1 存储有效期和作用域

##### 20.1.2 存储API

##### 20.1.3 存储事件

#### 20.2 cookie

##### 20.2.1 cookie属性：有效期和作用域

##### 20.2.2 保存cookie

##### 20.2.3 读取cookie

##### 20.2.4 cookie的局限性

##### 20.2.5 cookie相关的存储

#### 20.3 利用IE userData持久化数据

#### 20.4 应用程序存储和离线Web应用

##### 20.4.1 应用程序缓存清单

##### 20.4.2 缓存的更新

##### 20.4.3 离线Web应用

### 21 多媒体和图形编程

使用js来操作图片，控制音频和视频流以及画图
