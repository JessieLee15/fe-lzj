# 入门学习笔记

## 基础

### 组件
React 组件类，或者叫 React 组件类型 之类的。一个组件会接受名为 props 的参数，并通过名为 render 的方法返回一个嵌套结构的视图

render 返回的是你对你想要渲染内容的描述

* 状态提升
  当你遇到需要同时获取多个子组件数据，或者两个组件之间需要相互通讯的情况时，把子组件的 state 数据提升至其共同的父组件当中保存。之后父组件可以通过 props 将状态数据传递到子组件当中。这样应用当中的状态数据就能够更方便地交流共享了。

* Recommended Toolchains
  * If you’re learning React or creating a new _single-page app_, use [Create React App](https://react.docschina.org/docs/create-a-new-react-app.html#create-react-app).
  * If you’re building a _server-rendered website with Node.js_, try [Next.js](https://nextjs.org/learn/).
  * If you’re building a _static content-oriented website_, try [Gatsby](https://www.gatsbyjs.org/docs/).
  * If you’re building a _component library_ or _integrating with an existing codebase_, try More Flexible [Toolchains](https://react.docschina.org/docs/create-a-new-react-app.html#more-flexible-toolchains).

### props与state


## 设计思想
1. 操作DOM => 数据驱动
2. 抽象组件: 将UI才分为多个可重用的部分，并对上层隐藏实现细节
3. Memoization: 纯函数 => 结果是可缓存,自动地在相同参数的情况下直接返回

### react中的数据流

据说是只能单项：父组件 -> 子组件

状态通常被称为局部或封装。 除了拥有并设置它的组件外，其它组件不可访问。


### 航的react分享
1. jsx js+html结合
2. RN 与weex等差异 ？？？



__引用及参考资源__: 

[React 概念模型——脱离React谈谈它的设计思想](https://segmentfault.com/a/1190000005159165) 

