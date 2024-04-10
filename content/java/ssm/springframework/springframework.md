<p style="font-size:30px;">SpringFramework</p>

<p style="font-size:20px;">目录</p>
<!-- TOC -->

- [1 SpringFramework](#1-springframework)
  - [SpringFramework 主要功能模块](#springframework-主要功能模块)
  - [SpringFramework 主要优势](#springframework-主要优势)
- [2 Spring IoC](#2-spring-ioc)
  - [组件和组件管理](#组件和组件管理)
  - [Spring IoC 容器接口和实现类](#spring-ioc-容器接口和实现类)
  - [Spring IoC 容器的配置方式](#spring-ioc-容器的配置方式)
  - [使用基于Java注解的配置方式创建和使用Spring容器](#使用基于java注解的配置方式创建和使用spring容器)
    - [Bean注解标记和扫描](#bean注解标记和扫描)
    - [Bean作用域注解](#bean作用域注解)
    - [Bean周期方法注解](#bean周期方法注解)
    - [Bean属性赋值：引用类型自动装配（DI）](#bean属性赋值引用类型自动装配di)
    - [Bean属性赋值：基本类型属性赋值（DI）](#bean属性赋值基本类型属性赋值di)
- [3 Spring AOP](#3-spring-aop)
- [4 Spring 声明式事务](#4-spring-声明式事务)
- [5 总结](#5-总结)

<!-- /TOC -->

new 对象会造成耦合。

解除模块间、层之间的耦合：不能 new 需要的实现类。

解决思路：

- 提供一个容器，容器中存储一些对象(例：EmpService对象)
- controller程序从容器中获取EmpService类型的对象

对象如何交给容器管理，容器如何为程序提供依赖的资源？


# 1 SpringFramework
## SpringFramework 主要功能模块

|功能模块|功能介绍|
|-|-|
|Core Container|核心容器，在 Spring 环境下使用任何功能都必须基于 IOC 容器。|
|AOP&Aspects|面向切面编程|
|TX|声明式事务管理。|
|Spring MVC|提供了面向Web应用程序的集成功能。|
||


## SpringFramework 主要优势
 
# 2 Spring IoC
- **IoC容器**

  Spring IoC 容器，负责实例化、配置和组装 bean（组件）核心容器。容器通过读取配置元数据来获取有关要实例化、配置和组装组件的指令。

  降低bean之间的耦合

- **IoC（Inversion of Control）控制反转**

    面向对象编程设计思想

  IoC 主要是针对对象的创建和调用控制而言的，也就是说，当应用程序需要使用一个对象时，不再是应用程序直接创建该对象，而是由 IoC 容器来创建和管理，即控制权由应用程序转移到 IoC 容器中，也就是“反转”了控制权。这种方式基本上是通过依赖查找的方式来实现的，即 IoC 容器维护着构成应用程序的对象，并负责创建这些对象。

- **DI (Dependency Injection) 依赖注入**

  DI 是指在组件之间传递依赖关系的过程中，将依赖关系在容器内部进行处理，这样就不必在应用程序代码中硬编码对象之间的依赖关系，实现了对象之间的解耦合。在 Spring 中，DI 是通过 XML 配置文件或注解的方式实现的。它提供了三种形式的依赖注入：构造函数注入、Setter 方法注入和接口注入。

IoC通过依赖注入实现，IoC容器是实现依赖注入的关键。


- 理解控制反转（IoC）

创建类、配置文件。由IoC容器读取配置文件，在IoC容器中通过反射机制完成实例化。对象的创建权限给了Spring核心容器。


## 组件和组件管理
组件：可以复用的java对象
- 组件一定是对象
- 对象不一定是组件

Spring 充当组件管理

组件可以完全交给Spring 框架进行管理，Spring框架替代了程序员原有的new对象和对象属性赋值动作等！
- 组件对象实例化
- 组件属性属性赋值
- 组件对象之间引用
- 组件对象存活周期管理
- ......

我们只需要编写元数据（配置文件）告知Spring 管理哪些类组件和他们的关系即可！
- xml、java注解、java代码（类）

## Spring IoC 容器接口和实现类

ApplicationContext

## Spring IoC 容器的配置方式
XML配置、注解、Java配置类

在SpringBoot框架下，推崇“0配置文件” 不用xml配置

用配置类+注解


## 使用基于Java注解的配置方式创建和使用Spring容器
组件交给Spring IoC 容器管理，并获取和使用的步骤：
配置元数据--实例化IoC容器--获取组件(Bean)

1、类上添加IoC注解

2、（提高性能）告诉SpringIoC容器，在哪些包下添加了IoC注解（用xml文件 指定注解生效包的信息）

### Bean注解标记和扫描
1 准备组件类：普通组件、Controller组件、Service组件、Dao组件

Spring 提供了以下多个注解，这些注解可以直接标注在 Java 类上，将它们定义成 Spring Bean。

|注解|说明|
|-|-|
|@Component|该注解用于描述 Spring 中的 Bean，它是一个泛化的概念，仅仅表示容器中的一个组件（Bean），并且可以作用在应用的任何层次，例如 Service 层、Dao 层等。 使用时只需将该注解标注在相应类上即可。|
|@Repository|该注解用于将数据访问层（Dao 层）的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|
|@Service|该注解通常作用在业务层（Service 层），用于将业务层的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|
|@Controller|该注解通常作用在控制层（如SpringMVC 的 Controller），用于将控制层的类标识为 Spring 中的 Bean，其功能与 @Component 相同。|

> 理解：不同注解对于Spring使用IOC容器管理这些组件来说没有区别，也就是语法层面没有区别。所以@Controller、@Service、@Repository这三个注解只是给开发人员看的，让我们能够便于分辨组件的作用。

> !!!@Repository 能够启动与Spring数据访问相关联的其他功能 

2 xml配置文件确定扫描范围

在resources下添加.xml配置文件

```
<!--1. 普通配置包扫描
           base-package 指定ioc容器去哪些包下查找注解类 -> ioc容器
           一个包或者多个包  com.atguigu,com.atguigu.xxx 包,包
           指定包,相当于指定了子包内的所有类
    -->
    <context:component-scan base-package="com.atguigu.ioc_01" />
```
其他xml配置格式使用时查询即可

### Bean作用域注解
```
@Scope(scopeName = ConfigurableBeanFactory.SCOPE_SINGLETON) //单例,默认值
@Scope(scopeName = ConfigurableBeanFactory.SCOPE_PROTOTYPE) //多例  二选一
```
1. Bean作用域概念

    `<bean` 标签声明Bean，只是将Bean的信息配置给SpringIoC容器！

    在IoC容器中，这些`<bean`标签对应的信息转成Spring内部 `BeanDefinition` 对象，`BeanDefinition` 对象内，包含定义的信息（id,class,属性等等）！

    这意味着，`BeanDefinition`与`类`概念一样，SpringIoC容器可以可以根据`BeanDefinition`对象反射创建多个Bean对象实例。

    具体创建多少个Bean的实例对象，由Bean的作用域Scope属性指定！
2. 作用域可选值

|取值|含义|创建对象的时机|默认值|
|-|-|-|-|
|singleton|在 IOC 容器中，这个 bean 的对象始终为单实例|IOC 容器初始化时|是|
|prototype|这个 bean 在 IOC 容器中有多个实例|获取 bean 时|否|


  如果是在WebApplicationContext环境下还会有另外两个作用域（但不常用）：

|取值|含义|创建对象的时机|默认值|
|-|-|-|-|
|request|请求范围内有效的实例|每次请求|否|
|session|会话范围内有效的实例|每次会话|否|


### Bean周期方法注解
周期方法：定义当 IoC 容器在实例化（之后）、销毁（之前） 组件对象时的操作

从Java EE 5规范开始，Servlet中增加了两个影响Servlet生命周期的注解，分别是：@PostConstruct和@PreDestroy。

@PostConstruct 注解：

用于在对象初始化阶段执行一些必要的操作。<br>
方法会在对象的构造函数之后、依赖注入完成之后被调用。<br>
通常用于在 Bean 初始化时执行一些操作，例如初始化资源、配置等。<br>
在 Spring 应用程序中，会在 Spring 容器初始化 Bean 时执行。<br>

@PreDestroy 注解：

用于在销毁 Bean 之前执行一些清理操作。<br>
方法会在容器销毁 Bean 之前被调用。<br>
通常用于在销毁 Bean 之前执行一些操作，例如关闭资源连接、释放资源等。<br>
在 Spring 应用程序中，会在 Spring 容器销毁 Bean 时执行。<br>

```
@Service
public class TestPeriodMethod {

    public TestPeriodMethod() {
        System.out.println("创建");
    }

    //对象创建并赋值之后调用
    @PostConstruct
    public void init() {
        System.out.println("初始化");
    }

    //对象被从ioc容器中移除之前调用
    @PreDestroy
    public void destroy() {
        System.out.println("即将被销毁");
    }
}

   @Test
    public void test() {
        ClassPathXmlApplicationContext applicationContext
                = new ClassPathXmlApplicationContext("spring-jaren.xml");
        TestPeriodMethod periodMethod = applicationContext.getBean(TestPeriodMethod.class);
        System.out.println(periodMethod);
        applicationContext.close();
        System.out.println(periodMethod);
    }

```
结果
```
创建
初始化
com.atguigu.ioc_jaren.TestPeriodMethod@452e19ca
即将被销毁
com.atguigu.ioc_jaren.TestPeriodMethod@452e19ca
```
深入的Bean生命管理将进一步讨论：



### Bean属性赋值：引用类型自动装配（DI）
```
/**
     * 情况1: ${key} 取外部配置key对应的值!
     * 情况2: ${key:defaultValue} 没有key,可以给与默认值
     */
    @Value("${catalog:hahaha}")
    private String name;
```

### Bean属性赋值：基本类型属性赋值（DI）


# 3 Spring AOP

动态代理是 AOP 的主流实现，Spring AOP 旨在管理 bean 对象过程中，主要通过底层的代理机制，对特定方法进行编程。




# 4 Spring 声明式事务

# 5 总结

