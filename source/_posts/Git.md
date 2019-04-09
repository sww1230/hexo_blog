---
title: Git常用命令
date: 2019-03-25
tags:
---

## 参考文档
* [git fork工作流](http://blog.jobbole.com/76861/)
* [git远程操作指南](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)
* [git分支管理策略](http://www.ruanyifeng.com/blog/2012/07/git.html)
* [git checkout命令详解](http://www.tuicool.com/articles/A3Mn6f)

## 工作流
* [Git 怎样保证fork出来的project和原project（上游项目）同步更新](http://www.tuicool.com/articles/Mnmmqyi)
	1. 在 Fork 的代码库中添加上游代码库的 remote 源，该操作只需操作一次即可。如: 其中# upstream 表示上游代码库名， 可以任意。

		````
		git remote add upstream https://github.scm.corp.ebay.com/montage/frontend-ui-workspace
		````

	2. 将本地的修改提交 commit
	3. 在每次 Pull Request 前做如下操作，即可实现和上游版本库的同步。
	
      ````
      git remote update upstream
      git rebase upstream/{branch name}
 		````
		需要注意的是在操作3.2之前，一定要将checkout到{branch name}所指定的branch，如: 
		
		````
		git checkout develop
		````

	4. Push 代码到 Github
		
		````
		git push origin dev.161625
		````


## 分支
* 查看分支
	* git branch -a 
* 删除远程分支
	* git branch -r -d origin/<branch-name>
	* git push origin :<branch-name> 
* 删除不存在对应远程分支的本地分支
	* 查看远程分支
	* git remote show origin
		* refs/remotes/origin/b1 stale (use 'git remote prune' to remove)
		* git remote prune origin
	* 更简单的用法
		* git fetch -p  
* 新建分支

	`````
	//create branch
	git checkout -b dev.170220
	
	//coding
	
	//update upstream
	git remote update upstream 
	git rebase upstream/dev.170220
	
	//push
	git push --set-upstream origin dev.170220
	````
	
	====
	
	````
		创建分支： $ git branch mybranch
		切换分支： $ git checkout mybranch
		创建并切换分支： $ git checkout -b mybranch
		
		更新master主线上的东西到该分支上：$git rebase master
		
		切换到master分支：$git checkout master
		
		更新mybranch分支上的东西到master上：$git rebase mybranch
		
		提交：git commit -a
		
		对最近一次commit的进行修改：git commit -a –amend
		
		commit之后，如果想撤销最近一次提交(即退回到上一次版本)并本地保留代码：git reset HEAD^
		合并分支：(merge from) $ git checkout master
		$ git merge mybranch (merge from mybranch)
		删除分支： $ git branch -d mybranch
		强制删除分支： $ git branch -D mybranch
		列出所有分支： $ git branch
		查看各个分支最后一次提交： $ git branch -v
		
		查看哪些分支合并入当前分支： $ git branch –merged
		
		查看哪些分支未合并入当前分支： $ git branch –no-merged
		
		更新远程库到本地： $ git fetch origin
		推送分支： $ git push origin mybranch
		取远程分支合并到本地： $ git merge origin/mybranch
		取远程分支并分化一个新分支： $ git checkout -b mybranch origin/mybranch
		删除远程分支：　　　　　　　　　　　　　　　　　$ git push origin :mybranch
		
		rebase: $ git checkout mybranch
		$ git rebase master (rebase from master)
		
		举例： $ git checkout server
		$ git rebase –onto master server client
		$ git checkout master
		$ git merge client (fostforward)
		$ git rebase master server (checkout sever)
		$ git merge server
		$ git branch -d client
		$ git branch -d server
	````
			
## tag
* 删除tag
	* git tag -d <tagname>
	* git push origin :refs/tags/<tagname>
	
## 子模块
* 子模块（https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)

	```
 	git submodule update --remote
	```
	参考：http://blog.csdn.net/wangjia55/article/details/24400501
	```
	git submodule update --init --recursive
	```
[Git Submodule管理项目子模块](http://www.cnblogs.com/nicksheng/p/6201711.html)




## 安装数据库

yum install mariadb-server.x86_64

systemctl start mariadb

mysql -uroot

show databases
select user,host from mysql.user;


启动 phpmyading
systemctl restart httpd



# 桌面可视化编辑工具

## 参考文档
* [Eletron](https://electronjs.org/)
	````
	Electron 是一款可以利用 Web技术 开发跨平台桌面应用的框架，最初是 Github 发布的 Atom 编辑器衍生出的 Atom Shell，后更名为 Electron。
	````
* [Create React App](https://github.com/facebook/create-react-app)


### Electron 镜像
````
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install -g electron
````

### Electron 示例
````
git clone https://github.com/electron/electron-quick-start
cd electron-quick-start
npm install
npm start
````

### Create React App
````
npx create-react-app my-app
cd my-app
npm start
````

### Electron 知识点
````
//返回一个隐藏标题栏的全尺寸内容窗口
mainWindow = new BrowserWindow({width: 750, height: 500, titleBarStyle: 'hidden'})
//可拖拽窗口区域css设置
style="-webkit-app-region: drag"
````

````
默认打开浏览器
openBrowser(urls.localUrlForBrowser);
````

### commander
* 一个帮助快速开发Nodejs命令行工具的package

### respawn

### [electron进程与进程之间的通信](https://segmentfault.com/a/1190000011728194)
### [child_process](https://segmentfault.com/a/1190000007735211)
> 在node中，child_process这个模块非常重要。掌握了它，等于在node的世界开启了一扇新的大门。熟悉shell脚本的同学，可以用它来完成很多有意思的事情，比如文件压缩、增量部署等，感兴趣的同学，看文本文后可以尝试下。

* 创建进程
> 下面列出来的都是异步创建子进程的方式，每一种方式都有对应的同步版本。
> .exec()、.execFile()、.fork()底层都是通过.spawn()实现的。
> .exec()、execFile()额外提供了回调，当子进程停止的时候执行。

