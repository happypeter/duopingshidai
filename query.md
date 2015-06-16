---
layout: book
title: 媒体查询
---

响应式网站设计只有弹性布局这一个技巧是不够用的。有时候浏览器的视窗宽度可能会太小，小到甚至按比例缩放布局也会出现特别小的栏框，以至于网站内容不能有效地显示。尤其是当网站布局变得很小或很大的时候，网站上的文字可能会变得难以辨认，网站布局也可能会被打乱。这时候，media queries 就派上用场了，它能帮助你设计出更好的用户体验。

媒体查询（ media queries ）是对媒体类型（ media types ）的一次扩展，通常媒体类型会出现在链接 css 样式文件的时候。媒体查询可以为单个浏览器和设备类型指定不同的样式，诸如视窗（ viewport ）宽度或者设备方向， 对设备的判断能力进一步加强了。这种给不同设备使用其专属样式的能力，为响应式网站设计开启了一片新的天地。

在 CSS2.1 中定义了媒体类型，通过给 `<link>` 元素添加 media 属性，可以为不同的媒体类型加载不同的样式表。

{% highlight html %}
<link rel="stylesheet" href="main.css" media="screen">
{% endhighlight %}

### 初始化媒体查询

媒体查询有两种不同的使用方法，一种是在已有的样式表文件中使用 @media 规则，另一种是使用 @import 规则导入一张新的样式表，或在 HTML 文档中链接到一个单独的样式表文件。通常来说，推荐使用的方法是在已有的样式表文件中使用 @media 规则，避免增加额外的 HTTP 请求。

{% highlight html %}
<!-- Separate CSS File -->
<link href="main.css" rel="stylesheet" media="screen and (min-width: 480px)">
{% endhighlight %}

{% highlight css %}
/* @media Rule */
@media screen and (min-width: 480px) {...}

/* @import Rule */
@import url(main.css) screen and (min-width: 480px) {...}
{% endhighlight %}

每一个媒体查询可能会包含一个媒体类型，紧接着是一个或多个表达式。常见的媒体类型包括 all、screen、print、tv 和 braille。HTML5 规范包含了新的媒体类型，甚至包括三维眼镜。若媒体查询中没有指定媒体类型，则默认为 screen。

媒体查询表达式可能包括不同的媒体特性与值，表达式计算结果是 true 或 false。若结果为 true 的话，就会应用其包裹的样式。若结果为 false，则忽略其包裹的样式。

### 媒体查询操作符

媒体查询中的逻辑操作符可以构建强大的表达式。共有三个逻辑操作符，分布是 and、not 和 only。

在媒体查询中使用 and 逻辑操作符可以添加新的表达式，并且浏览器或设备必须满足列出的所有条件，才能执行相关的 css 样式。多个媒体查询之间用逗号分隔开。举例说明，若选择宽度介于800像素到1024像素之间的所有媒体类型，该如何表示呢？

{% highlight css %}
@media all and (min-width: 800px) and (max-width: 1024px) {...}
{% endhighlight %}

not 逻辑操作符对后面的表达式取反操作。下面的示例，css 样式将应用于非彩色屏幕的设备

{% highlight css %}
@media not screen and (color) {...}
{% endhighlight %}

only 逻辑操作符是一个新出现的运算符，使用 HTML4 算法的浏览器并不支持它，这样一些较老的，不支持媒体查询的浏览器就不能使用给定的样式了。

{% highlight css %}
@media only screen and (color) {...}
{% endhighlight %}

当使用 not 和 only 逻辑操作符的时候，如果没有指明媒体类型，则默认值为 all。

另外媒体查询是大小写敏感的，若媒体查询语句中包含未知名媒体的媒体类型，则计算结果为 false。

### 媒体特征

虽然已经知道了媒体查询的语法，逻辑操作符的用途，再来学习一下，真正起作用的媒体特征（ media features ）。在媒体查询表达式中，媒体特征能够识别设备的属性。

高度 & 宽度媒体特征

最常见的一个媒体特征，就是用来确定一个设备或浏览器视窗（ viewport ）的高度和宽度。借助 height、width、device-height、device-width 媒体特征可以得到浏览器视窗（ viewport ）的高度和宽度。其中的每一个媒体特征都可以加上前缀 min 或 max 标识符，从而构建一个新特征，比如 min-width 或 max-device-width。

这个 height 和 width 特征来自于视窗渲染区域的高度和宽度，比方说浏览器窗口。另一面，device-height 和 device-width 特征是基于输出设备的高度和宽度，可能要比实际的渲染区域大一些。这些代表高度和宽度的媒体特征，其值既可以用相对单位表示，也可以用绝对单位表示。

### 参考资料

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>
