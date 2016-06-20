---
title: ReactJS使用入门
date: 2016-06-05 21:18:07
tags:
- React
permalink: reactjs-guides
---
![React](/uploads/reactjs.png "reactjs")

先来看一段代码，直观感受一下：
``` jsx
var CommentBox = React.createClass({
  render: function() {
    return (
      <div className="commentBox">
        Hello, world! I am a CommentBox.
      </div>
    );
  }
});
ReactDOM.render(
  <CommentBox />,
  document.getElementById('content')
);
```
JSX转义后的js
```js
var CommentBox = React.createClass({displayName: 'CommentBox',
  render: function() {
    return (
      React.createElement('div', {className: "commentBox"},
        "Hello, world! I am a CommentBox."
      )
    );
  }
});
ReactDOM.render(
  React.createElement(CommentBox, null),
  document.getElementById('content')
);
```

### 概述

React 是一个 Facebook 和 Instagram 用来创建用户界面的 JavaScript 库。
React 的核心思想是：**封装组件**。
各个组件维护自己的状态和 UI，当状态变更，自动重新渲染整个组件。
基于这种方式的一个直观感受就是我们不再需要不厌其烦地来回查找某个 DOM 元素，然后操作 DOM 去更改 UI。
React 大体包含下面这些概念：
- 组件
- JSX
- Virtual DOM
- Data Flow

### 组件
#### 创建

在构建组件之前，需要根据功能将用户界面拆分为一个组件树，比如下面的评论区功能：
![comments](/uploads/react-component.png "react component example")

组件树划分完成后，就可以进行具体的开发工作。

引入`react.js`和`react-dom.js`，如果是开发环境可以通过`browser.min.js`在线转换JSX语法，大概的html模板样例如下：
``` html
<!DOCTYPE html>
<html>
  <head>
    <script src="../build/react.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      // ** Our code goes here! **
    </script>
  </body>
</html>
```
可以将代码直接写入script标签内，也可以作为外部文件引入：
`<script type="text/babel" src="scripts/helloworld.js"></script>`

创建组件通过 `React.createClass`方法，将组件渲染到指定DOM节点内：`ReactDOM.render`

#### props、state

父元素（组件）是通过props传递数据给子元素（组件）的，子元素通过`this.props.xxx`访问具体的属性值。

`this.props` 对象的属性与组件的属性一一对应，但是有一个例外，就是 `this.props.children` 属性。它表示组件的所有子节点

组件免不了要与用户互动，React 的一大创新，就是将组件看成是一个状态机，一开始有一个初始状态，然后用户互动，导致状态变化，从而触发重新渲染 UI 。

state是元素自身的状态属性，通过组件生命周期中的`getInitialState`设置默认值。

两者区别：`this.props` 表示那些一旦定义，就不再改变的特性，而 `this.state`是会随着用户互动而产生变化的特性。

#### ref、findDOMNode
React 支持一种非常特殊的属性，你可以用来绑定到 `render()`输出的任何组件上去。这个特殊的属性允许你引用 `render()`` 返回的相应的支撑实例（ backing instance ）。这样就可以确保在任何时间总是拿到正确的实例。

做法很简单：
1、绑定一个 ref 属性到 render 返回的东西上面去，例如：
`<input ref="myInput" />`
2、在其它代码中（典型地事件处理代码），通过 `this.refs` 获取支撑实例（ backing instance ），就像这样：
  `this.refs.myInput`
你可以通过调用 `this.refs.myInput.getDOMNode()` 直接获取到组件的 DOM 节点。

当组件加载到页面上之后（mounted），你都可以通过 react-dom 提供的 findDOMNode() 方法拿到组件对应的 DOM 元素。

#### 生命周期

- Mounting (已插入真实 DOM)
  + getInitialState
  + componentWillMount
  + componentDidMount
- Updating (正在被重新渲染)
  + componentWillReceiveProps
  + shouldComponentUpdate
  + componentWillUpdate
  + componentDidUpdate
- UnMounting (已移出真实 DOM)
  + componentWillUnmount

### JSX

JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。React 可以用来做简单的 JSX 句法转换。

利用 JSX 编写 DOM 结构，可以用原生的 HTML 标签，也可以直接像普通标签一样引用 React 组件。这两者约定通过大小写来区分，小写的字符串是 HTML 标签，大写开头的变量是 React 组件。

#### 为什么要使用JSX？
你不需要为了 React 使用 JSX，可以直接使用纯粹的 JS。但我们更建议使用 JSX , 因为它能定义简洁且我们熟知的包含属性的树状结构语法。
对于非专职开发者（比如设计师）同样比较熟悉。
XML 有固定的标签开启和闭合。这能让复杂的树更易于阅读，优于方法调用和对象字面量的形式。
它没有修改 JavaScript 语义。

#### HTML标签 与 React组件 对比
React 可以渲染 HTML 标签 (strings) 或 React 组件 (classes)。
要渲染 HTML 标签，只需在 JSX 里使用小写字母开头的标签名。

如同开篇的例子一样，JSX及转换后的JS：

``` jsx
var myDivElement = <div className="foo" />;
React.render(myDivElement, document.body);
```

``` js
var MyComponent = React.createClass({/*...*/});
var myElement = <MyComponent someProperty={true} />;
React.render(myElement, document.body);
```

> 注意:
由于 JSX 就是 JavaScript，一些标识符像 class 和 for 不建议作为 XML 属性名。作为替代，React DOM 使用 className 和 htmlFor 来做对应的属性

#### 属性表达式
要使用 JavaScript 表达式作为属性值，只需把这个表达式用一对大括号 ({}) 包起来，不要用引号 ("")。

``` jsx
// 输入 (JSX):
var person = <Person name={window.isLoggedIn ? window.name : ''} />;
// 输出 (JS):
var person = React.createElement(
  Person,
  {name: window.isLoggedIn ? window.name : ''}
);
```

#### 注释
JSX 里添加注释很容易；它们只是 JS 表达式而已。你只需要在一个标签的子节点内(非最外层)小心地用 {} 包围要注释的部分。

#### 延展属性
如果你事先知道组件需要的全部 Props（属性），JSX 很容易地这样写：

``` jsx
  var component = <Component foo={x} bar={y} />;
```

``` jsx
  var props = {};
  props.foo = x;
  props.bar = y;
  var component = <Component {...props} />;
```

### Data Flow

#### Flux
React 标榜自己是 MVC 里面 V 的部分，那么 Flux 就相当于添加 M 和 C 的部分。
Flux 是 Facebook 使用的一套前端应用的架构模式。
一个 Flux 应用主要包含四个部分：

- the dispatcher
处理动作分发，维护 Store 之间的依赖关系
- the stores
数据和逻辑部分
- the views
React 组件，这一层可以看作 controller-views，作为视图同时响应用户交互
- the actions
提供给 dispatcher 传递数据给 store

针对上面提到的 Flux 这些概念，需要写一个简单的类库来实现衔接这些功能，市面上有很多种实现，这里讨论 Facebook 官方的一个实现 Dispatcher.js

#### 单向数据流

先来了解一下 Flux 的核心“单向数据流“怎么运作的：
`Action -> Dispatcher -> Store -> View`

更多时候 View 会通过用户交互触发 Action，所以一个简单完整的数据流类似这样：

![Alt text](/uploads/flux-overview.png "flux overview")

整个流程如下：

- 首先要有 action，通过定义一些 action creator 方法根据需要创建 Action 提供给 dispatcher
- View 层通过用户交互（比如 onClick）会触发 Action
- Dispatcher 会分发触发的 Action 给所有注册的 Store 的回调函数
- Store 回调函数根据接收的 Action 更新自身数据之后会触发一个 change 事件通知 View 数据更改了
- View 会监听这个 change 事件，拿到对应的新数据并调用 setState 更新组件 UI

所有的状态都由 Store 来维护，通过 Action 传递数据，构成了如上所述的单向数据流循环，所以应用中的各部分分工就相当明确，高度解耦了。
这种单向数据流使得整个系统都是透明可预测的。

### 工具
预编译JSX（Precompiled JSX）
    1. 安装babel：`npm install -g babel-cli`
    2. 在项目目录中执行：`npm install babel-preset-es2015 babel-preset-react`
    3. 然后就可以直接调用`babel --presets es2015,react --watch src/ --out-dir lib/`编译输出
    4. 也可以通过`echo { "presets": ["es2015","react"] } > .babelrc`创建babel配置文件，这样就不需要每次指定`--presets`
    
### 插件
    1. 动画

### Q&A
    1. 为什么手写的情况下，不会报唯一id的警告，循环就会报警告?
    (http://react-china.org/t/key/5797)
    2. Jsx怎么进行调试？
