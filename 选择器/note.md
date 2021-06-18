# 选择器

## 选择器种类

1. id 选择器(`#id`)
2. 类选择器(`.active`)
3. 伪类选择器(`:hover`)
4. 属性选择器(`[attr=]`)
5. 标签选择器(`div`)
6. 伪元素选择器(`::before`)
7. 通用选择器(`*`)

## 选择器间的优先级

` id选择器 > 类选择器,伪类选择器, 属性选择器 > 标签选择器, 伪元素选择器 > 通用选择器`

## 常见的关系符

- A , B : A 或者 B
- A B: A 的所有子级元素 B
- A > B: A 的所有直接子级
- A + B: A 的下一个相邻兄弟元素
- A ~ B: A 的下面任意一个兄弟元素

## 属性选择器

属性选择器的使用. 用`[]`包括, 里面写属性的名称和属性值

```html
<p data-attr="nice">Paragraph 3</p>
<p alt="test">Paragraph 4</p>
```

```css
[data-attr='nice'] {
  font-weight: bolder;
}
[alt] {
  font-size: 12px;
}
```

`[alt]` : 选中所有带有 alt 属性的元素
`[id]` : 选中所有带有 id 属性的元素
`[class]` : 选中所有带有 class 属性的元素
`[data-attr='nice']`: 选中属性名为`data-attr` 并且属性值为`nice`的元素

## 伪类元素和伪元素

- 区别:
  - 伪类元素使用一个冒号(`:`)表示,伪元素是用两个冒号(`::`)
