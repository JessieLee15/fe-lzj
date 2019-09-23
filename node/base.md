# 基础


## CommonJS
* 每个js文件都是一个模块
* 模块对外暴露变量：```module.exports = variable;```
* 引用其他模块的变量：```var ref = require('module_name');```

### CommonJS原理
* 模块的隔离：Javascript是函数式编程语言，支持closure。把模块代码扔到一个自执行函数里面，实现封闭作用域/命名空间
* module.exports：Node事先准备一个对象-module（有load方法，返回module.exports）。在加载函数中（load方法）module作为参数传入（在模块内可以使用module，其实是一个函参）。。。。


### module.exports vs exports

* 区别：不能直接对exports赋值
* 原因：