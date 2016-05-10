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
无意间看到一个github的博客[w4lle.github.io]，感觉风格不错，然后查看了github上的项目源码，发现只有已经生成的静态文件，并无jekyll相关脚本。于是在博客园搜了一下：zzk.cnblogs.com 搜 jekyll，看到一篇”将博客从jekyll迁移到了hexo“ http://www.cnblogs.com/jasondan/p/3499227.html，说是一个台湾小伙使用nodejs开发的，赶紧跑到官网上体验了一把，果然找到了跟之前看到的博客一样风格的模板，于是看下文档如何使用。台湾小伙果然靠谱，既懂中国国情，也能接轨国际。



### 部署：
- 安装 hexo-deployer-git时，必须在目标目录下（如D:\github\hexo.kyleleeli.github.io）
$ npm install hexo-deployer-git --save
- 执行 hexo deploy时，需要使用 git bash，同样需要定位到目标目录下

### 参考：
[使用hexo搭建github.io博客(一)](http://www.cnblogs.com/liulangmao/p/4323064.html)

