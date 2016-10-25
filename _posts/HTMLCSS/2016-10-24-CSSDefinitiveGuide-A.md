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

- 类选择器和ID选择器都是需要在文档中事先作出构想和计划的，事先的布局，文档的配置，然后是选择OK

- **类选择器**的前提条件是，标签的class属性指定，然后定义样式

```
*.warning {font-weight: bold;}
```

- 这个样式会应用到所有class属性为warning的标签中

- 如果只是希望段落标签 p 中的类被选择应用，可以这样写样式

```
p.warning {font-weight: bold;}
```

- 逻辑上是并且的关系，是某个标签并且class的属性是warning

```
p.warning {font-weight: bold;}
span.warning {font-style: italic;}
```

- **多类选择器**：class属性可以包含一个列表，使用空格分割，多个词出现的顺序不要紧

- 样式中可以设定同时包含几个class同事存在才生效的声明

```
.warning {font-weight: bold;}
.urgent {font-style: italic;}
.warning.urgent {background: silver;}
```

- 结合标签选择和多类选择，同时存在才会生效，只有class中由warning又有help的p元素才会生效

```
p.warning.help {background: red;}
```

- **ID选择器**，类似于类选择器，id样式前面是井号，不是点

```
*#first-para {font-weight: bold;}
```

- 元素中的id属性配置为first-para之后，样式就会生效，忽略通配选择器星号，也能正常工作

- **类选择器还是ID选择器？**

	class可以应用到多个元素，但是id只可以有一个元素被应用，id的值在文档中必须是唯一的；

	id选择器不能像类选择器一样，列表使用，只能有一个值

	id和元素标签是无关的，具体演示会应用到什么元素上，无法确定

#### 属性选择器

	根据元素的属性及属性值来选择元素，有4种类型的属性选择器

- 简单属性选择

- 希望选择有某个属性的元素，不论这个属性的值是什么，只要标签中有这个属性，就会应用样式

```
h1[class] {color: silver;}
p[title] {color: gray;}
```

加上通配符进行组合，应用到所有有该属性的标签上

```
*[title] {font-weight: bold;}
```

类似于多类选择，可以指定多个属性同时存在的情况下才应用样式，a 标签需要同时有，href和title属性的标签应用样式

```
a[href][title] {font-weight: bold;}
```

- 根据具体属性值选择

根据具体属性值，可以缩小选择范围，只选择有特定属性值的元素，只选择某一个特定的链接的a标签

```
a[href="www.baidu.com"] { font-weight: bold;}
```

也可以类似多类选择器的情况

```
a[href="http://badu.com"][titile="W3C Home"] {font-size: 200%;}
```

- 根据部分属性值选择

词列表的情况，空格分割，可以根据任意一个词进行选择，比如class属性，接受一个或者多个词座位属性值，这种情况下，想要选择包含warning的元素

```
p[class~="warning"] {font-weight: bold;}
```

选择器中的波浪号，表示可以选择一个，如果没有波浪号就需要完全值匹配

这个方式不仅可以用于class，也可以适用于任何属性，只要是空格分割的词列表，就可以使用

部分属性选择器的规范说法是子串匹配属性选择器

![](http://ww2.sinaimg.cn/large/8d6a2535jw1f94vvdlcwtj20l704x3zb.jpg)

基本适用于任何属性的值筛选

```
img[src*="space"] {border: 5px solid red;}
```

- 特定属性类的选择器

```
*[lang|="en"] {color: white;}
```

将会匹配所有en或者en-开头的元素，这种选择器可以用于任何属性值，最常见的是匹配语言值

#### 使用文档结构

理解父子关系，理解选择器和文档之间的关系，需要再次分析文档的结构

