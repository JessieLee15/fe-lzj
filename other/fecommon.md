# FE组件库方案

## 项目demo
* 原型与说明：https://juejin.im/post/5d7860b0f265da03bc12a3d2（感恩大佬）
* 技术栈：vue rollup vuepress

## 探索
* npm发布完成 
`npm i fe-commom-testll`
```js
  import FileHandle from 'fe-commom-testll'
  Vue.use(FileHandle)
  <FileHandle />
```

* Vue项目使用
  * 全局引入（包括样式） OK
  * 按需引入 未尝试 貌似要改配置文件

* 其他项目使用
  * rollup打包format选项支持5种，按理讲是OK的
  * 正在了解模块加载



##  方案：。。。。。。
我：结果导向 
寿海：需求驱动

1. 为什么要重构
2. 重构哪些

3. 需求梳理（满足条件）
4. 老系统mis和vss还不一样

5. layui: 二次封装

问题：
1. fisp：公用组件内用artTemplate，调用处提供TPL和数据   =>   Table组件内，自己写提供转化中间件，把当前Table参数转化为Vue组件需要的参数
2. fisp如果不能使用npm包管理的方式，如何管理组件/插件资源？   systemJs

TODO:
1. fisp用npm的问题
  * 这些插件使fis3实现了npm爆管理 及 commonjs 加载模块； npm搜了下没有fis/fisp的包
    ```json
    "fis3-hook-commonjs": "^0.1.26",
    "fis3-hook-node_modules": "^2.2.9",
    ```
2. 再试一下张航的方式