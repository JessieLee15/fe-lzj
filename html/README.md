# HTML、CSS

## HTML 
### XML HTML XHTML
* XML： 
  * 可扩展标记语言, 为 __文档的创建__，__结构化存储和编码__ 提供了规则。
  * 元语言，为创造其他语言提供了语法机制，同时不会通过预定义的语法限制表达式。

* HTML：
  * 超文本标记语言
  * 词汇表: 它定义了你能写的元素类型 (tag soup)

* XHTML：基于XML的 HTML，语法更严格


### 关于标签的闭合

* 自闭合的标签，如：input, img ...  H5很宽松，填不添加都符合规范
* XHTML严格，必须在自闭合标签中添加"/"
* 自闭合标签来源：“空”元素。 这个词来源于DTD中的一个关键字，标签定义的时候用到，比如img标签的定义：
``` 
  <!ELEMENT img EMPTY>
  <!ATTLIST img %attrs;
  src %URI; #REQUIRED
  alt %Text; #REQUIRED
  longdesc %URI; #IMPLIED
  height %Length; #IMPLIED
  width %Length; #IMPLIED
  usemap %URI; #IMPLIED
  ismap (ismap) #IMPLIED
  >
```
ELEMENT 关键字说明它是一个元素， EMPTY 关键字说明它的内容必须是空白(没有有此关键字的标签使用时就要有闭合标签)
