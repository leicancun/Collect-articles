\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.maplesugar.top\](https://blog.maplesugar.top/hexo/next-theme-custom-friendlinks-page/#7-友链插件)

Next 主题自定义友链页面
==============

发表于 2019-08-06 分类于 [hexo](/categories/hexo/) Disqus：[0 Comments](/hexo/next-theme-custom-friendlinks-page/#comments "disqus") Hashover：[4 条评论](https://blog.maplesugar.top/hexo/next-theme-custom-friendlinks-page/#hashover "hashover") 本文字数： 9.4k

Hexo 官网：[https://hexo.io/plugins](https://hexo.io/plugins) 搜索 `friends`  
Hexo 插件：[https://github.com/maplesugarr/hexo-tag-friends](https://github.com/maplesugarr/hexo-tag-friends)  
其他博客借鉴：[https://github.com/maplesugarr/hexo-theme-next-friends-page](https://github.com/maplesugarr/hexo-theme-next-friends-page)

Next 主题自带的友链，需要在主题配置文件\_config.yml 中添加，渲染到侧边栏下面，视觉上比较臃肿。一个做法是自定义一个 swig 文件，用来渲染主题配置文件\_config.yml 中添加的友链，博文 [Hexo 修改友链样式](https://www.sanshuifeibing.com/posts/16e3649f.html) 中有写。另一个做法就是模仿博文 [Hexo NexT 博客增加瀑布流相册页面](https://blog.dlzhang.com/posts/31/) **自定义一个 js 文件，下载相应的 json 文件，渲染到页面。**第一种做法需要硬修改 next 主题，第二种不需要，下面根据第二种思路为 Next 主题添加友链页面。

*   [友链样式 1](#link-style-tab-1)
*   [友链样式 2](#link-style-tab-2)
*   [友链样式 3](#link-style-tab-3)
*   [友链样式 4](#link-style-tab-4)

上面是四个样式，**下面以第二种样式为例**，其他类似，相关文件在文末 GitHub 链接。

### [](#1-说明 "1. 说明")1\. 说明[](#1-说明)

next 升级后，两个重要改变。

**插件**：next 主题配置文件\_config.yml 中提供的插件选项对应的插件，不在默认在 next 目录中了。需要手动克隆到 next\\source\\lib 文件夹中，或者在主题配置文件\_config.yml 中添加相应的 vendors。

/themes/next/\_config.yml

```
vendors:
  jquery: //cdn.jsdelivr.net/npm/jquery@3/dist/jquery.min.js
  fontawesome: //cdn.jsdelivr.net/npm/font-awesome@4/css/font-awesome.min.css
  fancybox: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.js
  fancybox\_css: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.css
```

**配置文件**：第一种方式：原来的配置分散在站点根目录下 \_config.yml 和主题的 \_config.yml 中，现在都可以写在站点根目录下 \_config.yml 。

需要添加 theme\_config

/\_config.yml

```
theme\_config:
  主题的 \_config.yml的配置
```

第二种方式：把主题配置文件放在站点目录下的 source/\_data/next.yml 中

下面的操作，由于每个人的使用方式不一样，自己对应修改相应的文件就行了。

### [](#2-新建links页面，输入放置友链的html元素 "2. 新建links页面，输入放置友链的html元素")2\. 新建 links 页面，输入放置友链的 html 元素[](#2-新建links页面，输入放置友链的html元素)

`hexo new page links`

这样会在 /source/ 下创建 links/index.md。在文档的 front matter 添加 **type: links**，编辑好自己需要的友链页面内容，然后输入放置友链的 html 元素。示例：

/source/links/index.md

```
\---
title: 友链
type: links
---

{% note success %}

下面是本站的友链，随机排序。

{% endnote %}

<style>.links-container{margin:0 auto;text-align:center;width:100%;}.links-container::after{content:" ";display:block;clear:both}.link-item{display:block;float:left;width:130px;height:auto;margin-bottom:16px;border-radius:4px;box-shadow:2px 2px 6px 0 rgba(0,0,0,.12);background:#f5f5f5;text-decoration:none;transition:box-shadow .5s ease;}.link-item{margin-left:16px}.link-cover-container{width:100%;padding:0;border-top-left-radius:4px;border-top-right-radius:4px;position:relative;overflow:hidden}.link-cover{width:100%;height:auto;padding-bottom:100%;background-size:100% 100%!important;background-position:50% 50%;background-size:cover;transition:transform .5s ease,filter .5s ease}.link-item:hover{box-shadow:4px 4px 6px 0 rgba(0,0,0,.3)}.link-info{padding-bottom:0}.link-nickname p{margin:0;padding:10px 5px;font-style:normal;color:#2bbc8a;font-weight:700;font-size:16px;line-height:16px;overflow:hidden;white-space:nowrap;text-overflow:ellipsis}.link-item:hover .link-nickname p{color:#d480aa}.link-intro{position:absolute;top:0;bottom:0;left:0;right:0;margin:0;display:flex;justify-content:center;align-items:center;background-color:rgba(0,0,0,0);transition:background-color .5s ease}.link-intro p{margin:0;padding:20px 16px;font-size:16px;line-height:16px;overflow:hidden;word-break:break-all;opacity:0;color:#eee;transform:translateY(20px);-webkit-transform:translateY(20px);transition:opacity .5s ease,transform .5s ease}.link-item:hover .link-intro{background-color:rgba(0,0,0,.5)}.link-item:hover .link-intro p{transform:translateY(0px);-webkit-transform:translateY(0px);opacity:1}.link-item:hover .link-cover{-webkit-transform:scale(1.05);-moz-transform:scale(1.05);transform:scale(1.05);-webkit-filter:blur(4px);-moz-filter:blur(4px);filter:blur(4px)}@media(max-width:567px){.link-item{margin-left:16px;width:calc((100% - 16px) / 2)}.link-item:nth-child(2n+1){margin-left:0}.link-item:not(:nth-child(2n+1)){margin-left:16px}}@media(min-width:567px){.link-item{margin-left:16px;width:calc((100% - 32px) / 3)}.link-item:nth-child(3n+1){margin-left:0}.link-item:not(:nth-child(3n+1)){margin-left:16px}}@media(min-width:768px){.link-item{margin-left:16px;width:calc((100% - 48px) / 4)}.link-item:nth-child(4n+1){margin-left:0}.link-item:not(:nth-child(4n+1)){margin-left:16px}}@media(min-width:1200px){.link-item{margin-left:16px;width:calc((100% - 64px) / 5)}.link-item:nth-child(5n+1){margin-left:0}.link-item:not(:nth-child(5n+1)){margin-left:16px}.link-intro p{padding:16px 12px;font-size:12px;line-height:12px}}</style>
<div></div>

------

<div><span>
    <i></i>
  </span>留言添加友链<span>
    <i></i>
  </span></div>

------

{% note success %}

\*\*友链格式：\*\*

- 网站名称：枫糖
- 网站地址：https://blog.maplesugar.top
- 网站描述：From rookie to master
- 网站Logo/头像：https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.svg

{% endnote %}
```

### [](#3-侧边栏添加友链页面链接 "3. 侧边栏添加友链页面链接")3\. 侧边栏添加友链页面链接[](#3-侧边栏添加友链页面链接)

主题配置文件\_config.yml 中添加

/themes/next/\_config.yml

```
menu:
  home: / || home
  categories: /categories/ || th
  tags: /tags/ || tags  
  archives: /archives/ || archive
  photos: /photos || camera-retro
  links: /links || link
```

在语言文件中添加相关翻译

/themes/next/languages/zh-CN.yml

```
menu:
  home: 首页
  archives: 归档
  categories: 分类
  tags: 标签
  about: 关于
  search: 搜索
  schedule: 日程表
  sitemap: 站点地图
  commonweal: 公益 404
  photos: 相册
  links: 友链
  guestbook: 留言
```

### [](#4-添加友链的json文件 "4. 添加友链的json文件")4\. 添加友链的 json 文件[](#4-添加友链的json文件)

在页面目录 /source/links/ 中添加 linklist.json，示例：

/source/links/linklist.json

```
\[
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖枫糖枫糖枫糖枫糖枫糖枫糖枫糖枫糖枫糖枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。枫儿爱吃糖：From rookie to master。枫儿爱吃糖：From rookie to master。枫儿爱吃糖：From rookie to master。枫儿爱吃糖：From rookie to master。枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	},
	{
		"nickname": "枫糖",
		"avatar": "https://cdn.jsdelivr.net/gh/maplesugarr/blog-assets@master/imgs/maple-leaf-avatar.jpg",
		"site": "https://blog.maplesugar.top",
		"intro": "枫儿爱吃糖：From rookie to master。"
	}
\]
```

### [](#5-加载links-js "5. 加载links.js")5\. 加载 links.js[](#5-加载links-js)

主题配置文件\_config.yml 中添加

/themes/next/\_config.yml

```
custom\_file\_path:
  #添加在bodyEnd中的原因是保证links.js用到的其他js库加载完成了
  bodyEnd: source/\_data/body-end.swig
```

修改 source/\_data/body-end.swig

/source/\_data/body-end.swig

```
{% if page.type ==='links' %}
    <script src="/js/link.js"></script>
{% endif %}
```

links.js 内容

/source/js/links.js

```
var link ={
    init: function () {
        var that = this;
        //这里设置的是刚才生成的 json 文件路径
        $.getJSON("/about/links/linklist.json", function (data) {
            that.render(data);
        });
    },
    shuffle: function shuffle(arr){
        for(var i = 0, len = arr.length; i < len;i ++){
            var a = parseInt(Math.random()\*len);
            var temp = arr\[a\];
            arr\[a\] = arr\[i\];
            arr\[i\] = temp;
        }
        return arr;
    },
    render: function (data) {
        data = this.shuffle(data);
        var linkitem, nickname, avatar, site, intro, html = "";
        for (var i = 0; i < data.length; i++) {
            nickname = data\[i\].nickname;
            avatar = data\[i\].avatar;
            site = data\[i\].site;
            intro = data\[i\].intro;
            linkitem = '<a href="' + site + '" target="\_blank">' +
                            '<div>' +
                                '<div></div>' +
                                '<div><p>' + intro + '</p></div>' +
                            '</div>' +
                            '<div>' + 
                                '<div><p>' + nickname + '</p></div>' +
                            '</div>' +
                       '</a>';
           
            html += linkitem;
        };
        $("#links").empty();
        $("#links").append(html);
    }
};

link.init();
```

### [](#6-其他样式的友链 "6. 其他样式的友链")6\. 其他样式的友链[](#6-其他样式的友链)

看到很多小伙伴使用我的友链，有的加上了网站说明，样式就不好看了，原来的友链是 float 布局，并不是瀑布流，加上网站说明后，友链卡片的高度就不相同了，友链卡片挤在一起，比较难看。

所以，又写了几种样式，可以添加网站说明，添加网站标签。

仓库中有所有样式的源码，直接拷贝就好了。  
GitHub：[https://github.com/maplesugarr/hexo-theme-next-friends-page](https://github.com/maplesugarr/hexo-theme-next-friends-page)

### [](#7-友链插件 "7. 友链插件")7\. 友链插件[](#7-友链插件)

查了查 Hexo 的 Api，写了一个插件，直接下载插件使用就好了。

GitHub：[https://github.com/maplesugarr/hexo-tag-friends](https://github.com/maplesugarr/hexo-tag-friends)

相关文章

*   [Next 主题集成 hashover 评论系统](/hexo/next-theme-add-hashover-comment-system/)
*   [制作炫酷的 canvas 动画作为 banner 背景](/hexo/next-theme-title-background-canvas/)
*   [Next 主题集成 revolvermaps 访问统计功能](/hexo/next-theme-add-revolvermaps-statistics/)
*   [Next 主题启用 Pjax](/hexo/next-theme-enable-pjax/)
*   [批量替换文章图片链接为 jsdelivr cdn 链接](/hexo/next-jsdelivrcdn-for-postimg/)

*   **本文作者：** 枫儿爱吃糖
*   **本文链接：** [https://blog.maplesugar.top/hexo/next-theme-custom-friendlinks-page/](https://blog.maplesugar.top/hexo/next-theme-custom-friendlinks-page/ "Next主题自定义友链页面")
*   **版权声明：** 本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议。转载请注明出处！

[静态博客](/tags/静态博客/) [hexo](/tags/hexo/) [next 主题](/tags/next主题/) [webmagic 源码解析](/webmagic/webmagic-sourcecode-analyse/ "webmagic源码解析")[Next 主题背景图片，使用 unsplash.com 随机图片](/hexo/next-theme-custom-background-img-using-unsplash/ "Next主题背景图片，使用unsplash.com随机图片")