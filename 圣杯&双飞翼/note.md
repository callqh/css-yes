# 三栏中间自适应布局

## 圣杯布局

html 结构中将中间部分放在第一个,首先渲染

1. 给 left,right,middle 设置`float:left`进行浮动. 这时需要注意给外部包裹他们的父级设置`overflow:hidden` 触发 BFC
2. 给 left,right 设置对应的宽度 150px,middle 设置 100%的宽度
3. 给 left 设置`margin-left:-100%`,使其排列在 middle 的左侧
4. 给 right 设置`marin-left:-150px`,使其排列在 middle 的右侧
5. 这时 middle 区域的左右两侧是被 left 和 right 覆盖了的,这时我们需要给他们的父级 main 设置 padding,将左右两侧的距离挤压出来`padding: 0 150px`
6. 最后给 left 和 right 设置相对定位`position: relative`. left 区域的向左侧移动-150px 移动到 padding 挤压出来的区域,同理 right 向右侧移动-150px

```html
<!-- 上 -->
<div class="header">header</div>
<!-- 中 -->
<div class="main">
  <div class="middle">middle</div>
  <div class="left">left</div>
  <div class="right">right</div>
</div>
<!-- 下 -->
<div class="footer">footer</div>
```

## 双飞翼布局

其实前面的步骤和圣杯布局都一样.不同的是双飞翼在 middle 区域又添加了一个 div 来包裹.
然后主要区别在第 5,6 步

5. 给 middle-inner 设置 margin,讲 left,right 的位置给挤压出来

```html
<!-- 上 -->
<div class="header">header</div>
<!-- 中 -->
<div class="main">
  <div class="middle">
    <!-- 和圣杯布局区别的地方 -->
    <div class="middle-inner">middle</div>
  </div>
  <div class="left">left</div>
  <div class="right">right</div>
</div>
<!-- 下 -->
<div class="footer">footer</div>
```

## flex 布局

1. 直接给父级设置 flex 布局
2. left 和 right 设置`flex-basic: 200px`,进行固定宽度
3. middle 设置`flex:1`自适应
4. middle 布局的时候还是放在最上面.通过 order 来调整顺序: left: order=1,middle: order=2, right: order=3
