# css杂

## 语法
### at规则
[@charset](https://www.w3.org/TR/css-syntax-3/)
用于提示css文件使用的字符编码方式，如果被使用，必须在最前面。

[@import](https://www.w3.org/TR/css-cascade-4/)
用于引入一个css文件，除了@charset规则不会被引入，@import可以引入另一个文件的全部内容；支持supports和media query形势。

[@media](https://www.w3.org/TR/css3-conditional/)
media query

[@page](https://www.w3.org/TR/css-page-3/)
用于分页媒体访问网页时的表现设置，页面是一种特殊的盒模型结构，除了页面本身，还可以设置它周围的盒

[@counter-style](https://www.w3.org/TR/css-counter-styles-3)
产生一种数据，用于定义列表的表现

[@keyframes](https://www.w3.org/TR/css-animations-1/)
产生一种数据，用于定义动画关键帧

[@fontface](https://www.w3.org/TR/css-fonts-3/)
用于定义一种字体（icon font技术就是利用这个特性实现的）

[@supports](https://www.w3.org/TR/css3-conditional/)
检查环境的特性，跟media比较类似

[@namespace](https://www.w3.org/TR/css-namespaces-3/)
用于跟XML命名空间配合的一个规则，表示内部的CSS选择器全都带上特定命名空间

[@viewport] 用于设置视口的一些特性，不过兼容性不是喊好，多数时候被html的meta代替

[其它] 不太推荐使用的at规则：
* @color-profile：是SVG1.0引入的CSS特性，但是实现状况不怎么好
* @document：还没讨论清楚，被推迟到了CSS4中
* @font-feature-values：. . .

### 普通规则
主要由选择器和声明区块构成。

声明区块：由属性和值构成

#### 选择器
有一份独立的CSS和HTML共用的[标准](https://www.w3.org/TR/selectors-4/)

任何选择器都是由几个符号结构连接的：空格、大于号、加号、波浪线、双竖线
* > ：子代选择器
* ～ ： 后继选择器 （只作用一层）
* + ：直接后继选择器
* || ：选中表格中的一列

#### 声明：属性和值
属性是由中划线、下划线、字母等组成的标识符，CSS还支持用反斜杠转移。（属性不允许使用连续的两个中划线开头，被认为是CSS变量）

在[CSS Variables](https://www.w3.org/TR/css-variables/)标准中，以双中划线开头的属性被当作变量，与之配合的是var函数
``` css
:root {
  --main-color: #06c;
  --accent-color: #006;
}

# foo h1 {
  color: var(--main-color);
}
```

值的标准：[CSS Values and Unit](https://www.w3.org/TR/css-values-4/)，值的类型：
* CSS范围的关键字：initial，unset，inherit，任何属性都可以的关键字
* 字符串
* URL：使用url()函数的URL值
* 整数/实数：如flex属性
* 维度：单位的整数/实数，如width属性
* 百分比
* 颜色
* 图片
* 2D位置
* 函数：如transform属性

CSS支持一批特定的计算函数：
* calc()：支持四则运算。在针对维度进行计算时，允许不同单位混合运算
```css
section {
  float: left;
  margin: 1em; 
  border: solid 1px;
  width: calc(100%/3 - 2*1em - 2*1px);
}
```
* max()、min()和clamp()：比较大小

* toggle()：在规则选中多于一个元素时生效，它会在几个值之间来回切换。eg：让一个类标项的样式圆点和方点间隔出现：
```css
ul {
  list-style-type: toggle(circle, square)
}
```
* attr()：允许CSS接收属性值的控制