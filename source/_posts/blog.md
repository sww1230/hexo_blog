---
title: Hexo + github 搭建个人博客
date: 2019-04-09
tags:
---

### 一. 在github上先创建2个库

  1. 存储frontEnd_blog项目 - hexo编译后的资源存储在这里 -- [参考](https://github.com/sww1230/frontEnd_blog)
  2. 存储hexo_blog项目 [参考文档](https://hexo.io/zh-cn/docs/) -- [参考](https://github.com/sww1230/hexo_blog)


### 二. 设置frontEnd_blog项目

  1. 点击Settings
  2. 在GitHub Pages 下，点击 Choose a theme，随便选择一个主题
  3. 然后在GitHub Pages 下会看到：
    Your site is published at https://sww1230.github.io/frontEnd_blog/
    设置完毕后你就可以通过 username.github.io(username为你的用户名访问你的博客了)


### 三. 上传并配置hexo_blog

1. 安装hexo
````
  npm install hexo-cli -g
  hexo init hexo_blog
  cd hexo_blog
  npm install
  hexo g #生成或 hexo generate
  hexo s #启动本地服务器 或者 hexo server,这一步之后就可以通过http://localhost:4000  查看了
  hexo new "文章名" #新建文章
  hexo new page "页面名" #新建页面 
````

2. 修改_config.yml
````
title: frontEnd_blog
subtitle: 前端技术积累沉淀
author: wenwu.shang
url: https://sww1230.github.io/
root: /frontEnd_blog/

deploy:
  type: git
  repo: https://github.com/sww1230/frontEnd_blog.git
  branch: master 
````

3. 编译hexo_blog部署至frontEnd_blog
````
hexo d
````

4. 上传代码至hexo_blog库
````
git init
git remote add origin https://github.com/sww1230/hexo_blog.git
git add .
git commit -m 'update'
git push
````
