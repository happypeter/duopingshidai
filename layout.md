---
layout: book
title: 弹性布局和媒介
---

### 弹性布局

响应式网站设计主要包括三个部分，弹性布局，media queries，还有弹性媒介。其中弹性布局，就是说网站页面布局使用弹性网格，从而能够动态地把页面布局调整为任意宽度。弹性网格使用相对长度单位，最常用的是百分比或者是 em 单位。这些相对长度，然后用于声明常见的网格属性值，比如 width、margin 或者 padding。

弹性布局不使用固定的测量单位，比如像素或者英寸。原因是，视窗（ viewport ）的高度和宽度在不同设备之间不断地改变，那么网站布局就需要适应这样的改变，所以固定长度有太多的局限性。幸运的是，伊森
给出了一个简单公式，可以确定弹性布局的比例值。

这个公式的含义是，用一个元素的宽度（ target ）除以它的父元素的宽度（ parent ），那得到的计算结果（ result ）就是这个元素的相对宽度。

```
target / parent = result
```

<!-- https://teamtreehouse.com/library/responsive-layouts/responsive-theory/thinking-in-relative-units -->

### bootstrap 自带流体网格

### flexbox

- 弹性布局和媒介的信息
  http://learn.shayhowe.com/advanced-html-css/responsive-web-design/
