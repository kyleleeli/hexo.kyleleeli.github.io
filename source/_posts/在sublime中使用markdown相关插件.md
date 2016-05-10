---
title: 在sublime中使用markdown相关插件
date: 2016-05-10 17:27:44
tags: 
- sublime
- markdown
- plugin
permalink: sublime-related-markdown-plugins
---
### 安装Markdown Editing和Markdown Preview插件
按下键`Ctrl+Shift+p`调出命令面板，找到`Package Control: install Pakage`这一项。搜索markdown，找到`Markdown Editing`和`Markdown Preview`点击安装。

### Markdown Preview插件介绍
安装完插件后，我们来看一下具体的使用：
#### 使用
Markdown Preview较常用的功能是`preview in browser`和`Export HTML in Sublime Text`，前者可以在浏览器看到预览效果，后者可将markdown保存为html文件。

输入`Ctrl+Shift+P`调出命令窗口:
![ctrl+shift+p调出命令窗口](/uploads/20160510-1-1.png)
选择`Preview in Browser`就可以在浏览器中查看html效果，当然，也可以通过设置快捷键来快速预览：
在Sublime中，`Preferences`->`Key Bindings - User`，输入以下内容：
`{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"}}`
现在就可以通过快捷键`alt+m`快速预览效果了。

#### 设置语法高亮和mathjax支持
在`Preferences` -> `Package Settings` -> `Markdown Preview` -> `Setting - User`中添加如下参数：
``` python
{
    /*
        Enable or not mathjax support.
    */
    "enable_mathjax": true,

    /*
        Enable or not highlight.js support for syntax highlighting.
    */
    "enable_highlight": true
}
```

### Markdown Editing插件介绍
Markdown Editing插件安装完成后，具体的介绍可以查看github项目说明[MarkdownEditing](https://github.com/SublimeText-Markdown/MarkdownEditing)或者在Sublim通过`Preferences`->`Package Settings`->`Markdown Editing`->`README` 查看。

这里挑选几个个人感觉不错的功能介绍一下：
#### 快捷键
| Mac | Windows/Linux | 描述 |
|-----|---------------|------|
| `⌘⌥B` `⌘⌥I` | `Ctrl Shift B` `Ctrl Shift I` | 将选中或未选中的文字加粗或变为斜体，或反向操作|
| `⌘^ 1...6`|`Ctrl 1...6`|插入标题1 .. 标题6|

#### code snippet
输入 "mdi + tab" 会自动插入下面的图片标记
`![Alt text](/path/to/img.jpg "Optional title")`

输入 "mdl + tab" 会自动生成下面的链接标记
`[](link)`