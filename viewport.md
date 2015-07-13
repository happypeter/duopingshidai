---
layout: book
title: viewport 视窗
---

这节来聊 viewport 。涉及到的重要概念是 dip （ device-independent pixel 设备无关像素 ）和 CSS pixel 之间的关系。

如果没有 viewport 的设置，也就是下面这一行：

{% highlight html %}
 <meta name="viewport" content="width=device-width, initial-scale=1" />
{% endhighlight %}

那么当一个普通桌面版页面在手机上打开的时候，会发现页面各个元素都会变得很小。

![](images/viewport/iphone_no_viewport.jpg)

这是因为手机会自动对页面进行它自认为”最好“的缩放，从而尽量把整个页面能在手机这个小的多的屏幕上整个都装下。这个默认行为是我们在做响应式网页设计的时候不需要的，所以在一般的响应式页面中，第一步就是添加上面这一行，来禁用手机的这种默认缩放行为。但是究竟上面这些内容都是什么意思呢？不着急，下面慢慢来聊。

### 设备无关像素

英文叫 dip ，也有人翻译叫”逻辑像素“。简单来说，dip 是咱们在做设计的时候真正要关心的，而设备真正的物理像素值一般是不需要关心的。为啥？


- 硬件像素：显示器的物理像素。例如，iPhone 5所配屏幕的水平硬件像素为640。
- 设备无关像素(dip)：在正常视距下，符合统一参考像素的设备像素比例，此像素在所有设备上大小几乎相同。iPhone 5的设备无关像素宽度为320。
- CSS像素：用于页面布局的单位，由视口控制。样式的像素尺寸（例如width: 100px）是以CSS像素为单位指定的。CSS像素与设备无关像素的比例即为网页的比例系数或缩放级别。

上面内容摘自 [google developers](https://developers.google.com/speed/docs/insights/ConfigureViewport?hl=zh-cn) 。
<!-- Take a look at the fourth answer. Without a viewport set, your content may be scaled by the browser.
https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/e-3566519000/m-3565149257

现在知道为啥要设置 viewport 了
 -->



<!-- https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/m-3495129024

DIP: device independent pixel -->

<!-- 关于 <meta name="viewport" content="width=device-width, initial-scale=1"> 这一行怎么写，还是 bootstrap 上最权威一些，见 <http://getbootstrap.com/css/> 。
要不要禁用用户缩放功能呢？见 http://www.html5rocks.com/en/mobile/responsivedesign/
It's important to note that we're not disabling the user's ability to zoom the page (which you could do by adding user-scalable=no to the content attribute), even though we're optimizing the content for small screens. It's recommended to keep user zooming enabled to keep things as accessible as possible. However, there are use cases to disable user-zooming, such as if you're including fixed positioned elements.

http://learn.shayhowe.com/advanced-html-css/responsive-web-design/
  - viewport 的知识很重要 -->



### 参考

- [google&udacity 课程的 viewport 章节](https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/m-3493209336)
