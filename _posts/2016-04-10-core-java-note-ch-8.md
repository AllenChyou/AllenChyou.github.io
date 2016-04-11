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

#### 1.实例：处理按钮点击事件

点击按钮改变背景panel的颜色，首先创建按钮，传输标签字符串或者图标，或者两个都传入，就可以构造一个button出来。

之后使用panel的add方法将button添加到panel当中。

然后帮button添加action方法。

action方法需要实现actionlistener接口。


```Java
package button;

import java.awt.Color;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class ButtonFrame extends JFrame {

	private JPanel buttonPanel;
	private static final int DEFAULT_WIDTH = 300;
	private static final int DEFAULT_HEIGHT = 200;

	public ButtonFrame() {
		setSize(DEFAULT_WIDTH, DEFAULT_HEIGHT);

		// create buttons
		JButton yellowButton = new JButton("Yellow");
		JButton blueButton = new JButton("Blue");
		JButton redButton = new JButton("Red");

		buttonPanel = new JPanel();

		// add buttons to panel
		buttonPanel.add(yellowButton);
		buttonPanel.add(blueButton);
		buttonPanel.add(redButton);

		// add panel to frame
		add(buttonPanel);

		// create button actions
		ColorAction yellowAction = new ColorAction(Color.YELLOW);
		ColorAction blueAction = new ColorAction(Color.BLUE);
		ColorAction redAction = new ColorAction(Color.RED);

		// associate actions with buttons
		yellowButton.addActionListener(yellowAction);
		blueButton.addActionListener(blueAction);
		redButton.addActionListener(redAction);
	}

	/**
	 * An action listener that sets the panel's background color.
	 */
	private class ColorAction implements ActionListener {
		private Color backgroundColor;

		public ColorAction(Color c) {
			backgroundColor = c;
		}

		public void actionPerformed(ActionEvent event) {
			buttonPanel.setBackground(backgroundColor);
		}
	}
}

```

#### 2.建议使用内部类

上面三个button对象共享了一个监听器类，但是分贝使用不同的监听器对象。

使用匿名内部类简化代码的话，注意，其实每一个button的处理过程都是一样的

1. 用标签字符串构造按钮

2. 将按钮添加到panel上

3. 用对应颜色构造一个ActionListener

4. 添加ActionListener

可以使用辅助的方法实现

```Java
public void makeButton(String name, Color backgroundColor){
	JButton button = new JButton(name);
	buttonPanel.add(button);
	ColorAction action = ColorAction(backgroundColor);
	button.addActionListener(action);
}
```

之后就可以简化调用

```Java
makeButton("Yellow", Color.Yellow);
makeButton("Blue", Color.Blue);
makeButton("Red", Color.RED);
```

然后可以进一步简化，ColorAction类只是在makeButton方法是使用一次，所以可以用匿名类实现。

```Java
public void makeButton(String name, Color backgroundColor){
	JButton button = new JButton(name);
	buttonPanel.add(button);
	button.addActionListener(new ActionListener(){
		public void actionPerformed(ActionEvent event){
			buttonPanel.setBackground(backgroundColor);
		}
	});
}
```

如果实在不喜欢内部类，也可以实现将自己的容器称为监听器，实现ActionListener的接口。

```Java
yellowButton.addActionListener(this);
blueButton.addActionListener(this);
redButton.addActionListener(this);
```

这样做的话就要根据不同的事件来源分配代码，显得有些杂乱。

### 动作

### 鼠标事件

### AWT事件继承层次
