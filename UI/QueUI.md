### 安装nodejs,搭建Vue环境

```txt
1.下载node.js的msi在线安装文件，然后一路next安装完成（期间遇到问题，通过右键msi文件选择管理员授权解决） http://nodejs.cn/download/
2.新建nodejs缓存和全局文件夹，在安装目录C:\Program Files\nodejs下面新建node_global和node_cache两个文件夹,然后cmd执行命令：
    npm config set cache "C:\Program Files\nodejs\node_cache"
    npm config set prefix "C:\Program Files\nodejs\node_global"   
3.配置nodejs环境变量
   用户变量  修改PATH为  C:\Program Files\nodejs\node_global
   系统变量  新建NODE_PATH 为  C:\Program Files\nodejs
   系统变量  修改Path，在原先nodejs路径后面修改为  C:\Program Files\nodejs\;C:\Program Files\nodejs\node_modules
4.安装基于nodejs的淘宝镜像
    重点使用管理员权限打开cmd,执行以下命令，配置镜像站是为了安装快速+安装cnpm
    npm install -g cnpm --registry=https://registry.npm.taobao.org
5.安装vue和vue脚手架
    cnpm install vue -g
    cnpm install vue-cli -g
    
    如出现'cnpm' 不是内部或外部命令,也不是可运行的程序，是没有配置环境变量的 path 
    
新建Vue项目   
#创建一个基于webpack模板的新项目
新建一个文件夹nodeone
cmd 进入创建的文件夹 cd /d d:\nodeworkspace\nodeone
vue init webpack nodeone
期间会有很多反馈，按照提示回车就可以了，安装下载文件
# 切换至项目路径
cd d:\nodeworkspace\nodeone
# 安装项目依赖文件
cnpm install
# 项目启动
cnpm run dev 


```