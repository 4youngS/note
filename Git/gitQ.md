## 问题与实践

#### git 提交区别

```
$ git add .   //监控工作区的状态树，工作区所有变化全部添加到本地git缓存区中，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。
$ git add -u  //监控已经被tracked的文件，提交修改和删除到本地git缓存区中，但新文件未被tracked，不会被提交
$ git add -A  //两个功能合集，即修改+新增+删除，并全部tracked
```

#### git提交步骤

1.git status  查看当前状态

2.提交暂存区，git add，git commit 

3.git pull ，取回远程主机某个分支的更新，再与本地的指定分支合并，查看冲突并解决

4.git push ，提交到git本地仓库的代码推送到远程主机的某个远程分支之上

```
$ git status
$ git add .
$ git commit -m '0704new1'
$ git pull origin master
$ git push -u origin master
```

#### github push出错

You can't push to git:// Use https://

```
$ git remote rm origin
$ git remote add origin https://github.com/
$ git push -u origin master
```

