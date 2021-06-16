# 盒模型

盒模型分为两种:

1. IE 盒模型,也叫作**怪异盒模型**
2. **标准盒模型**

## 怎么使用两种模型

默认情况下, 正常的盒子采用的是`box-sizing: content-box`**标准盒模型**
我们可以通过`box-sizing: border-box`来切换成为 **IE 盒模型**

## 两种盒模型的差别

两种盒模型的差别主要体现在宽高的计算上.

- 怪异盒模型: `width = content + padding + border`.
- 标准盒模型: `width = content`

> 这里我们需要注意的是,在怪异盒模型下,当我们增加了 padding 和 border 的宽度之后,content 的对应的宽度就会缩减.
>
> 关注点不同:
>
> - 怪异盒模型它会保持总体的 width 不变,而去调整 content 的大小. 他的关注点是总体的宽度
> - 标准盒模型,在 padding 或者 border 增加之后,整体宽度会对应增加,content 区域不变,所以它的关注点是在 content
