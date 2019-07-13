### commander

Commander是node.js的轻量级，富有表现力和强大的命令行框架。

> commander.option

命令解析

```
commander.option('指令内容 [获取指令内容] <必填项提示>','help 中的指令描述')
```

> commander.version

版本号

```
commander.version('版本号可以获取package.json中的version字段','-V --version'默认指令)
```

> commander.parse

格式化命令行参数

```
commander.parse(process.argv)
```

`参考 vue --help`