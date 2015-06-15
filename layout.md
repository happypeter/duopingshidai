---
layout: book
title: 弹性布局和媒介
---

### 弹性布局

响应式网站设计主要包括三个部分，弹性布局，media queries，还有弹性媒介。其中弹性布局，就是说网站页面布局使用弹性网格，从而能够动态地把页面布局调整为任意宽度。弹性网格使用相对长度单位，最常用的是百分比或者是 em 单位。这些相对长度，然后用于声明常见的网格属性值，比如 width、margin 或者 padding。

弹性布局不使用固定的测量单位，比如像素或者英寸。原因是，视窗（ viewport ）的高度和宽度在不同设备之间不断地改变，那么网站布局就需要适应这样的改变，所以固定长度有太多的局限性。幸运的是，伊森
给出了一个简单公式，可以确定弹性布局的比例值。

这个公式的含义是，用一个元素的宽度（ target ）除以它的父元素的宽度（ parent ），那得到的计算结果（ result ）就是这个元素的相对宽度。

{% highlight html %}
target / parent = result
{% endhighlight %}

### 弹性网格

接下来看一个上面公式的应用实例，如何把一个固定宽度的两栏页面布局转变成一个弹性布局。

{% highlight html %}
<div class="main">
  <div class="content"></div>
  <div class="sidebar"></div>
</div>
{% endhighlight %}

一个父元素 main, 包含了两个子元素，子元素 content 居左，另一个子元素 menu 居右，[查看效果](http://book.haoduoshipin.com/go-responsive/demo/fixed-layout.html)。
为了叙述方便，抽取了一些 css 样式：

{% highlight css %}
.main {
  width: 900px;
}
.content, .menu {
  margin: 30px 20px;
}
.content {
  float: left;
  width: 600px;
}
.menu {
  float: right;
  width: 210px;
}
{% endhighlight %}

现在依照上面的弹性网格公式，把 content 和 menu 两个区块的宽度，以及它们的页边距用相对长度来表示，在这个例子中会使用百分比表示法，以 menu 区块为例：

{% highlight css %}
.menu {
  float: right;
  width: 23.33333333%; /* 210 / 900 = 0.2333333333 */
}
{% endhighlight %}


注意，无论父元素 main 变得有多宽，content 和 menu 区块的宽度和页边距都会按比例缩放。

[点击这里](http://book.haoduoshipin.com/go-responsive/demo/flexible-layout.html)，查看最终效果。当然，你需要调整浏览器窗口的大小才能看到变化。

知道了弹性布局的概念，和弹性网格计算公式，并将其运用起来，你就能创建一个完全动态的网站，网站布局按照视窗尺寸缩放。为了更好的掌控弹性布局，你也可以对 min-width、max-width、 min-height、和 max-height 属性值采用相对长度单位。

<!-- https://teamtreehouse.com/library/responsive-layouts/responsive-theory/thinking-in-relative-units -->

### bootstrap 自带流体网格

### flexbox

- 弹性布局和媒介的信息
  http://learn.shayhowe.com/advanced-html-css/responsive-web-design/
