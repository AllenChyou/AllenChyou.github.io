---
layout: post
title: "JavaScript权威指南 读书笔记-E"
categories: javascript
description: JavaScript权威指南读书笔记
tags: javascript
---

* content
{:toc}

全书的第一编：JavaScript语言核心

第8章：函数





### 8 函数

- 函数调用中，每次调用都有一个上下文，就是this关键字的值

- 对象的方法，调用上下文，就是对象

- js中函数即对象，可以有属性甚至方法

- 函数可以嵌套在函数中定义，这样就可以访问被定义时所处的作用域中的任何变量，也就是闭包

#### 8.1 函数定义

- 使用function来定义

- 其实还是分为有名字和匿名函数的

```
var square = function(x) { return x*x; };

data.sort(function(a,b) { return a - b; });
```

- 嵌套函数：嵌套的函数内定义的函数的作用域，可以访问外面的函数的变量

#### 8.2 函数调用

- 有4种方式来调用js函数

	- 函数调用
	- 方法
	- 构造函数
	- 通过函数的call()和apply()方法进行间接调用

##### 8.2.1 函数调用方式

- 函数表达式，函数名加上参数列表，圆括号包裹

##### 8.2.2 方法调用

- 保存在对象属性中的js函数

```
o.m = f;
o.m();
```

- 方法和函数调用的区别是，调用上下文，方法中，o称为调用上下文，函数体可以使用关键字this引用该对象

```
var calculator = {
	operand: 1,
	perand2: 1,
	add: function() {
		this.result = this.operand1 + this.operand2;
	}
};

calcuator.add();
calculator.result => 2
```

- 方法链：方法的返回值是对象的时候，可以在调用它的方法

##### 8.2.3 构造函数调用

- 函数或者方法调用钱有关键字new，就是构造函数调用。与普通的函数调用比在实参处理，调用上下文和返回值上都有不同

- 没有形参的构造函数可以省略圆括号

```
var o = new Object();
var o = new Obeject;
```

- 构造函数调用创建一个新的空对象，继承自构造函数的prototype属性；使用新的对象座位上下文，可以使用this关键字引用新的对象，所以咋new o.m()中，上下文并不是o

- 构造韩式的返回值不用写，它默认返回新对象

##### 8.2.4 间接调用

- 函数也是对象，有两个方法，call() apply()，可以间接地调用函数

- 可以显式制定调用的参数this，任何函数可以作为任何对象的方法来调用，即使这个函数不是那个对象的方法

#### 8.3 函数的实参和形参

- 函数调用不指定形参的数量，也不检查实参的类型，那怎么搞定？

##### 8.3.1 可选形参

- 如果传入的实参比形参少，剩下的就是默认为undefined，剩下的默认制定在函数内部搞定

##### 8.3.2 可变长的实参列表：实参对象

- arguments对象是一个类数组对象，可以通过它来访问实参列表

```
function f(x, y, z) {
	if (arguments.length != 3) {
		throw new Error("err");
}
// other code
}

function max(/* ... */) {
	var max = Number.NEGATIVE_INFINITY;
	for (var i = 0; i < arguments.lenghth; i++)
		if (arguments[i] > max) max = arguments[i];
	return max;
}

var largest = max(1, 10, 100, 10000); // => 10000
```

- callee caller 属性，arguments对象的另外两个属性，callee只带当前正在执行的函数，caller知道调用当前正在执行的函数的函数

##### 8.3.3 将对象属性用做实参

- 把要传入的参数列表，包装成一个对象传入，之后使用对象属性查询参数


```
function arraycopy(from, to, from_start, to_start, length){ // code}

function easycopy(args) {
	arraycopy(args.from, args.from_start, args.to, args.to_start, args.length);
}

var a = [1,2,3,4], b = [];
easycopy({ from:a, to:b, length:4 });
```

##### 8.3.4 实参类型

- js不检查，直接用，使用注释说明

- 自己在代码逻辑中检查实参类型，给出错误提示

#### 8.4 作为值的函数

- 函数不仅是一种语法也是一个值，函数可以赋值给一个变量，存储在对象的属性或者数组的元素中，作为参数传入另一个函数等

```
var s = arraycopy;
```

```
var a = [function(x) { return x*x; }, 20];
a[0](a[1]);
```

#### 8.5 作为命名空间的函数

- 函数内定义的变量，外部不可见










