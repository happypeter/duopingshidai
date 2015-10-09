# 移动优先


前面咱们已经介绍了响应式设计的概念，但是其实响应式设计是可以有两条道路可以走的，一条是“移动优先的响应式设计”（ Mobile First RWD ），一种是通常的响应式设计。像 Bootstrap 这样的前端 CSS 框架，就声称自己是 [Mobile First](http://getbootstrap.com/css/) 。 那什么是 “移动优先的响应式设计”？它的优势在哪里呢？

### 移动优先的响应式设计

[Luke Wroblewski](http://www.lukew.com/about/) 在2009年写得一篇名为 [Mobile First](http://www.lukew.com/ff/entry.asp?933) 的博客中首次提出了“移动优先”这个概念。 在这篇博客中，作者认为应该先设计移动端的网络应用或网站的用户体验，然后再考虑桌面版。

普通的响应式设计流程，引用作者的话解释如下：

>More often than not, the mobile experience for a Web application or site is designed and built after the PC version is complete.
>
>通常情况下，设计和建立一个网络应用或网站在移动端的用户体验，会等到其桌面版完成之后才进行。


那 “移动优先” 的响应式设计流程，就是这个样子的，如图所示：

![](images/mobile-first/mobile-first.png)

Luke 提出这个观点的时候，其实讨论了手机 APP 的各种优势，这个不是本书的关心内容，我们这里的“移动优先的响应式设计”只是针对网站设计而言的。指的是，先开发手机版网页，css 文件中的默认样式就是手机版页面的，然后通过 media-query，逐步添加样式进来，达成平板和桌面版网页。


简而言之，传统的响应式设计流程是，先桌面电脑，再平板，后手机。移动优先的响应式设计的流程正好相反，先手机，后平板，最后是桌面电脑。

### 为何要移动优先？
首先从市场份额角度来聊，随着移动互联网的爆发，如果还认为大家主要用桌面机访问网页，而只是“偶尔”使用手机来访问，手机端页面“可有可无”，那么这种观点肯定已经过时了。好，我承认现在手机端的很多流量是走 APP 的，但是不可否认移动端网页体验也变得越来越重要。

咱们都是开发者，所以现在来从技术实现的角度来聊。明显的一个事实，手机屏幕尺寸小，桌面电脑大。那么先设计手机页面意味着先设计一个简单版本的页面，然后随着平板版和桌面版的引入，页面会慢慢变得复杂起来，这是一个递增过程，是一个前期精力只放到最核心功能模块上的过程，不仅仅是思路上由简入繁，清爽怡人，同时当用手机打开网页的时候，默认打开的只是相对比较简单的手机版样式，而复杂一些的桌面版的相应样式都在 media-query 中包裹着，所以不会加载，那么这样页面访问速度是最佳的。 参考下面代码

```css
.content {
  /* 一些简单的样式，专门为手机而生 */
}

@media screen and (min-width: 400px)  {
  .content {
   /* 为大屏设备设计的比较复杂的样式 */
  }
}
```

同样，如果手机版页面是默认的，一些鼠标滑过效果，甚至是阴影，动画效果，图片等各种手机上用不到或者是不必要的内容也是可以用同样的上面的方法来避免在手机访问的时候加载的。例子如下

```css
.content {
   backgound: #bada55;
   /* 手机上也许现实一个简单的颜色就很好看了 */
}
@media screen and (min-width: 800px)  {
  .content {
     background-image: url("bg.png");
  }
  /* 电脑访问的时候再来加载大图，和鼠标滑过等效果 */

  .content:hover {
    ...
  }
}
```

具体的，可以查看这个例子：[button demo](demo/button/) 。（ 如果你正在用普通桌面电脑来打开这个 demo 那么可以把浏览器先拉窄，这样可以模仿出手机屏幕的效果，可以看到页面加载的按钮样式是非常简单的，下面来不断拉宽浏览器，到达一个临界点好，桌面版的按钮样式就会显示出来）。

但是反之，如果我们先有了一个桌面版的复杂网页，然后想要逐步做减法来最终达成手机版网页，那么这个过程就会很困难，容易造成重复设计劳动，如果处理不好，还可能导致臃肿的代码。

### “移动优先” 布局实例
在从页面大块布局角度来看看移动优先。手机屏幕比较窄，所以如果有两个大块，一般就可以上下排布，这样就是页面的一般流程。不需要设置 css 就可以达成。如下图：

![](images/mobile-first/phone-layout.png)

当到了大屏幕上面，可以再用 media-query 来引入 float 等 css 样式，达成左右排列的效果。

![](images/mobile-first/desktop-layout.png)


从这个例子，也一样可以看出，把手机版样式作为默认样式的好处。简化版代码如下

```css

.navbar {
  background-color: rgb(238, 110, 115);
}
.content {
  background-color: rgb(38, 166, 154);
}

@media all and (min-width: 420px) {
  .content {
    float: left;
    width: 65%;
  }
  .navbar {
    float: right;
    width: 30%;
  }
}
```


[实际代码在这里](demo/navbar/) 。 另外可以看看别人做的一个[功能更为丰富的一个例子](http://bradfrost.com/demo/mobile-first/) 。

### Peter 的结语

如果足够用心，其实不管道路是从大到小还是从小到大，最终达成的结果是应该是差不多的结果，那就是一个在手机端还是桌面端表现都非常好的网站。并且相信很多读者在看本书时，也跟我最初一样，是手头已经有了桌面版网页了，想要改为响应式，所以想要移动优先也不行了。但是，”移动优先“的策略的确越来越被大家接受为响应式设计的最佳实践了。

### 参考链接

- [google 和 udacity 的响应式课程的 mobile first 章节](https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/m-3473199720)
- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>
- [按钮样式来自 materializecss](http://materializecss.com/buttons.html)
- <https://web3canvas.com/what-is-mobile-first-responsive-design/>
- [Creating a Mobile-First Responsive Web Design](http://www.html5rocks.com/en/mobile/responsivedesign/)
