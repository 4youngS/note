### linux运维

1.CentOS6安装在虚拟机上（略）

```
id/pwd root/123456
查看IP地址 ：ifconfig  ;ip addr
查看版本：cat /etc/redhat-release，这种方法只适合Redhat系的Linux：
cat /proc/version
重启：
	reboot 普通重启
	shutdown -r now 立刻重启(root用户使用)
```

2.ssh连接虚拟机

```
1.看网络地址是否ping通，将虚拟机改成桥接模式
https://blog.csdn.net/weixin_39651356/article/details/105769127
https://www.cnblogs.com/cherry-ning/articles/15520623.html
```

3.怎么停止ping命令?

```
停止linux下正在执行的ping命令:
在Linux系统中，当能ping通一个主机时，此时ping命令会一直执行，要想终止，可采用CTRL+c或CTRL+z方式退出。
也可以设置选项方式，使得ping命令执行若干次包就终止。
ping 192.168.34.44 -c 4，此时ping命令将执行4次。
```

3.关于yum源失效的问题?

```
6.5的yum源已经停止更新，
1.fastestmirror.conf中修改为enabled=0
	sed -i "s|enabled=1|enabled=0|g" /etc/yum/pluginconf.d/fastestmirror.conf
2.备份
	mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
3.下载到 
curl -o /etc/yum.repos.d/CentOS-Base.repo https://www.xmpan.com/Centos-6-Vault-Aliyun.repo
 
yum clean all
yum makecache

或者将地址转换成
https://mirrors.tuna.tsinghua.edu.cn/centos-vault/
http://mirrors.aliyun.com/centos-vault/
yum 安装
https://blog.csdn.net/z20021111/article/details/125630652
```

4.安装vmware-tools

```
二、安装：

挂载光驱：
# mkdir /mnt/cdrom       ///创建挂载目录
# mount /dev/cdrom /mnt/cdrom    ///将光驱挂载到/mnt/cdrom目录
# cd /mut/cdrom 
里面有两个文件，.rpm文件是给Red Hat准备的，只需要.tar.gz的那个
# cp VMwareTools-XXXX.tar.gz /usr/local     ///复制VMware-tools到/usr/local目录 ，其中XXX是版本号。
# cd /usr/local     ///切换到local目录
# tar -vzxf VMware Tools-XXX.tar.gz     ///解压，区分大小写，也可以先输入前几个字母按Tab键系统补充后面的。


环境好了，下面开始安装VMware-tools
# cd vmware-tools-distrib  ///进入解压出来的目录
# ./vmware-install.pl    ///运行vmware-install.pl文件开始安装。
会提示若干次yes or no 直接一路回车就行，直到最后出现“Enjoy——the VMware team”的字样，VMwareTools安装完成。

如出现错误，是缺少perl环境造成
yum -y install gcc gcc-c++ perl make kernel-headers kernel-devel

三、卸载：

到刚才解压的目录/usr/local/vmware-tools-distrib/bin 目录或者 /usr/bin
# cd /usr/local/vmware-tools-distrib/bin
# ./vmware-uninstall-tools.pl    ///运行卸载程序
# rm -rf /etc/vmware-caf     ///递归强制 删除残留目录
# rm -rf /etc/vmware-tools   ///递归强制 删除残留目录
#  rm -rvf /usr/lib/vmware-tools     ///递归强制 删除残留目录

https://blog.csdn.net/wojiuguowei/article/details/93714447
```

5.安装vim

```
yum -y install vim*
自动下载全部VIM包并安装
VIM的配置：
sudo vim /etc/vimrc
最后一行，输入他们，可以让您的VIM变得更漂亮、舒服。
    set tabstop     " tab 长度设置为4
    set nobackup    " 覆盖文件时不备份
    set cursorline  " 突出显示当前行
	set nu          " 设置显示行号
    set showmode    " 设置在命令行界面最下面显示当前模式等
    set ruler       " 在右下角显示光标所在的行数等信息
    set autoindent  " 自动缩进设置每次单击Enter键后，光标移动到下一行时与上一行的起始字符对齐
    syntax on       " 即设置语法检测，当编辑C或者Shell脚本时，关键字会用特殊颜色显示
添加好了之后，按Esc，然后输入:wq
退出并保存即可。

vim常用命令：
        h,j,k,l 左下上右
        dd 删除一行
        yy 复制一行
        v选中 + y 复制
        p 粘贴
        ctrl + e 历史打开文件
        , + a 剪切板
        x 选中的部分删除
        u 撤销上一次操作
        ctrl + r 撤销上一次的撤销
        shift + v 全选一行
        shift + v + h,j,k,l 全选多行
        gg 光标移动到最上
        shift+g 光标移动到最下
        shift+4 光标移动到最后
        0 光标移动到最前
        w 光标移动一个词
        b 光标回退一个词
        g + , 跳转到上次编辑位置的下次
        g + ; 跳转到上次编辑位置
编辑模式：
        i 开启编辑模式
        o 换行开启编辑模式
        a 跳到下一格开启编辑模式
        s 删掉光标选中开启编辑模式
        esc 取消编辑模式
        , + t 开启NERDTree
vim命令:
        :vs 垂直分页
        :sp 水平分页
        :ctrl + w 分页跳转/切换
        :q 退出
        :q! 强制退出
        :w 保存
        :wq 保存退出
        :wq! 保存强制退出
        :wqa 全部保存退出
        :wqa! 全部保存强制退出
        :set nonumber 取消行号
        :set number 恢复行号
        :set nowrap 取消换行模式
        :set wrap 开启换行模式
```

6.Ubuntu 应用

```
1.当使用以下命令升级Ubuntu 16.04到18.04时

do-release-upgrade
如果出现以下提示：
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
可以用以下命令进行修复：（依次执行即可）

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dist-upgrade
中间遇到问题或者BUg
sudo dpkg --configure -a    --包问题    
sudo apt-get -f install    --解决依赖问题，重新安装
可解决然后重写执行命令，完成就好，

然后再执行升级命令进行升级即可
sudo do-release-upgrade

2.升级为图形界面
sudo apt-get install ubuntu-desktop
VM桌面自适应
sudo apt-get open-vm-tools-desktop
sudo apt-get update
sudo apt-get install open-vm-tools-desktop -y

3.Ubuntu开机无法进入桌面
https://blog.csdn.net/jxq1994/article/details/124489380
可以进入safe模式然后设置后自动进入
```



6.Ubuntu安装Python开发环境

```
1.更新
2.安装VIM
sudo apt-get install vim
3.pyenv+virtualenv
    pyenv管理版本环境
    pyenv-virtualenv插件管理虚拟环境
    pyenv环境管理工具好处：
        隔离项目之间的第三方包依赖
        在没有权限的情况下安装新的Python软件包
        部署应用时，把开发环境的虚拟环境打包到生产环境
4.
     git clone https://github.com/pyenv/pyenv.git ~/.pyenv
 配置环境
    echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
    echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(pyenv init -)"' >> ~/.bashrc
激活 
	source .bashrc
            pyenv version
            pyenv install
            pyenv global
			pyenv install -l
切换
	# xxx表示要切换的版本
  **有三种切换方式 glocal local shell**
　　1. glocal 全局环境,在未再次使用 glocal切换环境之前，一直使用此环境。
　　2. local 本次登录环境。重启后，则环境失效，并返回当前glocal的环境。
　　3. shell 局部（临时）环境。关闭命令行窗口，则环境失效，并返回当前glocal的环境。
   pyenv glocal xxx  
下载virtualenv
	git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
	echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
　　 source ~/.bashrc
　　 
　常用virtualenv　 
　　 pyenv virtualenv 3.7.0 env370
　　 pyenv activate env370
　　 pyenv deactivate
　　 rm -rf ~/.pyenv/versions/env370
```

创建桌面快捷方式

```
https://www.cnblogs.com/beimengRock/p/16026244.html


```

7.忘记root密码

```
https://blog.csdn.net/wyynetcn/article/details/122635937?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-122635937-blog-122925462.pc_relevant_3mothn_strategy_and_data_recovery&spm=1001.2101.3001.4242.2&utm_relevant_index=4
```





```
1.lsb_release -a 失效的问题，
	yum install -y redhat-lsb
2.centos网络连接失败后虚拟机设置的问题
	https://www.muzhuangnet.com/show/79230/2.html
	cd /etc/sysconfig/network-scripts
	vim ifcfg-ens33
	service network restart
3.解决“ssh服务器拒绝了密码 请再试一次”问题
	https://zhuanlan.zhihu.com/p/478405010
4.实在解决不了，可以用Public Key 方式登录，
	https://www.codetd.com/en/article/13615263
```



```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAuFx1JyeKla2bs2cCWk9bB5bQXeW/DJv/qJ404iTsSPcTocj/qzAUTp0v6U0Ec7XkV638Mp4sWef3gDkUxwLF7llwcYSr5IkmWmohoWkhA+6ozZ4fldODsTh5LSv1k2nDHHqR5P5ivdxZyy1pc/uYNsNcyCDhjmHqMZeVBovwSY38SNAn6aaoCIbux/Uw/33gi0Jx3ilKKOC3MrAdQLbnTLm3abcoT9oV+AI+7IXyE2NavmH5ifY4HMnrFypYAMuNSgP/KNhWeDVkRGoSy/A5Ugt9A0cq4PW0faJ+cW8dCSGrTCRb/nwmzK9Gwnstbzii0RnNvSlbukpURzsdm0iUXQ==
```

```

```

