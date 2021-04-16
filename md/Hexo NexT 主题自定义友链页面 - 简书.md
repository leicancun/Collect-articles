> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.jianshu.com](https://www.jianshu.com/p/ef110f36650b)

> [原文](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.liaofuzhan.com%2Fposts%2F1123041323.html) 首发 [北宸的小站](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.liaofuzhan.com)，欢迎访问！！！

Next 主题可增加友链，在主题配置文件`_config.yml`中`links`下添加，比如：

```
links:
  github: https://github.com/leafjame
  daovoice: http://www.daovoice.io/
  YouTube: https://youtube.com/channel/UCtzIJK9eLCWLQF13KpZE-0w
  Jianshu: https://www.jianshu.com/u/3b74c7b81348
```

首页展示效果：

![](http://upload-images.jianshu.io/upload_images/19151511-f87d09ef789d5e98.png) image

当链接变多以后，页面的排版很不美观，这时候就需要给友链新增一个**单独**的页面了。

步骤
==

新增 links 页面
-----------

在控制台使用命令创建：

```
$ hexo new page links
```

注：也可在`source`目录下手动创建（还需要手动创建 index.md 文件）

配置 menu
-------

主题配置文件`_config.yml`中`menu`下添加：

```
links: /links/ || link
```

`/themes/next/languages/zh-Hans.yml`文件中`menu`下增加中文描述：

```
links: 友链
```

做完这些工作，接下来就是要增加友链页面的样式了

新增`links.swig`页
---------------

在`/themes/next/layout/`新建`links.swig`，内容如下：

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
            <div class="link-navigation">

                {% for link in theme.mylinks %}

                    <div class="card">
                        <img class="ava" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank">@ {{ link.nickname }}</a></div>
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

修改`/themes/next/layout/page.swig`文件，在

```
#}{% elif page.type === "tags" and not page.title %}{#
    #}{{ __('title.tag') + page_title_suffix }}{#
```

位置下添加代码：

```
<!-- 友情链接-->
  #}{% elif page.type === 'links' and not page.title %}{#
    #}{{ __('title.links') + page_title_suffix }}{#
```

效果如下：

![](http://upload-images.jianshu.io/upload_images/19151511-f207c847b3fa2474.png) image

引入 links.swig
-------------

接着在`/themes/next/layout/page.swig`中，引入刚才新建的`page.swig`:

```
<!-- 友情链接-->
 {% elif page.type === 'links' %}
     {% include 'links.swig' %}
```

比如我是在

```
{% elif page.type === 'categories' %}
```

这个`if`下追加的：

![](http://upload-images.jianshu.io/upload_images/19151511-6018879a9cf6f812.png) image

到这里就完成页面样式的配置了。。。

配置友链
----

接下来，在`/themes/next/_config.yml`文件中配置友链，末尾处新增`mylinks`, 如下：

```
mylinks:

- nickname: Fi9Coder  #友链名称
  avatar: https://www.safeinfo.me/images/avatar.gif  #友链头像
  site: https://www.safeinfo.me  #友链地址
  info: 致力于Web安全与Python学习,研究,开发。  #友链说明
  
- nickname: Leaf's Blog
  avatar: https://leafjame.github.io/images/beichen.png
  site: https://leafjame.github.io
  info: Java狮 北漂男 摄影 旅行 赚钱
```

> 这里是配置了两个友链，多个的配置方式相同。

轻敲`hexo`命令三连，看看效果吧~😜  

![](http://upload-images.jianshu.io/upload_images/19151511-caa9e95c4521bc49.png) image

参考文章：[Hexo 修改友链样式](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.sanshuifeibing.cn%2Fposts%2F16e3649f.html)

还有一种比较不错的做法，可参考`枫糖`的博客：[Next 主题自定义友链页面](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.maplesugar.space%2Fhexo%2Fhexo-next%25E4%25B8%25BB%25E9%25A2%2598%25E8%2587%25AA%25E5%25AE%259A%25E4%25B9%2589%25E5%258F%258B%25E9%2593%25BE%25E9%25A1%25B5%25E9%259D%25A2%2F)。模仿 [Hexo NexT 博客增加瀑布流相册页面](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.dlzhang.com%2Fposts%2F3720dafc%2F)的功能实现的

相册功能参考：[Hexo NexT 主题内添加相册功能](https://links.jianshu.com/go?to=https%3A%2F%2Fasdfv1929.github.io%2F2018%2F05%2F26%2Fnext-add-photos%2F)