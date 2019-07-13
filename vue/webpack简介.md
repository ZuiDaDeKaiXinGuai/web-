> 什么是webpack

![image](http:localhost/book/webpack-2.png)

Webpack是模块化管理及打包工具/模块打包机（ module bundler）

它所做的事情是：分析你的项目结构，找到js模块以及其它的一些浏览器不能直接运行的拓展语言（Less、Sass、TypeScript），并将其打包为合适的格式供浏览器使用。

在webpack中所有的文件都是模块。

> 为何要使用webpack？

如今的Web可以看做是功能丰富的应用，拥有复杂的js代码和众多有依赖包，为简化开发复杂度，提高开发效率，涌现了大量的实践：

- es6 模块化
- 全新的js写法，如ES6、TypeScript、CoffeeScript
- Less、Sass等css预处理器

很多实践大大的提高了开发效率，但是浏览器不能解析这些代码，需要进行额外的处理才能让浏览器识别，而手动处理又非常繁琐，于是就需要一些专业的工具。

- Browserify -- 实现浏览器端的commonjs模块化，功能比较单一
- Gulp --- 优化项目的一个工具
- Grunt
- Webpack --- 最好的模块打包机