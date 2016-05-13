---
title: 使用hexo在github构建自己的博客
date: 2016-05-08 08:39:35
categories: 
- blog
tags: 
- hexo
- github
- blog
permalink: use-hexo-build-github-blog
---
# 使用hexo在github构建自己的博客

之前提到过使用jekyll搭建博客，并且使用boostrap-jekyll模版，但因为boostrap-jekyll项目长期未更新，已经跟不上jekyll的进度，再加上是国外作者设计的模版，跟国内大部分常见的模版还是有不小区别。
无意间看到一个github的博客，感觉风格不错，然后查看了github上的项目源码，发现只有已经生成的静态文件，并无jekyll相关脚本。于是在博客园搜了一下：zzk.cnblogs.com 搜 jekyll，看到一篇[将博客从jekyll迁移到了hexo](http://www.cnblogs.com/jasondan/p/3499227.html)，说是一个台湾小伙使用nodejs开发的，赶紧跑到官网上体验了一把，果然找到了跟之前看到的博客一样风格的模板，看了下文档感觉上手很方便，说明文档也有中英文支持。

### 搭建步骤
#### 1. 安装好node和git,注册好github账号
具体操作此处省略，查看对应的官方网站即可

#### 2. 安装hexo
执行: `npm install -g hexo`
比较耗时，常常安装了一半就卡住装不下去了,fq后就ok了...

#### 3. 创建hexo文件夹
自己找一个喜欢的路径,创建hexo文件夹,我的是安装在 E:\hexo 下的. 
cmd窗口切换到对应的目录下,然后执行: `hexo init`
也可以在 E:\hexo 下右键,选择git bash,在窗口中执行 `hexo init`
它就自动安装了需要的文件.

#### 4.安装依赖:
继续执行: `npm install`
安装好了所有的依赖

#### 5.完成本地安装:
继续在 E:\hexo 下执行:  `hexo generate`
继续执行: `hexo server`或`hexo server --watch`
然后在打开浏览器 localhost:4000 ,就可以看到,本地已经安装好了.

### 部署：
- 安装 hexo-deployer-git时，必须在目标目录下（如D:\github\hexo.kyleleeli.github.io）
$ npm install hexo-deployer-git --save
- 执行 hexo deploy时，需要使用 git bash，同样需要定位到目标目录下

### 参考：
- [使用hexo搭建github.io博客(一)](http://www.cnblogs.com/liulangmao/p/4323064.html)
- [基于Hexo+GitHub Pages 免费搭建个人博客最强教程](http://www.jianshu.com/p/2b9f202c13fd)


