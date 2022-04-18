# 注解（Annotation）

### 1.什么是注解

> 注解是放在Java源码的类、方法、字段、参数前的一种特殊“注释”。

### 2.元注解

@Target：用于描述注解的使用范围

@Retention：表示需要在什么级别保存该注释信息，用于描述注解的生命周期

@Inherit：子类可以继承父类的该注解



### 3.定义注解

```java
@Target(value = ElementType.METHOD)
@Retention(value = RetentionPolicy.RUNTIME)
public @interface MyAnnotation {
	//注解的参数：类型 注解名() default 默认值；
  String name() default "name";
}

```







# 反射

### 1.什么是反射

> 反射是借助ReflectionAPI在程序运行时期获取任何类的内部信息，并能直接操作任意属性和方法。



### 2.反射API

* Java.lang.Class

```java
Class c1 = Class.forName("com.example.demo.User");
```

| 方法名                             | 说明                      |
| ---------------------------------- | ------------------------- |
| static ClassforName（String name） | 返回类名为name的Class对象 |
| 对象.getClass()                    | 获取对象的Class对象       |
| 类名.class                         | 获取类名的Class对象       |

* java.lang.reflect.Method
* java.lang.reflect.Field
* Java.lang.reflect.Constructor



### 3.反射操作注解

* getAnnotations
* getAnnotation





