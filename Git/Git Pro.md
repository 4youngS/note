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

### Git基础

一、获取仓库：现有导入Git，服务器克隆Git仓库

```
$ git init //进入项目目录创建.git子目录   
$ git add *.c //跟踪目录下文件
$ git add LICENSE
$ git commit -m 'initial project version'`  // 提交被跟踪文件
```

```
$ git clone https://github.com/4youngS/imgbed/imgbed  imgbed1   //克隆远程仓库到本地目录
```

​    二、记录变更：工作目录下每一个文件都处于2种状态：tracked，untracked  

![image-20210307132635156](https://cdn.jsdelivr.net/gh/4youngS/imgbed@main/git/image-20210307132635156.png)

```
git$ git status //查看当前状态
S echo 'myproject' README
$ git add README //添加跟踪文件或者将修改文件添加到暂存区

$ git status -s  //??,A， M，M ，MM
$ git status --short //untrcaked文件，staged，已修改的未暂存，已修改且已暂存，已修改并暂存后又修改即暂存区与工作区都包含修改

$ git diff   //查看尚未添加到暂存区的变更
$ git diff --staged  //查看哪些已暂存的内容会进入下一次的提交 
$ git diff --cached  //查看当前已暂存的更改

$ git commit -m 'first  commit test' //将暂存区文件提交,其它未暂存的文件依然保持着修改状态
$ git commit -a -m 'new' //跳过暂存直接提交，直接把已跟踪的所有文件添加到暂存区然后提交，不用执行git add

$ rm ROJECT.md  //把文件从工作目录中移除
$ git rm PROJECT.md  //把文件移除状态记录到暂存区，提交后将不存在
$ git rm -f PROJECT.md  //强制移除
$ git rm --cache PROJECT.md  //保留文件在工作目录，但不在跟踪管理

$ git mv READ.md ROJECT //重命名文件

$ git log //查看历史记录
$ git log -p -2
$ git log --stat

$ git commit --amend
$ git reset HEAD READ.md //把文件移出暂存区，恢复到已修改但未暂存的状态
$ git checkout --READ.md //撤销修改重新签出

```

三 管理远程仓库

```
$ git remote //显示远程仓库
$ git remote -v

$ git remote add pb https://github.com/4youngS/pb  //添加远程仓库
$ git fetch pb   //获取远程仓库自上一次的新增变更数据，并不会合并或者修改本地数据，需要手动合并
$ git push origin master  //将变更推送远程仓库，权限与推送前无其他人推送
$ git remote show origin   //显示查看远程仓库信息
$ git remote rename pb paul   //重命名远程仓库
$ git remote rm paul  //删除远程仓库地址

$ git tag 
$ git tag -a V1.0 -m "version1.0" //创建并注释标签
```

### Git 分支

### Git服务器

### 分布式Git

