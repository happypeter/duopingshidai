# 第二章：安装开发环境

整个环境参考了这个项目： <https://github.com/shakyShane/jekyll-gulp-sass-browser-sync> ，整个环境搭建起来，跟 [Google 的 Web Starter Kit](https://developers.google.com/web/tools/starter-kit/) 差不多了，它的最核心的功能咱们几乎都用上了：Gulp ，Sass ，BrowserSync ，Autoprefixer 。有一个它不用的咱们也用上了，就是 Jekyll 。


## 第一节  jekyll&gulp 开发环境简介

主要是展示整个环境，各个部分的功能，让大家感觉有意思，不细说。
Jekyll 的功能很多，但是我这里会用的就是它的文件拼接功能。因为开发的代码比较多，都写到一个页面上就很乱套，所以要分割为一个个的小片段，然后 Jekll 就可以帮助我们拼接成一个页面。




## 第二节 安装 gulp 和 sass

这一集主要任务是安装 gulp ，看看怎么在 gulp 框架下把 sass 用起来。

### 安装 nodejs

我用的是 aliyun 的服务器，但是域名要备案。所以可以选择国外服务器，或者本地搭建虚拟机。

我的 aliyun 服务器上面安装的是 ubuntu 14.04 的 Linux 系统，要安装 Gulp ，首先要安装 nodejs 和 npm ，参考 [digital Ocean 的文档](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server) ，可以通过添加 PPA 来安装新版本的 nodejs ：

```
curl -sL https://deb.nodesource.com/setup | sudo bash -
sudo apt-get install nodejs
```

这样安装好 nodejs 之后，包管理工具 npm 也安装好了，但是有时候 npm 安装的包是需要编译的，所以还需要执行

```
sudo apt-get install build-essential
```

这样 nodejs 安装就结束了。

### 安装 Gulp

需要先全局安装，以便有一个固定的安装位置好导出 PATH 。同时还要在项目内安装，因为 require 命令要求包必须是局部安装的。在[官方文档上](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md)也有相应说明。

首先来全局安装 Gulp ，根据[这里](https://docs.npmjs.com/getting-started/fixing-npm-permissions)的说明，为了避免使用 sudo ，可以按以下步骤操作

```
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
```

然后把下面一行内容添加到 ~/.bashrc 文件中

```
export PATH=~/.npm-global/bin:$PATH
```

并运行 `source ~/.bashrc` 。现在再来执行

```
npm install -g gulp
```

就可以功能把 gulp 安装到 ~/.npm-global 文件夹里了。

下面再到项目本地安装 gulp 。

```
mkdir project
npm init
npm install --save-dev gulp
```

这样不但能在项目内安装 gulp ，而且还可以包 gulp 以及相应版本写入到 package.json 文件中。以后部署这个项目的时候，就可以运行 `npm install` 来安装了。

### 使用 Gulp


安装 sass

```
npm install --save-dev gulp-sass
```

<https://www.npmjs.com/package/gulp-sass> 上的 gulpfile 内容有问题，运行不了。下面是正确的 gulpfile.js 文件：

```
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
```

gulp 的插件系统不是闹着玩？css minfiy ， image compression ... 各种强大功能都有。

顺便提一个常见问题：现象是这样。修改 _scss/*.scss 中的内容，gulp 终端的信息都是 `0 file changed`，到页面上看，任何修改都不生效，但是也不报错，基本上就是 sass 任务运行了，但是里面的语句没有执行成功。 可能造成这种现象的原因之一是，_scss/_layout.scss 我删除了，但是 main.scss 中忘了删相应的 `@import layout` 语句，也就是说 gulp-sass 当遇到某些错误的时候是不报错的。不报错就很难定位错误，用了我半小时的时间才解决。所以还是要在调代码的时候慢一点，多测试。


### tmux

tmux 使用可以参考 <http://haoduoshipin.com/v/41> 。

## 第三节 jekyll 加入游戏

看一下幻灯片，整个图景之上还有一个第二主角就是 Jekyll ，这一集来把 Jekyll 和 Autoprefixer 都添加上。

Jekyll 功能，我们会关心的，主要有两个，第一，可以把很多 html 片段文件拼接成一个文件，第二个，就是做 Sass 的预处理。那一个问题就来了，为什么我们不用 Jekyll 的 Sass 预处理功能呢？原因有两个：

- 第一，Jekyll Build 命令执行一次时间比较长，而我们希望每次修改完之后，页面能够实时刷新
- 第二，Jekyll 的 sass 功能不容易扩展，比如我想要添加 autoprefixer 功能，或者是 css 文件压缩功能，这样还是用 gulp 系统的插件来实现比较方便。


现在我们先把 autoprefixer 添加上。到项目文件夹内，

```
npm install --save-dev gulp-autoprefixer
```


然后到 gulpfile.js 中添加相应的代码就可以了。最终的 gulpfile.js 代码大家可以在项目代码中找到。

### 使用 jekyll

Jekyll 本身的使用方法可以参考 [好多视频网第113期](http://haoduoshipin.com/v/113) 。

虽然 Gulp 系统很容易通过添加插件来扩展功能，但是使用 Jekyll 提供的文件组织规范来把 html 的 layout 文件，和各个 partial 文件进行拼接还是很方便的。下面安装 jekyll ：

```
gem install jekyll
```

注意，jekyll 是一个 ruby gem ，所以先要安装 ruby 语言，参考 [ Rails 十日谈](http://www.imooc.com/learn/230) 。

来新建一个 task 专门运行 `jekyll build` 这个命令。这个需要用到 nodejs 开启子进程的功能，可以需要一点 Unix 系统的基础知识才能理解，我们作为前端开发者，暂时不用太关心，主要是这些代码：

```
var cp = require('child_process');
...
gulp.task('jekyll-build', function (done) {
  return cp.spawn('jekyll', ['build'], {stdio: 'inherit'})
            .on('close', done);
});
```


每次执行 `jekyll-build` 任务的时候，都会有一些我们不想要的文件夹被拷贝的 _site 文件夹里面，可以通过配置 _config.yml 文件来解决：

```
exclude: ['node_modules/', 'package.json', 'gulpfile.js']
```

好，这一节就到这里。


## 第四节 使用 Browsersync 实现页面自动刷新

过程参考 Browsersync 官网的这篇文档：<http://www.browsersync.io/docs/gulp/> 。

### 静态服务器

首先需要安装 browser-sync

```
npm install browser-sync gulp --save-dev
```

打开 gulpfile 文件，添加下面的内容

```
var browserSync = require('browser-sync').create();

// Static server
gulp.task('browser-sync', function() {
    browserSync.init({
        server: {
            baseDir: "./_site"
        }
    });
});
```

这样，运行 `gulp browser-sync` 就可以看到服务器跑在 3000 端口了。

### 设置反向代理

服务器上不能直接访问 3000 端口，不过可以通过设置反向代理来解决。

创建 `/etc/nginx/sites-enabled/gulp.conf` 文件，内容如下：

```
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
```


这样，运行

```
sudo service nginx reload
```

重新加载一下设置，就可以通过访问 http://j.haoduoshipin.com 看 `_site` 目录（ 也就是文件夹 ) 下的内容了。


### 实时加载 css

咱们的目的还是要看到 css 修改后，页面实时刷新。

所以，先打开 _site/index.html 把里面的内容改为：

```
<!DOCTYPE HTML>
<html>
<head>
  <meta charset='utf-8'>
  <title>Index</title>
  <link rel="stylesheet" href="css/main.css">
</head>
<body>
  <div class="peter">
    Peter
  </div>
</body>
</html>
```


这样，再来启动 gulp ，到浏览器中刷新看一下，会有 'connetcted to browsersycn' 的字样，并且在源码中可以看到一些自动添加进来的 js 代码。那你可能会奇怪，为啥刚才没有这些东西呢？就是因为现在页面中有了 `<body>` 标签了，而 browsersync 工作是要依赖于这个标签的，参考 <http://www.browsersync.io/docs/> 的说明。

需要在 gulpfile.js 中添加的代码如下

```

gulp.task('sass', function () {
...
-         .pipe(gulp.dest('./css'));
+         .pipe(gulp.dest('./_site/css'))
+         .pipe(browserSync.stream());
...
});
...
gulp.task('default', ['browser-sync', 'watch']);
```

重启 gulp ，这样每次我修改 _scss/main.scss 文件的时候，就可以看到页面效果实时刷新了，yeeeah!

## 第五节 大功告成

来把剩下的工作完成，包括修改 html 后运行 jekyll build ，以及用 Sublime 修改然后同步到服务器。


### 修改 html

好，这时候 sass 任务没问题了，也就是每次修改 _scss/main.scss 之后，页面是可以自动刷新了。下面来看当 html 文件修改了怎么办？

首先，到 _layouts/default.html 中，添加 html 的基本骨架

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>res</title>
  <link rel="stylesheet" href="css/main.css">
</head>
<body>
{% raw %}
{{ content }}
{% endraw %}
</body>
</html>
```

然后到 res-demo/index.html 中填入

```
<div class="peter">Peter</div>
```

这样，当运行 jekyll-bulid 任务的时候，上面两个文件就会合并导出到 _site/index.html 了。

下面来看 gulpfile.js 中的改动


```
gulp.task('jekyll-rebuild', ['jekyll-build'], function () {
    browserSync.reload();
});
...
         .pipe(gulp.dest('./css'));
...
    gulp.watch(['index.html', '_layouts/*.html', '_includes/*.html', 'images/*'], ['jekyll-rebuild']);
```

### 最终版本的 gulpfile.js

内容如下：

```
var gulp = require('gulp');
var sass = require('gulp-sass');
var prefix = require('gulp-autoprefixer');
var cp = require('child_process');
var browserSync = require('browser-sync').create();

var messages = {
    jekyllBuild: '<span style="color: grey">Running:</span> $ jekyll build'
};
gulp.task('browser-sync', function() {
    browserSync.init({
        server: {
            baseDir: "./_site"
        }
    });
});


gulp.task('jekyll-build', function (done) {
  browserSync.notify(messages.jekyllBuild);
  return cp.spawn('jekyll', ['build'], {stdio: 'inherit'})
            .on('close', done);
});

gulp.task('jekyll-rebuild', ['jekyll-build'], function(){
  browserSync.reload();
});

gulp.task('sass', function () {
  return gulp.src('_scss/main.scss')
         .pipe(sass())
         .pipe(prefix())
         .pipe(gulp.dest('./_site/css'))
         .pipe(browserSync.stream())
         .pipe(gulp.dest('./css'));
});

gulp.task('watch', function () {
  gulp.watch('_scss/*.scss', ['sass']);
  gulp.watch(['index.html', '_layouts/*.html'], ['jekyll-rebuild']);
});

gulp.task('default', ['browser-sync', 'watch']);
```

### rsync 同步

res_demo_rsync.sh 脚本内容如下

```
#!/usr/bin/env bash
sync_server()
{
    echo
    rsync -arv  --exclude "css" --exclude ".git" --exclude "node_modules" --exclude "_site"  --delete ~/Desktop/res-demo/ peter@haoduoshipin.com:~/res-demo/
    echo
}

sync_server
```

对应的 sublime build 脚本内容

```
{
  "cmd": "/Users/peter/bin/res_demo_rsync.sh"
}
```
