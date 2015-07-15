---
title: 响应式模式
---

有意或者无意之间，我们的网页总会归于某种”响应式模式“（ Responsive Patterns ），这里来介绍一下几种常见的模式，相信是非常有启发性的。

非常常见的一种情况是，在手机上，网站内容是单列布局的，到了桌面电脑上面就变成了多列结构。所谓”模式“，要解决的重要问题，就是在临界点发生的时候，网站布局改做出怎样的变化。

常见的模式有四种，并且有时候也可以在一个页面上混合两种模式来使用。

### Mostly Fluid

<!-- 文字内容就参考 https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3484798853 -->
<!-- 给出一个实际中采用这种方案的例子 -->
<http://www.html5rocks.com/en/> 就是属于这种情况的一个例子。

### Column Drop



### 其他

还有一种模式叫 [layout shifter](https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3484798853) 。另一种叫 [Off Canvas](https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3530719305)，就是当在手机上显示的时候，把一些不常用的页面元素隐藏起来，当然要有一个汉堡包按钮能很方便的让他们显示出来。而当屏幕空间足够的时候，直接显示前面被隐藏的内容，例如一个导航栏。

下图来自 <https://www.canva.com/> ：

![](images/pattern/hamburger.png)

http://teamtreehouse.com/library/responsive-layouts


https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3518589214

column drop 这些名词很重要

mostly fluid 策略是我自己最长用到的：https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/e-3529819408/m-3571808936
