> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.juanertu.com](https://blog.juanertu.com/archives/dde01238.html)

这篇文章最后更新于 365 天前，文章内容可能已经过时，请优先查看最新文章！

[](#前言： "前言：")前言：
-----------------

本篇设置基于 NEXT 主题 7.7.2 版本！！

NexT 主题自带的友链模块放在侧边栏下面，视觉上比较臃肿。所以我直接新建一个单独的友链界面出来。

基本原理：新建 md 页面，渲染出一个 html 页面，其中包含一个 class 是`.link-navigation` 的网页元素。同时加载 `links.js`，下载 json 文件，渲染到这个网页元素中。

### [](#新建-links-页面 "新建 links 页面")新建 links 页面

新建 links 页面，输入放置友链的 html 元素：

```
hexo new page links
```

这样会在 `/source/` 下创建 `links/index.md`。在文档的 `front matter` 添加 `type: links`，编辑好自己需要的友链页面内容，然后输入放置友链的 html 元素。示例：

```
---
title: 友情链接
type: links
---

<style>.links-content{margin-top:1rem}.link-navigation::after{content:" ";display:block;clear:both}.card{width:130px;font-size:1rem;padding:0;border-radius:4px;transition-duration:.15s;margin-bottom:1rem;display:block;float:left;box-shadow:0 2px 6px 0 rgba(0,0,0,.12);background:#f5f5f5}.card{margin-left:16px}@media(max-width:567px){.card{margin-left:16px;width:calc((100% - 16px)/2)}.card:nth-child(2n+1){margin-left:0}.card:not(:nth-child(2n+1)){margin-left:16px}}@media(min-width:567px){.card{margin-left:16px;width:calc((100% - 32px)/3)}.card:nth-child(3n+1){margin-left:0}.card:not(:nth-child(3n+1)){margin-left:16px}}@media(min-width:768px){.card{margin-left:16px;width:calc((100% - 48px)/4)}.card:nth-child(4n+1){margin-left:0}.card:not(:nth-child(4n+1)){margin-left:16px}}@media(min-width:1200px){.card{margin-left:16px;width:calc((100% - 64px)/5)}.card:nth-child(5n+1){margin-left:0}.card:not(:nth-child(5n+1)){margin-left:16px}}.card:hover{transform:scale(1.1);box-shadow:0 2px 6px 0 rgba(0,0,0,.12),0 0 6px 0 rgba(0,0,0,.04)}.card .thumb{width:100%;height:0;padding-bottom:100%;background-size:100% 100%!important}.posts-expand .post-body img{margin:0;padding:0;border:0}.card .card-header{display:block;text-align:center;padding:1rem .25rem;font-weight:500;color:#333;white-space:normal}.card .card-header a{font-style:normal;color:#5073b8;font-weight:700;text-decoration:none;border:0}.card .card-header a:hover{color:#5073b8;text-decoration:none;border:0}</style><div><div><div></div></div></div>

---

<div><span>
    <i></i>
  </span>留言添加友链<span>
    <i></i>
  </span></div>
  
------

{% note success %}

## 友链格式

- 网站名称：你真是美好的人类
- 网站地址：[https://blog.juanertu.com](https://blog.juanertu.com/)
- 网站描述：能与你一起成长，我荣幸之至
- 网站 Logo/头像：[https://blog.juanertu.com/images/avatar.png](https://blog.juanertu.com/images/avatar.png)

{% endnote %}
```

### [](#侧边栏添加友链页面链接 "侧边栏添加友链页面链接")侧边栏添加友链页面链接

主题配置文件`_config.yml` 中添加：

```
menu:
  home: / || home
  categories: /categories/ || th
  tags: /tags/ || tags
  archives: /archives/ || archive
+  links: /links || link
```

### [](#添加友链的-json-文件 "添加友链的 json 文件")添加友链的 json 文件

在页面目录 `/source/links/` 中添加 `linklist.json`，示例：

```
[
  {
    "nickname": "你真是个美好的人类",
    "avatar": "https://blog.juanertu.com/images/avatar.png",
    "site": "https://blog.juanertu.com"
  }
]
```

### [](#加载-link-js "加载 link.js")加载 link.js

在自定义文件 `body-end.swig` 中添加：

```
{# 友链设置 #}
{% if page.type === 'links' %}
  <script src="/js/link.js"></script>
{% else %}

{% endif %}
```

`link.js` 内容如下：

```
link = {
  init: function () {
    var that = this
    
    $.getJSON('/links/linklist.json', function (data) {
      that.render(data)
    })
  },
  render: function (data) {
    var html,
      nickname,
      avatar,
      site,
      li = ''
    for (var i = 0; i < data.length; i++) {
      nickname = data[i].nickname
      avatar = data[i].avatar
      site = data[i].site
      li +=
        '<div>' +
        '<a href="' +
        site +
        '" target="_blank">' +
        '<div style="background: url( ' +
        avatar +
        ');">' +
        '</div>' +
        '</a>' +
        '<div>' +
        '<div><a href="' +
        site +
        '" target="_blank">' +
        nickname +
        '</a></div>' +
        '</div>' +
        '</div>'
    }
    $('.link-navigation').append(li)
  },
}
link.init()
```

在 `hexo/source` 文件夹下新建一个 js 文件夹，放入即可。

### [](#问题排查 "问题排查")问题排查

1.  浏览器 F12 查看页面源码，是否有一个 class 是`.link-navigation` 的网页元素。
2.  查看 `link.js` 是否正常加载了，json 文件是否正常加载了。

如果加载 js 文件的 `/source/_data/body-end.swig` 不起作用，我们也可以把 `link.js` 内容放到 `/source/links/index.md` 中，效果是一样的。

[](#参考 "参考")参考
--------------

*   [新增友链](https://tding.top/archives/73ce4e7.html)