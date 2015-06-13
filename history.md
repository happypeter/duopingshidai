---
layout: book
title: 八卦一下响应式
---

### 什么是响应式网页设计？

如果倒退五年，没有人能相信互联网会以今天这样爆炸式的速度发展，尤其是移动互联网的发展速度又远远超过了常规桌面网站，现在已经很难找到不拥有智能手机的朋友了，
很多人还拥有自己的 ipad，所以我们的生活正式进入了多屏时代，本书要讨论的响应式设计是一系列用于建造网站的技术，让网站能够适应多个屏幕尺寸。

![](images/history/multiple-screens.jpg)

内容用该像水一样，你把它放到茶壶里面，它就是个茶壶，放到茶杯里面它就应该是个茶杯，注意，这不是李小龙在聊功夫。

### ”相应式“这个词怎么来的？

2010年5月下旬，网页设计师 Ethan Marcotte，在 ALA 期刊上发布了一篇名为 [Responsive Web Design 的文章](http://alistapart.com/article/responsive-web-design/)。 从此响应式网页设计（RWD）的身影就出现在了公众面前。
文章提到，“相应式”这个词借用自建筑学领域，原本指的是建筑物本身会“相应”实际的使用情况，来自我调整。到 web 开发领域，“响应式“ 的意思就变成了，我们的页面会”相应“用户的设备尺寸。就像 Edthan 所说的。另外，Edthan 还专门写过一本书，就叫 [相应式设计](http://abookapart.com/products/responsive-web-design) ，是绝对值得一读的。

>This is our way forward. Rather than tailoring disconnected designs to each of an ever-increasing number of web devices, we can treat them as facets of the same experience.
>未来我们应该这样，随着网页访问设备的增加我们不会为每个设备单独设计，而是会只做一份设计，而把每个设备作为这个设计要照顾的一个方面。


换句话说，每个设备上都会去追求最佳的用户体验，设计会自动适应各个设备。在过去的时代，设计师精确的知道自己的媒介材质，比如一张 A4 纸张，一个名片，或者一张海报。但是在我们这个多屏时代，网页设计必须有这样的思维，我们要为”任意尺寸“而去设计。

![](images/history/responsive-term.png)

### 听起来复杂，实则不然

其实相应式，只是乍看起来很绕人，其实是有一些很简单的基本原则的。弹性布局，弹性媒体，和 Media-query 是做响应式设计的最重要的三个组件，后面我们都会结合实际代码来做详细介绍的。

弹性布局，弹性媒体的叫法来自 <http://learn.shayhowe.com/advanced-html-css/responsive-web-design/> 。
在[Ethan 的文章中](http://alistapart.com/article/responsive-web-design/)这“弹性布局”（ flexible layout ）没有提，而是被称为”流体网格“（ fliud grid ），不过意思是差不多的。


所谓的弹性媒体，其实主要就是针对图片而言，也包括视频。

### 参考链接

- <http://blog.teamtreehouse.com/modern-field-guide-responsive-web-design>
- <http://alistapart.com/article/responsive-web-design/>
- <http://blog.teamtreehouse.com/beginners-guide-to-responsive-web-design>
