> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_35479468/article/details/107454287?spm=1001.2014.3001.5501)

最新 hexo 教程请移步我的博客：[www.heson10.com](https://www.heson10.com)  
本文地址：[https://www.heson10.com/posts/51572.html](https://www.heson10.com/posts/51572.html)

新增 links 页面
-----------

```
hexo new page links
```

打开在 / source/links 里面刚生成的 index.md 文件，在头部加上`type: "links"`，

代码如下：

```
---
title: 朋友圈
date: 2020-07-19 22:28:52
type: "links"
---
```

配置 menu
-------

在主题配置文件 menu 下添加：

```
links: /links/ || fa fa-link
```

在`\themes\next\languages\zh-CN.yml`文件中`menu`下增加中文描述

```
links: 朋友圈
```

新增 links.swig 页面
----------------

在`\themes\next\layout`新建`links.swig`，内容如下：

```
{% block content %}
  {######################}
  {### LINKS BLOCK ###}
  {######################}

    <div id="links">
        <style>

            #links{
               margin-top: 5rem;
            }

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
        <div class="links-content">

             <div class="no-icon note warning"><div class="link-info">👨‍🎓 跟着大佬走，成为小大佬</div></div>
            <div class="link-navigation">
                    {% for link in theme.defaultlinks %}

                    <div class="card">
                        <img class="ava nofancybox" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank"> {{ link.nickname }}</a> </div>
                        <div class="info">{{ link.info }}</div>
                        </div>
                    </div>

                {% endfor %}

            </div>

            <div class="no-icon note primary"><div class="link-info">🍭 五湖四海的朋友们</div></div>

             <div class="link-navigation">
                    {% for link in theme.friendslinks %}

                    <div class="card">
                        <img class="ava nofancybox" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank"> {{ link.nickname }}</a> </div>
                        <div class="info">{{ link.info }}</div>
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

修改 page.swig
------------

修改`\themes\next\layout\page.swig`文件，在开头的`block title`内部两个 elif 之间加上：

```
{% elif page.type === 'links' and not page.title %}
    {{ __('title.links') + page_title_suffix }}
```

如图所示：

![](https://imgconvert.csdnimg.cn/aHR0cDovL3BpYy5oZXNvbi54eXovaW1nL2ltYWdlLTIwMjAwNzE5MjM0NDAwODYwLnBuZw?x-oss-process=image/format,png)

在下面`{% else %} {{ page.content }}`的前面加上：

```
{% elif page.type === 'links' %}
           {% include 'links.swig' %}
```

为了引入刚才新建的 links 界面。如图：

[外链图片转存失败, 源站可能有防盗链机制, 建议将图片保存下来直接上传 (img-aGpcGRtS-1595173918325)(http://pic.heson.xyz/img/image-20200719234743506.png)]

修改 links/index.md
-----------------

这个是友链页面的申请信息，可以按照自己想法修改：

```
---
title: 朋友圈
date: 2020-07-19 22:28:52
type: "links"
---
### 申请要求：

1、内容持续更新且可以稳定访问
        2、网页整洁无繁杂广告推广
        3、博客主页被百度或谷歌等搜索引擎收录
        4、头像能够快速加载
        5、拥有独立域名

### 友链声明：

1、本站会定期清理无法访问的友链，如果更换了链接信息请至评论区留言，谢谢合作！
        2、本站会定期查看双方是否互为友链，如果取消本站友链，本站也会将您的友链移除

### 申请方式：

先将本站的友链添加到您的友链，相关信息如下
        然后按照以下格式在本站留言区留言，待博主为您添上友链

>名         称：Heson
              头像链接：http://heson.xyz/images/avatar03.png
              主页链接：http://heson.xyz
              说明信息：人生在勤，不索何获
```

修改主题_config 配置文件
----------------

在结尾处添加：

```
# 友情链接
defaultlinks:
  - nickname: Heson     # 昵称
    avatar: http://heson.xyz/images/avatar03.png    # 头像地址
    site: https://www.heson10.com #友链地址
    info: 人生在勤，不索何获


friendslinks:
  - nickname: Heson     # 昵称
    avatar: http://heson.xyz/images/avatar03.png    # 头像地址
    site: https://www.heson10.com #友链地址
    info: 人生在勤，不索何获
```

`defaultlinks:`对应的是`links.swig`文件中 `👨‍🎓 跟着大佬走，成为小大佬`段落，此处链接写大佬的博客；  
`friendslinks:`对应的是`links.swig`文件中 `🍭 五湖四海的朋友们`段落，此处链接写朋友的博客。

欢迎参观我的博客：[www.heson10.com](https://www.heson10.com)