# Tips

## 浏览器拦截window.open
`window.open`如果不是在用户触发的事件内部，会被浏览器拦截（各种异步操作内部，最常见的如ajax）

浏览器这样做也是非常可以理解的，只有用户可以自发地打开新页面；防止恶意代码和广告

___解决：__

使用隐藏标签a或button

___


## 有毒的HTML转义字符-&#8236

现象：不知道用户以哪种方式剪切的数据，或者中间经过了什么转发，导致（微信）粘贴到mis这边的数据多了一个HTML的非常特殊的转义字符`&#8236`（猜测是个占位符），encodeURL后是`%E2%80%AC`

目前没有找到在js中处理这个字符的方法

参考文章：
[html】input标签value属性值的字符长度多了1的诡异bug] (https://blog.csdn.net/w390058785/article/details/80692930)