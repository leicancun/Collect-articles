> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [tding.top](https://tding.top/archives/73ce4e7.html)

NexT 主题自带的友链模块放在侧边栏下面，视觉上比较臃肿。

本文介绍两种修改友链样式的方法以及具体的步骤。其中第一种方法需要修改 NexT 主题文件，第二种则不需要。

*   本博客的友链见：[友链](https://tding.top/about/links.html)。

[](#第一种友链样式 "第一种友链样式")第一种友链样式
-----------------------------

*   本博客在 NexT-7.1.2 版本时采用的样式。

### [](#新建links-swig文件 "新建links.swig文件")新建 `links.swig` 文件

在 `themes/Next/layout/` 新建一个文件 `links.swig`，添加如下代码：

```
{% block content %}
  {######################}
  {### LINKS BLOCK ###}
  {######################}
  
    <div>
        <style>
            .links-content{
                margin-top:1rem;
            }
            
            .link-navigation::after {
                content: " ";
                display: block;
                clear: both;
            }
            
            .card {
                width: 300px;
                font-size: 1rem;
                padding: 10px 20px;
                border-radius: 4px;
                transition-duration: 0.15s;
                margin-bottom: 1rem;
                display:flex;
            }
            .card:nth-child(odd) {
                float: left;
            }
            .card:nth-child(even) {
                float: right;
            }
            .card:hover {
                transform: scale(1.1);
                box-shadow: 0 2px 6px 0 rgba(0, 0, 0, 0.12), 0 0 6px 0 rgba(0, 0, 0, 0.04);
            }
            .card a {
                border:none; 
            }
            .card .ava {
                width: 3rem!important;
                height: 3rem!important;
                margin:0!important;
                margin-right: 1em!important;
                border-radius:4px;
                
            }
            .card .card-header {
                font-style: italic;
                overflow: hidden;
                width: 236px;
            }
            .card .card-header a {
                font-style: normal;
                color: #2bbc8a;
                font-weight: bold;
                text-decoration: none;
            }
            .card .card-header a:hover {
                color: #d480aa;
                text-decoration: none;
            }
            .card .card-header .info {
                font-style:normal;
                color:#a3a3a3;
                font-size:14px;
                min-width: 0;
                text-overflow: ellipsis;
                overflow: hidden;
                white-space: nowrap;
            }
        </style>
        <div>
            <div>

                {% for link in theme.mylinks %}
                
                    <div>
                        <img src="{{ link.avatar }}"/>
                        <div>
                        <div><a href="{{ link.site }}" target="_blank">@ {{ link.nickname }}</a></div>
                        <div>{{ link.info }}</div>
                        </div>
                    </div>
                
                {% endfor %}

            </div>
            {{ page.content }}
            </div>
        </div>
  
  {##########################}
  {### END LINKS BLOCK ###}
  {##########################}
{% endblock %}
```

### [](#修改page-swig文件 "修改page.swig文件")修改 `page.swig` 文件

然后我们修改 `themes/next/layout/page.swig`，在下面这个位置添加两行代码：

```
#}{% if page.type 
    #}{{ __('title.category') + page_title_suffix }}{#
  #}{% elif page.type 
    #}{{ __('title.tag') + page_title_suffix }}{#
  #}{% elif page.type 
    #}{{ __('title.schedule') + page_title_suffix }}{#
+ #}{% elif page.type === 'links' and not page.title %}{#
+   #}{{ __('title.links') + page_title_suffix }}{#
  #}{% else %}{#
    #}{{ page.title + page_title_suffix }}{#
  #}{% endif %}{#
```

然后在如下位置添加两行代码：

```
{% elif page.type 
          {% include 'schedule.swig' %}
+       {% elif page.type === 'links' %}
+         {% include 'links.swig' %}
        {% else %}
          {{ page.content }}
        {% endif %}
```

### [](#修改主题配置文件-config-yml "修改主题配置文件_config.yml")修改主题配置文件`_config.yml`

在主题配置文件 `themes/_config.yml` 末尾处添加友链：

```
mylinks:
  - nickname: 小丁的个人博客                           
    avatar: https://tding.top/images/avatar.webp       
    site: https://tding.top                            
    info: 世间所有的相遇，都是久别重逢
```

[](#第二种友链样式——瀑布流友链实现 "第二种友链样式——瀑布流友链实现")第二种友链样式 —— 瀑布流友链实现
----------------------------------------------------------

基本原理：新建 md 页面，渲染出一个 html 页面，其中包含一个 class 是`.link-navigation` 的网页元素。同时加载 `links.js`，下载 json 文件，渲染到这个网页元素中。

*   本博客当前采用的样式。

### [](#新建links页面 "新建links页面")新建 links 页面

新建 links 页面，输入放置友链的 html 元素：

这样会在 `/source/` 下创建 `links/index.md`。在文档的 `front matter` 添加 `type: links`，编辑好自己需要的友链页面内容，然后输入放置友链的 html 元素。示例：

```
---
title: 友链
type: links
---

<style>.links-content{margin-top:1rem}.link-navigation::after{content:" ";display:block;clear:both}.card{width:130px;font-size:1rem;padding:0;border-radius:4px;transition-duration:.15s;margin-bottom:1rem;display:block;float:left;box-shadow:0 2px 6px 0 rgba(0,0,0,.12);background:#f5f5f5}.card{margin-left:16px}@media(max-width:567px){.card{margin-left:16px;width:calc((100% - 16px)/2)}.card:nth-child(2n+1){margin-left:0}.card:not(:nth-child(2n+1)){margin-left:16px}}@media(min-width:567px){.card{margin-left:16px;width:calc((100% - 32px)/3)}.card:nth-child(3n+1){margin-left:0}.card:not(:nth-child(3n+1)){margin-left:16px}}@media(min-width:768px){.card{margin-left:16px;width:calc((100% - 48px)/4)}.card:nth-child(4n+1){margin-left:0}.card:not(:nth-child(4n+1)){margin-left:16px}}@media(min-width:1200px){.card{margin-left:16px;width:calc((100% - 64px)/5)}.card:nth-child(5n+1){margin-left:0}.card:not(:nth-child(5n+1)){margin-left:16px}}.card:hover{transform:scale(1.1);box-shadow:0 2px 6px 0 rgba(0,0,0,.12),0 0 6px 0 rgba(0,0,0,.04)}.card .thumb{width:100%;height:0;padding-bottom:100%;background-size:100% 100%!important}.posts-expand .post-body img{margin:0;padding:0;border:0}.card .card-header{display:block;text-align:center;padding:1rem .25rem;font-weight:500;color:#333;white-space:normal}.card .card-header a{font-style:normal;color:#2bbc8a;font-weight:700;text-decoration:none;border:0}.card .card-header a:hover{color:#d480aa;text-decoration:none;border:0}</style><div><div><div></div></div></div>

------

<div><span>
    <i></i>
  </span>留言添加友链<span>
    <i></i>
  </span></div>
  
------

{% note success %}

## 友链格式

- 网站名称：小丁的个人博客
- 网站地址：[https://tding.top](https://tding.top)
- 网站描述：世间所有的相遇，都是久别重逢
- 网站Logo/头像：[https://tding.top/images/avatar.webp](https://tding.top/images/avatar.webp)

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
[{
		"nickname": "三水非冰博客",
		"avatar": "https://www.sanshuifeibing.com/usr/images/avatar2.jpg",
		"site": "https://www.sanshuifeibing.com"
	},
	{
		"nickname": "北宸",
		"avatar": "https://leafjame.github.io/images/beichen.png",
		"site": "https://leafjame.github.io"
	},
	{
		"nickname": "千灵夙赋",
		"avatar": "https://qianling.pw/images/avatar.png",
		"site": "https://qianling.pw/"
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
  init: function() {
      var that = this;
      
      $.getJSON("/links/linklist.json",
      function(data) {
          that.render(data);
      });
  },
  render: function(data) {
      var html, nickname, avatar, site, li = "";
      for (var i = 0; i < data.length; i++) {
          nickname = data[i].nickname;
          avatar = data[i].avatar;
          site = data[i].site;
          li += '<div>' + '<a href="' + site + '" target="_blank">' + '<div>' + '</div>' + '</a>' + '<div>' + '<div><a href="' + site + '" target="_blank">' + nickname + '</a></div>' + '</div>' + '</div>';

      }
      $(".link-navigation").append(li);
  }
}
link.init();
```

### [](#问题排查 "问题排查")问题排查

1.  浏览器 F12 查看页面源码，是否有一个 class 是`.link-navigation` 的网页元素。
2.  查看 `link.js` 是否正常加载了，json 文件是否正常加载了。

如果加载 js 文件的 `/source/_data/body-end.swig` 不起作用，我们也可以把 `link.js` 内容放到 `/source/links/index.md` 中，效果是一样的。

[](#参考 "参考")参考
--------------

*   [Hexo 修改友链样式](https://www.sanshuifeibing.cn/posts/16e3649f.html)
*   [Next 主题自定义友链页面](https://blog.maplesugar.space/hexo/hexo-next%E4%B8%BB%E9%A2%98%E8%87%AA%E5%AE%9A%E4%B9%89%E5%8F%8B%E9%93%BE%E9%A1%B5%E9%9D%A2/)