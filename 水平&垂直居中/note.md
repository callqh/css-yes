# 水平居中

- 行内元素
  - `text-align:center`
- 块级元素
  - 宽高已知:
    - 给需要居中的元素设置`margin: 0 auto`
    - 设置 `absolute`, `left: 50%`, `margin-left:-自身宽度的一半`
  - 宽高未知:
    - 设置 `absolute`, `left: 50%`, `transform: translateX(-50%)`
    - 给父级设置 flex 布局,并设置`jusitify-content: center`

# 垂直居中

- 宽高已知:
  - 设置 `absolute`, `top: 50%`, `margin-top:-自身宽度的一半`
- 宽高未知:
  - 设置 `absolute`, `left: 50%`, `transform: translateX(-50%)`
  - 给父级设置 flex 布局,并设置`align-items: center`

# 垂直水平居中

- 综合上面情况
- `position: absolute; top: 0; left: 0; bottom: 0; right: 0; margin: auto;` 注意这里 margin 必须左右都为`auto`,不能`0 auto`
