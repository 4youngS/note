

```
cat /etc/shells  : 列出所有shell类型
echo $SHELL ： 确认用户用的哪一种shell类型
hostname： 查看主机的完整名称
nano :命令行下的编辑工具
ll /bin/bash :查看文件的详细信息
type COMMAND :区分是否是内部命令还是外部
whereis COMMAND：详细查看命令的信息
hash：查看系统命令存储hash表
alias cdnet='cd /etc/sys' : 临时定义别名用于下次直接输入，放在.bashrc可以永久保持
unalias cdnet  :取消别名，同理彻底删除
当定义的别名与原始命令相同时，加'',""./等可以区分

lsblk：显示挂载盘符
lscpu：显示CPU
free -h：显示硬盘信息
echo $PATH
echo $SHELL 查看当前支持的shell
echo $PS1
ll /bin/bash
ifconfig
tty
who
pwd :显示在哪个目录下，当前路径 
lsb_release -a:显示系统版本
uname -r:显示内核
cat etc/centos-release  显示系统版本
cat file : 查看file文件内容
cat /etc/shells 查看系统支持哪些shell
help ,enable 查看内部命令

```



```
pwd ,cd ,cat ，
ls ,ls -a
```

同步服务器时间

```
vim  /etc/ntp.conf   //编辑该文件
server 对方服务器的IP地址  iburst  //添加对方服务器地址
systemctl start ntpd   //重启服务OS7
service ntpd start    //OS6
```

时间

```
clock：显示主板时间
date：Linux内核时间，月日小时分年.秒 修改格式分
clock -W ：主板时间同步内核时间
clock -s : 内核时间同步主板时间
ntpdate 对方服务器的地址 ：同步对方服务器地址
cat /etc/localtime  查看时区
localectl
localetcl status
cal -y 整年日历
timedatectl list-timezones 所有时区
timedatectl status
timedatectl set-timezone
```



```
shutdown -h +10
shutdown -c
w :显示终端的所有操作
rpm -ivh  :安装

screen -S help ：定义help名称的远程连接
screen -ls  ：显示远程连接
screen -x help  ：加入help名称的远程连接
exit 

rm 
touch
rm -f .bash_history
```





```
basename
dirname
man 
info
.当前目录
.. 上一级目录
```



```
systemctl status sshd.service #查看ssh服务状态
service sshd restart #重启sshd进程

ps aux #查看系统进程
grep gdm /etc/passwd #查看系统进程gdm信息
cat /etc/shadow
ll 
id root

useradd yang
passwd yang
usermod -L yang
usermode -U yang
userdel -r name
id 
su  name #切换身份,不完整，目录环境还在原账号
su - name
```

