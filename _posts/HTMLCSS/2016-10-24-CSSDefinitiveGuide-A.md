---
layout: post
title: "CSS权威指南 读书笔记-A"
categories: CSS
tags: CSS 读书笔记
---

* content
{:toc}

第1章：CSS和文档

第2章：选择器



### 1 CSS和文档

- 层叠样式表，Cascading Style Sheets，本身的存在依附于某种内容文档，来控制表现

#### Web的衰落 CSS作救星

- html早期很简单，人们越来越迫切想要更丰富的表现，但是导致的html本身开始混乱

- 内容与展现的分离，催生了css，单独对效果进行描述

#### 元素

- 元素是文档的基础，也就是一个html的标签，每一个元素都会生成一个box，也就是盒模型

##### 替换元素和非替换元素

- 元素和元素还是有些不同，分为替换和非替换

- 替换元素：是指替换元素内容的部分并非由文档内容直接显示，最直接的例子就是img元素，内容使用一个文件来替换，img没有具体的内容

```
<img src="howdy.gif" />
```

- 非替换元素：大多是元素都是非替换元素，内容是由用户代理显示，在本身元素的框中显示，比如span元素

```
<span>hi there</span>
```

##### 元素显示角色

- 块级元素和行内元素

![](http://ww2.sinaimg.cn/large/8d6a2535jw1f93pkc066xj20le04caao.jpg)

- 块级元素：生成一个元素框，默认会填满父元素的内容区，旁边不能有其他元素，也即是独占一行，在元素前后生成了分隔符好像，比如div和p

- 行内元素：在文本行内生成元素框，但不会打断这行文本，比如a元素，strong，em，不会独占一行

- 属性：display，

#### 结合CSS和XHTML

- 内容文档需要有一个固有结构，文档的内部结构不是视觉结构，而是结构含义的信息

- 引入css的多种方式

- link标记：关联一个文档

```
<link rel="stylesheet" type="text/css" href="sheet1.css" media="all" />
```

	- link的属性，rel代表关系，样式表，type总是css，描述加载的类型，href代表音容的URI，最后一个meida是all，要应用于所有表现媒体

- style元素直接写css

	- @import标记直接引入css文件

	```
	@import url(sheet2.css);
	```

- 内联样式，写在标签内的样式

### 2 选择器

#### 基本规则

- 每个规则有两个基本部分，选择器和声明块，声明块由一个或者多个声明组成，每一个生命更都是一个属性和值的对

![](http://ww4.sinaimg.cn/large/8d6a2535jw1f93q38jglnj20l60660tv.jpg)

#### 元素选择器

- 文档的元素就是最基本的选择器

```
html {color: balck;}
h1 {color: gray;}
h2 {color: silver;}
```

- css的声明如果出错是不会报错的，结果是不起任何效果

##### 分组

- 多个选择器应用同一个声明的情况，使用逗号分割

```
h2, p {color: gray;}
h1, h2, h3, h4, h5, h6 {color: purple;}
```

##### 通配选择器

- 显示为一个星号，这个选择器与任意元素匹配

```
* {color: red;}
```

##### 类选择器和ID选择器

- 将class属性标记为一类，应用一个css声明