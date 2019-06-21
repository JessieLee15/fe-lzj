# colure 笔记

## 闭包
### 概念
* 【MDN】：
  闭包指那些能够访问 _自由变量_ 的函数

  自由变量：在函数中使用的，但既不是函数参数也不是函数局部变量的变量

* 【ECMAScript】：
  1. 理论：所有函数。因为她们都在创建时就将上层上下文的数据保存了（作用域链）（注意理解误区：js执行上下文或作用域理解为闭包）
  2. 实践：
    * 即使创建它的上下文已经销毁，它仍然存在（eg：内部func从父func返回）
    * 在代码中引用了自由变量

* 理解： 闭包与普通函数的区别：携带了执行环境

* 组成部分：
  * 环境部分
    * 环境：函数的词法环境（执行上下文的一部分）
    * 标识符列表：函数中用到的未声明的变量
  * 表达式部分：函数体


```js
var scope = 'global scope';
function checkscope(){
  var scope = 'local scope';
  function f(){                 //f执行上下文维护了一个作用域链
    return scope;               //fContext = {
  }                             //  scope:{AO, checkscopeContext.AO, globalContext.AO}
  return f;                     //}
}
var foo = checkscope();
foo();
```
> This combination of a function object and a scope(a set of variable bindings)in which the function`s variables are resolved is called aclosure in the computer literature.

```js
var data = [];
for (var i = 0; i < 3; i++){
  data[i] = function(){
    console.log(i);
  }
}
data[0]();
data[1]();
data[2]();
```

```js
var data = [];
for (var i = 0; i < 3; i++){
  data[i] = (function(i){
    return function(){
      console.log(i);
    }
  })(i);
}
data[0]();
data[1]();
data[2]();
```



