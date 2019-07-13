#### Css解析
###### 1.下载 style-loader css-loader  
######  2.引入一个或多个样式表(在app.js中引入)
###### import "./css/style.css";
###### import "./css/reset.css";
###### import "./css/common.css";
###### 3.配置 在webpack.config.js中配置

```
  module: {
         rules: [{ //解析css
                test: /\.css/,
                use: ["style-loader", "css-loader"]
            }],
```
#### 图片解析
###### 1.下载  url-loader file-loader  
###### 2.webpack.config.js中配置

```
  module: {
        rules: [ { //解析图片
                test: /\.(jpg|jpeg|png|gif)/,
                loader: "url-loader"

            }]
        }
```
#### 解析矢量字体图标
######  1.引入一个或多个样式表(在app.js中引入)  
###### import "./css/bootstrap.min.css";
###### import "./css/common.css";
###### import "./css/font-awesome.min.css"

```

    module: {
        rules: [ { //解析矢量字体图标
                test: /\.(eot|svg|ttf|woff|woff2)/,
                loader: "url-loader"
            }]
          }
  
```
###### ?name=fonts/[name].[md5:hash:hex:7].[ext] webpack4.0会报错
#### 解析js
###### 1.下载  babel-loader 
###### 2.webpack.config.js中配置


```
  module: {
        rules: [  { //解析js
                test: /\.js/,
                exclude: /(node_modules)/,
                use: {
                    loader: 'babel-loader'
                }
            }]
          }
  
```
### 二. html页面加载(创建一个html页面)
###### 1.下载 html-webpack-plugin
###### webpack.config.js中引入 
###### const webpack = require("webpack");
###### const HtmlWebpackPlugin = require('html-webpack-plugin');
###### 2.webpack.config.js中配置
```
 plugins: [
        //每new一次就会创建一次html页面
        new HtmlWebpackPlugin({
            name: "index",     index页面
            title: "主页",     title中的标题
            filename: "index.html",   
            template: './index.html'   利用的模板，从根目录下找
        }),
    ]
```
###### 利用根目录下的的html,新建一个html页面
###### 每new一次就会创建一次html页面
###### 输出到 dist目录下

### 提取/切割公共样式
==避免重复加载==
###### 1..webpack.config.js中引入 const webpack = require("webpack");
###### 2.webpack.config.js中配置
```
 plugins: [
          //提取/切割公共代码
        new webpack.optimize.CommonsChunkPlugin({
            name: "common",
            filename: "common.js"
        })
    ]
  
```
### 热替换  不需手动更新html页面
###### 1.起服务 下载 webpack-dev-server
###### 2.webpack.config.js中配置
```
   devServer: {
        host: "localhost",
        port: 8080,
        contentBase: ".",
        setup(app) {}
    },
    plugins:[
      //模块的热替换
            new webpack.HotModuleReplacementPlugin(),
        ]
```
### 压缩js
###### 1.下载 uglifyjs-webpack-plugin
###### 2.webpack.config.js中引入const UglifyJsPlugin = require('uglifyjs-webpack-plugin');
###### 2.webpack.config.js中配置

```
   plugins: [
      
        //js压缩
            new UglifyJsPlugin({
            exclude: /\/node_modules/,
            uglifyOptions: {
                compress: {
                    warnings: false
                }
            },
            cache: true,
            //开启多核处理(硬件加速)
            parallel: 4,
            sourceMap: true //资源地图
        }),
        ]
```

### 抽离样式
###### 1.下载 extract-text-webpack-plugin
###### 2.webpack.config.js中引入const ExtractTextPlugin = require("extract-text-webpack-plugin");
###### 2.webpack.config.js中配置

```
   plugins: [
      //抽离样式表
        new ExtractTextPlugin("mian.css"),
      
        ]
```
###### 注：抽离的样式在dist目录下

## ==webpack注意事项注意==
#### 1.包得版本
######  "webpack": "^3.10.0",
######   "webpack-cli": "^2.0.12"
######   "html-webpack-plugin": "^3.0.6",
###### 2.去node_modules中看配置
#### 3.scripts配置
 
```
   "scripts": {
        "build": "webpack --config webpack.config.js",
        "start": "webpack-dev-server --progress --inline --config webpack.config.js --hot --open"
    },
```
#### 4.别配置提取/切割公共代码








