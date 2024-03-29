# 研磨Java设计模式

### SimpleFactory

简单工厂模式，又称静态工厂方法模式，提供一个创建对象实例的功能，无须关心具体实现.

核心是定义工厂类获取创建的对象，进而通过对象接口获取了实现方法。

	接口与抽象类，封装隔离、面向接口编程
	组件：完成一定功能的封装体
	
	API api=new Impl();只知接口不知实现，就无法调用接口使用
	通过工厂方法的不同参数调用不同的方法接口实现方法，只是将实现方法独立出来封装解耦
	本质：选择实现
	特点：
	     1.静态简单工厂方法
		 2.不同的参数选择返回创建不同的实现接口类。
		 3.通过工厂方法将组件接口封装独立，实现调用端和接口的解耦
		 4.不同参数选择调用不同接口实现，是最佳的接口说明



### Facade

外观模式，为子系统的一系列接口提供统一的界面，定义了一个高层接口使调用更加简单容易统一；

核心是高层接口，外部与内部通道；

引入外观类，定义方法实现客户端与内部模块的调用实现功能，让客户端只与外观类交互变得简单。

```
目的：减少外部与子系统模块的交互，松散耦合，让外部简单使用
	 外观类为子系统对外的接口，负责封装组合已有功能，不建议定义子系统没有的功能或添加新的实现
本质：封装交互，简化调用
特点：
	1.外观类实现可以是静态方法，单例，或者接口
    2.通道，实现外部与内部调用，封装减少与外部交互
	3.最少知识原则
```



### Adapter		

适配器模式；类接口转换成另外的接口，实现兼容使用；转换匹配，复用已有功能，变更和组合满足新的需求

核心是已有功能改造成可以被既定的接口供调用；

复用已有功能Adaptee,转换匹配Adapter类，满足新的需求接口Target，复用扩展。

```
本质：转换匹配，复用功能
特点：
	1.Adapter类可是双向继承和实现Target和Adaptee，也可以单向实现接口Target。
	2.Adapter类调用Adaptee，实现Target接口，是一个Target类型。
	3.分为对象适配器（组合），类适配器（继承），接口适配器（抽象类部分实现适配器），互相区别。
```

​		  

### FactoryMethod

工厂方法；

定义用于创建对象的接口让子类决定实例化哪一个类；使类的实例化延迟到子类中，可以是抽象工厂方法继承，也可以是普通工厂方法继承，重要的是子类实现。

选择性的创建，将控制创建的权利开放，更加灵活。

 框架：能完成一定功能的半成品软件；特点是加快应用开发速度，精良的程序架构。

	本质：延迟到子类来选择实现；
	特点：  
	    1.分离平行化类层次结构，使用工厂方法模式连接
		2.易于增加类层次结构，扩展更多类型对象的新版本
		3.工厂方法不需要了解具体实现就可实现编程
		4.工厂方法创建和具体的产品对象是耦合的
		5.参数化工厂方法与简单工厂方法类似；后者是静态方法。
		6.工厂方法依赖于抽象而不是具体实现，即是接口
		8.DI/IOC ,依赖倒置原则

​		

### Abstract Factory	

抽象工厂；提供一个创建一系列相关和相互依赖对象的接口，无需指定它们具体的类。

抽象工厂的实现是产品簇的选择组合模式

```
本质：产品簇的选择实现
特点：
	1.抽象工厂创建需要的对象，分离接口和实现
	2.产品簇的实现切换选择更加容易
	3.增加产品簇更加繁琐
```



### Builder	

生成器；将一个复杂对象的构建与表示分离，同样的构建过程可创建不同的表示。

构建细化、分步骤的复杂产品；

```
本质：分离构建算法和部件构造装配
特点： 
	1.构建与表示分离，松散耦合
	2.容易改变产品的内部表示
	3.构建算法易复用
```



### Prototype

原型（Prototype）；



### Mediator

中介者；用一个中介对象封装各对象交互，使各对象不需显式的相互引用；松散耦合，独立改变各交互行为

本质：封装交互

```
结构和说明
    Mediator：中介者接口，定义各同事类间公共的通信交互方法
    ConcreteMediator：具体中介者实现对象；负责各同事类具体的交互关系
    Colleague:同事类定义，通常为抽象类；负责约束同事类对象类并实现具体同事类间的公共功能。
    ConcreteColleague:具体同事类实现
```

### Proxy

代理;为其他对象提供一种代理以控制对该对象的访问

本质：控制对象访问

```
结构和说明
    proxy：代理对象；实现与具体的目标对象一样的接口；保存一个指向具体目标的引用；
    subject：目标接口，定义代理和具体目标对象的接口
    RealSubject：具体的目标对象，真正实现目标接口要求的功能
    
```

### Observer

观察者模式；

### Command

命令模式；将请求封装为一个对象，使不同的请求对客户进行参数化，对请求排队或记录以及可撤销操作

本质：封装请求

```
结构和说明
   command：定义命令的接口，声明执行的方法
   concreteCommand：命令接口实现对象
   reciver：接收者，执行命令的对象
   Invoker:触发命令对象
   Client:装配者，组装命令对象和接收者
```



### Iterator

迭代器（Iterator）;	



### Composite

组合(Composite);将对象组合成树形结构以表示“部分-整体”的层次结构，使用户对单个对象和组合对象的使用具有一致性。
    本质：统一叶子对象和组合对象

 

### TemplateMethod

 模板方法(TemplateMethod) ；定义一个操作中算法的骨架，将步骤延迟到子类中；从而是子类在不改变算法骨架的结构下可以重定义算法下的某些特定步骤



### Strategy

策略(Strategy)； 定义一系列算法，封装并且可以相互替换，是得算法独立于使用随其变化而变化



### State

状态(State)



### Memento

备忘录，

定义：不破坏封装性的前提下，捕获一个对象内部状态，并在该对象外保存以便恢复到原先保存的状态

本质：保存和恢复内部状态

```
结构和说明 
    备忘录Memento：存储原发器对象的内部状态
    原发器Originator：使用备忘录保存某个时刻原发器的状态
    备忘录管理者Caretaker：负责保存备忘录对象，但不能对备忘录对象内容进行操作

```



FlyWeight

Interpreter

Decorator

Chain of Responsibility

Bridge

Visitor











![img](https://cdn.jsdelivr.net/gh/4youngS/imgbed@main/git/472002-20210813170309766-1036089411.png)