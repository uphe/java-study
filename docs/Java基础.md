#### 基础

**1.八种基本数据类型是什么？他们的包装类型是什么？各占多少个字节？**
byte Byte 1个字节、short Short 2个字节、int Integer 4个字节、long Long 8个字节、float Float 4个字节、double Double 8个字节、char Character 2个字节、boolean Boolean 1位

**2.==与equals的区别**
==比较的是地址，equals比较的是内容

**3.重载和重写的区别**
重载：发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。
重写：发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为private则子类就不能重写该方法。

**4.StringStringBuffer和StringBuilder的区别是什么**
StringBuffer和StringBuilder的实现原理一样，其父类都是AbstractStringBuilder。StringBuffer是线程安全的，StringBuilder是JDK 1.5新增的，其功能和StringBuffer类似，性能有一些提升，但是线程不安全。

**5.String为什么不可变**
String类中使用字符数组保存字符串，private final char value[]，被final修饰了。

**6.&和&&的区别**
&运算符：1、按位与；2、逻辑与。
&&运算符是短路运算符，当有一个为false的时候，结果就为false。

**7.final的作用**
final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。

**8.final finally finalize区别**
final可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。
finally一般作用在try-catch代码块中，在处理异常的时候，通常我们将一定要执行的代码方法finally代码块中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
finalize是一个方法，属于Object类的一个方法，而Object类是所有类的父类，该方法一般由垃圾回收器来调用，当我们调用System.gc() 方法的时候，由垃圾回收器调用finalize()，回收垃圾，一个对象是否可回收的最后判断。

**9.private default protect public的作用范围**
private：Java语言中对访问权限限制的最窄的修饰符，一般称之为”私有的”。被其修饰的类、属性以及方法只能被该类的对象访问，其子类不能访问，更不能允许跨包访问。
default：即不加任何访问修饰符，通常称为“默认访问模式“。该模式下，只允许在同一个包中进行访问。
protect：一般称之为“受保护的”。被其修饰的类、属性以及方法只能被类本身的方法及子类访问，即使子类在不同的包中也可以访问。
public：Java语言中访问限制最宽的修饰符，一般称之为“公共的”。被其修饰的类、属性以及方法不仅可以跨类访问，而且允许跨包（package）访问。

**10.BIO,NIO,AIO的区别**
BIO：Block IO 同步阻塞式 IO，就是我们平常使用的传统 IO，它的特点是模式简单使用方便，并发处理能力低。
NIO：Non IO 同步非阻塞 IO，是传统 IO 的升级，客户端和服务器端通过 Channel（通道）通讯，实现了多路复用。
AIO：Asynchronous IO 是 NIO 的升级，也叫 NIO2，实现了异步非堵塞 IO ，异步 IO 的操作基于事件和回调机制。


#### 集合

#### 多线程

#### JVM

**更新中...**