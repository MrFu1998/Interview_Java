## Java面试题

* 问题：如果`main`方法被声明为`private`会怎么样？
  * 答案：能正常编译，但运行的时候会提示" `main`方法不是`public`的"

* 问题：`Java`里的传引用和传值的区别是什么？
  * 答案：传引用是指传递的是地址而不是指本身，传值则是传递值的一份拷贝

* 问题：如果要重写一个对象的`equals`方法，还要考虑什么？
  * 答案：`hashCode`

* 问题：`Java`的“一次编码，处处运行”是如何实现的？
  * 答案：`Java`程序会被编译成字节码组成的`class`文件，这些字节码可以运行在任何平台，因此`Java`是平台独立的

* 问题：说明一下`public static void main(String[] args)`这段声明里每个关键字的作用？
  * 答案：
     * `public`:`main`方法是`Java`程序运行时调用的第一个方法，因此它必须对`Java`环境可见。所以可见性设置`public`
     * `static`:`Java`平台调用这个方法时不会创建这个类的一个实例，因此这个方法必须声明为`static`
     * `void`:`main方法没有返回值`
     * `String`是命令行传进参数的类型，`args`是指命令行传进的字符串数组

* 问题 ：`==` 与 `equals` 的区别
  * 答案：`==` 是比较两个对象在内存里是不是一个对象，就是说内存里的存储位置一致。两个`String`对象存储的值是一样的，但有可能在内存里存储在不同的地方，`==` 比较的是引用而`equals`方法比较的是内容。`public boolean equals(Object obj)`这个方法是有`Object`对象提供的，可以由子类进行重写。默认的实现只有当对象和自身进行比较时才会返回`true`，这个时候和`==` 是等价的。`String , BitSet ,Date`和`File`都对`equals`方法进行了重写。对两个`String`对象而言，值相等意味着他们包含同样的字符序列。对于基于类型的包装类来说，值相等意味着对应的基本类型的值一样，下面是代码示例：

  ```java
    public class EqualsTest{
      public static void main(String[] args){
        String s1 = "abc";
        String s2 = s1;
        String s3 = "abc";
        String s4 = new String("abc");
        String s5 = new String("abc");
          System.out.printIn("== comparison :" + （s1 == s3）);
        System.out.printIn("== comparison :" + （s1 == s2）);
        System.out.printIn("Using equals method :" + s1.equals(s2));
        System.out.printIn("== comparison :" + （s4 == s5）);
        System.out.printIn("Using equals method :" + s3.equals(s4)); 

      }
    }
  ```

  **结果**

  ```java
  == comparison : true
  == comparison : true
  Using equals method : true
  == comparison : false
  Using equals method : true
  ```

* 问题：如果去掉了`main`方法的`static`修饰符会怎样？
  * 答案：程序能正常编译。运行时会抛出`NoSuchMethodError`异常

* 问题：为什么`oracle type4`驱动被称作瘦驱动？
  * 答案：`oracle`提供了一个`type4 JDBC`驱动被称为瘦驱动，是因为这个驱动包含了一个`Oracle`自己完全用`	Java`实现的一个`TCP/IP`的`Net8`的实现，因此它是平台独立的，可以在运行时由浏览器下载，不依赖任何客户端的`oracle`实现。客户端连接字符串用的是`TCP/IP`的地址窗口，而不是数据库名的`tnsname`

* 问题：介绍一下`finalize`方法
  * 答案：`final`：常量声明，`finally`：处理异常，`finalize`：帮助进行垃圾回收
    接口里声明的变量默认是`final`，`final`类无法继承，也就是没有子类。这么做是出于基础类型的安全考虑，比如`String`和`Interger`。这样也使得编译器进行一些优化，更容易保证线程的安全性。`final`方法无法重写，`final`变量的值不能改变。`finalize()`方法在一个对象被销毁和回收前会被调用。`finally`通常用于异常处理，不管有没有异常被抛出都会被执行到。比如，关闭连接通常放到`finally`块中完成

* 问题：什么是`Java API`?

  * 答案：`Java API`是大量软件组件的集合，提供了大量有用的功能，比如`GUI`组件

* 问题：`GregorianCalendar`类是什么东西？

  * 答案：`GregorianCalendar`提供了西方传统日历的支持

* 问题：`ResourceBundle`类是什么？

  * `ResourceBundle`用来存储指定语言环境的资源，应用程序可以根据运行时语言环境来加载这些资源，从而提供不同语言的提示

* 问题：为什么`Java`里面没有全局变量？

  * 答案：全局变量是全局可见的，`Java`不支持全局可见的变量，因为全局变量破坏了引用透明性原则。全局变量导致了命名空间的冲突

* 问题：如何将`String`类型转化成`Number`类型？

  * 答案：`Integer`类的`valueOf`方法可以将`String`转成`Number`。下面是代码示例：

    ```java
    String numString = "1000";
    int id = Intrger.valueOf(numString).intValue();
    ```

* 问题：`SimpleTImeZone`类是什么

  * 答案：`SimpleTimeZone`提供公历日期支持

* 问题：`While`循环和`do / while`循环有什么不同？

  * 答案：`while`结构在循环的开始就判断下一个迭代是否应该继续。`do / while`结构是在循环的结尾来判断是否将继续下一轮迭代。`do / while`结构至少会执行一次循环体

* 问题：`locale`类是什么？

  * 答案：`Locale`类用来根据语言环境来动态调整程序的输出

* 问题：面对对象变成的原则什么？

  * 答案：主要3点，继承，多态，封装

* 问题：继承，多态和封装是什么？

  * 答案：简单来说，多态是指一个名字多种实现，多态使得一个实体通过一个通用的方式来实现不同的操作。具体的操作是由实际的实现来决定的，多态在`Java`里有三种表现方式：方法重载通过继承实现方法重写通过`Java`接口进行方法重写

* 问题：介绍下继承的原则？

  * 答案：继承使得一个对象可以获取另一个对象的属性。使用继承可以让已经测试完备的功能得以复用，并且可以一次修改，所有继承的地方都同时生效

* 问题：什么是隐式的类型转换？

  * 答案：隐式的类型转换就是简单的一个类型赋值给另一个类型，没有显示的告诉编辑器发生了转化，并不是所有的类型都支持隐式的类型转换,隐式转化有叫自动类型转换。由系统自动完成的类型转换

    从存储范围小的类型到存储范围大的类型

    ```java
    byte -> short(char) -> int -> long -> float        -> double
    int d = 3;
    double n = d;
    ```

* 问题：什么是显式类型转换？

  * 答案：显式的类型转换是明确告诉了编译器来进行对象的转换，显式类型转换也叫强制类型转换。

    从存储范围大的类型到存储范围小的类型。具体规则为：		

    ```java
    double -> float -> long -> int -> short(char) -> byte
    ```

    语法格式为：(转换到的类型)需要转换的值示例代码：

    ```java
    double d = 3.10;
    int n = (int)d;
    ```

* 问题：`sizeof`是`Java`的关键字？

  * 答案：不是

* 问题：`natlve`方法是什么？

  * 答案：`natlve`方法是非`Java`代码实现的方法

* 问题：在`System.out.println()`里面的`System,out,println`分别是什么？

  * 答案：
    * `System`是系统提供的预定义的`final`类
    * `out`是一个`PrintStream`对象
    * `println`是`out`对象里面一个重载的方法

* 问题：什么是`Java`虚拟机？

  * 答案：`Java虚拟机是能够移植到不同硬件平台上的软件系统`

* 问题：类型向下转换是什么？

  * 答案：向下转换是指由一个通用类型转换成一个具体的类型，在继承结构上向下运行

* 问题：`Java`的访问修饰符是什么？

  * 答案：访问权限修饰符是表明类成员的访问权限的关键字。使用这些关键字来限定程序的方法或者变量的访问权限。它们包含：
    * `public`所有类都可以访问`protected`同一个包内以及所有子类都可以访问
    * `private`只有归属的类才能默认访问，归属类及相同包的子类可以访问

* 问题：所有类的父类是什么？

  * 答案：object

* 问题：所有`Java`的基本类型有那些？

  * 答案：`byte, char, short, int, long, float, double, boolean`