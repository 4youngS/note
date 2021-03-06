#### 设计模式分类

创建型：5；  单例、抽象工厂、建造者、工厂、原型

结构性：7；  适配器、桥接、装饰、组合、外观、享元、代理

行为型：11； 模板方法、命令、迭代器、观察者、中介者、备忘录、解释器、状态、策略、职责链、访问

例外：并发型模式和线程池模式 



#### 设计6大原则

 开闭原则：对扩展开放、对修改封闭

 单一职责：不要存在多于一个导致类变更的原因，也就是说每个类应该实现单一的职责，否则就应该把类拆分。

 里氏替换原则（Liskov Substitution Principle）： 任何基类可以出现的地方，子类一定可以出现。里氏替换原则是继承复用的基石，只有当衍生类可以替换基类，软件单位的功能不受到影响时，基类才能真正被复用，而衍生类也能够在基类的基础上增加新的行为。
里氏代换原则是对“开-闭”原则的补充。实现“开闭”原则的关键步骤就是抽象化。而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。里氏替换原则中，子类对父类的方法尽量不要重写和重载。因为父类代表了定义好的结构，通过这个规范的接口与外界交互，子类不应该随便破坏它。

 依赖倒转原则（Dependence Inversion Principle）：面向接口编程，依赖于抽象而不依赖于具体。写代码时用到具体类时，不与具体类交互，而与具体类的上层接口交互。

接口隔离原则（Interface Segregation Principle）：每个接口中不存在子类用不到却必须实现的方法，如果不然，就要将接口拆分。使用多个隔离的接口，比使用单个接口（多个接口方法集合到一个的接口）要好。

迪米特法则（最少知道原则）（Demeter Principle）：一个类对自己依赖的类知道的越少越好。无论被依赖的类多么复杂，都应该将逻辑封装在方法的内部，通过public方法提供给外部。这样当被依赖的类变化时，才能最小的影响该类。
最少知道原则的另一个表达方式是：只与直接的朋友通信。类之间只要有耦合关系，就叫朋友关系。耦合分为依赖、关联、聚合、组合等。我们称出现为成员变量、方法参数、方法返回值中的类为直接朋友。局部变量、临时变量则不是直接的朋友。我们要求陌生的类不要作为局部变量出现在类中。

合成复用原则（Composite Reuse Principle）：尽量首先使用合成/聚合的方式，而不是使用继承。




#### UML

关联关系(Association)：双向关联，单向关联，自关联、多重性关联Multiplicity、

聚合(Aggregation)：整体与部分的关系，整体对象销毁时成员对象不销毁，一般是构造函数或Set方法传入成员对象。

组合(Composition)：整体与部分的关系，整体对象销毁时成员对象一并销毁，一般在构造函数中创建成员对象。

泛化关系(Generalization)：父类与子类之间，由子类指向父类

实现关系(Realization)：接口与实现类之间，由实现类指向接口 


依赖关系(Dependency)：Driver类依赖Car类的move方法，Driver--->Car