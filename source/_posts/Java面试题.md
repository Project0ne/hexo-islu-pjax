---
title: Java面试题
author: 闲花手札
img: 'https://images.islu.cn/article/mianshiti.jpeg'
top: false
toc: true
mathjax: false
categories: 后端面试题
tags:
  - JAVA面试题
  - 面试题
keywords: JAVA,JSP,面试题,Java面试题,面向对象,String,Integer,&,List,Vector,HashMap,Hashtable
essay: false
summary: Java面试题
abbrlink: 60410
date: 2021-05-09 22:57:44
---

# Java面试题

## 面向对象的特征有哪些方面

### 抽象

抽象就是忽略一个主题中与当前目标无关的那些方面，以便更充分地注意与当前目标有关的方面。抽象并不打算了解全部问题，而只是选择其中的一部分，暂时不用部分细节。

> 抽象包括两个方面
>
> 1. 过程抽象
> 2. 数据抽象

### 继承

继承是一种联结类的层次模型，并且允许和鼓励类的重用，它提供了一种明确表述共性的方法。对象的一个新类可以从现有的类中派生，这个过程称为类继承。新类继承了原始类的特性，新类成为原始类的派生类（子类），而原始类成为新类的积累（父类）。派生类可以从它的基类那里继承方法和实例变量，并且类可以修改或增加新的方法使之更适合特殊需要。

### 封装

封装是把过程和数据包围起来，对数据的访问只能通过已定义的界面。面向对象计算始于这个基本概念，即现实世界可以被描绘成一系列完全自治、封装的对象，这些对象通过一个受保护的接口访问其它对象。

### 多态

多态性是指允许不同类的对象对同一消息作出响应。多态性包括参数化多态行和包含多态性。多态语言具有灵活、抽象、行为共享、代码共享的优势，很好的解决了应用程序函数同名问题。

## String是最基本的数据类型吗？

基本数据类型包括一下8种

> byte、int、char、long、float、double、boolean、short

java.lang.String类是final类型的，因此不可以继承这个类、不能修改这个类。为了提高效率节省空间我们应该用StringBuffer类

## String和StringBuffer的区别

JAVA平台提供了两个类：String和StringBuffer，它们可以储存和操作字符串，即包含多个字符的字符数据。这个String类提供了数值不可改变的字符串。而这个StringBuffer类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。

典型地，你可以使用StringBuffer来动态构造字符数据

### String、StringBuffer与StringBuilder比较

> 三者运行速度不同

#### String运行速度

遍历一百万次

```java
String a = "";
long startTime = System.currentTimeMillis();
for(int i=0; i<100*100*10;i++){
    a+="aa";
}
long endTime = System.currentTimeMillis();
System.out.println("耗时："+String.valueOf(endTime - startTime));

```

运行结果为 `耗时:7614`

#### StringBuffer运行速度

遍历一亿次

```java
StringBuffer a = new StringBuffer();
String aa = "aa";
long startTime = System.currentTimeMillis();
for(int i=0;i<100*100*100*100;i++){
    //字符串拼接
    a.append(aa);
}
long endTime = System.currentTimeMillis();
System.out.println("耗时："+String.valueOf(endTime - startTime));
```

运行结果为 `耗时：3128` 

#### StringBuilder运行速度

遍历一亿次

```java
StringBuilder a = new StringBuilder();
String aa = "aa";
long startTime = System.currentTimeMillis();
for(int i=0;i<100*100*100*100;i++){
    a.append(aa);
}
long endTime = System.currentTimeMillis();
System.out.println("耗时："+String.valueOf(endTime - startTime));
```

运行结果为 `耗时：1240` 

#### 比较结果

速度比较：String < StringBuffer < StringBuilder 且String的处理速度要比StringBuffer、StringBuilder要慢得多

> 分析为什么String的处理速度要比StringBuffer、StringBuilder慢得多？

1. String是不可变对象

2. StringBuffer和StringBuilder是可变对象

   > + String本身就是一个对象，因为String不可变对象，所以，每次遍历对字符串做拼接操作，都会重新创建一个对象，循环100万次就是创建100万个对象，非常的消耗内存空间，而且创建对象本身就是一个耗时操作，创建100万次对象就相当的耗时了。
   > + StringBuffer和StringBuilder只需要创建一个StringBuffer或StringBuilder对象，然后用append拼接字符串，就算拼接一亿次，仍然只有一个对象。

> 是不是可以抛弃使用String，转而使用StringBuffer和StringBuilder呢？

No!!!

1. String遍历代码：开始定义一个String常量（创建一个String对象），再开始遍历

2. StringBuffer遍历代码：开始定义一个String常量（创建一个String对象）和一个StringBuffer对象，再开始遍历

3. StringBuiler遍历代码：开始定义一个String常量（创建一个String对象）和一个StringBuiler对象，再开始遍历

   > `StringBuffer`和`StringBuiler`比`String`多了一个创建对象流程，所以，如果数据量比较小的情况建议使用`String`。

> 说说StringBuffer和StringBuilder的区别？

1. StringBuffer是线程安全的
2. StringBuilder是非线程安全的， 这也是速度比StringBuffer快的原因

> 适用场景？

1. 如果要操作少量的数据用 String
2. 单线程操作字符串缓冲区 下操作大量数据 StringBuilder
3. 多线程操作字符串缓冲区 下操作大量数据 StringBuffer

##  int和Integer有什么区别

Java提供两种不同的类型：引用类型和原始类型（内置类型）。int是Java的原始数据类型，Integer是Java为int提供的封装类。Java为每个原始类型提供了封装类

| byte    | Byte    |
| ------- | ------- |
| short   | Short   |
| float   | Float   |
| double  | Double  |
| boolean | Boolean |
| char    | Char    |
| int     | Integer |
| long    | Long    |

> 引用类型与原始类型的行为完全不同，并且它们具有不同的语义。引用类型和原始类型具有不同的特征和用法，它们包括：大小和速度问题，这种类型以哪种类型的数据结构存储，当引用类型和原始类型用作某个类的实例数据时所指定的缺省值。对象引用实例变量的缺省值为null，而原始类型实例变量的缺省值与它们的类型有关。

## 运行时异常与一般异常有何异同

异常表示程序运行过程中可能出现的非正常状态，运行时异常表示虚拟机通常操作中可能遇到的异常，是一种常见运行错误。Java编译器要求方法必须声明抛出可能发生的非运行时异常，但是并不要求必须声明抛出未捕获的运行时异常。

## &和&&的区别

&和&&都可作为逻辑运算符”与“使用，但是&&是“短路与”，运算时先判断符号前面的表达式的值，如果能够确定整个表达式的值，则不进行符号后面的表达式的运算。

> &亦可做为运算符使用。



## 说出ArrayList，Vector，LinkedList的存储性能和特性

ArrayList和Vector都是使用数据方式存储数据，此数组元素大于实际存储的数据以便以添加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢，Vector由于使用了synchronized方法（线程安全），通常性能上较ArrayList差，而LinkedList使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。

## Collection和Collections的区别

Collection是集合类的上级接口，继承它的接口主要有Set和List。

Conllections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作。

## HashMap和Hashtable的区别

1. HashMap是Hashtable的轻量级实现（非线程安全的实现），它们都完成了Map接口，主要区别在于HashMap允许空（null）键值（key），由于非线程安全，效率上可能高于Hashtable。
2. HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。
3. HashMap把Hashtable的contains方法去掉了，改成containsValue和containsKey。因为contains方法容易让人引起误解。
4. Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Map interface的一个实现。
5. 最大的不同是，Hashtable的方法是Synchronize的，而HashMap不是，在多个线程访问Hashtable时，不需要为它的方法实现同步，而HashMap就必须为之提供外同步。
6. Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差异。