[toc]
## vuex：集中式管理数据
### 什么是vuex
- 主要应用于vue中管理数据状态的一个库
- 通过创建一个集中的数据存储，供程序中所有组件访问
    
### 怎么使用

1. npm i vuex (需要单独安装)
2. 新建一个store.js
```
    需要实例化vuex中的store对象
    格式：
    let 对象 = new Vuex.Store({
    state:{ },//状态，把需要在多个组件之间共享的数据，放在这里。理解为vue实例的data
    mutations:{},//要修改state中的数据，你只能通过mutaions中的方法。
    Actions:{},  //异步的操作
    getters:{}  //在state中的数据的基础上，获取新数据。类似于computed
})
```

3. 在main.js里面导入store.js，并且挂载到vue实例上边


    每一个 Vuex 应用的核心就是 store（仓库）。store是一个容器，包含着vue应用的状态(state)

**特点**


1. Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新
2. 你不能直接更改 store 中的状态。==改变 store 中的状态的唯一途径就是显式地提交(commit) mutations==。这样使得我们可以方便地跟踪每一个状态的变化

### 核心概念

#### state(放数据。在组件之间共享)

#### mutation(修改数据)
更改 Vuex 的 store 中的状态的唯一方法是提交 mutation

在store.js
```
    const store = new Vuex.Store({
          state: {
            count: 1
          },
          mutations: {
            add (state,obj) { // 默认第一个参数是state,当然也可以接受第二个参数,第二个参数是通过commit触发时传过来的参数
              // 变更状态
              state.count++
            }
          }
    })
   //没有第三个参数，如果需要传递一个很复杂的数据，可以放到一个对象里面通过第二个参数传过来。
```
 ==这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数==

在触发事件的组件里面
    
    语法：this.$store.commit(“mutations中的属性名”,参数) 
    
==第一个参数不需要指定==
``` 
    // this.$store.state.count++;(不建议这样写，在devtool里面完全没有记录)
    
    例如：
     this.$store.commit('add'，100);(有记录)
```
#### Getters:从state中的数据中，取出一部分来，依据数据项产生新的结果。类似于uve实例中的computed（计算属性）
    
    


#### Actions:在对数据实现异步操作时，要用的


