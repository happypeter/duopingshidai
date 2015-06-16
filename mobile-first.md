---
layout: book
title: 移动优先
---

前面咱们已经介绍了响应式设计的概念，但是其实响应式设计是可以有两条道路可以走的，一条是“移动优先的响应式设计”（ Mobile First RWD ），一种是通常的响应式设计。像 Bootstrap 这样的前端 CSS 框架，就声称自己是 [Mobile First](http://getbootstrap.com/css/) 。 那什么是 “移动优先的响应式设计”？它的优势在哪里呢？

### 移动优先的响应式设计

[Luke Wroblewski](http://www.lukew.com/about/) 在2009年写得一篇名为 [Mobile First](http://www.lukew.com/ff/entry.asp?933) 的博客中首次提出了“移动优先”这个概念。 在这篇博客中，作者认为应该先设计移动端的网络应用或网站的用户体验，然后再考虑桌面版。

普通的响应式设计流程，引用作者的话解释如下：

>More often than not, the mobile experience for a Web application or site is designed and built after the PC version is complete.
>
>通常情况下，设计和建立一个网络应用或网站在移动端的用户体验，会等到其桌面版完成之后才进行。


那 “移动优先” 的响应式设计流程，就是这个样子的，如图所示：

![](images/mobile-first/mobile-first.png)

Luke 提出这个观点的时候，其实讨论了手机 APP 的各种优势，这个不是本书的关心内容，我们这里的“移动优先的响应式设计”只是针对网站设计而言的。指的是，先开发手机版网页，然后通过 media-query 等响应式技术，逐步添加功能进来，达成平板电脑和桌面端的网页。


简而言之，传统的响应式设计流程是，先桌面电脑，再平板，后手机。移动优先的响应式设计的流程正好相反，先手机，后平板，最后是桌面电脑。

### 为何要移动优先？



### “移动优先” 实例

<!-- http://book.haoduoshipin.com -->
<!-- /go-responsive/demo/mobile.html -->

<!-- http://bradfrost.com/demo/mobile-first/ -->

### 参考链接

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>

- <https://web3canvas.com/what-is-mobile-first-responsive-design/>

- <http://www.lukew.com/ff/entry.asp?933>
  - 手机屏幕要比普通桌面机屏幕小很多，那么这样，其实会促使你对一些不重要的功能选择放弃。
  - 想象一下，如果我们先设计桌面电脑的网页，那么肯定上面会放比较多的内容，这样，再来往小屏幕迁移的时候就会比较麻烦
  - 而反之，如果在手机上的版本先出来，然后逐步添加内容，就会比较容易。
