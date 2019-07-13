![image](http://www.runoob.com/wp-content/uploads/2016/02/react.png)

> React 用于构建用户界面的 JavaScript 库

> React 主要用于构建UI，很多人认为 React 是 MVC 中的 V（视图）。

> React 起源于 Facebook 的内部项目，用来架设 Instagram 的网站，并于 2013 年 5 月开源。

> React 拥有较高的性能，代码逻辑非常简单，越来越多的人已开始关注和使用它。

> 构建那些数据会随时间改变的大型应用

#### React 特点

- `声明式设计` −React采用声明范式，可以轻松描述应用。

- `高效` −React通过对DOM的模拟，最大限度地减少与DOM的交互。

- `灵活` −React可以与已知的库或框架很好地配合。

- `JSX` − JSX 是 JavaScript 语法的扩展。React 开发不一定使用 JSX ，但我们建议使用它。

- `组件` − 通过 React 构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中。

- `单向响应的数据流` − React 实现了单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。

##### 简单的表述任意时间点你的应用应该是什么样子的，React将会自动的管理UI界面更新当数据发生变化的时候

##### 在数据发生变化的时候，React从概念上讲与点击了F5一样，实际上它仅仅是更新了变化的一部分而已

----

#### 什么是 MVVM？比之 MVC 有什么区别？

##### MVVM是Model-View-ViewModel的简写
- View 很简单，就是用户看到的视图
- Model 同样很简单，一般就是本地数据和数据库中的数据

![image](https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike80%2C5%2C5%2C80%2C26/sign=66a90cd31d950a7b613846966bb809bc/e61190ef76c6a7efe4baffc3fdfaaf51f2de66b2.jpg)

传统的 MVC 架构通常是使用控制器更新模型，视图从模型中获取数据去渲染。当用户有输入时，会通过控制器去更新模型，并且通知视图进行更新。

![image](https://note.youdao.com/yws/public/resource/f6042c576c71004af0b357646a723091/xmlnote/1AD076E1CBC049DC803430133C03A9D3/4142)

但是 MVC 有一个巨大的缺陷就是控制器承担的责任太大了，随着项目愈加复杂，控制器中的代码会越来越臃肿，导致出现不利于维护的情况.

----

#### Virtual DOM

大家都知道操作 DOM 是很慢的，为什么慢的原因是因为浏览器渲染原理

那么相较于 DOM 来说，操作 JS 对象会快很多，并且我们也可以通过 JS 来模拟 DOM

```
const ul = {
  tag: 'ul',
  props: {
    class: 'list'
  },
  children: {
    tag: 'li',
    children: '1'
  }
}
```

```
<ul class="list">
    <li>1</li>
</ul>
```

那么既然 DOM 可以通过 JS 对象来模拟，反之也可以通过 JS 对象来渲染出对应的 DOM。当然了，通过 JS 来模拟 DOM 并且渲染对应的 DOM 只是第一步，难点在于如何判断新旧两个 JS 对象的`最小差异`并且实现`局部更新`DOM。


React 团队优化了算法

Virtual DOM 提高性能是其中一个优势，其实最大的优势还是在于:
1. 将 Virtual DOM 作为一个兼容层，让我们还能对接非 Web 端的系统，实现跨端开发。
2. 同样的，通过 Virtual DOM 我们可以渲染到其他的平台，比如实现 SSR、同构渲染等等
3. 实现组件的高度抽象化

----
##### 认识React元素

React中提供了React.createElement方法用来创建React元素；
react元素其实本质上一个对象，下边是React.createElement的使用：
```
 React.createElement(type/reactClass/function,props,children)
```

##### jsx

React 使用 JSX 来替代常规的 JavaScript。

JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。

我们不需要一定使用 JSX，但它有以下优点：

- JSX 执行更快，因为它在编译为 JavaScript 代码后进行了优化。
- 它是类型安全的，在编译过程中就能发现错误。
- 使用 JSX 编写模板更加简单快速。

**我们可以在 JSX 中使用 JavaScript 表达式。表达式写在花括号 {}  中**

**在 JSX 中不能使用 if else 语句，但可以使用 conditional (三元运算) 表达式来替代**

**React 推荐使用内联样式。我们可以使用 camelCase 语法来设置内联样式. React 会在指定元素数字后自动添加 px**

**注释需要写在花括号中**


