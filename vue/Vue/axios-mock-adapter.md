#### 1.利用axios-mock-adapter开接口
##### 1.下载
######  axios 和 axios-mock-adapter
##### 2.引入
###### import axios from "axios";
###### import mockAdapter from "axios-mock-adapter";
##### 3.实例化
###### let mock = new mockAdapter(axios)
##### 4.导入数据 开接口
###### mock.onGet("接口").reply(200, 数据);

```
import banner from "./data/banner.js"
mock.onGet("/banner").reply(200, banner);
```
##### 5.在app.js入口文件中调用
###### import "./mock"
##### 注：  mock.onGet("接口").reply()可以接收一个函数,并返回promise对象
##### 注：必须在app.js中调用

```

mock.onGet("/newsDetail").reply((config) => {})
config.params.xx 可以得到数据中的参数
```
#### 2.利用mock做假数据
[link] (http://mockjs.com/)
###### 1.下载 mockjs
###### 2.导入 import mock from "mockjs"
###### 3.mock.mock(数据)

```
mock.mock({
    id: i,
    title: "@ctitle",
    content: "@cparagraph",
    ptime: "@datetime",
    ctime: "@time",
    url: `./static/news${temp}.jpg`
  })
```
###### 参数
- [x] cname     中文名字
- [x] title     标题
- [x] content   内容  
- [x] ptime     日期
- [x] ctiem     事件
- [x] sentence  语句




