> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.guaini.blog](https://www.guaini.blog/archives/13407.html)

*   博主： [Leslie](https://www.guaini.blog/author/1/)
*   发布时间：2019 年 12 月 06 日
*   240 次浏览
*   [暂无评论](#comments)
*   5844 字数
*   分类： [建站相关](https://www.guaini.blog/category/jz/)

1.  [首页](https://www.guaini.blog/)
2.  正文  

[![](https://cdn.jsdelivr.net/gh/BruceXiaoWang/Images/img/20200131232838.png)](https://cdn.jsdelivr.net/gh/BruceXiaoWang/Images/img/20200131232838.png)

NexT 主题自带的友情链接的位置是在侧栏的 Social Link 中，位置不太明显，而且容量比较小，不美观。因此可以自定义一个特定的页面，单独显示友情链接。  

新增 links 页面：
------------

这样在 `~/source/` 目录下会生成一个 `links` 文件夹，打开其中的 `index.md` 文件，在标题头中写入 `type = "links"` 这个属性头，如下：

配置 menu
-------

主题配置文件中`menu`下添加：

在 `/themes/next/languages/zh-Hans.yml` 文件中 `menu` 下增加中文描述

做完这些工作，接下来就是要增加友链页面的样式了

新增 links.swig 页
---------------

首先，在 `~/themes/next/layout/` 目录下新建一个 `links.swig` 文件，并写入以下内容

其中的样式可以根据个人喜好进行更改。

修改 page.swig
------------

修改 `~/themes/next/layout/page.swig` 文件，在如下所示位置处进行添加：

[![](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)

[未命名 1575567921.png](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)

在 `/themes/next/layout/page.swig` 中 `PAGE BODY` 内部，引入刚才新建的 `page.swig`

[![](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)

[image.png](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)

配置友链
----

在主题配置文件 `~/themes/next/_config.yml` 文件中按照以下格式添加友链

**扫一扫支付**

![](https://cdn.jsdelivr.net/gh/BruceXiaoWang/Images/img/20201025025319.png)![](https://cdn.jsdelivr.net/gh/BruceXiaoWang/Images/img/20201025025319.png)

[Leslie](#) • 2019 年 12 月 06 日

![](https://cdn.jsdelivr.net/gh/BruceXiaoWang/Images/img/20200131232838.png)

NexT 主题自带的友情链接的位置是在侧栏的 Social Link 中，位置不太明显，而且容量比较小，不美观。因此可以自定义一个特定的页面，单独显示友情链接。  

新增 links 页面：
------------

这样在 `~/source/` 目录下会生成一个 `links` 文件夹，打开其中的 `index.md` 文件，在标题头中写入 `type = "links"` 这个属性头，如下：

配置 menu
-------

主题配置文件中`menu`下添加：

在 `/themes/next/languages/zh-Hans.yml` 文件中 `menu` 下增加中文描述

做完这些工作，接下来就是要增加友链页面的样式了

新增 links.swig 页
---------------

首先，在 `~/themes/next/layout/` 目录下新建一个 `links.swig` 文件，并写入以下内容

其中的样式可以根据个人喜好进行更改。

修改 page.swig
------------

修改 `~/themes/next/layout/page.swig` 文件，在如下所示位置处进行添加：

![](https://i.loli.net/2019/12/06/Gd72hgF6xIaj8ZE.png)

在 `/themes/next/layout/page.swig` 中 `PAGE BODY` 内部，引入刚才新建的 `page.swig`

![](https://i.loli.net/2019/12/06/CZsel4HDYB8WdxU.png)

配置友链
----

在主题配置文件 `~/themes/next/_config.yml` 文件中按照以下格式添加友链