---
layout: course
title: 第四章 最窄屏幕设计
---

前面介绍了“移动优先”的设计思路，那么动手的第一步，其实就是为最窄屏幕的设备，例如 iphone5 ，来做最初版本的网站了。其实就当前来说，这样也具有现实合理性，我们做好的页面很可能是通过微信或者微博，QQ，这样在手机上进行传播的，所以手机上直接打开观看的情况可能已经是主要情形了。

# 第一节 Chrome 移动调试工具

这一集里面，来一起认识一下 Chrome 移动调试工具。并了解一下 viewport 设置对于移动页面开发的作用。明确一下需求，并且把代码的骨架搭建起来。

- 简介一下 in-browser-design 的优势
- 明确一下需求
- 动手搭建页面排版骨架
- 给每个部分设置高度
- 用 chrome mobile dev tool 打开
- 设置 viewport


scss 代码分割成很多小文件，用 `import` 语句，导入到 main.scss 中，同理，html 代码也分割成很多小的局部文件，然后用 jekyll 的 `include` 导入到当前 html 文件中。文件小，不超过四五十行，这样一旦打开这个文件，那么结构是一目了然的，这个对于开发和排错其实都是蛮重要的。

为 iphone5 来涉及并不一定真的需要买一个 iphone5 啦。所以给大家推荐一位新朋友，Chrome 移动调试工具。

<!-- 下面的操作都要在 iphone5 状态下作，不然有些图片进来就不合适了 -->

viewport 那一句必须提到了，不然后面垂直排几个大块儿的时候，高度都没办法设置了。


### 第二节 定制色盘

### 明确需求

Peter 是 In-Browser-Design 的信徒，反对先 photoshop/sketch 然后再 css 的传统设计流程。所以明确需求阶段，最多也就是用铅笔在纸上勾勒一下客户要的效果，然后快速就进浏览器了。这里我们就来重新设计一下慕课网的课程展示页面，例如
<http://www.imooc.com/view/390> 。所以内容比较明确了，现在直接上手写 html/css 了。


先来划定好大块，根据 imooc 的页面需求
{% highlight html %}
<header></header>
<section class="course-intro"></section>
<section class="action"></section>
<section class="stat"></section>
<section class="toc"></section>
<section class="author"></section>
<section class="warning"></section>
<footer></footer>
{% endhighlight %}

然后来定制色盘。

http://www.materialpalette.com/brown/deep-orange

来定制 common.scss 文件。

{% highlight scss %}
$primary-color-dark:   #5D4037;
$primary-color:        #795548;
$primary-color-light:  #D7CCC8;
$primary-color-text:   #FFFFFF;
$accent-color:         #FF5722;
$primary-text-color:   #212121;
$secondary-text-color: #727272;
$divider-color:        #B6B6B6;
{% endhighlight %}

用色盘色来填充大块。

第一块，用课程 poster 来填充。
   - 这个还是用 primary color 暂时弄上吧，一个任意背景色的大图，放到页面上，很难不对整个的页面色调造成影响，挑战主色的地位。
   - 不行在小屏上，就把他弄成圆形的，用主色当他的背景？。。。下一集再说了。


第二块，课程介绍

正好可以使用 primary-text-color 和 secondary-text-color

第三块，action

正好可以用来使用 accent-color

第四块 toc 留白就行，未来使用 google 的小圆图标背景的样式。
https://design.google.com/resources/#material-design-guidelines

或者这里也有很多小圆圈：http://webdesign.tutsplus.com/tutorials/web-design-for-kids-color--cms-24378

第五块，stat

用来使用 primary-color 和 primary-color-text 。用上 svg 图标。

第六块，author

用来使用 primary-color 作为大背景，以及  primary-color-text 和 primary-color-secondary-text
用 primary-color-dark 来做 github/dribble 等标签的字体色，表示强调

- warning： 用一下 primary-color-light/dark ? 真的不知道怎么用？
  - 老师告诉你能学到什么，用 light ，表示没有 warning 的部分重要
    - warning 用 primary-color-dark 或者 primary-color .
  - 深浅搭配其实能出很多美妙效果的
    - 例如这里的进度条 https://dribbble.com/shots/1422850-Team-Messages
    - 这里的 follow 按钮：https://dribbble.com/shots/1546643-Twitter-Profile
    - 甚至是这里的，深色托主色，主色内嵌入浅色：https://dribbble.com/shots/2066081-Elephone-Landing-Page-V2/attachments/370465

  - https://design.google.com/videos/palette-perfect/
    - 视频中给的建议：
      - 500 作为页面主色
      - dark：700 作为状态栏
      - light: 300 作为次要信息栏
      - 的确如果这三种上面用了相同透明度的白色字体，那么显眼程度是很不一样的。

footer 就用黑色


google 的官网上有关于色盘使用的详细介绍：https://www.google.com/design/spec/style/color.html#
视频：https://design.google.com/videos/palette-perfect/


### 第三节 色盘上各个辅助色用法


字体设置

{% highlight css %}
font-family: "Helvetica Neue", "Segoe UI", Helvetica, Arial, "Hiragino Sans GB", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
{% endhighlight %}
