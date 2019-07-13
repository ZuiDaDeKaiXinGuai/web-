##### 引入vue-router
```
new VueRouter({
     routes:[
         //配置路由规则
         {
             path:路由要跳到的连接   :路由名 =》 动态路由  ($route.params.路由名)
             component:对应组件
             name:组件名
             children:[] 嵌套的组件 子组件的
         }
     ]
 })
```
##### 实例对象中配置router
```
 new Vue({
     router:VueRouter实例对象
 })
```
##### router-link 
```
<router-link to="path"></router-link>
```
> 控制链接变化

##### router-view
```
<router-view></router-view>
```
> 盛放组件容器
---
##### 组件加载规则
- 组件根据url地址进行加载
- 对应匹配path路径
- path匹配之后加载组件 组件会加载到其父组件的router-view的位置

##### 路径切换
- window.location
- router-link :to="路径地址"
- router.push(任何路径)
```
 router.push({
     name:组件名，
     params:{
         :(动态路由名):值
     },
     query:{  //url?key=value
        key:value
     }
 })
```
##### 命名视图

- 重定向
```
访问a跳转b
{
    path:a
    redirect:b
}
```

- 别名
```
a和b指向同一个组件
{
    path:a,
    alias:b,
    component:组件
}
```