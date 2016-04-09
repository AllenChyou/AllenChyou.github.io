---
layout: post
title: Core Java读书笔记-Chapter 5 继承
categories: Java
description: Java核心技术第一卷，第五章 继承-读书笔记
keywords: Java
---

继承（inheriteance），可以基于已存在的类构造一个新类，复用已存在的类的方法和域。也可以添加一些新的方法和域。

反射（reflection），是指在程序运行期间发现更多的类及其属性的能力。主要是开发软件工具的喜欢这个特性。

### 类，超类和子类

定义新的类Manager，重用Employee中的代码，所有的域都保留下来。

```Java
class Manager extends Employee{
	添加方法和域
}
```

超类，基类，父类。子类，派生类，孩子类；

在扩展超类，定义子类的时候，只是需要说明不同的，或者增量的地方。

覆盖：实现Manager的getSalary方法。返回工资和奖金的和；

```Java
public double getSalary(){
	return salary + bonus;
}
```

但是manager的getSalary方法并不能访问Employee的私有域。想访问就一定要走方法。而且是父类的方法被指定调用才可以。

```Java
public double getSalary(){
	double baseSalary = super.getSalary();
	return baseSalary + bonus;
}
```

多态：一个对象变量可以指示多种实际类型的现象；

动态绑定：在运行时可以自动地选择调用那个方法的现象；

#### 1.继承层次

一个公有类派生出来的所有类的集合被称为继承层次；

从某个特定的类到其祖先的路径被称为该类的继承链；

#### 2.多态

是否应该使用继承，is-a原则，子类的每个对象也是超类的对象。每一个经理都是雇员。

is-a规则的另一种表述：置换法则，在程序中出现超类对象的任何地方都可以使用子类对象替换。

```Java
Employee e;
e = new Employee();
e = new Manager();
```

#### 3.动态绑定

调用对象方法的执行过程；

第一步：编译器查看对象的声明类型和方法名；

第二步：编译器查看调用方法时提供的参数类型；在多个名字一样但是参数不同的方法中选一个，这个过程叫做重载解析。

第三步，如果是private，static，final的方法，编译器可以准确知道调用哪个。叫做静态绑定。与此对应，是方法依赖于隐式参数的实际类型，并在运行时决定的动态绑定。

第四步，程序运行的时候，找一个签名的方法，子类里面找到了就用，没找到就到父类里面找。

动态绑定的重要特性，无需对现存的代码进行修改，就可以对程序进行扩展。

#### 4.阻止继承：final类和方法

不允许扩展的类称为final类，在class前面使用final就可以，别的类就不能继承

```Java
final class Executive extends Manager{}
```

这个Executive类就不允许别的类去扩展了。

类中的方法也可以指定成final。子类就不能覆盖这个方法（final类中的方法自动称为final方法）

```Java
class Employee{
	public final String getName()
	{}
}
```

#### 5.强制类型转换

第一，只能在继承层次内部进行类型转换

第二，在将超类转换成子类之前，应该使用instanceof进行检查。

#### 6.抽象类

包含一个或者多个抽象方法的类本身必须被声明为抽象的

```Java
abstract class Person{
	public abstract String getDescription();
}
```

抽象类不能被实例化，可以定义一个抽象类的对象变量，但是只能引用非抽象子类的对象。

#### 7.受保护访问

域标记为private，方法标记为public，声明为私有的东西其他类是不可见的。包括子类对超类的private域也是不能访问的。

如果Employee中的域hireDay设置成protected，而不是private，那么Manager中的方法就可以直接访问hireDay；

Java控制可见性的4个访问操作符：

private--仅对本类可见；

public--对所有类可见；

protected--对本包和所有子类可见；

默认，没有修饰符，对本包可见；

### Object：所有类的超类

Object类默认是所有类的超类。

#### 1.equals方法

检测一个对象是不是等于另一个对象；

第一要符合两个对象是不是引用相等，还要看对象内部的状态是不是相等；

两个对象还要是同一个类的才有可能相等；

```Java
class Employee{
	...
	public boolean equals(Object otherObject){
		if (this == otherObject) return true;

		if (otherObject == null) return false;

		if (getClass() != otherObject.getClass())
			return false;

		Employee other = (Employee)otherObject;

		return name.equals(other.name)
			&& salary == other.salary
			&& hireDay.equals(other.hireDay);
	}
}
```


#### 2.相等测试与继承

Java语言规范要求equals方法需要符合的原则：

自反性：对于任意非空的x，x.equals(x)应该返回true；

对称性：对于任意的引用X和Y，当且仅当x.equals(y)返回true时候，y.equals(x)返回true。

传递性：xyz，当x.equals(y)为true，且y.equals(z)为true的时候，x.equals(z)也要为true。

一致性：如果x和y没有发生变化，那么反复调用x.equals(y)的结果应该一直是一致的。

对于任意非空引用x，x.equals(null)应该是false。

##### 如何写一个完美的equals方法

1-显式参数命名为otherObject，稍后需要转换为另一个叫做other的变量。

2-检测this和otherObject是不是同一个对象。

```Java
if(this == otherObject) return true;
```

3-检测otherObject是不是为null，如果为null就返回false

```Java
if(otherObject == null) return false;
```

4-比较this和otherObject是不是同一个类的

```Java
if(getClass() != otherObject.getClass()) return false;
```

5-将otherObject转换为相应类型的对象

```Java
ClassName other = (ClassName)otherObject;
```

6-现在开始对所有的域进行比较，基本类型使用==，对象使用equals如果所有的域都匹配就返回true

```Java
return field1 == other.field1
	&& Objects.equals(field2, other.field2)
	&& ...;
```

如果在子类中重新定义了equals，要调用super的equals；

Tips：对于数组类型的域，使用静态方法Array.equals进行检测

#### 3.hashCode方法

散列码hashCode是由对象导出的一个整型值。String类通过自己的方式计算hashCode

```Java
int hash = 0;
for (int i = 0; i < length(); i++)
	hash = 31 * hash + cahrAt(i);
```

String的hashCode是自己的内容导出的，所以String得内容相同，hashCode就相同，对象的hashCode是对象地址导出的，Object默认的是用对象地址。不覆盖Object的方法就是默认的。

自己定义的hashCode方法，最好使用null安全的方式，如果参数null，hashcode会返回0。

```Java
class Employee{
	public int hashCode(){
		return 7 * Objects.hashCode(name)
		+ 11 * new Double(salary).hashCode()
		+ 13 * Objects.hashCode(hireDay);
	}
}
```

组合多个散列值的时候可以调用Objects的另一个组合方法。各自调用相应的hashCode，组合成一个int。

```Java
public int hashCode(){
	return Objects.hash(name, salary, hireDay);
}
```

如果存在数组形态的域，那就调用Array的静态方法。

#### 4.toString方法

toString()返回表示对象值的字符串，默认的实现，比如String，就是类名加上一个个的域的字符串。

最好不要硬写类型名字，可以使用getClass().getName()获得类名的字符串。

### 泛型数组列表

C语言里面必须在编译时就确定数组的大小，Java里面允许在运行时确定数组的大小。

```Java
int actualSize=...;
Employee[] staff = new Employee[actualSize];
```

在运行时候动态改变数组的大小要使用ArrayList类。这个是使用类型参数的泛型类。尖括号里面的就是类型参数。

在ArrayList里面可以动态的添加删除对象。

```Java
ArrayList<Employee> staff = new ArrayList<Employee>();
staff.add(new Employee("Harry",...));
sraff.add(new Employee("Tony",...));
```


### 对象包装器和自动装箱

### 参数变量可变的方法

### 枚举类

### 反射

### 继承设计的技巧
