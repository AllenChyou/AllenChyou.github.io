---
layout: post
title: "JavaScript权威指南 读书笔记-K"
categories: javascript
description: JavaScript权威指南读书笔记
tags: javascript 
---

* content
{:toc}

全书的第二编：客户端JavaScript

第17章：事件处理





### 17 事件处理

客户端js是异步事件驱动编程模型，程序的驱动有时候是依赖某些事件的发生，比如文档加载完成，点击鼠标等。如果关注某种特定类型的时间，就可以注册事件发生要调用的函数，基本上所有的UI程序都是这个模型

事件类型，是一个说明发生了什么的字符串，比如mousemove，keydown，load，用这个字符串来标识所谈论的特定类型的事件

事件目标是发生的事件与之相关的对象，一个时间，肯定有相关的类型和目标，比如window上的load事件和button的click事件，在客户端js中window，document和element是最常见的事件目标

**事件处理程序**，event handler，或者说**事件监听程序**，event listener 是处理或相应事件的函数

事件发生时候，对象上注册的事件处理程序被调用的时候，会说浏览器触发或者派发了事件

**事件对象**，最为参数传递给事件处理函数，都会有包含type属性和target属性

**事件传播**，是浏览器决定那个对象触发其事件处理程序的过程，类似的概念是事件捕获

**事件类型**，各种各样的事件

#### 17.1 事件类型

web初期的事件已经有很好的支持了，新的事件api定义来源有3个，w3c的新标准草案，H5规范产生的新事件，移动端的发展带来的新事件

**事件分类**

1. 依赖于设备的输入事件，比如鼠标和键盘，mousedown，mousemove，mouseup，keydown，keypress，touchmove，gesturerechange

2. 独立于设备的输入事件，没有直接相关的输入设备，click事件，textinput

3. 用户界面事件，较高级的事件，通常出现在定义web应用UI的html表单元素上，文本输入获取键盘焦点的focus事件，用户改变表单元素显示的嫦娥事件，单机表单中提交按钮的submit事件

4. 状态变化事件，有些时间不是用户触发，而是网络或者浏览器触发，表示某种状态的变化，比如文档加载完成的load事件，还有I/O的异步通知

5. 特定API事件，拖放的事件dragstart，dragenter，dragover，drop，H5的video和audio元素有很多事件来控制音视频播放

6. 计时器和错误处理程序

##### 17.1.1 传统事件类型

很多老API都是常用并且广泛被支持的

- 表单相关事件，submit，reset，文本域change的事件等等

- window事件，浏览器窗口本身触发的事件，而不是文档元素触发的

- 鼠标事件，在文档上移动或者单击鼠标都会产生鼠标事件

- 键盘事件，按下或者释放键盘按键都会产生事件

##### 17.1.2 DOM事件

DOM Level 3 Events，W3C的规范

##### 17.1.3 HTML5事件

HTML5加入的新元素，audio和video元素，都有很长的事件列表

拖放API，历史管理机制，表单的重新定义，离线的web应用支持

##### 17.1.4 触摸屏和移动设备事件

一般来讲使用的是和传统事件的映射，比如点击，但是有些比较特殊，比如旋转设备，手势事件等，在iPad和iphone的safari上有所实现

