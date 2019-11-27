# css 居中

## 水平居中（左右）
* 文字
`text-align: center;` 容器必须是块级元素
* 图片
`text-align: center;` 容器必须是块级元素
* 定宽
  1. `margin: 0 auto;` 定宽容器居中(容器必须是块级元素) `text-align: center;` 容器内文字居中
  2. `left: 50%; margin-left: -150px;` 绝对定位+负边距(容器不限) `text-align: center;` 容器内文字居中
* 未知宽度
  1. 基础的 `text-align + inline-block`
  2. 绝对定位+transform
  3. 浮动
  4. flex
  5. fit-content配合margin：“fit-content”是CSS中给“width”属性的一个属性值。