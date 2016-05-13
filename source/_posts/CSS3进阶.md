---
title: CSS3进阶
date: 2016-05-12 11:29:37
tags:
- CSS3
permalink: css3-learning
---
最近要准备开发移动web app项目，之前一直是在做PC端的Web项目，为了在移动端有更好的体验，必须要重新学习html5和css3，写这篇文章的目的也是为了记录自己的学习历程。同时，会把自己觉得比较重要，且难以理解的知识做重点分析和示例。

## 1. 从border开始（CSS边框）

#### CSS3 圆角
_一个用于设置所有四个边框- *-半径属性的速记属性_

**语法**
`border-radius: 1-4 length|% / 1-4 length|%;`
_**注意**: 每个半径的四个值的顺序是：左上角，右上角，右下角，左下角。如果省略左下角，右上角是相同的。如果省略右下角，左上角是相同的。如果省略右上角，左上角是相同的。_

|值 |描述|
|---|---|
|length|  定义弯道的形状。
|%   |使用%定义角落的形状。

__示例__
比较简单，不再详述

```css
div
{
    border:2px solid;
    border-radius:25px;
}
```


#### CSS3盒阴影
**语法**
`box-shadow: h-shadow v-shadow blur spread color inset;`
_**注意**：boxShadow 属性把一个或多个下拉阴影添加到框上。该属性是一个用逗号分隔阴影的列表，每个阴影由 2-4 个长度值、一个可选的颜色值和一个可选的 inset 关键字来规定。省略长度的值是 0。_

|值 |说明|
|---|-----|
|h-shadow |必需的。水平阴影的位置。允许负值
|v-shadow |必需的。垂直阴影的位置。允许负值
|blur    |可选。模糊距离
|spread  |可选。阴影的大小
|color   |可选。阴影的颜色。在CSS颜色值寻找颜色值的完整列表
|inset   |可选。从外层的阴影（开始时）改变阴影内侧阴影

__示例__
```css
div
{
    box-shadow: 10px 10px 5px #888888;
}
```

#### CSS3边界图片
__语法__
`border-image ： none | <image> [ <number> | <percentage>]{1,4} [ / <border-width>{1,4} ]? [ stretch | repeat | round ]{0,2}`

`border-image: source slice width outset repeat;`

|值 |描述
|---|----
|border-image-source |用于指定要用于绘制边框的图像的位置
|border-image-slice  |图像边界向内偏移
|border-image-width  |图像边界的宽度
|border-image-outset |用于指定在边框外部绘制 border-image-area 的量
|border-image-repeat |这个例子演示了如何创建一个border-image 属性的按钮。

**其中 `border-image-slice` 是比较难理解的一个属性，我们重点分析这个属性的使用**
border-image-slice相当于剪切功能，将目标图片从`上、右、下、左`的顺序切了四刀，切的时候支持number或percentage两种方式，number就是像素数，percentage是百分比。

比如，边框图片的大小是300px*240px,我们取百分比为25% 30% 15% 20%，那么它们实际对应的效果就是剪切了图片的60px 90px 36px 60px的四边大小，如图所示：
![按比例切割示例图片](/uploads/border-image-slice.jpg)

也可以按像素：
![](/uploads/groovy-border-image-slice.png)

切完之后就变成了一个九宫格，我们再来以W3C官网的图片为例：
![](/uploads/border-image-jugongtu.png)
![](/uploads/border-image-jugongtu-2.png)
切完之后，四个边角的图片是保持现状不变，不能应用round（平铺）、repeat（重复）、strength（拉伸）效果的（即：2，4，6，8位置的图片）。能够应用这三种效果的就是（1，3，7，9）四个位置的图片。

**水平round效果**
```css
  .border-image {
    width: 150px;
    height: 100px;
    border: 27px solid orange;
  }
  .border-image-round {
     -webkit-border-image: url("../images/border.png") 27 round stretch;
     -moz-border-image: url("../images/border.png") 27 round stretch;
     -o-border-image: url("../images/border.png") 27 round stretch;
     border-image: url("../images/border.png") 27 round stretch;
   }
```
![](/uploads/border-image-round-h.png)
**水平repeat效果**
```css
  .border-image-repeat {
    -webkit-border-image: url("../images/border.png") 27 repeat stretch;
    -moz-border-image: url("../images/border.png") 27 repeat stretch;
    -o-border-image: url("../images/border.png") 27 repeat stretch;
    border-image: url("../images/border.png") 27 repeat stretch;
  }
```
![](/uploads/border-image-repeat-h.png)
**水平拉伸效果**
```css
  .border-image-stretch {
     -webkit-border-image: url("../images/border.png") 27 stretch round;
     -moz-border-image: url("../images/border.png") 27 stretch round;
     -o-border-image: url("../images/border.png") 27 stretch round;
     border-image: url("../images/border.png") 27 stretch round;
  }
```
![](/uploads/border-image-stretch-h.png)
垂直方法的效果类似，不再展示。
**注意：**
_repeat和round效果不一样，round会压缩或伸展border-image的背景图片以其刚好适应border-width的宽度，从而正好在边框区域内显示，而repeat就不一样了，他不管什么适合不适合，直接居中重复，我个人认为repeat是边框中间向两端重复。因此大家可记住了：round平铺可能会改变边框背景图片大小来适应边框宽度排列，repeat重复是不改变背景图片大小而直接从中间向两端排列。_
_另外，webkit（safari、chrome）下repeat和round效果是一样的，只有在Mozilla和Opera下有区别_

**应用场景**
- 制作Button
![](/uploads/border-image-demo-button.png)
- 制作Tabs
![](/uploads/border-image-demo-tabs.png) ![](/uploads/border-image-tab-2.png)
- 圆角+Drop box shadow效果
![](/uploads/border-image-demo-drop-boxshadow.png)
- 相框效果
![](/uploads/border-image-deom-imageframe.png)

更多说明，请参考[W3CPLUS](http://www.w3cplus.com/content/css3-border-image)，里面写的很详细，非常感谢！