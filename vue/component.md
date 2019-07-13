#### 什么是组件

 组件 (Component) 是 Vue.js 最强大的功能之一。组件可以扩展 HTML 元素，封装可重用的代码。在较高层面上，组件是自定义元素，Vue.js 的编译器为它添加特殊功能。在有些情况下，组件也可以表现为用 `is `特性进行了扩展的原生 HTML 元素。

#### 组件的好处
- 提高开发效率
- 方便重复使用
- 便于协同开发
- 更容易管理和维护


#### 注册组件

1. 全局注册

> 它们在注册之后可以用在任何新创建的 Vue 根实例 

###### 全局注册的行为必须在根 Vue 实例 (通过 new Vue) 创建之前发生。

```html
<div id="app">
  <my-component></my-component>
</div>
```
```js
// 注册
Vue.component('my-component', {
  template: '<div>A custom component!</div>'
})
var vm = new Vue({
  el: '#app',
  data: {
       
  } 
})

```

2. 局部注册

>全局注册往往是不够理想的。比如，如果你使用一个像 webpack 这样的构建系统，全局注册所有的组件意味着即便你已经不再使用一个组件了，它仍然会被包含在你最终的构建结果中。这造成了用户下载的 JavaScript 的无谓的增加。

```js

var vm = new Vue({
  el: '#app',
  components: {
      myComponent 
  } 
})

```




