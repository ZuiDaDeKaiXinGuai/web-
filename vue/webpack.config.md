==下载本地webpack==

>  基础配置

```
module.exports = {
    mode: 'development',开发模式
	entry: 入口文件路径（绝对路径）,
	
	output: {
		path: 输出文件路径
		filename: 输出文件名（单入口默认是main）[name].js 本来文件名称
	}
}
```

---
> 自动编译

- watch: true watch属性自动编译
- webpack -w package.json中定义指令
- 引入一个外部服务器

```
//下载包
$ webpack-dev-server
//配置
devServer:{
    port: 端口号,
    host:地址,
    before(app){
        app.get(接口地址,(req,res)=>{
            
        })
    }
}
```

---

> loaders

通过使用不同的loader，webpack有能力调用外部的脚本或工具，实现对不同格式的文件的处理，比如说分析转换scss为css，或者把下一代的JS文件（ES6，ES7)转换为现代浏览器兼容的JS文件。

++不同的loader使用之前要安装++


```
module: {
    //规则
    rules: [{
        test: 正则匹配特定文件,
        loader: 字符串或数组,
        exclude: 正则，匹配忽略的文件夹
    }]
}
```


- 处理css文件

```
style-loader
css-loader
```

---
> plugins


