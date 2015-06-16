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

高度 & 宽度

最常见的一个媒体特征，就是用来确定一个设备或浏览器视窗（ viewport ）的高度和宽度。借助 height、width、device-height、device-width 媒体特征可以得到浏览器视窗（ viewport ）的高度和宽度。其中的每一个媒体特征都可以加上前缀 min 或 max 标识符，从而构建一个新特征，比如 min-width 或 max-device-width。

这个 height 和 width 特征来自于视窗渲染区域的高度和宽度，比方说浏览器窗口。另一面，device-height 和 device-width 特征是基于输出设备的高度和宽度，可能要比实际的渲染区域大一些。这些代表高度和宽度的媒体特征，其值既可以用相对单位表示，也可以用绝对单位表示。

{% highlight css %}
@media screen and (min-width: 320px) and (max-width: 780px) {...}
{% endhighlight %}

在响应式设计中，最常用的媒体特征包括 min-width 和 max-width。与设备特性区分开来，有助于在桌面或移动设备上建立同样的响应式网站。

为什么使用 min 和 max 前缀？

min 和 max 前缀可以用于相当多的媒体特征。min 前缀的意思是 “大于或等于”，max 前缀的意思是 “小于或等于”。使用 min 和 max 前缀，就不必使用 < 和 > 符号了，从而避免与普通的 html 语法产生冲突。

### 方向

这个 orientation 媒体特征决定一个浏览器窗口是 landscape（横向）还是 portrait（纵向）。当浏览器窗口的宽度大于高度的时候，就会触发 landscape 模式，反之，则触发 portrait 模式。这个媒体特性主要在移动设备上发挥作用。

{% highlight css %}
@media all and (orientation: landscape) {...}
{% endhighlight %}

### 长宽比

aspect-ratio 是指浏览器窗口的长宽比，device-aspect-ratio 是指输出设备的长宽比。min 和 max 前缀可以用于这两个长宽比特征。 长宽比的计算公式：

{% highlight html %}
宽度值 / 高度值
{% endhighlight %}

公式中的宽度和高度单位是像素，且都为整数。

### 像素比

除了长宽比媒体特征之外，还有一个 pixel-ratio 特征，那另一个与之相对应的特征就是 device-pixel-ratio，同样这两个特征也可以添加 mix 和 max 前缀。具体地说，像素比特征能够识别高清晰度设备，包括视网膜显示器。看一个例子：

{% highlight css %}
@media only screen and (-webkit-min-device-pixel-ratio: 1.3), only screen and (min-device-pixel-ratio: 1.3) {...}
{% endhighlight %}

### 分辨率

这个 resolution 媒体特征指定输出设备的分辨率，即像素密度，也称为每英寸点数或 DPI。它也支持 min 和 max 前缀。另外，它的数值单位可以是每英寸点数（ 1.3dppx ），每厘米点数（ 118dpcm ），或是基于分辨率值的其它长度单位。

{% highlight html %}
@media print and (min-resolution: 300dpi) {...}
{% endhighlight %}

### 其它媒体特征

除了以上介绍的媒体特征之外，还有一些特征，这里稍微提一下，确定可用的输出颜色的 color、color-index 和 monochrome 特征，确定位图设备的 grid 特征，确定电视扫描方式的 scan 特征。这些特征都不经常使用，若用到的话，请查阅相关文档。

### 浏览器对媒体查询的支持情况

不幸的是，IE 8 及其以下，还有其它一些比较老的浏览器，都不支持媒体查询。然而，有两个不错的 javascript 库可以解决这个问题。

Respond.js 是一个轻量级库，它只查找 min/max-width 媒体特征，若网站中只使用了 min/max-width 媒体特征，那这个解决方案就是完美的。

CSS3-MediaQueries.js 是一个功能比较全，代码量比较大的 js 库，它支持更多更复杂的媒体查询语句。另外，始终要记住，使用 js 库可能会带来性能问题，减缓网站加载速度，所以要确定值得牺牲网站性能来使用额外的 js 库。

### 媒体查询 demo

通过使用媒体查询，我们将重写之前创建的弹性布局 demo。当前面临的一个问题是，视窗宽度很小的时候，右边的 menu 区块会变得太小，导致不能有效的显示内容。这时就可以添加一个媒体查询，对于宽度小于 420 像素的视窗，我们可以改变布局，清除浮动，改变 content 和 menu 区块的宽度。

### 确认断点

你的直觉可能是要围绕常见的由不同设备分辨率决定的视窗尺寸来编写媒体查询断点，诸如 320px、 480px、 768px、 1024px、 1224px等等。这是一个糟糕的想法。

当构建一个响应式网站的时候，应该适应一组不同的视窗尺寸，而不是考虑设备。只有当网站布局打乱，看起来奇怪，或者用户体验受到了阻碍的时候，才应该引入一个断点。

此外，每时每刻都会有新的设备和新的分辨率发布出来。试图追赶上这些改变是一个永无止境的过程。

### 参考资料

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>
