1. 下载 react-router-dom

#### BrowserRouter
> react-router-dom扩展，利用HTML5 新增的history API (pushState, replaceState)，是web应用最常用的路由组件

#### HashRouter
> react-router-dom扩展，利用window.location.hash，适用于低版本浏览器或者一些特殊情境

#### Route

> 路由配置的具体实现，它指定当路径匹配的时候渲染哪一个UI

- path

是用于指定路径名的

- exact

匹配路径名时指定更为严格的匹配规则(path等于location.pathname时才会匹配成功)

- strict

严格验证尾随线，path和location.pathname都有或者都没有才会匹配成功

- component

当路径匹配时渲染UI，内部实现用的是React.createElement()方法，即每一次都会触发卸载和创建组件，如果渲染的UI没有多余的内容，推荐使用render。

- render

当路径匹配时渲染UI，与component不同的是，它只调用render()方法去渲染组件，不会去重新创建元素，所以速度更快，只适用于行内渲染。

- children

与render类似，唯一的区别是不管路径是否匹配都会渲染，所以它最适合用于做转场动画

这三个方法在渲染组件的同时还传递了几个参数过去，这些参数也不是它的，是从前面传下来的：
```
const props = { match, location, history, staticContext }
//history是我们的bom对象
//location记录的是当前页面的url信息以及匹配的时候传递的一些额外数据
//match记录的是匹配信息
```


#### withRouter

高阶组件 用于传递router props


#### Link

为你的应用提供声明式的、可访问的导航链接

to：string 

to：object

一个对象形式的链接地址，可以具有以下任何属性：

pathname - 要链接到的路径

search - 查询参数

hash - URL 中的 hash，例如 #the-hash

state - 存储到 location 中的额外状态数据

replace：true

点击链接后将替换历史堆栈中的当前条目，而不是添加新条目

#### NavLink

activeClassName: string

当元素处于激活状态时应用的类，默认为 active

activeStyle：object

#### Redirect

使用 <Redirect> 会导航到一个新的位置。新的位置将覆盖历史堆栈中的当前条目

to: string

to：object

#### Switch

渲染第一个被location匹配到的并且作为子元素的<Route>或者<Redirect>



#### url传参

```
<Route exact path="/detail/:id" component={Detail}/>
```

使用this.props.match.params获取url传过来的参数

#### 隐式传参

通过push函数隐式传参

```
this.props.history.push({
        pathname: '/detail',
        state: {
            id: 3
        }
})
```
可以使用this.props.history.location.state获取传过来的参数



