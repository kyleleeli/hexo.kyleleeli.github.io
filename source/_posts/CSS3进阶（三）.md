---
title: CSS3进阶（三）
tags:
  - CSS3
permalink: css3-learning-three
date: 2016-06-13 22:23:57
---

# 需要了解的内容
- vw,vh,vmin,vmax,em,rem
- flex
- box-sizing
- transform
- transition
- animation
- gradient

### 3. box-sizing
#### 盒模型（box model）

讲box-sizing之前，先了解一下css中重要的概念：**盒模型**
盒模型就是元素的宽（width）、高（height）和内容（content）、外边距（margin）、内边距（padding）、边框（border）之间的计算关系。
主要分为两类：W3C标准模型和IE传统模型。
- W3C标准盒模型
``` css
 /*外盒尺寸计算（元素空间尺寸）*/
  Element 空间高度 = content height + padding + border + margin
  Element 空间宽度 = content width + padding + border + margin
  /*内盒尺寸计算（元素大小）*/
  Element Height = content height + padding + border （Height为内容高度）
  Element Width = content width + padding + border （Width为内容宽度）
```
- IE传统模型（IE6以下）
``` css
  /*外盒尺寸计算（元素空间尺寸）*/
  Element空间高度 = content Height + margin (Height包含了元素内容宽度，边框宽度，内距宽度)
  Element空间宽度 = content Width + margin (Width包含了元素内容宽度、边框宽度、内距宽度)
  /*内盒尺寸计算（元素大小）*/
  Element Height = content Height(Height包含了元素内容宽度，边框宽度，内距宽度)
  Element Width = content Width(Width包含了元素内容宽度、边框宽度、内距宽度)
```

对比上面的两个公式，可以发现：外盒尺寸=内盒尺寸+margin，而不同的地方就在：**内盒尺寸**的计算方式不同。
如果打开IE和chrome的调试窗口，观察盒子模型的计算就可以发现不同之处（以宽度示例）：IE下定义元素的宽度是包含了padding、border的宽度的，而chrome下是不包含的，这样如果定义了padding、border的话，会导致元素的实际宽度比定义的要宽。

为了解决这个差异，css3就定义了box-sizing样式：
`box-sizing ： content-box || border-box || inherit`

`content-box`: 是默认值，即W3C标准模型，width=定义的元素width+padding+border
`border-box`：IE传统模型，width=定义的元素width
看一张图片就很明显了，特别是在有padding、margin、border的情况下，元素的宽度差别还是挺大的：
![box-sizing](/uploads/box-sizing.png "box sizing")

### 4. transform

#### 2D 转换（2D transform）


#### 3D 转换（3D transform）


### 5. transition

### 6. animation

