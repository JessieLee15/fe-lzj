# Thread

js执行环境：单线程，浏览器只给js任务开了一个线程，多个任务排队执行，遇到长耗时任务或死循环，页面就会无响应。

js的同步和异步：本质还是单线程，只是任务的执行模式不同 （异步任务不具有“堵塞”效应，为不连续的执行）

## js的异步编程

#### 一. 回调函数（Callback）
简单、容易理解和实现；不利于阅读和维护，耦合高，导致Callback Hell； 每个任务只能指定一个回调函数；try catch捕获不到异常，不能直接return
``` javascript
ajax(url, () => {
   // 处理逻辑
   ajax(url1, () => {
       // 处理逻辑
       ajax(url2, () => {
           // 处理逻辑
       })
   })
})
```

#### 二. 事件监听
代码顺序不代表执行顺序，事件触发控制执行
容易理解，可绑定多个事件，每个事件可指定多个回调函数，去耦合，有利于模块化； 事件驱动型，运行流程不清晰，阅读性差
```javascript
f1.on('done', f2);
function f1() {
 setTimeout(function () {
   // ...
   f1.trigger('done');
 }, 1000);
}
```

#### 三. 发布订阅(publish-subscribe pattern/observer partten)
同“事件监听”类似；出现“消息中心”统一管理信号

#### 四. Promise/A+

缺点：无法取消 Promise，错误需要通过回调函数捕获

##### 1. Promise 状态
1. Pending - Promise对象实例创建时的初始状态
2. Fulfilled - 成功的状态
3. Rejected - 失败的状态

resolved => then

rejected => catch

__这个承诺一旦从等待状态变成其他状态就永远不能更改状态了__

__当我们在构造Promise的时候，构造函数内部的代码是立即执行的：__

```javascript
new Promise((resolve, reject) => {
 console.log('new Promise')
 resolve('success')
})
console.log('end')
// new Promise
//end
```

##### 2. Promise 的链式调用
* 每次返回的都是一个新的Promise实例
* 如果then中返回的是一个结果，会把这个结果传递下一次then中的成功回调
* then中使用return：会被Promise.resolve()包装
* catch 会捕获到没有捕获的异常


#### 五. 生成器 Generators/yield
* es6语法
* 可以控制函数执行
* __generator/iterator并非异步代码，是一些框架（co）使用这样的特性来模拟async/await；但是generator/iterator并非被设计成实现异步__
```js
function *foo(x) {
 let y = 2 * (yield (x + 1))
 let z = yield (y / 3)
 return (x + y + z)
}
let it = foo(5)
console.log(it.next())   // => {value: 6, done: false}
console.log(it.next(12)) // => {value: 8, done: false}
console.log(it.next(13)) // => {value: 42, done: true}
```

#### async/await
* async/await 是基于 Promise 实现的，它不能用于普通的回调函数
* async/await 与 Promise 一样，是非阻塞的

一个函数如果加上 async ，那么该函数就会返回一个 Promise

##### Async/Await 并发请求






__引用及参考资源__: 

[js的同步异步](https://mp.weixin.qq.com/s/Y21LMWcEatoBvtnqvQyxXg)