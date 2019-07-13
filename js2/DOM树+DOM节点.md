### 什么是DOM

> Document Object Model（文档对象模型）的缩写

#### DOM树

![image](https://github.com/typeofYh/bookpic/blob/master/ct_htmltree.png?raw=true)

#### 节点分类

> 元素节点（每个 HTML 元素是元素节点）

```
<div></div>
<p></p>
<ul><li></li></ul>
```


> 文本节点

```
<p>这是文本节点</p>
```


> 属性节点（每个 HTML 属性是属性节点）

```
<div class="wrap" id="wrap"></div>
```

> 注释节点

```
<!-- -->
```

> 文档节点（整个document是一个文档节点）

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
</html>
```

#### 节点属性

元素类型 | nodeType | nodeName(tagName) | nodeValue 
---|--- | ---|---
元素节点 | 1 | 标签名大写 | null
属性节点 | 2 |属性名小写 | 属性值
文本节点 | 3 |#text | 文本内容
注释节点 | 8 |#comment  | 空
文档节点 | 9 |#document  | null

> 理解节点关系

![image](http://localhost/book/ct_parentnode.png)


```
parent.firstChild
```
```
parent.lastChild
```
```
target.parentNode
```
```
parent.childNodes
```
```
target.nextSibling
```
```
target.nextElementSibling
```
```
target.previousSibling
```
```
target.previousElementSibling
```
> 元素属性方法

```
target.getAttributeNode('属性名')<!--获取属性节点-->
```

```
target.getAttribute('属性名')
```

```
target.setAttribute('属性名','属性值')
```

```
target.removeAttribute('属性名')
```
>获取节点
```
parent.getElementById('id')
```
```
parent.getElementsByTagName('标签名')
```
```
parent.getElementsByName('name')
```
```
parent.getElementsByClassName('class')<!--兼容IE9及以上-->
```
> css选择符

```
parent.querySelector()
```
```
parent.querySelectorAll()
```




> 创建节点

```
document.createElement('标签名')
```
```
document.createTextNode('文本')
```
> 操作节点

```
parent.removChild(childnode)
```
```
parent.appendChild(childnode)
```
```
parent.insertChild(新节点,要在它之前插入的节点)
```
```
parent.replaceChild(新节点,要替换的节点)
```
```
target.cloneNode(true/false)
```