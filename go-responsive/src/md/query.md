# 媒体查询

响应式网站设计只有弹性布局这一个技巧是不够用的，媒体查询（ media queries ）也是响应式设计的核心技巧之一。媒体查询是可应用于 CSS 样式的简单过滤器。有了这些过滤器，我们可以根据设备呈现内容的特点轻松更改样式，包括显示屏类型、宽度、高度、方向甚至是分辨率。


![](images/query/css-media-queries.jpg)

在 CSS2.1 中定义了媒体类型，通过给 `<link>` 元素添加 media 属性，可以为不同的媒体类型加载不同的样式表。

```html
<link rel="stylesheet" href="main.css" media="screen">
```

媒体查询（ media queries ）是对媒体类型（ media types ）的一次扩展，通常媒体类型会出现在链接 css 样式文件的时候。媒体查询可以为单个浏览器和设备类型指定不同的样式，诸如视窗（ viewport ）宽度或者设备方向， 对设备的判断能力进一步加强了。这种给不同设备使用其专属样式的能力，为响应式网站设计开启了一片新的天地。

### 初始化媒体查询

媒体查询有两种不同的使用方法，一种是在已有的样式表文件中使用 @media 规则，另一种是使用 @import 规则导入一张新的样式表，或在 HTML 文档中链接到一个单独的样式表文件。通常来说，推荐使用的方法是在已有的样式表文件中使用 @media 规则，避免增加额外的 HTTP 请求。

```html
<!-- Separate CSS File -->
<link href="main.css" rel="stylesheet" media="screen and (min-width: 480px)">
```

```css
/* @media Rule */
@media screen and (min-width: 480px) {...}

/* @import Rule */
@import url(main.css) screen and (min-width: 480px) {...}
```

每一个媒体查询可能会包含一个媒体类型，紧接着是一个或多个表达式。常见的媒体类型包括 all、screen、print、tv 和 braille。HTML5 规范包含了新的媒体类型，甚至包括三维眼镜。若媒体查询中没有指定媒体类型，则默认为 screen。

媒体查询表达式可能包含不同的媒体特性与值，表达式计算结果是 true 或 false。若结果为 true 的话，就会应用其包裹的样式。若结果为 false，则忽略其包裹的样式。

### 媒体查询操作符

媒体查询中的逻辑操作符可以构建强大的表达式。共有三个逻辑操作符，分布是 and、not 和 only。

在媒体查询中使用 and 逻辑操作符可以添加新的表达式，并且浏览器或设备必须满足列出的所有条件，才能执行相关的 css 样式。多个媒体查询之间用逗号分隔开。举例说明，若选择宽度介于800像素到1024像素之间的所有媒体类型，该如何表示呢？

```css
@media all and (min-width: 800px) and (max-width: 1024px) {...}
```

not 逻辑操作符对后面的表达式取反操作。下面的示例，css 样式将应用于非彩色屏幕的设备

```css
@media not screen and (color) {...}
```

only 逻辑操作符是一个新出现的运算符，使用 HTML4 算法的浏览器并不支持它，这样一些较老的，不支持媒体查询的浏览器就不能使用它所给定的样式了。

```css
@media only screen and (color) {...}
```

当使用 not 和 only 逻辑操作符的时候，如果没有指明媒体类型，则默认值为 all。

另外媒体查询是大小写敏感的，若媒体查询语句中包含未命名的媒体类型，则计算结果为 false。

### 媒体特征

虽然已经知道了媒体查询的语法，逻辑操作符的用途，再来学习一下，真正起作用的媒体特征（ media features ）。在媒体查询表达式中，媒体特征能够识别设备的属性。下面我们就介绍最常见的一个媒体特征，

就是用来确定设备或浏览器视窗（ viewport ）的高度和宽度。借助 height、width、device-height、device-width 媒体特征可以得到浏览器视窗（ viewport ）和设备的高度和宽度。其中的每一个媒体特征都可以加上前缀 min 或 max 标识符，从而构建一个新特征，比如 min-width 或 max-device-width。

这个 height 和 width 特征来自于视窗渲染区域的高度和宽度，比方说浏览器窗口。另外两个，device-height 和 device-width 特征是基于输出设备的高度和宽度的，可能要比实际的渲染区域大一些。这些代表高度和宽度的媒体特征，其值既可以用相对单位表示，也可以用绝对单位表示。

```css
@media screen and (min-width: 320px) and (max-width: 780px) {...}
```

在响应式网站设计中，最常用的媒体特征包括 min-width 和 max-width。与设备特性区分开来，有助于在桌面或移动设备上建立风格一致的网站。

为什么使用 min 和 max 前缀？

min 和 max 前缀可以用于相当多的媒体特征。min 前缀的意思是 “大于或等于”，max 前缀的意思是 “小于或等于”。使用 min 和 max 前缀，就不必使用 < 和 > 符号了，从而避免与普通的 html 语法产生冲突。

另外还有长宽比，像素比，分辨率，以及一些其他的媒体特征可供查询。

### 浏览器对媒体查询的支持情况

不幸的是，IE 8 及其之前的浏览器，还有其它一些比较老的浏览器，都不支持媒体查询。然而，有两个不错的 javascript 库可以解决这个问题。

Respond.js 是一个轻量级库，它只查找 min/max-width 媒体特征，若网站中只使用了 min/max-width 媒体特征，那这个解决方案就是完美的。

CSS3-MediaQueries.js 是一个功能比较全，代码量比较大的 js 库，它能支持更多更复杂的媒体查询语句。另外，始终要记住，使用 js 库可能会带来性能问题，减缓网站加载速度，所以要评估一下，是否值得牺牲网站性能来使用额外的 js 库。

### 如何确定临界点（ Break Point ）

实用 media-query 最重要的是要确定“临界点”，也就是页面布局不得不做出改变的那个阈值。直观上我们可能会这么想，嗯，设备基本有三类，手机，平板和桌面电脑。那我可以按照这三类设备宽度来设置临界点（也有人翻译为断点）。但是实际上，对于此时此刻，这种想法其实是错误的。因为新的设备不断涌现，各种宽度都会有的。参考 [google 的设备宽度图表](https://www.google.com/design/tool/devices/)。

正确的方式是，应该按内容设置断点，而不是按设备宽度设置临界点，所以无需考虑成千上万的设备。具体的做法是，还是本着移动优先的思想，先考虑最小宽度的设备，例如 iphone5 ，来进行页面布局。好，这个基本设计稿定下来之后，就可以来把屏幕往宽处拽了（可以使用 Chrome 浏览器的，移动设备调试工具来辅助这一过程）

![](images/query/chrome_mobile.png)

直到我们看到，我们的内容看起来已经变得难看了，那么在这个位置，就要来设置一个临界点了。

引用 Responsive Design Workflow 作者 Stephe Hay 的话来说：

>Start with the small screen first, then expand until it looks like
shit. Time for a breakpoint!
>
>从你需要适配的最小屏幕宽度开始测试，慢慢地拉伸，当你发现页面像坨屎的时候，一个新的断点就确定了。

最好的方案是，先出手机版的页面，这样内容基本上都是单列布局的。接下来不断拉伸宽度，每当内容看上去很难看松散了，这时候就要确定新的断点，直到你所需要适配的最大屏幕宽度为止。最后，你会发现通过“按内容设置断点”所使用的断点数量远比“屏幕分辨率确定断点”要少。

![](images/query/break-point.jpg)

来举一个简单的例子，比如在小屏幕设备上，我们希望字体是 16px 大小，但是到了大屏设备上我们希望字体也大一些，变成 18px ，那么如果把临界点设置为 480px ，代码就应该写成这样：

```css
body {
  font-size: 16px; /* 移动优先，这个默认值是为移动设备而生 */
}

@media (min-width: 500px) {
  body {
    font-size: 18px; /* 大屏设备 */
  }
}
```

也有人提出了“主要临界点”和“次要临界点”的概念。例如我可以给我的页面设置3个“主要临界点”，每到一个，页面结构就会有“大”的调整，例如内容由一列变为两列。在两个临界点之间，有时候需要做一些小的页面调整，比如改变一下按钮大小，这样可以通过设置“次要临近点”来实现。

总之，并没有一套“最佳临近点”可以供每个网站都去使用，随着内容不同，每个网站开发者要自己去“找”适合自己的各个临近点。

### 参考资料

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>
- [知乎上讨论临界点的帖子](http://www.zhihu.com/question/28653799)
- [定义临界点](http://responsivedesign.is/strategy/page-layout/defining-breakpoints)
- [google&udacity 课程的“选择断点”章节](https://www.udacity.com/course/viewer#!/c-ud893/l-3533879576/m-3492369998)
- <http://bradfrost.com/blog/post/7-habits-of-highly-effective-media-queries/>
