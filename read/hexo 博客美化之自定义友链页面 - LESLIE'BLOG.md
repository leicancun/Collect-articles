> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.guaini.blog](https://www.guaini.blog/archives/13407.html)

NexT 主题自带的友情链接的位置是在侧栏的 Social Link 中，位置不太明显，而且容量比较小，不美观。因此可以自定义一个特定的页面，单独显示友情链接。  

新增 links 页面：
------------

```
hexo new page "links"
```

Bash _复制_

这样在 `~/source/` 目录下会生成一个 `links` 文件夹，打开其中的 `index.md` 文件，在标题头中写入 `type = "links"` 这个属性头，如下：

```
title: 友情链接
date: 2019-09-29 13:08:43
type: "links"
```

YAML _复制_

配置 menu
-------

主题配置文件中`menu`下添加：

```
links: /links/ || link
```

YAML _复制_

在 `/themes/next/languages/zh-Hans.yml` 文件中 `menu` 下增加中文描述

```
links: 友链
```

YAML _复制_

做完这些工作，接下来就是要增加友链页面的样式了

新增 links.swig 页
---------------

首先，在 `~/themes/next/layout/` 目录下新建一个 `links.swig` 文件，并写入以下内容

```
<!-- 所在目录：~/themes/next/layout/ -->

{% block content %}
  {######################}
  {###  LINKS BLOCK   ###}
  {######################}
  
    <div id="links">
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
                width: 240px;
                font-size: 1rem;
                padding: 10px 20px;
                border-radius: 4px;
                transition-duration: 0.15s;
                margin-bottom: 1rem;
                display:flex;
            }
            @media (max-width: 767px) {
                .card:nth-child(odd) {
                    float: left;
                }
                .card:nth-child(even) {
                    float: left !important;
                }
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
                width: 100%;
            }
            .card .card-header a {
                font-style: normal;
                color: #2bbc8a;
                font-weight: bold;
                text-decoration: none;
            }
            .card .card-header a:hover {
                color: #a166ab;
                text-decoration: none;
            }
            .card .card-header .info {
                font-style:normal;
                color:#a3a3a3;
                font-size:14px;
                min-width: 0;
                overflow: hidden;
                white-space: nowrap;
            }

            span.focus-links {
                font-style: normal;
                margin-left: 10px;
                position: unset;
                left: 0;
                padding: 0 7px 0 5px;
                font-size: 11px;
                border-color: #42c02e;
                border-radius: 40px;
                line-height: 24px;
                height: 22px;
                color: #fff !important;
                background-color: #42c02e;
                display: inline-block;
            }
            span.focus-links:hover{
                background-color: #318024;
            }

            .friends-btn{
                text-align: center;
                color: #555!important;
                background-color: #fff;
                border-radius: 3px;
                font-size: 15px;
                box-shadow: inset 0 0 10px 0 rgba(0,0,0,.35);
                border: none!important;
                transition-property: unset;
                padding: 0 15px;
                margin: inherit;
            }

            .friends-btn:hover{
                color: rgb(255, 255, 255) !important;
                border-radius: 3px;
                font-size: 15px;
                box-shadow: inset 0px 0px 10px 0px rgba(0, 0, 0, 0.35);
                background-image: linear-gradient(90deg, #a166ab 0%, #ef4e7b 25%, #f37055 50%, #ef4e7b 75%, #a166ab 100%);
                margin: inherit;
            }
        </style>
        <div class="links-content">
            <div class="link-navigation">

                {% for link in theme.mylinks %}
                
                    <div class="card">
                        <img class="ava" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank"> {{ link.nickname }}</a> <a href="{{ link.site }}"><span class="focus-links">关注</span></a></div>
                        <div class="info">{{ link.info }}</div>
                        </div>
                    </div>
                
                {% endfor %}

            </div>
            {{ page.content }}
            </div>
        </div>
  
  {##########################}
  {###   END LINKS BLOCK  ###}
  {##########################}
{% endblock %}
```

PHP _复制_

其中的样式可以根据个人喜好进行更改。

修改 page.swig
------------

修改 `~/themes/next/layout/page.swig` 文件，在如下所示位置处进行添加：

```
<!-- 友情链接-->
#}{% elif page.type === 'links' and not page.title %}{#
  #}{{ __('title.links') + page_title_suffix }}{#
```

PHP _复制_

[![](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)

[未命名 1575567921.png](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)

引入 links.swig
=============

在 `/themes/next/layout/page.swig` 中 `PAGE BODY` 内部，引入刚才新建的 `page.swig`

```
<!-- 友情链接-->
{% elif page.type === 'links' %}
    {% include 'links.swig' %}
```

PHP _复制_

[![](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)

[image.png](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)

配置友链
----

在主题配置文件 `~/themes/next/_config.yml` 文件中按照以下格式添加友链

```
# 友情链接
mylinks:
  - nickname: # 昵称
    avatar: # 头像地址
    site: #友链地址
    info: #相关说明
    
  - nickname: # 昵称
    avatar: # 头像地址
    site: #友链地址
    info: #相关说明
```

YAML _复制_