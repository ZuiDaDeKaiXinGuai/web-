## VUE
#### 1.概念
###### 是一套构==用户界面==(user interface)的渐进式框架
###### 关注点：Vue 只关注==视图层==， 从根本上采用:最小成本、==渐进增量==(incrementally adoptable)的设计
###### Vue.js 的==核心==是：==可以采用简洁的模板语法来声明式的将数据渲染为 DOM==
- [x]  数据和 DOM 已经被关联在一起，所有的==数据和 DOM 都是响应式的==   

###### 注意：Vue.js 不支持 IE8 及其以下 IE 版本。
#### 2.下载
- [x] BootCDN（国内） : https://cdn.bootcss.com/vue/2.2.2/vue.min.js
- 或链接
[x] - https://cdn.bootcss.com/vue/2.4.2/vue.min.js
#### 3.vue使用

```
//1.链接
<script src="https://cdn.bootcss.com/vue/2.4.2/vue.min.js"></script>
//2.new 实例化
new Vue({
  el: '#app',  //vue作用范围
  data: {     //定义属性
    message: 'Hello Vue.js!'
  },
 methods: {  //定义方法
            details: function() {
                return  this.site + " - 
            }
 },
   filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
 注：1.当一个 Vue 实例被创建时，它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。当这些属性的值发生改变时，html 视图将也会产生相应的变化。
```
#### 4.指令
==指令用于在表达式的值改变时，将某些行为应用到 DOM 上==
###### 1.{{}}  用于输出对象属性和函数返回值。
###### 里面可以做条件判断/数据加减运算
{{属性名}}
###### 2.==v-html==    输出 html 代码
---- v-html="属性名"
###### 3.==v-bind== 绑定标签属性中的值(例如class)
###### 缩写 :href="属性名"
 ---- v-bind:class="{'样式名': boolean}"
 ---- v-bind:href="属性名"
######  注：v-bind:class="数据里的{}"
######  注：v-bind:class="[]",
######  注：v-bind:class="{}"直接设置属性

```
v-bind:style="{}" 直接设置样式
v-bind:style="数据里的{}"
v-bind:style="[]",

```

###### 4.==v-model== 表单元素的双向绑定
---- v-model="属性名"
###### 5.v-if 显示/隐藏元素
---- v-if="true"    显示 

---- v-if="false"   隐藏 把元素从页面删除
 
###### 5.==v-show== 显示/隐藏元素
---- v-show="true"    显示  

---- v-show="false"   隐藏 
相当于dispay=none
######  6.==v-on== 用于监听 DOM 事件
 ---- v-on:click="函数
######  缩写 @on:click="函数"
###### 6.==v-else==    条件判断 否则
如果为假，执行下面内容
###### 7.==v-else-if==   条件判断 如果为真，执行下面内容
 ---- v-else-if="type === 'B'"
######  8.==v-for== 渲染一个列表,数据可以是数组,对象,数值,字符串

```
---- v-for="(v,i) in 数组"
```


```
---- v-for="(val,key,i) in 对象"
```

###### val 健名   key 健值  i 下标

```
---- v-for="(v) in 数值"
```

```
---- v-for="(v) in 字符串"
```


####  5.过滤器
###### 定义
==必须有return==
```
 filters: {
        name1(options) {
            return options;
        }
  }
```

###### 调用 {{ 数据 | 过滤器名 }}

###### 使用
1.可以串联

```
{{ message | 过滤器名1 | 过滤器名2 }}
```
2.可以接受参数

```
{{ message | 过滤器名('arg1', arg2) }}
```

#### CDN
###### 内容分发网络
###### 基本思路：
是尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节
###### 作用
使内容传输的更快、更稳定
###### 过程
通过在网络各处放置节点服务器即==虚拟网络==
###### 通过什么手段实现
 CDN系统能够实时地根据==网络流量==和各==节点的连接==、==负载状况==以及到用户的==距离==和==响应时间==等综合信息将用户的请求重新导向离用户最近的服务节点上
