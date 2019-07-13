##### 什么是Redux

Redux是一个流行的JavaScript框架，为应用程序提供一个可预测的状态容器。Redux基于简化版本的Flux框架，Flux是Facebook开发的一个框架。在标准的MVC框架中，数据可以在UI组件和存储之间双向流动，而Redux严格限制了数据只能在一个方向上流动。

![image](https://segmentfault.com/img/bVWi0h?w=687&h=330)

在Redux中，所有的数据（比如state）被保存在一个被称为**store**的容器中 → 在一个应用程序中只能有一个。**store**本质上是一个状态树，保存了所有对象的状态。任何UI组件都可以直接从**store**访问特定对象的状态。要通过本地或远程组件更改状态，需要分发一个**action**。分发在这里意味着将可执行信息发送到**store**。当一个**store**接收到一个**action**，它将把这个**action**代理给相关的**reducer**。**reducer**是一个纯函数，它可以查看之前的状态，执行一个**action**并且返回一个新的状态。


> store 仓库 描述的是整个数据流的过程


> state 每次计算出来的状态，可以由getState获取


> action 描述数据如何改变


> reducer 接受上一次的状态和action 计算出来真正的新数据

> dispatch 触发action

> getState 获取最新状态

> subscribe 订阅/注册 接受一个函数 观察者/监听者 监听数据计算

> combineReducers 合并reducres

> bindActionCreators 绑定action