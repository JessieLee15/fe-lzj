# 模块



# 模块加载
1. commonJS
  1. 特点：
    * 缓存
    * 同步加载
  2. 环境：服务器环境
  3. 应用：nodejs的模块规范是参照commonJS实现的
  4. 规范：
    * 导入：require('路径')
    * 导出：module.exports和exports

2. AMD
  1. 特点：
    * 异步加载
    * 管理模块之间的依赖性，便于代码的编写和维护
  2. 环境：浏览器环境
  3. 应用：requireJS是参照AMD规范实现的
  4. 规范：
    * 导入：require(['模块名称'], function ('模块变量引用'){// 代码});
    * 导出：define(function (){return '值');

3. CMD
  1. 特点：
    * CMD是在AMD基础上改进的一种规范，和AMD不同在于对依赖模块的执行时机处理不同，CMD是就近依赖，而AMD是前置依赖
    * CMD loader 的模块加载大体流程
      1. 首先，通过 use 方法来加载入口模块，并接收一个回调函数， 当模块加载完成， 会调用回调函数，并传入对应的模块。use 方法会 check 模块有没有缓存，如果有，则从缓存中获取模块，如果没有，则创建并加载模块。
      2. 获取到模块后，模块可能还没有 load 完成，所以需要在模块上绑定一个 "complete" 事件，模块加载完成会触发这个事件，这时候才调用回调函数。
      3. 创建一个模块时，id就是模块的地址，通过创建 script 标签的方式异步加载模块的代码（factory），factory 加载完成后，会 check factory 中有没有 require 别的子模块:
        * 如果有，继续加载其子模块，并在子模块上绑定 "complete" 事件，来触发本身 的 "complete" 事件；
        * 如果没有则直接触发本身的 "complete" 事件。
      4. 如果子模块中还有依赖，则会递归这个过程。
      5. 通过事件由里到外的传递，当所有依赖的模块都 complete 的时候，最外层的入口模块才会触发 "complete" 事件，use 方法中的回调函数才会被调用。
  2. 环境：浏览器环境
  3. 应用：
  4. 规范：
    * 导入：define(function(require, exports, module) {});
    * 导出：define(function (){return '值');
    ```js
    // a.js
    define(function (require, exports, module){
    　　exports.a = 'hello world';
    });
    // b.js
    define(function (require, exports, module){
        var moduleA = require('./a.js');
        console.log(moduleA.a); // 打印出：hello world
    });
    ```


4. UMD
  1. 特点：
    * 兼容AMD和commonJS规范的同时，还兼容全局引用的方式
  2. 环境：浏览器或服务器环境
  3. 应用：seajs是参照UMD规范实现的，requireJS的最新的几个版本也是部分参照了UMD规范的实现
  4. 规范：无
    ```js
    //常规写法
    (function (root, factory) {
      if (typeof define === 'function' && define.amd) {
          //AMD
          define(['jquery'], factory);
      } else if (typeof exports === 'object') {
          //Node, CommonJS之类的
          module.exports = factory(require('jquery'));
      } else {
          //浏览器全局变量(root 即 window)
          root.returnExports = factory(root.jQuery);
      }
    }(this, function ($) {
        //方法
        function myFunc(){};
        //暴露公共方法
        return myFunc;
    }));
    ```

  5. ES6 module
    1. 特点：
      * 按需加载（编译时加载）
      * import和export命令只能在模块的顶层，不能在代码块之中（如：if语句中）,import()语句可以在代码块中实现异步动态按需动态加载
    2. 环境：浏览器或服务器环境（以后可能支持）
    3. 应用：ES6的最新语法支持规范
    4. 规范：
      * 导入：import {模块名A，模块名B...} from '模块路径'  /////  import('模块路径').then()方法
      * 导出：export和export default
      * 注意：export只支持对象形式导出，不支持值的导出，export default命令用于指定模块的默认输出，只支持值导出，但是只能指定一个，本质上它就是输出一个叫做default的变量或方法
      ```js
      /*错误的写法*/
      // 写法一
      export 1;

      // 写法二
      var m = 1;
      export m;

      // 写法三
      if (x === 2) {
        import MyModual from './myModual';
      }

      /*正确的三种写法*/
      // 写法一
      export var m = 1;

      // 写法二
      var m = 1;
      export {m};

      // 写法三
      var n = 1;
      export {n as m};

      // 写法四
      var n = 1;
      export default n;

      // 写法五
      if (true) {
          import('./myModule.js')
          .then(({export1, export2}) => {
            // ...·
          });
      }

      // 写法六
      Promise.all([
        import('./module1.js'),
        import('./module2.js'),
        import('./module3.js'),
      ])
      .then(([module1, module2, module3]) => {
        ···
      });
      ```