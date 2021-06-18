# BFC

BFC: 块级格式化上下文. 具有 BFC 特性的元素相当于是一个独立的容器,它内部的子元素如何排列都不会影响到容器外面的元素

## 触发 BFC 的方式

- html 根元素
- 浮动元素: float 不为 none
- 绝对定位元素: position 为 absolute,fixed
- overflow 为 hidden,auto,scroll
- display 为 inline-block,table-cell,flex

## BFC 的应用

### 1. 解决 margin 高度塌陷的问题

两个元素之间的 margin 会选取较大的那一个,而不是两个元素 margin 的和

```html
<p style="border: 1px solid red; margin-bottom: 20px">123</p>
<p style="border: 1px solid red; margin-top: 30px">456</p>
```

上面这个代码就会造成一个问题: 两个元素之间的 margin 只有 30px,而不是 20+30=50px,这就是外边距折叠
而我们解决这个问题只需要将其中一个或者两个元素放在一个 BFC 中

```html
<!-- 触发BFC -->
<div style="overflow: hidden">
  <p style="border: 1px solid red; margin-bottom: 20px">123</p>
</div>
<!-- 触发BFC -->
<div style="overflow: hidden">
  <p style="border: 1px solid red; margin-top: 30px">456</p>
</div>
```

这样两个元素的外边距就是正常的 20+30=50px 了

### 2. BFC 可以包裹浮动的元素(清除浮动)

当一个元素产生浮动后,就脱离标准文档流了,所以没办法撑开父级元素的高度,这时就需要我们去清除浮动,让他正常的去撑开父级的宽度.

```html
<div style="border: 1px solid red">
  <p style="border: 1px solid green; float: left">我要浮动啦</p>
</div>
```

上面这段代码因为 p 标签发生了浮动,所有 div 的高度没有被撑开,变成了一条线.
解决办法也很简单,就是给他的父级触发 BFC 特性

```html
<div style="border: 1px solid red; overflow: hidden">
  <p style="border: 1px solid green; float: left">我要浮动啦</p>
</div>
```

这样父级元素就包裹住了浮动元素,使其高度被撑开

### 3. 解决浮动造成的元素覆盖

下面这段代码就被浮动元素给覆盖了

```html
<!-- 被浮动元素覆盖 -->
<p style="border: 1px solid green; float: left">我要浮动啦</p>
<p style="border: 1px solid black; width: 50px; height: 50px">没人权</p>
```

通过触发第二个元素的 BFC 特性就可以解决这个问题

```html
<p style="border: 1px solid green; float: left">我要浮动啦</p>
<p style="border: 1px solid black; width: 50px; height: 50px;overflow:hidden">没人权</p>
```

## 清除浮动

1. 触发 BFC 上文已经提过
2. 利用伪元素`::after`

```css
.clear::after {
  content: '';
  display: block;
  clear: both;
}
```

> `clear: both`: 意味着该块级元素左右两侧不允许存在浮动. 在父级元素的后面创建该伪元素并且设置 clear:both,来清除浮动
