# 坑坑坑


### Firefox
#### focus()不起作用
根本原因：（网上说的）因为在火狐中设置标签焦点的顺序是失去焦点之后才能得到焦点（不知道怎么证实。。。。nima浏览器非要这么个性吗）

解决办法：（网上说的）
   1. 在focus前先blur (亲测没用。。。)
   2. `setTimeout(function(){focus}, 0)` (亲测没用。。。)

😠😠😠

看了下MDN上关于focus()的说明，尼玛也没有提到。。。，唯一的note是：注意在mousedown中调用focus时要注意preventDefault；

他的example倒是起作用，原因是。。。把focus()的调用放在了一个btn的点击事件里面。so, it realy works...(滑稽)

好吧，进一步test:

1. 直接在控制台el.focus()：
    1. safari OK,而且符合失去焦点之后才能得到焦点规律 😺
    2. chrome和firefox Don`t work...根本无法focus

2. 按照MDN中的，在btn click事件中focus：All works；直接在html文档后的script中focus，chrome&safari没问题，firefox不管用（用上面两种方法也没用）。。。。（符合预期呢，呵呵呵呵呵😠）
    1. 会不会是dom加载问题，那么在setTimeout中设置个大的时间吧，结果还是不管用。。。尼玛。。。这个原因排除

结果是博友门说的原因和解决办法也不完全正确。。。

至于真正原因：尼玛，这些个性浏览器还是交给那些大神制裁吧，我这么弱小无能为力

解决办法：。。。。目前想不出来（花了大半天时间弄上面的，这个待续吧）。。。。。

最后顺便补充一下发现这个的地方：[Vue.directive](https://vuejs.org/v2/guide/custom-directive.html#ad  "vue API")好死不死地用focus做example。。。。。哈哈哈哈

本来想做现在现在项目兼容safari的，结果跳出来这么个坑。。。


---

### IE

---

### Safari

---

### Chrome



