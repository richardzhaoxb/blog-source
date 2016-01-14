---
title: Hexo + GitHub Pages 搭建免费的静态博客
date: 2016-01-11 00:31:46
categories: 博客
tags: [Hexo, NexT]
---

终于把博客搭好了。在这里把整个过程的大致步骤记录下来，供以后改造升级时参考。

# 选型

从开始决定要重新开始写博客时，就一直在考虑用什么来写博客。作为新时期有理想有节操的IT狗，肯定是要自己动手搭建才能体现出不同的逼格。另外一个要考虑的就是节约点成本。那第一个知道的就是 WordPress，是在比较传统的 LAMP 技术上搭建的，功能很丰富，有很多成熟漂亮的主题可以直接用。但是对于我来说，WP 太庞大，太过臃肿。另外一个目前比较流行的是用 Jekyll 在 GitHub 上写 Markdown 然后生成静态页面，还有它的表哥 Octopress，号称是想黑客一样写博客。其实是不错的选择，毕竟把静态页面放在 GitHub 上既稳定又不用花钱。不过由于 Jekyll 是基于 Ruby 技术栈的，我对 Ruby 不熟悉又暂时不打算学习 Ruby（听说性能有问题），所以迟迟没有动手去弄。前几天看到一个新的博客平台Ghost，它是基于 Node.js 基础上搭建的，听说是要成为 WP 的继任者，所以就下下来试了一下，确实是比较简单，很快就安装好了，和 Jekyll 一样，Ghost 也是用 Markdown 来写作的，而且 Ghost 还支持一边用 Markdown 写作，一边就可以看到生成文章的效果。但是有两点最后导致我暂时放弃了 Ghost，(1)就是 Ghost 刚出来，版本很不稳定，而且在社区中还没有太多的插件和主题供选择；(2)就是它需要我们自己部署到一个外网的服务器上才能访问。 后来我就在想有没有结合了 Jekyll 和 Ghost 的优势，即用 Node.js 技术做 Markdown 的生成静态页面部署到 GitHub 上去呢？到网上一找，最后找到了 Hexo。有种相见恨晚的感觉。Hexo 是由台湾的 [tommy351](https://github.com/hexojs/hexo) 开发的一款基于Node.js的静态博客框架。它支持用 支持GitHub Flavored Markdown 写作，因为基于 Node.js 运行，生成静态网页数据的速度极快，而且配合 Node.js 的生态，开发网页模板、定制主题、及开发插件都很方便。

# 环境准备

在安装使用 Hexo 之前，需要先安装一下软件：
* Node.js
* Git

安装的方式网上都有，这里就不赘述了。

# 建立自己的 GitHub 静态站

GitHub 真是一个好东西，不但为开源世界提供了优质的资源，还给我们这种屌丝提供了免费的、稳定的静态站点服务。

登录 GitHub，创建一个新的仓库，仓库的名字必须为你的 GitHub 的账户名开头，加上 github.io 为后缀，我的静态站仓库就是：richardzhaoxb.github.io

# 安装

如果前面 Node.js 和 Git 都安装好了，安装 Hexo 就是超级简单，比 Jekyll 的简单多了。执行下面的命令：

``` bash
npm install -g hexo
```

# 初始化

初始化就是生成一个 blog 的实例，还是很简单，执行下面的命名，指定要生成的目录：

``` bash
hexo init <folder>
```

你可以在自己的机器上生成多个不同的实例，用于开发插件、测试主题、或者只为备份，随你。只要每次别进错目录就好。

# 写文章

还是很简单，一个命令，指定要生成的文章的名字：

``` bash
hexo new <post-name>
```

这个命令其实是在博客的根目录的 **/source/_posts/** 子目录下，生成了 post-name.md 的文件。如果知道了这一点，其实也可以复制**_posts**目录下的其他md文件来创建新文章。

接下来，就可以用 Markdown 在新生成的文件中写博客了。我用的是 Sublime Text，还装了一个叫做 MarkdownEditing 的插件，写起来很爽。

# 本地预览

执行以下命令，就可以启动 Node.js 本地服务，进行文章的预览调试。

``` bash
hexo server
```

默认的调试地址是：http://localhost:4000，也可以用 -p 的命令参数指定端口号。

# 生成静态页面

如果本地调试好了，准备发布到 GitHub 上去，就必须先生成静态页面。在博客的根目录下，执行如下命令：

``` bash
hexo generate
```

# 发布到 GitHub

先到站点配置文件中，修改git库信息

``` ruby
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:richardzhaoxb/richardzhaoxb.github.io.git
```

然后安装 Hexo 在 git 上部署的插件：

``` bash
npm install hexo-deployer-git --save 
```

最后就可以执行命令发布了：

``` bash
hexo deploy
```

Hexo 还支持发布到不同的 静态 Pages 平台：Heroku、Rsync、OpenShift， 做法和上面类似，在不同的地方修改参数即可，具体参考[官网的说明](https://hexo.io/docs/deployment.html) 。

# 主题

在 Hexo 官网上的主题推荐中，看中了 NeXT 主题。这个 Theme 简洁，突出内容，而且 NeXT 主题还有一个专门的 [主页](http://theme-next.iissnan.com/) 来介绍具体的使用。按照上面的一步一步做即可。感谢 [iissnan](https://github.com/iissnan/hexo-theme-next) 提供这么优秀的主题。
