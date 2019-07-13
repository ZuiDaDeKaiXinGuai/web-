#### webpack中手动创建路由
##### 1.下载vue-router
##### 2.在vue.js中引入
###### import VueRouter from 'vue-router' //引入路由
###### import Login from "./components/login.vue" //引入路由页面
###### 3.使用
###### Vue.use(VueRouter) //使用
###### 4.定义路由

```
let router = new VueRouter({ //定义路由
    routes: [{
            path: "/login",
            component: Login
        },
        {
            path: "/regist",
            component: Regist
        }
    ]
})
```
###### 5.在new Vue()调用
###### 6.App.vue文件中的<template>中写路由锚点/视图
- [x] 注: ==routes:[{}]==
- [x] 注: ==path:"/",路劲的有“/”==

```
 <router-link to="/login">跳转loin链接</router-link >
      <router-link to="/regist">跳转loin链接</router-link>
      <router-view></router-view>
```
##### 7.路由的模块化
###### 在src目录下建一个router文件夹，里面建一个 index.js
- [x] 从routers中导入路由数据 import router from './router' //从router文件夹中引入路由   
###### 建一个router.js的文件,提供路由数据并抛出 
1.链接路由页面
2.export default router;

###### 注：import Regist from "../components/regist.vue""
```



```


