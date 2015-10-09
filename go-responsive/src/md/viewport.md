# viewport 视窗

<!-- 这个内容是动手制作 响应式 页面的第一步，是否应该放到比较靠前的章节呢？ -->

这节来聊 viewport （视窗）， viewport 就是浏览器可以用来显示页面内容的屏幕区域。会涉及到的重要概念是 dip （ device-independent pixel 设备无关像素 ）和 CSS pixel 之间的关系。

如果没有 viewport 的设置，也就是下面这一行：

```
 <meta name="viewport" content="width=device-width, initial-scale=1" />
```

那么当一个普通桌面版页面在手机上打开的时候，会发现页面各个元素都会变得很小。

![](images/viewport/iphone_no_viewport.jpg)

这是因为手机会自动对页面进行它自认为”最好“的缩放，从而尽量把整个页面能在手机这个小的多的屏幕上整个都装下。这个默认行为是我们在做响应式网页设计的时候不希望看到的，所以在一般的响应式页面中，第一步就是添加上面这一行，来禁用手机的这种默认缩放行为。但是究竟上面这些内容都是什么意思呢？不着急，下面慢慢来聊。

### 设备无关像素

英文叫 dip ，也有人翻译叫”逻辑像素“。简单来说，dip 是咱们在做设计的时候真正要关心的，而设备真正的硬件像素值一般是不需要关心的。先来了解一下下面三个概念：


- 硬件像素：显示器的物理像素，同样尺寸的屏幕，像素密度大的设备，硬件像素会更多。例如，iPhone 5所配屏幕的水平硬件像素为640。
- 设备无关像素(dip)：这个是跟设备的硬件像素密码无关的。一个 dip 在任意像素密度的设备屏幕上都占据相同的空间。例如：iPhone 5的设备无关像素宽度为320。
- CSS像素：用于页面布局的单位。样式的像素尺寸（例如 width: 100px）是以CSS像素为单位指定的。CSS像素与 dip 的比例即为网页的缩放级别，也就是网页在没有做缩放的时候，一个 css 像素就对应一个 dip 。


举个例子，比如我有一个笔记本，当我把浏览器调到800像素宽的时候，那么此时我的 viewport 就是800像素宽。但我把浏览器拉宽，viewport 也就不断变宽。但是不同的笔记本的像素密度其实是不一样的，比如我的笔记本的硬件像素是：2560x1700 。但是当我把浏览器拉成全屏的时候，viewport 的宽度值是 1280 。这里显然我的笔记本的设备像素比是2，1280 是 dip 值。

### 参数作用详解

使用元视口值width=device-width可指示网页与屏幕宽度（以设备无关像素为单位）进行匹配。这样，网页就可以重排内容以匹配不同的屏幕尺寸。

有些浏览器（包括iOS和Windows Phone）在旋转为横向模式时会保持网页宽度不变，并且会缩放（而非重排）网页以填充屏幕。添加属性initial-scale=1均可指示浏览器将CSS像素与设备无关像素的比例设为1:1（而不用考虑设备的屏幕方向），并且可让网页利用整个横向宽度。

上面内容摘自 [google developers](https://developers.google.com/speed/docs/insights/ConfigureViewport?hl=zh-cn) 。

可以设置 `user-scalable=no` 来禁用用户缩放功能，但是一般不建议这样做。

<!-- Take a look at the fourth answer. Without a viewport set, your content may be scaled by the browser.
https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/e-3566519000/m-3565149257

现在知道为啥要设置 viewport 了
 -->



<!-- https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/m-3495129024

DIP: device independent pixel -->

### 参考

- [google&udacity 课程的 viewport 章节](https://www.udacity.com/course/viewer#!/c-ud893/l-3494350031/m-3493209336)

- <http://getbootstrap.com/css/>
