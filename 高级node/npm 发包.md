#### npm 发包

> 注册npm账号

[点击前往npm官网地址](https://www.npmjs.com/)

> 准备要发布的包

```
package.json
    {
        main:"入口文件" //之后require要加载的文件
        bin:{
            指令:"要运行的文件" //#!/usr/bin/env node 指定以nodejs运行 
        },
        name:包名 //以后npm要下载的包名
    }
README.md
    md格式的说明文件，最终会展示在该包的首页
其他目录自己定义
```

> 登陆

```
npm login
//登陆一次就可以
```
`必须保证下载源地址为http://registry.npmjs.org`

> 发布

```
npm publish
```
`失败查看报错信息`


------


#### npm 更新包

> 更新版本号

```
package.json
    {
        version:'x.y.z',
        //修复bug,小改动，增加z
        //增加了新特性，但仍能向后兼容，增加y 
        //有很大的改动，无法向后兼容,增加x 
    }
```

更新部分 | 指令
---|---
z | npm version patch
y | npm version minor
x | npm version major



> 发布更新之后的包

```
npm publish
```

----

#### 删除包

```
npm unpublish 包名称 --force
```

推荐使用

```
npm deprecate 包名称 '警告信息'
```

使用这个命令，并不会在社区里撤销你已有的包，但会在任何人尝试安装这个包的时候得到警告

