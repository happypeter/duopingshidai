# 第四章 最窄屏幕设计

前面介绍了“移动优先”的设计思路，那么动手的第一步，其实就是为最窄屏幕的设备，例如 iphone5 ，来做最初版本的网站了。其实就当前来说，这样也具有现实合理性，我们做好的页面很可能是通过微信或者微博，QQ，这样在手机上进行传播的，所以手机上直接打开观看的情况可能已经是主要情形了。

### 第一节 Chrome 移动调试工具

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

Peter 是 In-Browser-Design 的信徒，反对先 photoshop/sketch 然后再 css 的传统设计流程。所以明确需求阶段，最多也就是用铅笔在纸上勾勒一下客户要的效果，然后快速就进浏览器了。这里我们就来重新设计一下慕课网的课程展示页面，例如 <http://www.imooc.com/view/390> 。所以内容比较明确了，现在直接上手写 html/css 了。


先来划定好大块，根据 imooc 的页面需求

```
<header></header>
<section class="course-intro"></section>
<section class="action"></section>
<section class="stat"></section>
<section class="toc"></section>
<section class="author"></section>
<section class="warning"></section>
<footer></footer>
```

然后来[定制色盘](http://www.materialpalette.com/brown/deep-orange
)。


来定制 common.scss 文件。

```
$primary-color-dark:   #5D4037;
$primary-color:        #795548;
$primary-color-light:  #D7CCC8;
$primary-color-text:   #FFFFFF;
$accent-color:         #FF5722;
$primary-text-color:   #212121;
$secondary-text-color: #727272;
$divider-color:        #B6B6B6;
```

用色盘色来填充大块。

google 的官网上有关于色盘使用的[详细介绍](https://www.google.com/design/spec/style/color.html)，还有一个[精彩视频](https://design.google.com/videos/palette-perfect/) 。

### 第三节 色盘上各个辅助色用法

字体设置

```
font-family: "Helvetica Neue", "Segoe UI", Helvetica, Arial, "Hiragino Sans GB", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
```


深浅背景色搭配是可以出很漂亮的效果的。例如[这里的进度条](https://dribbble.com/shots/1422850-Team-Messages) 以及 [这里的 follow 按钮](https://dribbble.com/shots/1546643-Twitter-Profile)
