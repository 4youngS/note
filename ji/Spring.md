#### Spring概述

##### 整体架构

1. Spring IOC ：IOC容器和接口，应用上下文的实现

2. Spring AOP

3. Spring MVC

4. Spring JDBC/ORM 

5. Spring 事务管理

6. Spring 远端调用

7. Spring应用

   ###### 特点：

   非侵入式框架，使依赖最小化

   面向对象和面向接口编程

   应用核心为IOC容器与AOP框架

##### 8大模块

1. DataAcess：JDBC,Transations事务,ORM,OXM,JMS等
2. Web模块：Web,WebSocket,Servlet,Portlet
3. AOP：JVM动态代理和CGLIB动态代理  
4. Aspects：集成AspectJ框架 
5. Instrumentation：容器集成和类加载器的扩展实现
6. Messageing：
7. Core Container：根基，由Beans，Core，Context，SpEL模块
8. Test： MockObject  ，JUnit或TestNG  

##### 3种领域模型

1. 容器Context模型：上下文，对Bean进行生命周期管理
2. 核心Bean模型：
3. 代理Advisor模型：定义后生成Spring代理

Spring中一切Java类为资源，都是Bean，IOC容器通过DI被动创建对象，实现控制反转

#### Spring IOC容器

基于BeanFactory与ApplicationContext两个接口和扩展实现初始化

Bean与IOC容器的生命周期

依赖查找与依赖注入

构造器注入

setter注入

接口注入



Spring配置优先顺序：约定优先配置的开发原则

隐式Bean的发现机制和自动装配原则>接口与类中实现配置>XML配置，

1. XML装配Bean：简易值，集合，命名空间
2. 注解装配Bean：组件扫描，自动装配

 













