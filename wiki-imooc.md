---
title: 课程大纲
---

### 第一章 举杯多屏时代

为啥当代 web 开发者必须要会响应式布局，响应式布局的历史渊源，所涉及到的主要技术，实例展示。本套课程的讲解思路，以及适合观众。

- 第一节 是时候学习响应式了
- 第二节 旅途介绍

<!-- 相应式三大技术一定要提一下
理论知识课程里面一定从略，指向我的书，在我的书里面要详细讲

鼓吹一下：咱们课程中用到的 gulp 这套系统，其实也是 google 全力推动的，见  web starter kit
同样的思路也会在 http://yeoman.io/ 中被看到，所以这套课程也可以为学习 yeoman 打下基础。
 -->

<!--  就是重新设计  http://www.imooc.com/view/333  -->

### 第二章 开发环境准备

使用 jekyll 这个简单的框架来辅助开发。因为代码量比较大，直接都写在一个文件中维护起来就很头疼，jekyll 带有布局文件和代码片段导入的各种小功能，可以让代码结构清晰。另外会配合 Gulp 来运行一些自动化任务，比如 sass 编辑，添加 vendor 前缀，以及用 browersync 来调试页面。

- 第一节 jekyll&gulp 开发环境简介
- 第二节 安装 gulp 和 sass
- 第三节 jekyll 加入游戏
- 第四节 使用 Browsersync 实现页面自动刷新
- 第五节 大功告成


### 第三章 移动优先

如果您认为一个网站应该先设计桌面版然后在去为小屏设备去调整，对不起，您错了！“移动优先”恰好是一套相反的思路。

- 第一节 由简入繁易，由繁如简难
- 第二节 四种响应模式


### 第四章 最窄屏幕设计

根据移动优先的思路，开始为所有设备中最小宽度的屏幕来制作页面。这时布局一般是很简单的，单列布局。采用 Google Material Design 风格来制作页面。会涉及色盘定制和 SVG 图标制作。


- 第一节 Chrome 移动调试工具
- 第二节 定制色盘
- 第三节 使用色盘上的颜色
- 第四节 使用 SVG 来制作图标


### 第五章 寻找临界点

最窄的设计出来了，下一步就是不断拉伸浏览器视窗宽度，当页面看起来已经不好看了，那么这时就有必要设置一个临界点了。代码层面我们要用 Media Query 来给宽度大于临界点的屏幕做出样式调整。

- 第一节 寻找临界点（ Break Point ）
- 第二节 绝对变相对


<!-- FIXME:

https://teamtreehouse.com/library/responsive-layouts/media-queries/creating-breakpoints

弹性布局绝对是应该放在，media-query 之前讲清楚的
图片要用 Max-width 了
section 用 50% 了。

第二节：绝对变相对。可以单独作为一章

- 我的页面上多处用到了网格，目前的实现方案还是比较土。应该参照 http://getbootstrap.com/2.3.2/scaffolding.html#gridSystem 的方式，先制作出类似的网格系统，然后往里面填入内容。
  - 调页面的过程应该是这样，先把具体每一网格中的 html 内容都注释掉，然后等流体网格调试出来之后，再插入具体内容。

自己拿不准的问题，一律参考：http://yeoman.io/

http://mediaqueri.es/
### break point

 - Peter 自己的观点是，不要设置全局的三个临界点，每个部分（ 也就是每个 css 中）自己顾自己就可以了。
   - web component 是趋势，所以还是“模块化”思想，每个元器件负责自己，只有当 have to 的时候再用清晰的接口跟其他模块沟通。设计上也应该是这样。
 -->


### 第五章 弹性媒体

大屏设备，视网膜屏，智能手表这些设备的出现，给图片和视频的使用带来了新的挑战，技术上又哪些要注意的点，本章来揭晓。

- 第一节 响应式环境下的图片

<!-- http://www.botaiusti.com/ hero 大图绝对值得一讲 -->
- 第二节 弹性视频播放器

<!--
https://css-tricks.com/video-screencasts/141-getting-the-images-and-numbers-for-responsive-images/

http://webdesign.tutsplus.com/tutorials/quick-tip-how-to-use-html5-picture-for-responsive-images--cms-21015

https://developers.google.com/web/fundamentals/media/images/?hl=en

- http://webdesign.tutsplus.com/tutorials/simplify-your-media-queries-with-sass-breakpoint--cms-22706
 - 14:00 有图片的讲解，包含了 retina 设备

 http://webdesign.tutsplus.com/articles/how-to-create-responsive-images-using-the-picture-element--cms-24003


当屏幕变大之后，用 background-image 加载一个比较大的图片。
图片的使用注意事项绝对值得讲一节 -->


### 第六章 响应式活在生态系统里

这不是一个重造轮子的时代。web 开发生态系统几乎已经全面倒向响应式，各个框架都声称自己“移动优先”，这个如何理解？随着多屏时代到来，火起来的技术，工具和第三方库都有哪些，为什么？

- 第一节 web 元器件与响应式
- 第二节 前端框架中的响应式启示
- 第三节 响应式优化过的第三方库

<!--
webstarter kit
h5bt
http://yeoman.io/
pure/foundation/bs
ploymer
 -->

### 第七章 Goodbye

录制这门课程，我自己认为是把网上所有最优秀的学习资源都看了，但是有哪些值得推荐呢？只是其中的一小部分。
<!--
http://webdesign.tutsplus.com/categories/responsive-web-design?page=4

觉对值得推荐的资源
 -->

<!-- peter,相关的参考资料等，从这门课一开始，做个统计，可以添加到本网站的wiki中，如参考资料链接、补充资料、相关教学资料等。
 -->

<!-- 做成一个 webapp 挺有意思https://developers.google.com/web/fundamentals/device-access/?hl=en -->

### 大纲重叠

happypeter  15:24:07
cool
知音  15:25:09
是讲CSS3 Media Queries 实现响应式设计这个内容吗？
happypeter  15:25:20
是的
知音  15:27:14
可以详细的讲解下，其实有些老师在讲解案例的时候也用到和讲到css3 响应布局。一般是1-2节。
happypeter  15:28:07
对，我这门是专门讲响应式的，所以内容会比较深入的
知音  15:29:47
嗯。
happypeter  10:26:26
早上好美女，大纲出来了：http://book.haoduoshipin.com/go-responsive/imooc
happypeter  10:26:33
多提宝贵意见啊
知音  10:39:01
好的。会尽量反馈意见。
happypeter  10:40:05
另外，这个大纲会头我录课程的时候可能会有小幅度的调整，不会给你那边带来不便吧？
知音  10:48:32
[文件: 教学大纲-进入移动web世界.xlsx]
知音  10:49:46
peter, 你看看这个大纲，有部分有重叠，看看是否重。
happypeter  10:54:01
确实有重叠的部分。你的意思是要我根据他的大纲去调整吗？那为什么不是他按照我的大纲去调整？
知音  10:55:35
把侧重点调整下。
知音  11:02:51
分析下：
 你们重复的内容都要会让老师看，想下调方案。
因为细节不做大纲可能也看不出来。

1. 那位老师一开始定位是移动web。
2. 你这个定位响应式，之前问了下是否讲Media Query，以为以他为主。

现在大纲都出来了，有重叠的内容。

解决方案：

1：先看看重叠的是否很多，如多，调整下侧重点。
2. 如不多，每个老师讲课之前避免不了重复 ，那就中用调整了。
happypeter  11:06:22
好，我这边调整一下。美女你们那边给我一些比较直接的调整意见。总之就是避免我录完的视频被枪毙掉就行了。
happypeter  11:07:33
另外，我自己的感觉是大家的讲解思路不同，即使是同一个知识点，有可能讲的内容也是非常不一样的。所以为了保证各自课程的完整性，应该允许少量重复的存在，你觉得呢?
知音  11:09:15
因为正好都发给我大纲，从大纲我上来看，有重合的知识内，但因为只是大纲，所以不好确定具体内容，所以让你们都看看重合的部分，是否相同。然后在出解决方案。
happypeter  11:11:25
是这样啊
知音  11:12:06
“所以为了保证各自课程的完整性，应该允许少量重复的存在，你觉得呢?”这个我认同，所以让你看看，重合不多可以不调整，如多，做下侧重点调整。
happypeter  11:12:52
“响应式布局不在课程内容，但是其重要性还是需要申述，分析其优缺点。” 这是那位老师大纲中的内容。
happypeter  11:13:28
的确”移动 web" 和 ”响应式 web"的确是两个东西。
知音  11:13:44
也在和那位老师讨论中，不想老师们的辛苦讲解白付出。
happypeter  11:14:52
谢谢！我觉得还是比较好调整的，大家多沟通一下就行了。
知音  11:15:56
那个老师说的重复的部分。
happypeter  11:19:43
的确是这样。
happypeter  11:23:10
那我的《第三章弹性布局》部分，viewport 和 rem 部分我这里删掉。正好我这里侧重的也是实例开发，理论方面我给出参考文档就好了。
知音  11:24:55
那两部分你在讲解时大概多长时间。
happypeter  11:26:07
大概半个小时多一点吧。
happypeter  11:26:39
第五章我也可以融入到其他章节中，不细讲理论了。
知音  11:27:06
根据你对那位老师的大纲情况来，重复度有多少。
happypeter  11:28:06
就这这两章而言，理论部分的重合应该是 90% 的。
知音  11:28:38

happypeter  11:28:51
但是我这边确实是以动手内容为主的。
知音  11:31:11
peter，你这边以实践为主，
那位老师以整体移动web知识为主，同时个老师以小案例来说明问题。
happypeter  11:33:08
对。我的思路就是：我的这两章我都删掉，动手部分都融入到其他章节。后面我录的时候参照他的大纲绕开他要讲的内容就好了。
