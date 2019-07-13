#### getter

> 有时候我们需要在state 中派生出一些状态，例如对state里面的数据进行过滤，筛选出来班级人数大于30的班级

1. 计算属性里面

```
     getPeople(){
          return this.$store.state.arr.filter(item => item.people > 30);
    }
```
但是如果多个组件都需要用到这个方法，我们就需要复制出来很多个这样的方法，不够简洁

2. getters

Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性)

**跟计算属性一样，getter 的返回值会根据它的依赖被缓存起来，且只有当它的依赖值发生了改变才会被重新计算**

在store.js里面
```
     getters:{
        getPeople(state){//state作为第一个参数,也可以接受getter 作为第二个参数
            console.log(state);
            return state.arr.filter(item => item.people > 30);
        },
        getCount(state,getter){
            return getter.getPeople.length;
        }
    }
```

在组件中

- this.$store.getters.getPeople（这种写法太长了，不美观）
- mapGetters  获取数据
```
    import {mapState,mapGetters} from 'vuex';
    
      computed: {
        ...mapGetters(['getPeople']),
        // getPeople(){
        //   return this.$store.state.arr.filter(item => item.people > 30);
        // }
    },

```

如果在当前的组件中，你希望计算属性用另一个名字，则可以这样
```
     ...mapGetters({'aa':'getPeople'},{'bb':'getnews'}),
```