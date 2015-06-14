---
layout: book
title: 移动优先
---

要设计一个网站，首先要有移动优先的基本思路，然后构建弹性布局，布局内插入弹性媒体，这样网站的基本结构建立起来之后，再结合常见设备选择合适的临界点，通过 media queries
技术，为不同尺寸的设备优化用户体验，这就是当代响应式网站设计的基本流程，同时也是本书的行文思路。

现在我们再引入一个概念，叫做 “移动优先的响应式网站设计”，不难看出它就是给 “响应式网站设计” 术语前面加上了一个修饰词 “移动优先”，
把整个词拆开理解，对我们是有帮助的。因为在本章之前，我们已经知道了什么是响应式网站设计，接下来只要知道什么是 “移动优先”，就能明白整个概念。

### “移动优先” 这个词是怎么来的?

“移动优先”，是 [Luke Wroblewski](http://www.lukew.com/about/) 在2009年写得一篇名为 [Mobile First](http://www.lukew.com/ff/entry.asp?933) 的博客中首次提出了这个概念。
在这篇博客中，作者认为应该先设计移动端的网络应用或网站的用户体验，然后再考虑桌面版，代替传统的设计流程。

传统的设计流程，引用作者的话解释如下：

>More often than not, the mobile experience for a Web application or site is designed and built after the PC version is complete.
>
>通常情况下，设计和建立一个网络应用或网站在移动端的用户体验，会等到其桌面版完成之后才进行。

那 “移动优先” 设计流程，就是这个样子的，如图所示：

![](images/mobile-first/mobile-first.png)

简而言之，响应式网站设计和移动优先的响应式网站设计是有差异的，前者先设计网站内容在大屏幕设备上面的布局样式，然后通过 media queries
来调整网站布局以适应不同的屏幕尺寸，让网站内容也能在小屏幕设备上面显示出来，搭建移动网站；而后者与前者正好相反，按照从小屏到大屏的顺序进行设计。

### 为什么要 “移动优先”？

对于这个问题，Luke Wroblewski 给出我们三点原因：

1. 移动设备爆炸式增长

2. 强迫开发人员把精力聚焦到应用的核心功能之上

3. 拓展你的能力

以上三点，笔者认为第一个是最最重要的原因。移动设备，尤其是智能手机的普遍使用，把人们变成了 “低头族”，改变了人们的日常生活、工作和思维方式。

![](images/mobile-first/mobile-children.jpg)

这种大家有目共睹的巨大变革，给人们带来了新的机遇，也迫使企业和公司改变了他们的工作策略，默认对手机用户提供友好的服务体验，而且不遗余力的培养用户在手机上面的操作习惯。

就拿最近两天刚发生的一件事为例，一个名为 [TNW](http://thenextweb.com/) 的网站上有一篇[文章](http://thenextweb.com/opinion/2015/06/12/the-new-york-times-wisely-blocks-staff-from-viewing-its-desktop-homepage/)爆料说，灰色女士（纽约时报的戏称）正成为一个时髦的现代女性，她喜欢4.7英寸视网膜屏幕胜过她的28英寸桌面显示器。
事情起因是这样的，纽约时报因其用户流量一半以上都来自移动设备，于是决定，阻止员工查看其桌面主页，而员工只能借助智能手机或平板电脑来访问其官方网站。真是一个明智的决策！

### “移动优先” 实例




### 参考链接

- <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/>

- <http://designshack.net/articles/css/mobilefirst/>

- <https://web3canvas.com/what-is-mobile-first-responsive-design/>

- <http://www.lukew.com/ff/entry.asp?933>
