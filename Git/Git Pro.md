# Git Pro

### 入门

一.版本控制：本地RCS，集中式CVCS，分布式DVCS ;注意Subversion，Git 区别

​                          快照，文件状态，快照流，本地执行，完整性-SHA-1散列

 二. 3种文件状态：committed,modified,staged

​                          已提交：已经存入本地数据库中

​                          已修改：改动文件，未提交数据库

​                          已暂存：一修改文件的当前版本做出标识并将加入下一次要提交的快照中

三.3个主要区域：Git目录，工作目录，暂存区(位于Git目录下，索引，保存下次要提交内天的信息)

​       基本工作流：修改工作目录下文件；暂存文件，将这些文件的快照加入暂存区；提交暂存区文件，将快照永久的保存在Git目录下

### Git本地基础

一、获取仓库：现有导入Git，服务器克隆Git仓库

```git
$ git init //进入项目目录创建.git子目录   
$ git add *.c //跟踪目录下文件
$ git add LICENSE
$ git commit -m 'initial project version'`  // 提交被跟踪文件
```

```
$ git clone https://github.com/4youngS/imgbed/imgbed  imgbed1   //克隆仓库到本地目录
```

​      





