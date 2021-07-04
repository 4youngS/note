廖雪峰JavaEE企业级分布式架构师

## MyBatis框架

#### 一、框架整体概况

##### 简介

1.对JDBC的封装，目的是简化JDBC开发流程，实现事务松耦合管理，将实体类与SQL命令进行动态对应

2.MyBatis的官网：  https://github.com/mybatis/mybatis-3

​    官方文档：https://mybatis.org/mybatis-3/zh/index.html

了解：JDBC ，ORM，持久化框架，Hibernate，POJO，EJB ,

#### 二、MyBatis框架



#### 三、MyBatis框架收尾



### 深入浅出MyBaits技术原理与实践

#### MyBaits的基本构成：

SqlSessionFactoryBulider(构造器)：根据配置代码生成SqlSessionFactory

SqlSessionFactory:依靠工厂生成SqlSession

SqlSession:可以发送SQL执行并返回结果；获取Mapper接口

SQL Mapper:MyBaits新设计的组件，由一个Java接口和XML文件(或注解)构成，需要给出对应的SQL和映射规则；负责发送SQL执行并返回结果

![image-20210515084000652](K:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20210515084000652.png)



##### SqlSessionFactory的构建

![image-20210515084720109](K:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20210515084720109.png)

1.用xml方式构建

DataSource：获取数据库连接实例的数据源

TransactionManager：决定事务范围和控制方式的事务管理器

SQL Mapper：映射器



2.代码方式构建：实际中不建议使用

##### 创建SqlSession

SqlSession是接口类，实现类2个DefaultSQLSession和SqlSessionManager,用前者，用途2种：

1.获取映射器，找到对应SQL，发送数据库执行并返回结果

2.直接通过命名信息执行SQL返回结果

##### 映射器实现

由JAVA 接口和XML 文件(注解)共同组成；作用：定义参数类型，描述缓存，描述SQL ,定义查询结果和POJO的映射关系

1.XML文件配置实现Mapper

由一个Java接口和一个XML文件构成

2.以Java注解方式实现，不建议使用

#### 生命周期

![image-20210515105137341](https://cdn.jsdelivr.net/gh/4youngS/imgbed@main/git/image-20210515105137341.png)

