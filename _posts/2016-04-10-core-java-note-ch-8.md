---
layout: post
title: Core Java读书笔记-Chapter 8 事件处理
categories: Java
description: Java核心技术第一卷读书笔记
keywords: Java
---

实现用户界面，必须明白Java事件处理的基本方法。接下去是，Java AWT事件模型的工作机制，从中看到如何捕获用户界面组件和输入设备产生的事件。还有如何更加结构化的方式处理动作，actions，事件。

### 事件处理基础

任何支持GUI的操作环境都要不断监视按键或者鼠标点击这样的事件。

事件过程，也就是事件和代码之间的对应关系，对相关的事件编写特定的代码。

事件源，event source，到事件监听器，event listener。事件委托模型，event delegation model。

面向对象，将事件相关的信息封装在事件对象，event object。

AWT事件处理机制概要：

* 监听器对象是一个实现了特定监听器接口，listener interface的类的实例

* 事件源是一个能够注册监听器对象并发送事件对象的对象

* 当事件发生时，事件源将事件对象传递给所有注册的监听器

* 监听器对象将利用事件对象中的信息决定如何对事件作出响应

监听器的实例

```Java
ActionListener listner = ...;
JButton button = new JButton("OK");
button.addActionListener(listener);
```

现在只要产生一个动作事件，事件监听器就会收到通告，按钮的话，那就是点击到了。

```Java	
class MyListener implements ActionListener {
	...
	public void actionPerformer(ActionEvent event){
		...
	}
}
```

#### 实例：处理按钮点击事件





### 动作

### 鼠标事件

### AWT事件继承层次
