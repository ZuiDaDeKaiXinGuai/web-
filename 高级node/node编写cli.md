### 什么是cli

命令行界面（英语：command-line interface，缩写：CLI）是在图形用户界面得到普及之前使用最为广泛的用户界面，它通常不支持鼠标，用户通过键盘输入指令，计算机接收到指令后，予以执行。也有人称之为字符用户界面（CUI）。

![image](https://note.youdao.com/yws/public/resource/3c39708a20e4a060a913ea3fa4c27750/xmlnote/0BE5EBC55AFD49019FAF0ADF8A4E9CEB/4447)

### 用node编写cli

1. 创建package.json `name属性不能跟npm上已有包重名`
2. package.json中的bin字段
```
bin{
    "指令":"要运行的文件"
}
```
3. 创建要运行文件

```
#!/usr/bin/env node 
```
使用nodejs运行该程序
4. 全局安装你的包
5. 接受命令行参数
```
process.argv来获取命令行参数
process.argv是一个参数数组
第一项为node.exe的绝对路径
第二项为执行该js的绝对路径
```

6. 发布npm包