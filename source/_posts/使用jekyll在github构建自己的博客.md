---
title: 使用jekyll在github构建自己的博客
date: 2016-05-07 16:49:12
tags: 
- jekyll
- github
- blog
categories:
- blog
permalink: use-jekyll-build-github-blog
---
现在越来越多的人，主要是程序员喜欢在Github上写博客，一切都任由你左右，一个commit就能提交一篇文章，还有着无限流量免费的空间，想想就惬意不止。

进入正题，如何利用Github和Jekyll搭建一个博客：

-----------------------------------------------------------------
## 1. 关于Github

![](/uploads/github.jpg)
- [如何高效利用Github](http://www.yangzhiping.com/tech/github.html)
- [git - 简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)

#### 免费托管到GitHub页面(Free hosting with GitHub Pages)
[阅读官方指引](https://pages.github.com/)
1. 在GitHub创建自己的库，名字必须是 username.github.io，
**注意：username必须是在github上注册的名称，而不能随意命名，否则访问 http://username.github.io 时会报404错误。**
2. 通过命令行或GitHub Desktop Clone库到本地；
3. 创建一个index.html页面，并提交到github服务器；
4. 通过浏览器访问 http://username.github.io ，如果正常显示index.html内容，则表示已经成功。

## 2. 关于Jekyll

![](/uploads/jekyll.jpg)
- [Jekyll中文指导手册](http://jekyllcn.com/)

[阅读官方指引](https://help.github.com/articles/using-jekyll-with-pages/)
GitHub Pages为了提供对HTML内容的支持，选择了Jekyll作为模板系统，Jekyll是一个强大的静态模板系统，作为个人博客使用，基本上可以满足要求，也能保持管理的方便，你可以查看[Jekyll官方文档](http://jekyllrb.com/docs/home/)。

#### 安装Jekyll
- 安装Ruby，如果是windows系统，使用RubyInstaller安装，下载地址：http://rubyinstaller.org/downloads/，
    安装时指定一个路径地址即可（安装时选择将ruby路径写入到环境变量PATH）。
- 安装Bundler，运行命令： `gem install bundler`。
    如果命令无法识别，则a步骤没有将ruby路径添加到PATH中，另外在办公网，尽量使用Staff-Wifi
- 切换到github本地库目录下，创建名称为 Gemfile 的文件，并将以下内容粘贴到文件内，保存。
    `source 'https://rubygems.org'`
    `gem 'github-pages'`
- 下载Ruby DEVELOPMENT KIT(http://rubyinstaller.org/downloads/),安装说明参考（https://github.com/oneclick/rubyinstaller/wiki/Development-Kit）
    将文件提取到某个目录，如D:\env\devkit
    `cd D:\env\devkit`
    `ruby dk.rb init`
    编辑 config.yml, 最后面加入 - D:/env/Ruby22-x64
    `ruby dk.rb review`，校验
- 回到github本地库目录下，运行 `bundle install`，等待安装。

#### 运行Jekyll
在github本地库根目录下，运行命令：`bundle exec jekyll serve`，启动后访问 http://localhost:4000 查看页面效果

#### 更新Jekyll为最新版本
在github本地库根目录下，直接运行命令 `bundle update` 即可

#### 安装python，http://www.python.org/download/

#### 安装 ‘Easy Install‘
下载 ez_setup.py 并保存，然后从python运行 python “目录/ez_setup.py”

#### 开始使用
基本的Jekyll结构如下：
``` html
|-- _config.yml
|-- _includes
|-- _layouts
|   |-- default.html
|   `-- post.html
|-- _posts
|   |-- 2007-10-29-why-every-programmer-should-play-nethack.textile
|   `-- 2009-04-26-barcamp-boston-4-roundup.textile
|-- _site
`-- index.html
```

**_config.yml**

配置文件，用来定义你想要的效果，设置之后就不用关心了。

**_includes**

可以用来存放一些小的可复用的模块，方便通过{ % include file.ext %}（去掉前两个{中或者{与%中的空格，下同）灵活的调用。这条命令会调用_includes/file.ext文件。

**layouts**

这是模板文件存放的位置。模板需要通过YAML front matter来定义，后面会讲到，{ { content }}标记用来将数据插入到这些模板中来。

**posts**

你的动态内容，一般来说就是你的博客正文存放的文件夹。他的命名有严格的规定，必须是2012-02-22-artical-title.MARKUP这样的形式，MARKUP是你所使用标记语言的文件后缀名，根据_config.yml中设定的链接规则，可以根据你的文件名灵活调整，文章的日期和标记语言后缀与文章的标题的独立的。

**site**

这个是Jekyll生成的最终的文档，不用去关心。最好把他放在你的.gitignore文件中忽略它。

#### YAML Front Matter和模板变量

对于使用YAML定义格式的文章，Jekyll会特别对待，他的格式要求比较严格，必须是这样的形式：

```yaml
---
layout: post
title: Blogging Like a Hacker
---
```

前后的---不能省略，在这之间，你可以定一些你需要的变量，layout就是调用_layouts下面的某一个模板，他还有一些其他的变量可以使用：

- `permalink` 你可以对某一篇文章使用通用设置之外的永久链接
- `published` 可以单独设置某一篇文章是否需要发布
- `category` 设置文章的分类
- `tags` 设置文章的tag
上面的title就是自定义的内容，你也可以设置其他的内容，在文章中可以通过{ { page.title }}这样的形式调用。

#### 使用[Jekyll-Bootstrap](http://jekyllbootstrap.com/)模板
- 安装 Jekyll-Bootstrap
``` shell
git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
cd USERNAME.github.com
git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
git push origin master
```
- 本地运行Jekyll
`$ gem install jekyll`
`$ cd USERNAME.github.com` 
`$ jekyll serve`
- 创建日志
`$ rake post title="Hello World"`

- 部署
`$ git add .`
`$ git commit -m "Add new content"`
`$ git push origin master`

**注意：Jekyll-boostrap模板已经很长时间没有更新，建议不要直接使用该模板，可以根据ruby语言，自己构建模板**

## 3. 给Github项目创建Jekyll站点
- 在github.com进入到指定的repository
- 创建gh-pages 分支即可
**分支的名称必须为：gh-pages**