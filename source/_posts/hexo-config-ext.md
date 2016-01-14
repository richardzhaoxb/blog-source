---
title: Hexo 配置修改及安装扩展
date: 2016-01-13 23:47:02
categories: 博客
tags: [Hexo, NexT]
---

Hexo 其实整体来说还是能满足自己的需求的，简洁、大方、突出内容。但是还是有个别细节看上去不是很爽，比如说这个主题的文章字体太小又很粗，更何况每个人的审美又不同，架不住IT狗又是喜欢折腾的。此文特记录自己对 Hexo 和 NexT 主题做的配置修改、自定义样式、及扩展安装，以后 Hexo 或 NexT 升级后可以参考。

# 正文字体美化

参考了[NexT主题的作者和使用者在GitHub上的交流](https://github.com/iissnan/hexo-theme-next/issues/111) ，在博客的根目录下的 /source/css/_custom/custom.styl 文件中加入如下 css 代码：


``` css
body {
  font-family: "TIBch", "Classic Grotesque W01", "Helvetica Neue", Arial, "Hiragino Sans GB", "STHeiti", "WenQuanYi Micro Hei", SimSun;
  font-size: 16px;
  line-height: 1.7;
  color: #555;
  -webkit-font-smoothing: antialiased;
}
```

# 设置标题和副标题

修改博客根目录下的 _config.yml 文件中的 #site 节：

``` javascript
title: <博客标题>
subtitle: <博客副标题>
description: <博客简介>
author: <博客主的昵称>
```

# 设置显示语言

修改博客根目录下的 _config.yml 文件中的 language 属性：

``` javascript
language: zh-Hans
```

# 生成摘要

修改主题目录下的 _config.yml 文件中的 auto_excerpt 属性：

``` javascript
auto_excerpt:
  enable: true
  length: 150
```

# 代码高亮

修改主题目录下的 _config.yml 文件中的 highlight_theme 属性，我比较喜欢 night eighties 配色方案

``` javascript
highlight_theme: night eighties
```

这是现实效果：

``` javascript
function abc() {
    var x = 1;
    var b = 3;
    return math.abs(x);
}
```

# 添加 RSS 订阅

用到 [hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed) 插件，按照它的向导两步完成添加 RSS 订阅。 NexT 主题也很给力，它会自动在右侧边栏的**站点概览**中自动添加 RSS 按钮。

# 添加标签页和分类页面

参考 [NexT 主页的指南](http://theme-next.iissnan.com/theme-settings.html#标签云页面) 即可。 

另外在每篇文章的开头要加上标签和分类的属性才能被识别出来，例如：

``` javascript
---
title: Hexo 配置修改及安装扩展
tags: Hexo
category: blog
---
```

# 添加数学公式支持

编辑 主题配置文件，将 mathjax 设定为 true 即可，下面是一个数学公司的例子：

$$J\_\alpha(x)=\sum _{m=0}^\infty \frac{(-1)^ m}{m! \, \Gamma (m + \alpha + 1)}{\left({\frac{x}{2}}\right)}^{2 m + \alpha }$$

我只能默默的感叹，NexT 主题真强！

