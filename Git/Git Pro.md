# Git Pro

参考了廖雪峰的博客网站https://www.liaoxuefeng.com/wiki/896043488029600

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

$ git commit -m 'first  commit test' //将文件提交暂存区,其它未暂存的文件依然保持着修改状态
$ git commit -a -m 'new' //跳过add直接提交暂存，直接把已跟踪的所有文件添加到暂存区然后提交，不用执行git add

$ rm ROJECT.md  //把文件从工作目录中移除
$ git rm PROJECT.md  //把文件移除状态记录到暂存区，提交后将不存在
$ git rm -f PROJECT.md  //强制移除
$ git rm --cache PROJECT.md  //保留文件在工作目录，但不在跟踪管理
rm -rf .git //清除初始化文件目录即git init 命令

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

##### 一、分支基本操作：

```
$ git checkout -b mac //创建mac分支，然后切换到mac分支,-b 相当于2条命令$ git branch mac 和 $ git checkout mac
$ git branch //查看所有分支，当前分支前面会标一个*号
```

```
$ git switch -c mac //创建mac分支，然后切换到mac分支
$ git switch mac  //直接切换到已有的mac分支,即使有修改也可以
```

修改文件后提交暂存区，完成后切换分支,合并分支到主分支，然后删除

```
$ git add Git/'Git Pro.md'
$ git commit -m 'branch test'  //如果要切换分支，则要保持本地目录干净全部提交暂存区，否则提示错误不能切换
$ git commit -a -m 'new branch test'   //跳过add直接提交暂存区
$ git checkout master //切换分支后，会看到所有修改都消失，不用担心，再切换回来时就会恢复
```

```
$ git branch 
$ git switch master
$ git merge mac  //合并分支mac到当前分支master，Fast-forward快进模式
$ git branch -d mac //删除分支
```

##### 二、解决冲突：

2个分支分别各自提交暂存区后，合并操作发现冲突，打开冲突文件修改后重新提交并解决

```
$ git merge mac //分支各自提交，此时合并将报冲突
$ git status  //寻找并固定冲突文件，手动修改解决冲突
$ git add Git/'Git Pro.md'
$ git commit -m 'conflict fixed' //提交已经解决的冲突文件
$ git log  //查看冲突解决日志
$ git branch -d mac //删除已合并分支
```

##### 三、分支管理：

在实际开发中，我们应该按照几个基本原则进行分支管理：

1.`master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

2.干活都在`dev`分支上，dev`分支是不稳定的，到某个时候，比如1.0版本发布时，再把`dev`分支合并到`master`上，在`master`分支发布1.0版本；

3.个人都在`dev`分支上干活，同时每个人都在`dev`分支有自己的分支，时不时地往`dev`分支上合并就可以了

4.合并分支时，加上`--no-ff`参数就可以用普通模式合并，而`fast forward`合并就看不出来曾经做过合并



##### 四、Bug分支策略：

每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除

修复代号101的bug的任务时，创建一个分支`issue-101`来修复，但是当前正在`dev`上进行的工作没有提交：

1.可以用$ git stash把当前在dev 分支上的工作现场“储藏”起来，等以后恢复现场后继续工作，这时用$ git status查看工作区就是干净的

2.确定在哪个分支上修复bug，假定需要在`master`分支上修复，就从`master`创建临时分支

3.修复bug，然后提交

4.修复完成后，切换到`master`分支，并完成合并，最后删除`issue-101`分支

5.回到`dev`分支，用`git stash list`命令看看

6.恢复工作现场，

   git stash apply 恢复，并用`git stash drop`来删除；或者git stash pop恢复同时并删除

7.将`master`工作分支上修改的Bug，复制到`dev`分支，使2者同步，避免重复劳动

​    `cherry-pick`命令，让我们能复制一个特定的提交到当前分支

```
$ git stash
$ git status

$ git checkout master
$ git checkout -b issue-101

$ git add readme.txt 
$ git commit -m "fix bug 101"

$ git switch master
$ git merge --no-ff -m "merged bug fix 101" issue-101

$ git switch dev
$ git status
$ git stash list

$ git stash pop

$ git cherry-pick 4c805e2  //复制提交的区块到当前分支

```

##### 五、Feature分支策略

每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支

```
$ git switch -c feature-vulcan
$ git branch -d feature-vulcan  //分支提交合并后，才可
$ git branch -D feature-vulcan  //强制删除
```

##### 六、多人协作

1.从远程仓库克隆时，实际上Git自动把本地的`master`分支和远程的`master`分支对应起来了，远程仓库的默认名称是`origin`

- `master`分支是主分支，因此要时刻与远程同步；
- `dev`分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。

2.抓取分支

多人协作时，大家都会往`master`和`dev`分支上推送各自的修改

如果推送失败，则先本地更新 ，用pull合并 ，解决冲突并本地提交，再push

如果pull提示no tracking information，则说明地分支和远程分支的链接关系没有创建，用git branch --set-upstream-to=origin/dev dev建立连接

3.推送远程分支

```
$ git remote
$ git remote -v
$ git push origin master
$ git push origin dev

$ git checkout -b dev origin/dev
$ git pull origin dev

$ git branch --set-upstream-to=origin/dev dev
$ git push origin dev

```

##### 七、变基：

多人在同一个分支上协作时，很容易出现冲突。即使没有冲突，后push的不得不先pull，在本地合并，然后才能push成功，rebase操作可以把本地未push的分叉提交历史整理成直线,使得我们在查看历史提交的变化时更容易

```
$ git rebase
```



#### 其它

##### 打标签

`git tag <name>`就可以打一个新标签

`git tag`查看所有标签

`git show <tagname>`查看标签信息

```
$ git tag v1.0
$ git tag v0.9 f52c633  //commitID 

$ git tag -a v0.1 -m "version 0.1 released" 1094adb  //标签名，指定说明文字
```

##### 删除标签



```
$ git tag -d v0.1   //删除本地标签

$ git push origin v1.0      //推送本地标签到远程
$ git push origin --tags    // 一次性全部推送本地标签

$ git push origin :refs/tags/v0.9  //远程标签删除要先删除本地标签
```

##### 忽略文件

##### 配置别名

##### 版本回退

### Git服务器



### 分布式Git
