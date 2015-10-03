
# 写在多屏时代

> 世界上最远的距离是我在你身边，但是你却在玩手机！

移动互联网时代到来，有人喜，有人忧，我是极度乐观派。手机，平板，笔记本，iMac，让更多的屏幕进入生活吧。

### 什么是响应式网页设计？

如果倒退五年，没有人能相信互联网会以今天这样爆炸式的速度发展，尤其是移动互联网的发展速度又远远超过了常规桌面网站，现在已经很难找到不拥有智能手机的朋友了，
很多人还拥有自己的 ipad，所以我们的生活正式进入了多屏时代，响应式设计其实是很多技巧的集合，目的是让一个网站，一份代码，能够适应多个屏幕尺寸，而不是像以前那样专门给手机做一套移动版的代码。

![](images/forward/res.png)

内容应该像水一样，你把它放到茶壶里面，它就是个茶壶，放到茶杯里面它就应该是个茶杯。

### “响应式” 这个词怎么来的？

![](images/forward/responsive-term.png)

2010年5月下旬，设计师 Ethan Marcotte，在 ALA 期刊上发布了一篇名为 [Responsive Web Design 的文章](http://alistapart.com/article/responsive-web-design/)。 从此响应式网页设计（ RWD ）的身影就出现在了公众面前。
文章提到，“响应式” 这个词借用自建筑学领域，原本指的是建筑物本身会 “响应” 实际的使用情况，来自我调整。到 web 开发领域，“响应式” 的意思就变成了，我们的页面会 “响应” 用户的设备尺寸而自动调整布局。另外，Edthan 还专门写过一本书，就叫 [响应式设计](http://abookapart.com/products/responsive-web-design) 。

>This is our way forward. Rather than tailoring disconnected designs to each of an ever-increasing number of web devices, we can treat them as facets of the same experience.
>
>未来我们应该这样，随着网页访问设备的增加我们不会为每个设备单独设计，而是会只做一份设计，而把每个设备作为这个设计要照顾的一个方面。


换句话说，每个设备上都会去追求最佳的用户体验，设计会自动适应各个设备。在过去的时代，设计师精确的知道自己的媒介材质，比如一张 A4 纸张，一个名片，或者一张海报。但是在我们这个多屏时代，网页设计必须有这样的思维，我们要为“任意尺寸”而去设计。


### 听起来复杂，实则不然

响应式网站设计，只是乍看起来很绕人，其实是有一些很简单的基本原则的。弹性布局，弹性媒体，和 Media-query 是做响应式设计的三个组件，后面我们都会结合实际代码来做详细介绍的。

弹性布局，弹性媒体的叫法来自 <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/> 。
在[Ethan 的文章中](http://alistapart.com/article/responsive-web-design/) “弹性布局”（ flexible layout ）没有提，而是被称为 “流体网格”（ fliud grid ），不过意思是差不多的。所谓的弹性媒体，其实主要就是针对图片而言，也包括视频。

### 为什么写这本书？

是为了卖钱吗？ 不是，因为本书的网页版会免费开放在[这个链接]()。当然，每次 peter 和 billie 看到你在[这里]()购买了本书的 PDF 和 EPUB 版的时候，他们也会感到非常惊喜。所以请买书，拜托！！

但是，为什么会写这本书呢？ 这是由于最近我们的几个网站正在由原传统的单一桌面转为响应式，重构代码的过程也是一个愉悦的学习过程，但也发现有两个问题：

* 首先网上优秀的资料非常多，但却太零散，其实我们最需要的是这样一本书，先解释清基本原理，然后告诉我们第一、二、三步怎么做。

* 第二个问题是很多资料都是英文的，当我们想把一些东西分享给朋友的时候，有些朋友会有语言的障碍，所以我们写了这本书，希望能把全网搜集到的所有优秀资料系统整理做为一个精美的礼物送给我们身边每一位朋友。

![](images/forward/gift.jpg)

<!-- https://teamtreehouse.com/library/responsive-layouts/responsive-theory/what-is-responsive-web-design -->
<!-- 把上面视频中精彩的内容提炼出来，插入到本文 -->

### 参考链接

- <http://blog.teamtreehouse.com/modern-field-guide-responsive-web-design>
- <http://alistapart.com/article/responsive-web-design/>
- <http://blog.teamtreehouse.com/beginners-guide-to-responsive-web-design>
