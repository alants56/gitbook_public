# Design Pattern



# 面向对象七大原则

1.开闭原则

> 对扩展开放，对修改关闭。增加新功能的时候，能不改代码就尽量不要改，如果只增加代码就完成了新功能，那是最好的。

2.里式替换原则

> 调用父类能够成功，则调用子类能够成功

3.依赖倒置原则

> 面向接口编程，不要面向实现编程

4.单一职责原则

> 控制的类的粒度大小、对对象解耦、提高其内聚性。

5.接口隔离原则

> 要为各个类建立它们需要的专用接口

6.迪米特法则

> 只有自己的朋友关联，不跟“陌生人”说话

7.合成复用原则

> 尽量先使用组合或者聚合等关联关系来实现，其次才考虑使用继承关系来实现。

# 创新型模式

### 1. 单例模式

* 饿汉式
* 懒汉式
    * 需要注意线程安全。
* 



### 2. 工厂模式

> 通过工厂模式实例化对象。
>
> 将选择实现类、创建对象统一管理，从而将调用者和使用者分离。

* 简单工厂模式
    * 用来生产同一等级结构中的任意产品（对于新产品，需要覆盖已有产品）

* 工厂方法模式
    * 用来生产同一等级结构中的固定产品（支持增加产品）

> 简单工厂：结构复杂度低，代码复杂度低，编程复杂度低，管理的复杂度低。

### 3.抽象工厂模式

> 围绕一个超级工厂创建其他工厂的。提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。

优点：

* 具体产品在应用层的代码隔离
* 将一系列的产品统一到一起创建

缺点：

* 规定了所有可能被创建的产品集合
* 增加了系统的抽象性和理解难度

### 4.建造者模式

### 5. 原型模式











# 结构型模式



# 行为型模式



 