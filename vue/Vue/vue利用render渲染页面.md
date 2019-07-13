#### 1.vue在webpack中的使用
###### 1.将vue配置到webppack中
###### 2.在app.js中引入
- [x] import Vue from "vue"
- [x] import App from "./app.vue"
- 引入内容
- [x] 实例化vue,利用render去渲染

```
new Vue({
    el: "#app",
    data: {
        mes: "123",
    },
    render: h => h(App)
})
```
###### 3.在app.vue中写

```
<template>内容</template>
<script>
  export default{
       data(){
            return{}
        },
  }
</script>
<style>
    @import url("./css/style.css");
</style>
```

