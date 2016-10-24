---
layout: post
title: "JavaScript权威指南 读书笔记-I"
categories: javascript
description: JavaScript权威指南读书笔记
tags: javascript 
---

* content
{:toc}

全书的第二编：客户端JavaScript

第14章：WIndow对象





### 14 Window对象

- js客户端的全局对象，Window对象有哪些属性和方法？有些什么api

#### 14.1 计时器

- setTimeout和setInterval用来注册指定时间之后单词或者重复调用的函数

- setTimeout会返回一个值，这个值可以传递给clearTimeout用于取消这个函数的运行

![](http://ww2.sinaimg.cn/large/8d6a2535gw1f93hmg8ytfj20j40efwhi.jpg)

#### 14.2 浏览器定位和导航

- window的属性localtion是Location对象，表示窗口当前的URL

##### 14.2.1 解析URL

- location对象的属性有很多关于url的信息，可以使用来提取

##### 14.2.2 载入新的文档

- 最直接的就是改变loaction属性的值，或者使用assign方法

```
location = "http://www.baidu.com";
location.assign("http://www.baidu.com");
```

#### 14.3 浏览历史

- window对象的history属性，把窗口的浏览历史文档和文档状态列表的形式表示

- back，forward方法表示前进和后退

```
history.back();
history.forward();
```

- go方法可以接受一个整数参数，表示前进和后退多少页

- 流行框架中一般都有历史管理的功能，比如jQuery的history插件

#### 14.4 浏览器和屏幕信息

- 脚本获取浏览器和所在的桌面信息，window对象的navigator和screen属性

##### 14.4.1 Navigator对象

- navigator表示浏览器本身的信息等等

##### 14.4.2 Scren对象

- 有关窗口显示的大小和可用的颜色数量的信息

#### 14.5 对话框

- window对象提供3个方法来显示简单的对话框，alert显示消息并提示关闭，confirm要求点击确定还是取消，并返回布尔值，prompt等待用户输入字符串，并返回字符串

- 更复杂的对话框，showModalDialog在浏览器中显示一个模态窗口

![](http://ww1.sinaimg.cn/large/8d6a2535gw1f93icpp1dgj20jv083wfs.jpg)

