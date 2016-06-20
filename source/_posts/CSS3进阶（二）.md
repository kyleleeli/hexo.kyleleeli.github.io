---
title: CSS3进阶（二）
date: 2016-05-26 09:54:30
tags:
- CSS3
permalink: css3-learning-two
---
# 需要了解的内容
- vw,vh,vmin,vmax,em,rem
- flex
- box-sizing
- transform
- transition
- animation
- gradient


### 1. 宽、高度单位

#### vw,vh

|名称|描述|
|----|----|
|vw|相对于视窗的宽度：视窗宽度是100vw|
|vh|相对于视窗的高度：视窗高度是100vh|

`vw`、`vh`都是css3新增的长度单位。

以`vw`为例，先给个公式：
`vw = 1/100 * viewport`

这里的`viewport`指的视窗，也就是浏览器内的可视区域（不包含浏览器自己的状态栏、工具栏等）。
vw单位跟百分比很相似，不同的是vw的值对所有的元素都一样，与他们父元素或父元素的宽度无关。有点像rem单位那样总是相对于根元素。

`vh`的效果类似，就不再阐述。

**特别注意：viewport单位会把滚动条宽度也包含在内**

#### vmin,vmax

`vh`和`vm`总是与视口的高度和宽度有关，与之不同的，`vmin`和`vmax`是与这次宽度和高度的最大值或最小值有关，取决于哪个更大和更小。例如，如果浏览器设置为`1100px`宽、`700px`高，`1vmin`会是`7px`,`1vmax`为`11px`。然而，如果宽度设置为`800px`，高度设置为`1080px`，`1vmin`将会等于`8px`而`1vmax`将会是`10.8px`。

`vh`,`vw`的使用场景比较好理解，`vmin`,`wmax`到底什么时候使用呢？

场景一：
> 一个正方形的元素总是至少接触屏幕的两条边

``` css
    .box {
        height: 100vmin;
        width: 100vmin;
    }
```
![](/uploads/vmin.png "css3 vmin")

场景二：
> 需要一个总是覆盖可视窗口的正方形

``` css
    .box {
        height: 100vmax;
        width: 100vmax;
    }
```
![](/uploads/vmax.png "css3 vmax")

#### em,rem

`em`单位被定义为当前字体大小，但`em`存在嵌套被放大的问题，比如我们将`div`的样式定义为`font-size:1.2em`

``` html
    <body>
        <div>
            Test <!-- 14 * 1.2 = 16.8px -->
            <div>
                Test <!-- 16.8 * 1.2 = 20.16px -->
                <div>
                    Test <!-- 20.16 * 1.2 = 24.192px -->
                </div>
            </div>
        </div>
    </body>
```
使用`rem`正好可以解决这个问题，`r`代表`root`，`font-size`大小相对于根元素，一般根元素是`html`元素。
有时候考虑将`rem`和`em`组合使用。

#### 相对长度
相对长度单位指定了一个长度相对于另一个长度的属性。对于不同的设备相对长度更适用。

|单位|  描述 |
|----|-------|
|em  |它是描述相对于应用在当前元素的字体尺寸，所以它也是相对长度单位。一般浏览器字体大小默认为16px，则2em == 32px；|
|ex  |依赖于英文子母小 x 的高度|
|ch  |数字 0 的宽度|
|rem |根元素（html）的 font-size|
|vw  |viewpoint width，视窗宽度，1vw=视窗宽度的1% |
|vh  |viewpoint height，视窗高度，1vh=视窗高度的1% |
|vmin |   vw和vh中较小的那个。|
|vmax |   vw和vh中较大的那个。|
|%|  |

#### 绝对长度
绝对长度单位是一个固定的值，它反应一个真实的物理尺寸。绝对长度单位视输出介质而定，不依赖于环境（显示器、分辨率、操作系统等）。

|单位 | 描述|
|-----|-----|
|cm  |厘米  
|mm  |毫米  
|in  |英寸 (1in = 96px = 2.54cm)    
|px *|   像素 (1px = 1/96th of 1in)    
|pt  |point，大约1/72英寸； (1pt = 1/72in)  
|pc  |pica，大约6pt，1/6英寸； (1pc = 12 pt)

像素或许被认为是最好的"设备像素"，而这种像素长度和你在显示器上看到的文字屏幕像素无关。px实际上是一个按角度度量的单位。

### 2. Flex
#### 概述
Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性。
任何一个容器都可以指定为Flex布局。

``` css
.box{
  display: flex;
}
```
行内元素也可以使用Flex布局。
``` css
.box{
  display: inline-flex;
}
```
Webkit内核的浏览器，必须加上-webkit前缀。
``` css
.box{
  display: -webkit-flex; /* Safari */
  display: flex;
}
```

#### 基本概念
![](/uploads/flexbox.png "flexbox")

基本上，Flex项目是沿着main axis(从main-start向main-end)或者cross axis(从cross-start向cross-end)排列。

- `main axis`:Flex容器的主轴主要用来配置Flex项目。注意，它不一定是水平，这主要取决于flex-direction属性。
- `main-start` | `main-end`:Flex项目的配置从容器的主轴起点边开始，往主轴终点边结束。
- `main size`:Flex项目的在主轴方向的宽度或高度就是项目的主轴长度，Flex项目的主轴长度属性是width或height属性，由哪一个对着主轴方向决定。
- `cross axis`:与主轴垂直的轴称作侧轴，是侧轴方向的延伸。
- `cross-start` | `cross-end`:伸缩行的配置从容器的侧轴起点边开始，往侧轴终点边结束。
- `cross size`:Flex项目的在侧轴方向的宽度或高度就是项目的侧轴长度，Flex项目的侧轴长度属性是width或height属性，由哪一个对着侧轴方向决定。

#### 容器的属性
以下6个属性设置在容器上。

> 
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

**flex-direction属性**
flex-direction属性决定主轴的方向（即项目的排列方向）。
``` css
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
![](/uploads/flex-direction.png "flex-direction")

> 
- row（默认值）：主轴为水平方向，起点在左端。
- row-reverse：主轴为水平方向，起点在右端。
- column：主轴为垂直方向，起点在上沿。
- column-reverse：主轴为垂直方向，起点在下沿。

**flex-wrap属性**
默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
``` css
.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

**flex-flow**
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

``` css
.box {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

**justify-content属性**
justify-content属性定义了项目在主轴上的对齐方式。
``` css
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
![](/uploads/flex-justify-content.png "justify-content")
它可能取5个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。
> 
- flex-start（默认值）：左对齐
- flex-end：右对齐
- center： 居中
- space-between：两端对齐，项目之间的间隔都相等。
- space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

**align-items属性**
align-items属性定义项目在交叉轴上如何对齐。
``` css
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```
![](/uploads/flex-align-items.png "align-items")
它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。
> 
- flex-start：交叉轴的起点对齐。
- flex-end：交叉轴的终点对齐。
- center：交叉轴的中点对齐。
- baseline: 项目的第一行文字的基线对齐。
- stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

**align-content属性**
align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
``` css
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```
![](/uploads/flex-align-content.png "align content")
该属性可能取6个值。
> 
- flex-start：与交叉轴的起点对齐。
- flex-end：与交叉轴的终点对齐。
- center：与交叉轴的中点对齐。
- space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
- space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
- stretch（默认值）：轴线占满整个交叉轴。

#### 元素属性
以下6个属性设置在项目上。
> 
- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self

**order属性**
order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。
``` css
.item {
  order: <integer>;
}
```
![](/uploads/flex-order.png "order")

**flex-grow属性**
flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
``` css
.item {
  flex-grow: <number>; /* default 0 */
}
```
![](/uploads/flex-grow.png "flex-grow")
如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

**flex-shrink属性**
flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
``` css
.item {
  flex-shrink: <number>; /* default 1 */
}
```
![](/uploads/flex-shrink.jpg "flex-shrink")

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
负值对该属性无效。

**flex-basis属性**
flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
```css
.item {
  flex-basis: <length> | auto; /* default auto */
}
```
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

**flex属性**
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
``` css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```
该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

**align-self属性**
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
``` css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```
![](/uploads/flex-align-self.png "align-self")
该属性可能取6个值，除了auto，其他都与align-items属性完全一致。

以上内容转自 [阮一峰博客](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html) 

#### 使用示例

[请参考](https://chriswrightdesign.com/experiments/using-flexbox-today/)

#### 移动端支持情况

- 无前缀：Android 4.4+, Opera mobile 12.1+, BlackBerry 10+, Chrome for Android 39+, Firefox for Android 33+, IE 11+ mobile
- 需要前缀：iOS 7.1+需要前缀-webkit-

#### 引用列表
> 
[一个完整的Flexbox指南](http://www.w3cplus.com/css3/a-guide-to-flexbox-new.html)
[今天就用Flexbox](http://www.w3cplus.com/css3/using-flexbox-today.html)
[时下Web App中的Flexbox应用](http://www.w3cplus.com/css3/harnessing-flexbox-for-todays-web-apps.html)
[Flex 布局语法教程](http://www.runoob.com/w3cnote/flex-grammar.html)