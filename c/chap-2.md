---
layout: course
title: 第二章：安装开发环境
---

## 第一节  jekyll&gulp 开发环境简介

展示整个环境的妙用。


![](images/chap2/overview.png)

Jekyll 的功能很多，但是我这里会用的就是它的文件拼接功能。因为开发的代码比较多，都写到一个页面上就很乱套，所以要分割为一个个的小片段，然后 Jekll 就可以帮助我们拼接成一个页面。
主要是展示整个环境，各个部分的功能，让大家感觉有意思，不用细说。

## 第二节 安装 gulp 和 sass

我用的是 aliyun 的服务器，但是域名要备案。所以可以选择国外服务器，或者本地搭建虚拟机。

### 安装 nodejs
我的 aliyun 服务器上面安装的是 ubuntu 14.04 的 Linux 系统，要安装 Gulp ，首先要安装 nodejs 和 npm ，参考 [digital Ocean 的文档](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server) ，可以通过添加 PPA 来安装新版本的 nodejs ：

{% highlight console %}
curl -sL https://deb.nodesource.com/setup | sudo bash -
sudo apt-get install nodejs
{% endhighlight %}

这样安装好 nodejs 之后，包管理工具 npm 也安装好了，但是有时候 npm 安装的包是需要编译的，所以还需要执行

{% highlight console %}
sudo apt-get install build-essential
{% endhighlight %}

这样 nodejs 安装就结束了。

### 安装 Gulp

需要先全局安装，以便有一个固定的安装位置好导出 PATH 。同时还要在项目内安装，因为 require 命令要求包必须是局部安装的。在[官方文档上](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md)也有相应说明。

首先来全局安装 Gulp ，根据[这里](https://docs.npmjs.com/getting-started/fixing-npm-permissions)的说明，为了避免使用 sudo ，可以按以下步骤操作

{% highlight console %}
mkdir ~/npm-global
npm config set prefix '~/npm-global'
{% endhighlight %}

然后把下面一行内容添加到 ~/.bashrc 文件中

{% highlight console %}
export PATH=~/npm-global/bin:$PATH
{% endhighlight %}

并运行 `source ~/.bashrc` 。现在再来执行

{% highlight console %}
npm install -g gulp
{% endhighlight %}

就可以功能把 gulp 安装到 ~/.npm-global 文件夹里了。

下面再到项目本地安装 Gulp 。

{% highlight console %}
mkdir project
npm init
npm install --save-dev gulp
{% endhighlight %}

这样不但能在项目内安装 gulp ，而且还可以包 gulp 以及相应版本写入到 package.json 文件中。以后部署这个项目的时候，就可以运行 `npm install` 来安装了。

### 使用 Gulp

使用 Gulp 参考了这个项目： <https://github.com/shakyShane/jekyll-gulp-sass-browser-sync>

安装 sass

{% highlight console %}
npm install --save-dev gulp-sass
{% endhighlight %}

<https://www.npmjs.com/package/gulp-sass> 上的 gulpfile 内容有问题，运行不了。下面是正确的 gulpfile.js 文件：

{% highlight js %}
var gulp = require('gulp');
var sass = require('gulp-sass');

gulp.task('sass', function () {
  return gulp.src('_scss/main.scss')
         .pipe(sass())
         .pipe(gulp.dest('./css'));
});

gulp.task('watch', function () {
  gulp.watch('_scss/*.scss', ['sass']);
});
{% endhighlight %}

gulp 的插件系统不是闹着玩？css minfiy ， image compression ... 各种强大功能都有。

顺便提一个常见问题：现象是这样。修改 _scss/*.scss 中的内容，gulp 终端的信息都是 `0 file changed`，到页面上看，任何修改都不生效，但是也不报错，基本上就是 sass 任务运行了，但是里面的语句没有执行成功。 可能造成这种现象的原因之一是，_scss/_layout.scss 我删除了，但是 main.scss 中忘了删相应的 `@import layout` 语句，也就是说 gulp-sass 当遇到某些错误的时候是不报错的。不报错就很难定位错误，用了我半小时的时间才解决。所以还是要在调代码的时候慢一点，多测试。

## 第三节 jekyll 和 browsersync

{% highlight console %}
gem install jekyll
{% endhighlight %}

这个需要装。

<!-- ### 文件组织

大的原则是：每一个文件内容都很少，打开一眼就能看清结构
- index.html 里面几乎全部是 `include hero.html `
- hero.html 还可以 `include hero_action_btn.html `
- 所有的 partial 包括 sub_partial 都放在 _inlcludes/ 顶级下，用文件名作 namespace
- 每个 partial 都有一个跟自己同名的 .scss
- main.scss 中同样只 import 第一级 partial 的 .scss 文件（ 其中 import sub_partial 的 .scss ），
 -->

<!--


### 搭建开发环境

### 3000 -> 80

像 jekyll 或者是 rails s 这些都是跑在 3000 端口的，放到服务器上默认是不能访问的，解决方法是设置 reverse proxry
ref: https://github.com/sharelatex/sharelatex/wiki/Nginx-as-a-Reverse-Proxy


/etc/nginx/site-enabled/site.conf

peter@aliyun:~/jekyll-gulp-sass-browser-sync$ cat /etc/nginx/sites-enabled/jekyll.conf
server {
    listen         80;
    server_name j.haoduoshipin.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header Host $http_x_forwarded_host;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_read_timeout 3m;
        proxy_send_timeout 3m;
    }
}


- jekyll build 耗时很长，大概5秒，其中有一半时间是在拷贝 node_modules 目录到 _site/ 蠢！

` .pipe(gulp.dest('css'));`  jekyll-gulp-sass-browser-sync 项目中的这一句是必要的，没有这一句，再 执行 ‘jekyll-rebuild' task 的时候，_site/* 会被删除。而源码目录中又没有 css/ 目录，所以是不能正确生成网站的。


  -->
