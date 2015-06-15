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
<link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
{% endhighlight %}

{% highlight css %}
/* @media Rule */
@media all and (max-width: 1024px) {...}

/* @import Rule */
@import url(styles.css) all and (max-width: 1024px) {...}
{% endhighlight %}

每一个媒体查询可能都会包含一个媒体类型，紧接着是一个或多个表达式。常见的媒体类型包括 all、screen、print、tv 和 braille。HTML5 规范包含了新的媒体类型，甚至包括 3D 眼镜。若媒体查询中没有指定媒体类型，则默认为 screen。

媒体查询表达式可能包括不同的媒体特性和数值，然后计算结果是 true 或 false。当一个媒体特性和数值的结果是 true 的话，就会应用其包裹的样式。如果媒体特性和数值结果是 false，则忽略其包裹的样式。

### 媒体查询运算符

<!-- https://teamtreehouse.com/library/responsive-layouts/media-queries/media-query-review -->

### 参考资料

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>
