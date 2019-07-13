#### 1.组件调用
######  1.在components文件夹写好header.vue组件
###### 2.在其他页面引入

```
<script>   //组件引入
import heads from "@/components/include/header.vue"
import wraps from "@/components/include/wrap.vue"
import foots from "@/components/include/footer.vue"

export default {
  name: 'Login',
 components: {  //组件注册
      heads,
      wraps,
      foots
  }
}

```

###### 3.组件调用(在template模板中调)

```
<template>
  <div>

    <heads></heads>
    <wraps></wraps>
    <foots></foots>
  </div>
</template>

```

#### 2.webpack-cli


```
import Vue from 'vue'
import App from './app.vue'
new Vue({
    el: '#app',
    components: { App },
    template: '<App/>'
})
```


###### 在app.vue中抛出

```
export default {
 name:"App",
  data(){
    return{
       data:"111"
    }
        

  }
}
```

