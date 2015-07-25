- demo 用色
  - https://dribbble.com/shots/1790652-Google-Material-exploration?list=searches&tag=material_design&offset=2
  - content >> background-color: #93675C;
  - navbar >> background-color: #1EAAF1;

http://alistapart.com/article/responsive-web-design/

中的很多内容，我在 history.md 中用了，但是还是有很多其他内容都是非常精彩的，后面可以继续用。尤其是再讲 media-query 的时候。

- http://webdesign.tutsplus.com/categories/responsive-web-design?page=3
  - 还有很多好文章没看

<!-- 要设计一个网站，首先要有移动优先的基本思路，然后构建弹性布局，布局内插入弹性媒体，这样网站的基本结构建立起来之后，再结合常见设备选择合适的临界点，通过 media queries
技术，为不同尺寸的设备优化用户体验，这就是当代响应式网站设计的基本流程，同时也是本书的行文思路。 -->

整个网站采用 material design 风格，在 dribble 和 materialup 网站上也有很多 md 自己的响应式效果，可以选一些实用的做到这个 demo 中


http://c.haoduoshipin.com/guaishou/ 上面有几集内容

多版本图片技术，参考 https://designschool.canva.com/ 上的图片
svg 来取代 png 来解决清晰度问提
总之，就是多屏时代的网站，区别于传统时代的所有的技术点（每个配 demo ），设计思维（参考 alistapart 的文章），所有来源。



### EM 的妙用
我的思路是这样，大屏上面比如一个自然段的字体是 18px 那么手机上看这样页面的时候，因为离眼睛会近一些，所以字体可以变成 18x0.9，那么这时候如果 p 标签的 margin-bottom 是用像素设置的比如说 10px ，那么对于手机来说可能就不好看了，需要用 media-query 在设置一个小一点的值才好（ a list apart 就是这样）。但是如果 p 的 margin-bottom: 1em 那么这个就不用专门改了。

找个例子？

- ala 和 html5rocks 上面手机上都没有用 smaller 的 font-size 。
- https://laracasts.com/discuss/channels/general-discussion/default-appscss-node-modules-path-highlighted-in-error-in-phpstorm 是这个思路。


- http://simurai.com/blog/2014/05/04/cssconf/
  - 18: 41 em for padding rem for margin
  - img+code == cool: http://simurai.com/img/posts/cssconf-color2.gif

- http://webdesign.tutsplus.com/tutorials/quick-tip-try-combining-ems-and-rems--cms-23270

- em/rem 学习并不难？devtools 中查看 computed 一项就知道了

- <!-- http://webdesign.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972 -->

Important to Know:

It’s a somewhat widespread misconception that em units are relative to the font size of the parent element. In fact, as per the W3 spec, they are relative to the font size “of the element on which they are used”.
