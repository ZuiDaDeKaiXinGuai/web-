#### actions

> 在mutations中，如果操作是异步的

```
mutations：{
    add(state){
            // console.log(state);
            setTimeout(()=>{
                state.count++;
            },2000);
        },
}
```
此时会有一个问题，就是devtool里面，点击的时间跟数据实际变化的时间不一致，会影响数据的跟踪。此时需要用到actions

action类似于mutations，不同在于：

- Actions 提交的是 mutations，而不是直接变更状态。
- Actions 可以包含任意异步操作。
- Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象，可以通过context.commit提交，也可以通过context.state获取state。
- 
在store.js
``` 
    mutations:{
        add(state){
            // console.log(state);
            state.count++;
        }
    },
    actions:{
        add(context){
            console.log(context);
            setTimeout(()=>{
                context.commit('add');
            },2000);
        }
    }
```


在组件里面

- this.$store.dispatch('add')
```
     methods: {
       ...mapMutations(['addList']),
       add(){
         this.$store.dispatch('add');
       },
     }
```

- mapActions 管理所有的事件

```
    methods: {
       ...mapActions(['add']),
       
       // add(){
        // this.$store.dispatch('add');
      // },
    }
```



```
    import {mapActions,mapGetters} from 'vuex'
    //之前
    methods:{
        方法1(){
            
        },
        方法2(){
            
        }
    }
    //现在
    methods:mapActions([
        方法1，方法2
    ])
```