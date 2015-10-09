# 响应模式

有意或者无意之间，我们的网页总会归于某种”响应模式“（ Responsive Patterns ），这里来介绍一下几种常见的模式，相信是非常有启发性的。

基本思路就是这样，在手机上，网站内容是单列布局的，到了桌面电脑上面就变成了多列结构。所谓”模式“，就是在临界点发生的时候，网站布局该做出怎样的变化。比较常见的模式有四种，当然有时候也可以在一个页面上混合两种模式来使用。

下面的主要内容和各个图片都来自[这篇文档](https://github.com/santhoshvai/Responsive-Web-Design-Fundamentals/wiki/4-Common-Responsive-patterns)

### Column Drop

![](images/pattern/column_drop.png)

Peter 这个翻译做“列下沉”。最窄的屏幕上，所有元素就垂直一个跟一个排成一列。 屏幕变宽时，到达第一个临界点后，第一个和第二个元素就变成左右两列排布了。后面屏幕继续变宽，第三课元素又”下沉“（反向的）到了这一行中。
这是最简单最常见的一种模式。


```
<div class="container">
  <div class="box dark_blue"></div>
  <div class="box light_blue"></div>
  <div class="box green"></div>
</div>
```

```
.container {
    display: flex;
    flex-wrap: wrap;
}
.box {
    width: 100%;
}
@media screen and (min-width: 450px) {
    .dark_blue {
        width: 25%;
    }
    .light_blue {
        width: 75%;
    }
}
@media screen and (min-width: 450px) {
    .dark_blue,
    .green {
        width: 25%;
    }
    .light_blue {
        width: 50%;
    }
}
```

实际中的一些网站：

- <http://modernizr.com/>
- <http://weenudge.com/>

### Mostly Fluid

<!-- 文字内容就参考 https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3484798853 -->
<!-- 给出一个实际中采用这种方案的例子 -->

![](images/pattern/mostly_fluid.png)

这种模式我翻译为“基本流体”，这种方式其实跟 Column Drop 差不多，只是稍微灵活了一点。跟前面的 Column Drop 一样，当屏幕最窄的时候，元素一个跟一个排成一列。当布局开始变宽，会出现网格模式，具体每一行上有几列内容就不一定了，根据我们自己页面的内容自由调整。宽到一定程度，主体内容的左右两侧就会出现 margin ，而不是让主体内容一直跟着 viewport 来变宽。

实现方式不唯一，下面的代码是用 flexbox 方式实现的，可供参考。首先 html 写成下面这样：
```
<div class="container">
  <div class="box dark_blue"></div>
  <div class="box light_blue"></div>
  <div class="box green"></div>
  <div class="box red"></div>
  <div class="box orange"></div>
</div>
```

对应的 CSS ：
```
.container {
    display: flex;
    flex-wrap: wrap;
}
.box {
    width: 100%;
}
@media screen and (min-width: 450px) {
    .light_blue,
    .green {
        width: 50%;
    }
}
@media screen and (min-width: 550px) {
    .dark_blue,
    .light_blue {
        width: 50%;
    }
    .green,
    .red,
    .orange {
        width: 33.33333%;
    }
}
@media screen and (min-width: 700px) {
    .container {
        width: 700px;
        margin-left: auto;
        margin-right: auto;
    }
}
```

实际例子：

- <http://www.html5rocks.com/en/>
- <http://mediaqueri.es/ala/>
- <http://mediaqueri.es/>


### Layout Shifter

![](images/pattern/layout_shifter.png)

这个我翻译为“变换式布局”。这种方式就比较灵活了，跟前面的两种方式一样的部分是：随着屏幕变宽，单列布局变多列。但是，
前面两种方式都是各个元素由原本的独占一行，变为依次变成多个元素共同占有一行。注意，没有哪个元素是跨越多行的，或者说就是同行上每个元素的高度是相同的。 而 Layout Shifter 这种方式的特点是各个元素的摆放位置不一定遵循原来的顺序，而可以根据需要任意调整，这就是所谓的“变换”（ shift ），也会出现上面图中所示的一个元素的跨多行的情况。

当然，这种布局如果使用 flexbox 的 `order` 来实现是非常方便的：

```
<div class="container">
  <div class="box dark_blue"></div>
  <div class="container" id="container2">
    <div class="box light_blue"></div>
    <div class="box green"></div>
  </div>
  <div class="box red"></div>
</div>
```

CSS 代码如下：

```
.container {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
}
.box {
    width: 100%;
}
@media screen and (min-width: 500px) {
    .dark_blue {
        width: 50%;
    }
    #container2 {
        width: 50%;
    }
}
@media screen and (min-width: 600px) {
    .dark_blue {
        width: 50%;
        order: 1; /* appear last, default value is 0*/
    }
    #container2 {
        width: 50%;
    }
    .red {
        width: 50%;
        order: -1; /* appear first, default value is 0*/
    }
}
```

达成这种模式也不一定非要用 flexbox，比如下面这些实际中的例子：

- <http://foodsense.is/>
- <http://www.anderssonwise.com/>
- <http://alistapart.com/d/responsive-web-design/ex/ex-site-FINAL.html>


### Off Canvas 抽屉式

![](images/pattern/off_canvas.png)

Peter 翻译为”抽屉式“。[Off Canvas](https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/m-3530719305) 模式的特点是当在手机上显示的时候，把一些不常用的页面元素隐藏起来，当然要有一个汉堡包按钮能很方便的让他们显示出来。而当屏幕空间足够的时候，直接显示前面被隐藏的内容，例如一个导航栏。

实现方式，html 代码如下：

```
<nav id="drawer" class="dark_blue">
</nav>
<main class="light_blue">
</main>
```

CSS 代码：

```
html,
body,
main {
    width: 100%;
    height: 100%;
}
nav {
    width: 300px;
    height: 100%;
    position: absolute;
    transform: translate(-300px, 0);
    transition: transform 0.3s ease;
}
nav.open {
    transform: translate(0, 0);
}
/* breakpoint that repositions everything back to its normal spot */
@media screen and (min-width: 600px) {
    nav {
        position: relative;
        transform: translate(0, 0);
    }
    body {
        display: flex;
        flex-flow: row nowrap;
    }
    main {
        width: auto;
        flex-grow: 1;/* Allows the element to grow and take up the full remaining width of the viewport*/
    }
}
```

还要配合一些 js 代码：

```
menu.addEventListener('click', function(e) {
    drawer.classList.toggle('open');
    e.stopPropagation();
})
```

实际例子：下图来自 <https://www.canva.com/> ：

![](images/pattern/hamburger.png)


### 参考

- [google&udactiy 课程](https://www.udacity.com/course/viewer#!/c-ud893/l-3561069759/e-3529819408/m-3571808936)
- [google developer 上跟上面课程对应的网页](https://developers.google.com/web/fundamentals/layouts/rwd-patterns/mostly-fluid?hl=en)

<!-- http://teamtreehouse.com/library/responsive-layouts
 -->
