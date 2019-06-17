# html-标签

# 标签
* head里面的元信息类（title meta style link base）：描述文档的基本信息
* 语义类（section nav 类div）
* 替换类（img video audio）
* 表单类 （input button）
* 表格类
* ...

## 元信息类标签
* 描述自身的信息，HTML用于描述文档自身的一类标签，常出现在<head></head>中，一般都不会在页面被显示出来（其他标签描述的是业务）
* 多数情况是给浏览器、搜索引擎等机器阅读的；这些信息有时会在页面之外显示给用户，有时则不会

### 逐一介绍：
> head
  * 本身不携带任何信息，主要作为容器
  * 规定自身必须是html标签中的第一个标签
  * 其内容必须包含一个title(如果作为iframe，或其他方式指定了标题，可不包含)，最多只能包含一个base

> title
  * 作为元信息，可能会被用在浏览器收藏夹、微信推送卡片、微博等场景（上下文缺失，title应完整概括整个网页内容）
  * headding(h1 - h6)：用于页面展示，可默认有上下文，有链接辅助，可简写

> base
  * 历史遗留标签，给页面上所有URL相对地址提供一个基础
  * 最多只有一个，改变全局的链接地址（dangerous），实际开发中建议用javascript代替他

> meta
  * 一组键值对，它是一种通用的元信息表示标签
  * 可任意多个。
  * 一般由name（元信息的名）和content（元信息的值）两个属性来定义
    * name：约定比较自由，http规定了一些作为大家使用的共识，也鼓励大家发明自己的name
  * meta的一些变体：简化书写或声明自动化行为
    * 具有charset属性的meta（无需再有name和content）
      * ```<meta charset="UTF-8" >```
      * 描述了HTML文档自身的编码形式，建议放在head的第一个
    * 具有 http-equiv属性的meta
      * 表示执行一个命令（不需要name属性了）
      * ```<meta http-equiv="contant-type" content="text/html; charset=UTF-8" > ``` 相当于添加了content-type这个http头，并制定了http编码方式
      * 其他命令： 
        * content-language 指定类容的语言
        * default-style 指定了默认样式表
        * refresh 刷新
        * set-cookie 模拟http头set-cookie，设置cookie
        * x-ua-compatiable 模拟http头x-ua-compatiable，声明ua兼容性
        * content-security-policy 模拟http头content-security-policy，声明内容安全性
    * name 为 viewport 的meta
      * 没有在HTML标准中定义，确是移动端开发的事实标准
      * 它的content是一个复杂结构，用逗号分隔的键值对，格式是key=value
      * eg： ```<meta name="viewport" content="width=500, initial-scale=1" >
        * width/height：页面宽度/高度，具体数字或device-width/device-height，表示跟设备宽度/高度相等
        * initial-scale：初始化缩放比例
        * minimum-scale：最小缩放比例
        * maximum-scale：最大缩放比列
        * user-scalable：是否允许用户缩放（已经做好移动端适配的网页，应该把用户缩放功能禁止掉，宽度为设备宽度）
      * 一个标准的meta：```<meta name="viewport" contant="width=device-width,initial-scale=1,maxinum-scale=1,user-scale=no">```
    * 其他预定义的meta
      * applica-name: 应用名称
      * author: 页面作者
      * description: 页面描述（用于搜索引擎等）
      * generator: 生成页面使用的工具，主要用于可视化编辑器（手写的不需要）
      * keywords: 页面关键字，SEO
      * referrer: 跳转策略，一种安全考量
      * theme-color: 页面风格颜色，实际不会影响页面，浏览器可能据此调整页面之外的UI


###  补充（杂）
  ``` html
  <!-- 默认使用最新浏览器 -->
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

  <!-- 不被网页（加速）转码 -->
  <meta http-equiv="Cache-Control" content="no-siteapp">

  <!-- 搜索引擎抓取 -->
  <meta name="robots" content="index,follow">

  <!--  删除苹果默认的工具栏和菜单栏 -->
  <meta name="renderer" content="webkit">
  <meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,minimum-scale=1,user-scaleble=no,minimal-ui">
  <meta name="apple-mobile-web-app-capable" content="yes">

  <!-- 设置苹果工具栏颜色 -->
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  ```

* 第三方分享： 
  * Open Graph 标签组，包括title、type、URL、site_name、description和image，为Facebook分享提供信息；
  * Twitter 标签组，包括card、title、description和image，为Twitter分享提供信息；
  * msapplication 标签组，包括TitleColor和TitleImage，为Windows8以及以上系统识别favicons用

* format-detection: 禁止iPhone自动识别（ios的webview的一种特性，针对长串的数字符合手机号、电话就自动识别成可拨号链接，然后标成绿色）
  ```<meta name="format-detection" content="telephone=no,date=no,address=no,email=no,url=no"/>```




 












## 语义类标签

* div和span：在“界面场景”中，直接使用
* 其他语义类标签：多用可能效果不好（冗余 增加嵌套） 分场景使用
  * 对开发者友好，可读性
  * 文字表现力丰富，SEO 读屏软件

#### W3C 上的说明
定义和用法：

以下元素都是短语元素。虽然这些标签定义的文本大多会呈现出特殊的样式，但实际上，这些标签都拥有确切的语义。

我们并不反对使用它们，但是如果您只是为了达到某种视觉效果而使用这些标签的话，我们建议您使用样式表，那么做会达到更加丰富的效果。

用对 > 不用 > 用错

### eg
作为自然语言和纯文本的补充，用来表达一定的结构或消除歧义

* ruby：和善美好（shangxinbingkuang） ``` <ruby></ruby> <rt></rt> <rp><rp>```
* 必要的标签：表达意思 ```<em></em>```
  * ```<em> ```标签告诉浏览器把其中的文本表示为强调的内容。对于所有浏览器来说，这意味着要把这段文字用斜体来显示。最好还是不要滥用强调。
  * ```<strong>``` 标签和 ```<em>``` 标签一样，用于强调文本，但它强调的程度更强一些。如果常识告诉我们应该较少使用 ```<em>``` 标签的话，那么 ```<strong>``` 标签出现的次数应该更少。

作为标题摘要    ```<h></h> <hgroup></hgroup> <section><section>(h5)```
* 自动生成目录结构 （HTML标准中还专门规定了生成目录结构的算法）

作为整体结构
* 浏览器的“阅读模式”


## 