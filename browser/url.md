# 你了解URL吗

## URI与URL


## URL详解

## URL设计

## BOM 与 URL （window.location）

* lacation : a.保存着当前文档的信息；b.将URL解析为独立资源
* window.location 与 document.location 引用的是同一个obj
* location所有属性：

属性名 | 例子 | 说明
  - | - | - 
  href | "http://www.test.com:80/test/list?params1=2&params2=3#footer" | 完整URL，同location.toString()
  protocol | "http:" | 协议
  host | "www.test.com:80" | 服务器名称和端口号
  hostname | "www.test.com" | 服务器名称(不带端口号)
  port | "8080" | 端口号或空串
  pathname | "/test/list" | 目录和（或）文件名
  search | "?params1=2&params2=3" | 查询字符串
  hash | "#footer" | hash或空串

* URL中的查询字符串一般是被编码过的。编码：window.encodeURIComponent()；解码：window.decodeURIComponent()
* location常用方法：
  * location.assign(newURL): 直接给location或location.href赋值其实就是调用的此方法
    * 注：用以上方法修改URL或修改location的属性(除hash)，页面都会重新加载
    * 注：用以上方法修改URL或修改location的属性(包括hash)，浏览器的历史记录都会产生新记录可返回）
  * location.replace(newURL): 不会在历史记录中生成新纪录（不能返回）
  * location.reload(): 无参-以最有效的方式重新加载页面；参数为true-强制从服务器重新加载
    * 位于reload后面的代码可能会也可能不会执行，取决于网络延迟或系统资源等因素



__引用及参考资源__: 

[JavaScript高级程序设计 第三版]


[浏览器输入 URL 后发生了什么](https://zhuanlan.zhihu.com/p/43369093) 
