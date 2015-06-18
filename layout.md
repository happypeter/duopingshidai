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

### 弹性媒介

接下来，介绍一下响应式网站设计的另一重要部分，弹性媒介。随着视窗开始改变大小，网站上的媒介并不总是变得很合适。图片、视频和其它媒介类型需要可伸缩性，按照视窗变动的大小，来改变它们的尺寸。

一个快速的方法，让媒介具有可伸缩性，就是把 max-width 的属性值设置为 100%。这样做就确保了当视窗变小的时候，网站上的任何媒介都会根据其容器的宽度缩小。

{% highlight css %}
img, video, canvas {
  max-width: 100%;
}
{% endhighlight %}

### 弹性媒介 demo

### 弹性嵌入式媒介

不幸的是，这个 max-width 属性并不适用所有的媒介应用场景，尤其是对于嵌入式媒介，像通过 <iframe> 标签 或 在 HTML5 中使用 <video> 标签嵌入的视频，这种情况下，仅仅一个 max-width 属性是不能解决问题的。

实现嵌入式媒介的响应式布局，嵌入式媒介在其父元素中的摆放位置，需要采用绝对定位方式确定。父元素的宽度要设置为 100%，这样父元素就能基于视窗宽度来调整其大小。另外，为了触发 IE 浏览器的 hasLayout 机制，父元素的高度需要设置为0。

父元素的下内边距 padding-bottom 的属性值要与视频的长宽比保持一致。这是为了让父元素的高度与其宽度是相称的。记得前面那个响应式设计公式吗？ 如果一个视频的长宽比是 16:9，16除以9等于 .5625，这样父元素下内边距为56.25%。设置下内边距而不是上内边距是为了专门阻止 IE 5.5 把父元素当做绝对定位元素看待。

{% highlight html %}
<figure>
  <iframe src="https://www.youtube.com/embed/4Fqg43ozz7A"></iframe>
</figure>
{% endhighlight %}

{% highlight css %}
figure {
  height: 0;
  padding-bottom: 56.25%; /* 16:9 */
  position: relative;
  width: 100%;
}
iframe {
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
{% endhighlight %}

<!-- https://teamtreehouse.com/library/responsive-layouts/responsive-theory/thinking-in-relative-units -->

### bootstrap 自带流体网格

### flexbox

- 弹性布局和媒介的信息
  http://learn.shayhowe.com/advanced-html-css/responsive-web-design/
