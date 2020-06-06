---
title: hexo 基本用法
date: 2015-01-19 00:34:14
---


Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)

### hexo+github搭建个人博客
主要步骤：
1.安装gitforWindows，官网下载，需要配置一下
2.安装nodejs，官网下载，一直下一步即可
3.安装hexo，npm一条命令就可以
4.hexo中有部分文件相当于源码性质，再github单独建立了一个仓库，这样即使电脑坏了，也可以重新复原博客


## 问题记录：
### 2020.05.31 cannot GET /20%/
这个问题是更新了hexo出现的，之前的旧版本配置文件中home: / || home是带空格的，新版本的hexo取消了空格。我最开始的hexo可能比较老，这次升级到了4.2.1就出现问题了。
把next主题配置文件中，||之前的空格全部去掉

### 2020.05.31  class="fa fa-angle-right" 
估计也是升级hexo导致的，找到hexo-theme-next的翻页组件，就是pagination.swig直接改成大于号和小于号
``` js
{% if page.prev or page.next %}
  <nav class="pagination">
    {{
      paginator({
        prev_text: '<i class="fa fa-angle-left"></i>',
        next_text: '<i class="fa fa-angle-right"></i>',
        mid_size: 1
      })
    }}
  </nav>
```
改成
``` js
{% if page.prev or page.next %}
  <nav class="pagination">
    {{
      paginator({
        prev_text: '<',
        next_text: '>',
        mid_size: 1
      })
    }}
  </nav>
{% endif %}
```
### 2020.05.31  代码格式符号是`不是单引号