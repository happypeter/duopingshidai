---
layout: book
title: viewport
---

通常，现在的移动设备可以很美观的显示网站内容，从而用户可以在手机上愉悦的浏览网页。但有时候移动设备也需要一点帮助，尤其是在要确认一个网站的视窗大小、缩放和分辨率的情况下。为了弥补这一不足，苹果公司发明了
viewport 元标签（ meta tag ）。

### 视窗高度和宽度

若 viewport 元标签中包含了 height 或 width 属性，就可以分别定义视窗的高度和宽度。height 或 width 的属性值不是一个正整数就是一个关键字。height 属性值可以是 device-height 关键字，width 的属性值可以是 device-width 关键字。使用这些关键字就是把视窗的高度和宽度设置为设备的默认高度和宽度。为了让你的网站能在移动设备上完美地呈现出来，达到最好的用户体验，建议大家使用这两个关键字。

{% highlight html %}
<meta name="viewport" content="width=device-width">
{% endhighlight %}

### 视窗缩放

控制一个网站在移动设备上如何缩放，用户是否可以缩放网站，使用 minimum-scale、 maximum-scale、 initial-scale 和 user-scalable 属性。

当移动设备垂直放置的时候，网站的 initial-scale 应该设置为1，它表示设备高度与视窗高度之间的比率。当移动设备水平放置的时候，intial-scale 则表示设备宽度与视窗宽度之间的比率。initial-scale 取值范围是在0到10之间的正整数。

{% highlight html %}
<meta name="viewport" content="initial-scale=2">
{% endhighlight %}

minimum-scale 和 maximum-scale 这对属性决定了视窗可以缩放到多小和多大。当使用 minimum-scale 属性的时候，它的属性值应该是一个小于或等于 initial-scale 属性值的正整数。同样的，maximum-scale 的属性值应该是一个大于或等于 initial-scale 属性中的正整数。这对属性的取值范围也在0到10之间的正整数。

{% highlight html %}
<meta name="viewport" content="minimum-scale=0">
{% endhighlight %}

一般来说，minimum-scale 和 maximum-scale 的属性值不应该和 initial-scale 属性值一样。这将禁用缩放功能，也可以通过设置 user-scalable 属性达到同样的效果。若
user-scalable 属性值设为 no，则禁用缩放功能。若 user-scalable 属性值设为 yes，则打开缩放功能。

把网站的缩放功能关闭掉并不是一件好事。因为这样破坏了网站的可访问性和易用性，会阻止残疾人士浏览需要的网站。

{% highlight html %}
<meta name="viewport" content="user-scalable=yes">
{% endhighlight %}

### 视窗分辨率

让浏览器基于视窗缩放值来决定如何缩放网站通常是管用的。但是当需要更精确的控制时，特别是超出了设备的分辨率，就会用到 target-densitydpi 属性。它的属性值包括
device-dpi、high-dpi、medium-dpi、low-dpi 或一个实际的 DPI 数值。

虽然很少使用 target-densitydpi 视窗属性，但是当需要缩放到像素级别的时候就尤为重要了。

{% highlight html %}
<meta name="viewport" content="target-densitydpi=device-dpi">
{% endhighlight %}

### 整合视窗属性

这个 viewport 元标签允许在 content 属性值之内，同时设置多个视窗属性，它们之间用逗号分隔开。下面这个例子就同时设置了 width 和 initial-scale 属性。

{% highlight html %}
<meta name="viewport" content="width=device-width, initial-scale=1">
{% endhighlight %}

### CSS 视窗规则

因为 viewport 元标签主要和网站的风格样式打交道，所以建议把它从 html 元标签中移到 CSS 样式中，变成 @viewport 规则。

目前一些浏览器虽然已经实现了 @viewport 规则，不过整个浏览器家族对它支持并不是很好。看一下，@viewport 规则如何编写：

{% highlight html %}
@viewport {
  width: device-width;
  zoom: 1;
}
{% endhighlight %}
