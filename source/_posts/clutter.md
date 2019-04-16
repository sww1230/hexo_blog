---
title: 杂烩 Screen MariaDB mock mysql gitlab 允许MySqlWorkbench访问数据库 ...
date: 2019-04-01
tags: shell
---

### 安装数据库
````
yum install mariadb-server.x86_64

systemctl start mariadb

mysql -uroot

show databases
select user,host from mysql.user;

启动 phpmyading
systemctl restart httpd
````


### cnpm库系统搭建
	1. 仓库地址：github.com/fengmk2/cnpmjs.org.git
	2. 文档说明：https://www.jianshu.com/p/659fb418c9e3

### mockapi接口系统搭建
	1. rap2-delos: 后端数据API服务器，基于Koa + MySQL   
		https://github.com/thx/rap2-delos
	2. rap2-dolores: 前端静态资源，基于React
		https://github.com/thx/rap2-dolores

### gitlab仓库系统搭建
	> 后续增加


### git 去掉最近一次的提交
````
git reset --hard HEAD~1
git push -f // 强制推送提交代码
````


### 登录服务器的用户名IP及密码
````
ssh username@127.0.0.1
password123
````

### 远程登录数据库
````
mysql -u root -h 127.0.0.1 -p
password123@!#
````


### 安装node

````
yum -y install nodejs

超级简单的升级node.js的方法
npm install -g n
安装稳定的版本
n stable
````

### 安装MariaDB数据库

> MariaDB数据库管理系统是MySQL的一个分支，主要由开源社区在维护，采用GPL授权许可 MariaDB的目的是完全兼容MySQL，包括API和命令行，使之能轻松成为MySQL的代替品。

1. 安装mariadb
	````
	yum -y install mariadb-server mariadb-client
	````

2. maria常用命令
	````
	systemctl start mariadb #启动服务
	systemctl enable mariadb #设置开机启动
	systemctl restart mariadb #重新启动
	systemctl stop mariadb.service #停止MariaDB
	````

3. 登录数据库 重置密码
	````
	# 本机登录
	mysql -u root -p;
	SET PASSWORD = PASSWORD('10quan10m@i');
	# 远程登录
	mysql -u root -h 192.168.2.128 -p
	password123@!#
	````

4. 数据库常用命令
	````
	显示DBMS的所有数据库；
	show databases;
	创建数据库
	create database db_name；
	删除数据库
	drop database db_name；
	选择数据库 
	use db_name;

	显示当前使用的数据库
	select database();
	显示当前登录的用户名称
	select user();
	显示当前数据库支持及默认的存储引擎
	show engines;
	显示当前数据库的触发器信息
	show triggers;

	显示当前数据库的表信息
	show tables;
	创建数据库表
	create table table_name；
	删除数据库表
	drop table table_name；
	显示当前数据库的表状态
	show table status;
	显示表结构信息
	describe table_name; 或 desc table_name; 或 show columns from able_name;
	显示表中的所有记录
	select * from table_name；

	查看mysql端口号
	mysql> show global variables like 'port';

	````

### 安装git
````
yum install -y git
````


### 安装 screen
````
Screen是一款由GNU计划开发的用于命令行终端切换的自由软件。用户可以通过该软件同时连接多个本地或远程的命令行会话，并在其间自由切换。GNU Screen可以看作是窗口管理器的命令行界面版本。它提供了统一的管理多个会话的界面和相应的功能。

yum install -y screen
screen -dmS RAP2
screen -x RAP2
启动一个api后台服务
npm start
control + a + d
````

### rap2前端服务nginx配置
````
git clone https://github.com/thx/rap2-dolores.git front-end

nginx配置
server{
    listen *:80;
    server_name mockapi.nixin8.com;
    root /opt/rap2/front-end/build;
    index index.html;
    location / {
        root /opt/rap2/front-end/build;
        index index.html;
    }
}
````

### RAP2-Delos 后端数据API服务器
````
1. git clone https://github.com/thx/rap2-delos.git back-end
2. cd back-end
3. npm install
4. 确认/config/config.dev.js中的配置
5. npm run build
6. 修改/config/config.prod.js中的服务器配置
7. npm start
````

### 允许MySqlWorkbench访问数据库
````
在服务器上进行操作，进入mysql
mysql>GRANT   ALL   PRIVILEGES   ON   *.*   TO   'root'@'%'   WITH   GRANT   OPTION  //赋予任何主机访问数据的权限
mysql>FLUSH   PRIVILEGES  //修改生效
mysql>EXIT  //退出MySQL服务器
````



### 其它命令记录一下

```
场景：
无hexo这个命令
只能/data/www/node-v8.4.0-linux-x64/bin/hexo这样执行该命令

解决：
vi /etc/profile
export PATH=$PATH:/data/www/node-v8.4.0-linux-x64/bin/
source /etc/profile
```

```
远程复制：
scp md.zip root@192.168.258.126:/home/sww 

移动：
mv md.zip /data/www/sww/

解压：
unzip md.zip
```

```
跟踪日志：
tailf /data/logs/nginx/error_sww.log

执行过的命令记录：
history
```

```
ssh-keygen生成git ssh密钥:
cd ~/.ssh
ssh-keygen -t rsa -C "happysww1230@163.com"
密钥会包含id_rsa和id_rsa.pub两个文件，分别表示生成的私钥和公钥
使用cat ~/.ssh/id_rsa.pub命令，并将相应内容复制到源代码管理服务器即可实现git的无密码管理
```