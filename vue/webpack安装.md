
```
 npm install -g webpack
```
==如果使用 webpack 4+ 版本，还需要安装 CLI。==

```
npm install -g webpack-cli
```
> 基本使用

```
npm init
npm install webpack webpack-cli --save-dev
```

++webpack打包前确保已完成的工作++
1. 查看webpack版本 webpack -v
2. webpack4的版本里，CLI被单独分离出来了所以要我们单独安装  执行全局命令 npm i -g webpack-cli 安装完脚手架

==出现以下报错==

![image](http://localhost/book/webpack-1.png)

==错误提示并不是我们环境装错了，而是webpack4 更新后对webpack语法进行了更严格的要求==


```
//语法不符合规范
webpack 入口文件 输出文件
//规范语法后警告消失
npx webpack 入口文件 --output-filename 输出文件 --output-path . --mode development 
```

