### MVC

MVC是一种设计模式,软件架构设计模式，不同于23种类的组织设计模式。

关注点分离：只注意需要注意的，分层分部分处理；约定优于配置

Model的责任：持久化，
     数据处理：数据库操作，数据结构定义，数据格式验证。
     技术：EF，Nhibernate,LINQ,ADO.net

View的范围：数据显示+显示逻辑

Model的概念：程序外部提供的数据所演算出来的结果，在数据源+中介层之上，将上层应用程序分离，不必关注数据源
       类型：DomainModel，ViewModel，InputModel；常用数据库中心架构
       设计方式：DTO，POCO
       职责分离：中介层Repository（主数据资源库）负责Model与数据源的协调合作，通常用接口和抽象工厂模式设计，提升不同数据源的兼容集成
ADO.NET:数据访问方法，面向连接+面向无连接  
        数据强类型和弱类型的解决：ORM，泛型
	泛型解决：兼容不同的数据类型
LINQ：
   数据库：SQLServer,Oracal,mySQL,Access, Redis,MongoDB