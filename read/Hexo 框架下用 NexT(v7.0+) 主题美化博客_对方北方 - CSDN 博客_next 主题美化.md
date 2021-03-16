> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_39345384/article/details/80785373)

1. 前言
=====

前文：[Windows 下通过 GitHub+Hexo 搭建个人博客的步骤](https://blog.csdn.net/weixin_39345384/article/details/80095883)；  
博主的个人博客：[https://hunter1023.github.io/](https://hunter1023.github.io/) 按照本篇博客美化。

在 Hexo 中有 **2 份**主要的配置文件，其名称都是`_config.yml`。 其中，一份位于**博客根目录下**，主要包含 **Hexo 本身的配置**；另一份位于`themes/next/`目录下，用于配置**主题相关的选项**。

2. 基础设置
=======

2.1 设置站点名、作者昵称和站点描述等内容
----------------------

打开**根目录下的`_config.yml`**

```
# Site
title: 特叔服务
subtitle: 
keywords:
author: Hunter
description: Tough times never last, but tough people do.
```

2.2. NexT 主题的安装
---------------

顾名思义，所谓主题就是界面的展示样式。Hexo 安装主题，只需要将主题文件拷贝至博客所在目录的`themes`目录下，修改相关配置文件即可生效。

博客所在目录下打开`git bash`，再通过`Git clone https://github.com/theme-next/hexo-theme-next themes/next`即可完成。

2.3 启用主题
--------

打开**根目录下的`_config.yml`**, 查找`theme`字段，将字段改为`theme: next`(**冒号`:`之后要有空格分隔，否则无效**) ，之后通过`hexo g`和`hexo s`，再在浏览器中访问`localhost:4000`即可本地预览主题效果。

3. 主题设定
=======

3.1 选择 scheme
-------------

打开`themes/next/`下的`_config.yml`, 查找`scheme`，可以看到如下四种不同的风格方案：

```
scheme: Muse
#scheme: Mist
#scheme: Pisces
#scheme: Gemini
```

去掉`#`注释，即启用对应的 scheme，博主采用 Muse 主题，大家可以依次测试效果，选择自己喜欢的 scheme。

3.2 设置语言
--------

博客框架默认的语言是英文，前往`/themes/next/languages`，查看当前 NexT 版本简体中文对照文件的名称是`zh-Hans`还是`zh-CN`。

再前往根目录下的`_config.yml`，查找`language`，设置成`language: zh-Hans`或`language: zh-CN`，即显示简体中文。

3.3 设置菜单及对应页面
-------------

*   打开`themes/next/`下的`_config.yml`，查找`menu`
    
    ```
    menu:
      home: / || home
      #about: /about/ || user
      tags: /tags/ || tags
      categories: /categories/ || th
      archives: /archives/ || archive
      #schedule: /schedule/ || calendar
      #sitemap: /sitemap.xml || sitemap
      #commonweal: /404/ || heartbeat
    ```
    
    去掉`#`注释即可显示对应的菜单项，也可自定义新的菜单项。 `||`之前的值是目标链接，之后的是分类页面的图标，图标名称来自于 FontAwesome icon。若没有配置图标，默认会使用问号图标。
    
*   新添加的菜单需要翻译对应的中文  
    打开`hexo/theme/next/languages/zh-CN.yml`，在 menu 下自定义，如：
    
    ```
    menu:
      resources: 资源
    ```
    
*   `hexo new page "categories"`  
    此时在根目录的`source`文件夹下会生成一个 categories 文件，文件中有一个`index.md`文件，修改内容如下
    
    ```
    ---
    title: 分类
    date: 2017-12-14 13:05:38
    type: "categories"
    comments: false
    ---
    ```
    
    注：如果有启用评论，默认页面带有评论。需要关闭的话，添加字段 comments 并将值设置为 false。
    

3.4 设定站点建立时间
------------

打开 **`themes/next/`下的`_config.yml`**，查找`since`

```
footer:
  # Specify the date when the site was setup.
  # If not defined, current year will be used.
  #since: 2015
```

**如果不设置，默认显示当前年份**。

4. 美化
=====

4.1 设置头像
--------

打开`themes/next/`下的`_config.yml`，查找`avatar`

```
# Sidebar Avatar
# in theme directory(source/images): /images/avatar.gif
# in site  directory(source/uploads): /uploads/avatar.gif
avatar: http://XXXXXXXXX
```

`avatar`的值是**图片的链接地址** (完整的 URI 或者 站内的相对地址皆可)

<table><thead><tr><th align="left">地址</th><th align="left">值</th></tr></thead><tbody><tr><td align="left">完整的 URI</td><td align="left"><a href="http://example.com/avatar.png">http://example.com/avatar.png</a></td></tr><tr><td align="left">站点内地址</td><td align="left">图片放至<code>themes/next/source/images/</code>配置为：<code>avatar: /images/图片名</code></td></tr><tr><td align="left">站点内地址</td><td align="left">图片放至<strong>根目录下</strong><code>source/uploads/</code>(初始无 uploads 文件夹，自行创建) 目录下配置为：<code>avatar: /uploads/图片名</code></td></tr></tbody></table>

**之后创建博文，对图片的引用 同样可以按照上述地址获取**。

4.2 网站图标设置
----------

*   图标素材网站：[iconfont](https://www.iconfont.cn/)；[easyicon](https://www.easyicon.net/)
*   下载 16x16 以及 32x32 大小的 **PNG 格式图标**，置于`/themes/next/source/images/`下
*   打开 **`themes/next/`下的`_config.yml`**，查找`favicon`
    
    ```
    favicon:
      small: /images/favicon-16x16-next.png
      medium: /images/favicon-32x32-next.png
      apple_touch_icon: /images/apple-touch-icon-next.png
      safari_pinned_tab: /images/logo.svg
      #android_manifest: /images/manifest.json
      #ms_browserconfig: /images/browserconfig.xml
    ```
    
    修改 small 和 medium 的路径为下载的图标路径

4.3 背景动画
--------

### 4.3.1 [Canvas-nest 风格](https://blog.csdn.net/weixin_39345384/article/details/80544660)

### 4.3.2 JavaScript 3D library 风格

1.  进入 theme/next 目录
2.  执行命令：`git clone https://github.com/theme-next/theme-next-three source/lib/three`
3.  将`themes/next/_config.yml`中查找`theme-next-three`，将想要的效果改为 true 即可：

```
# three_waves
three_waves: false
# canvas_lines
canvas_lines: true
# canvas_sphere
canvas_sphere: false
```

4.4 背景图片 / 顶栏、底栏图片（背景色）、侧栏背景及内部文字颜色
-----------------------------------

打开`theme/next/source/css/_custom/custom.styl`，添加以下代码

```
//背景图片
body{   
        background:url(图片链接);
        background-size:cover;
        background-repeat:no-repeat;
        background-attachment:fixed;
        background-position:center;
}
//顶栏图片
.header {
          background:url(图片链接) none repeat scroll !important;
}
//底栏背景色
.footer {
          background:rgba(颜色rgb,透明度) none repeat scroll !important;
}
//侧栏图片及内部文字颜色修改
#sidebar {
            background:url(图片链接);
            background-size: cover;
            background-position:center;
            background-repeat:no-repeat;
            p,span,a {color: 颜色代码;}
}
```

其中的 css 样式属性都可以根据图片修改，以达到满意的效果。

4.5 侧栏置于左侧，修改控制按钮样式
-------------------

默认情况下，侧栏仅在文章页面（拥有目录列表）时才显示，并放置于右侧位置。打开`themes/next/`下的`_config.yml`，查找`sidebar`

### 4.5.1 设置侧栏在左侧 / 右侧

*   Pisces 或 Gemini 方案
    
    ```
    sidebar:
    position: left
    #position: right
    ```
    
*   Mist 或 Muse 方案

1.  打开`next/source/js/src/motion.js`，查找`paddingRight`，把所有（2 个）`PaddingRight`更改为`paddingLeft`即可。
2.  打开`next/source/css/_custom/custom.styl`，添加如下内容：
    
    ```
    //侧边栏置于左侧
    .sidebar {
      left: 0;
    }
    //侧栏开关置于左侧
    .sidebar-toggle {
      left: $b2t-position-right;
    }
    ```
    
3.  打开`next/source/css/_common/components/back-to-top.styl`，将`right: $b2t-position-right;`改为`left: $b2t-position-right;`

### 4.5.2 显示侧边栏的时机

```
#post - 默认行为，在文章页面（拥有目录列表）时显示
	#always - 在所有页面中都显示
	#hide - 在所有页面中都隐藏（可以手动展开）
	#remove - 完全移除
	display: post
	#display: always
	#display: hide
	#display: remove
```

### 4.5.3 侧边栏控制按钮样式修改

打开`themes/next/layout/source/js/src/motion.js`，找到如下代码处，更换 close 的内容

```
var sidebarToggleLine1st = new SidebarToggleLine({
    el: '.sidebar-toggle-line-first',
    status: {
      arrow: {width: '50%', rotateZ: '45deg', top: '2px', left: '6px'},
      // close: {width: '100%', rotateZ: '-45deg', top: '5px', left: '0px'} //X形
      close: {width: '50%', rotateZ: '-45deg', top: '2px', left: '0px'} //箭头形
    }
  });
  var sidebarToggleLine2nd = new SidebarToggleLine({
    el: '.sidebar-toggle-line-middle',
    status: {
      arrow: {width: '90%'},
      // close: {opacity: 0} //X形
      close: {width: '90%'} //箭头形
    }
  });
  var sidebarToggleLine3rd = new SidebarToggleLine({
    el: '.sidebar-toggle-line-last',
    status: {
      arrow: {width: '50%', rotateZ: '-45deg', top: '-2px', left: '6px'},
      // close: {width: '100%', rotateZ: '45deg', top: '-5px', left: '0px'} //X形
      close: {width: '50%', rotateZ: '45deg', top: '-2px', left: '0px'} //箭头形
    }
  });
```

4.6 文章底部标签显示的优化
---------------

修改`/themes/next/layout/_macro/post.swig`，搜索 `rel="tag">#`，将 `#` 换成 `<i></i>`

4.7 文章添加阴影、透明效果
---------------

打开`theme/next/source/css/_custom/custom.styl`，添加以下代码

```
// 主页文章添加阴影效果
.post {
   margin-top: 60px;
   margin-bottom: 60px;
   padding: 25px;
   background:rgba(255,255,255,0.9) none repeat scroll !important;
   -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
   -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
}
```

4.8 Hexo 添加文章时自动打开编辑器
---------------------

*   首先在 Hexo 目录下的 scripts 目录中创建一个 JavaScript 脚本文件。  
    如果没有这个 scripts 目录，则新建一个。
*   scripts 目录新建的 JavaScript 脚本文件可以任意取名。

通过这个脚本，我们用其来监听`hexo new`这个动作，并在检测到`hexo new`之后，执行编辑器打开的命令。

*   如果你是 windows 平台的 Hexo 用户，则将下列内容写入你的脚本：

```
var spawn = require('child_process').exec;
hexo.on('new', function(data){
  spawn('start  "markdown编辑器绝对路径.exe" ' + data.path);
});
```

如果你是 Mac 平台 Hexo 用户，则将下列内容写入你的脚本：

```
var exec = require('child_process').exec;
hexo.on('new', function(data){
    exec('open -a "markdown编辑器绝对路径.app" ' + data.path);
});
```

4.9 点击侧栏头像回到首页
--------------

修改`/themes/next/layout/_macro/sidebar.swig`，找到如下代码：

```
<img class="site-author-image" itemprop="image"
    src="{{ url_for( theme.avatar | default(theme.images + '/avatar.gif') ) }}"
    alt="{{ theme.author }}" />
```

在其前后加上`<a href="/"></a>`即可，如下：

```
<a href="/">
   <img class="site-author-image" itemprop="image"
       src="{{ url_for( theme.avatar | default(theme.images + '/avatar.gif') ) }}"
       alt="{{ theme.author }}" />
</a>
```

4.10 修改中文字体
-----------

1.  前往 [Google Fonts](https://fonts.google.com/) 查看合适的字体
2.  打开`themes/next/`下的`_config.yml`，查找`font`
    
    ```
    font:
    	enable: true
    	 # Uri of fonts host. E.g. //fonts.googleapis.com (Default). 修改为墙内镜像
    	host: https://fonts.loli.net
    	global:
    		external: true
    		family: Noto Serif SC // 挑选的字体
    		size: 16
    ```
    
    3.  修改`/themes/next/source/css/_variables/base.styl`  
        将
    
    ```
    $font-family-monospace    = consolas, Menlo, $font-family-chinese, monospace
    $font-family-monospace    = get_font_family('codes'), consolas, Menlo, $font-family-chinese, monospace if get_font_family('codes')
    ```
    
    改为
    
    ```
    $font-family-monospace    = consolas, Menlo, $font-family-base, monospace
    $font-family-monospace    = get_font_family('codes'), consolas, Menlo, $font-family-base, monospace if get_font_family('codes')
    ```
    

4.11 新建文章时，在相同目录下创建同名文件夹（便于图片管理）
--------------------------------

*   打开站点配置文件`_config.yml`，搜索`post_asset_folder`字段，设置其值为`true`
*   安装 hexo-asset-image：`npm install hexo-asset-image --save`
*   此时`hexo new "fileName"`会在`/source/_posts`目录下创建同名的文件夹
*   只需在 md 文件里使用 `![title](图片名.jpg)` ，无需路径名就可以插入图片。

4.12 首页显示文章摘要（阅读全文）及配图（文章内不重复显示）
--------------------------------

1.  打开`themes/next/`下的`_config.yml`，查找`excerpt`
    
    ```
    auto_excerpt: //自动摘录
      enable: true
      length: 150 //摘录字数
    read_more_btn: true //显示全文按钮
    ```
    
2.  打开`themes\next\layout\_macro\post.swig`，在`{% if is_index %}`和`{% if post.description and theme.excerpt_description %}`之间添加如下内容
    
    ```
    {% if post.images %}
    	<div class="out-img-topic">
    		<img src={{ post.images }} class="img-topic">
    	</div>
    {% endif %}
    ```
    
3.  向`themes\next\source\css\_custom\custom.styl`中添加如下内容
    
    ```
    //文章摘要配图
    //图片外部的容器方框，限制图片大小
    .out-img-topic {
      display: block;
      max-height:500px;
      margin-bottom: 24px;
      overflow: hidden;
    }
    //图片
    img.img-topic {
      display: block ;
      margin-left: .7em;
      margin-right: .7em;
      padding: 0;
      float: right;
      clear: right;
    }
    ```
    
4.  将摘要图片储存于`themes\next\source\images`中，建议**在此路径下**单独建一个文件夹存放摘要图片，**这个图片和文章中插图的存放路径不同，不是一个概念**。然后在文章 YAML 头信息中添加 images 字段，将值填为`/images/imagename.jpg`。
    
    ```
    images: "images/文章摘要配图/Win10桌面.png"
    ```
    

4.13 给页面、侧边栏添加背景图片
------------------

打开`theme/next/source/css/_custom/custom.styl`，添加以下代码：

```
body {
  background: url(/images/blogbk.jpg) no-repeat;
  /* 背景图垂直、水平均居中 */
  background-position: center center;
  /* 当内容高度大于图片高度时，背景图像的位置相对于viewport固定 */
  background-attachment: fixed;
  /* 让背景图基于容器大小伸缩 */
  background-size: cover;
  /* 设置背景颜色，背景图加载过程中会显示背景色 */
  background-color: rgba(0, 0, 0, 0.5);
}
.sidebar {
            background:url(/images/sidebar.jpg);
            background-size: cover;
            background-position:center;
            background-repeat:no-repeat;
            p,span,a {color: rgba(255, 255, 255, 1);}
}
```

4.14 文字背景以及半透明的设置
-----------------

打开`theme/next/source/css/_custom/custom.styl`，添加以下代码：

```
.content {
	border-radius: 20px; //文章背景设置圆角
	padding: 30px 60px 30px 60px;
	background:rgba(255, 255, 255, 0.8) none repeat scroll !important;
}
```

4.15 去除 NexT 主题 Markdown 分割线渲染效果
--------------------------------

修改`/source/css/_common/scaffolding/base.styl`，注释或删除以下内容：

```
background-image: repeating-linear-gradient(
    -45deg,
    white,
    white 4px,
    transparent 4px,
    transparent 8px
  );
```

4.16 图片可点击放大查看，放大后可关闭
---------------------

*   打开站点配置文件`_config.yml`，搜索`fancybox`字段，设置其值为`true`
*   进入到`theme/text/`文件夹下，打开`git bash`
*   `git clone https://github.com/theme-next/theme-next-fancybox3 source/lib/fancybox`

4.17 博客总访问量统计
-------------

*   打开`themes/next/`下的`_config.yml`，查找`busuanzi`
    
    ```
    busuanzi_count:
      enable: true
      total_visitors: false
      total_visitors_icon: user
      total_views: false
      total_views_icon: eye
      post_views: true
      post_views_icon: eye
    ```
    

当前版本的 NexT 集成的不蒜子，总访问人数和人次只是分别用 icon 来表示，故取消显示，自行改动

*   打开`/themes/next/layout/_partials/footer.swig`，在最后添加如下内容：
    
    ```
    <span id="busuanzi_container_site_uv">
      本站访问次数：<span class="busuanzi-value" id="busuanzi_value_site_pv"></span>
    </span>
    ```
    

**效果：**  
![](https://img-blog.csdn.net/2018062323493260?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zOTM0NTM4NA==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
**配置：**  
查找主题配置文件`themes/next/_config.yml`中的`creative_commons`

```
creative_commons:
  license: by-nc-sa
  sidebar: false
  post: true  # 将false改为true即可显示版权信息
  language:
```

4.19 本地搜索（其余搜索方案的劣势只有收费）
------------------------

*   `npm install hexo-generator-search`
*   查找主题配置文件`themes/next/_config.yml`中的`local_search`
    
    ```
    local_search:
      enable: true
    ```
    

4.20 图床和上传工具
------------

[盘点一下免费好用的图床](https://zhuanlan.zhihu.com/p/35270383)

4.21 文章置顶
---------

[Hexo 博客彻底解决置顶问题](http://wangwlj.com/2018/01/09/blog_pin_post/)  
效果：  
![](https://img-blog.csdnimg.cn/20190329140445995.png)  
注：若有多篇文章需要置顶，排序方式为 在需要置顶的文章的`Front-matter`的`top:`填写阿拉伯数字即可，数越大，排序越靠前。

Google 统计
---------

Sitemap 网站地图
------------

提交谷歌收录本站 Google Search
----------------------

[文章阅读量统计](https://blog.csdn.net/weixin_39345384/article/details/80787998)
-------------------------------------------------------------------------

参考：

*   [HEXO+NEXT 主题个性化配置](http://mashirosorata.vicp.io/HEXO-NEXT%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE.html)
*   [打造个性超赞博客 Hexo+NexT+GitHubPages 的超深度优化](https://reuixiy.github.io/technology/computer/computer-aided-art/2017/06/09/hexo-next-optimization.html)
*   [[EasyHexo 专栏] #2 - 魔改 Next 不完全教程](https://juejin.im/post/5c45a503f265da616b10fe4e#heading-28)
*   [基于 Hexo+Node.js+github+coding 搭建个人博客——进阶篇 (从入门到入土)](https://blog.csdn.net/MasterAnt_D/article/details/56839222#t50)
*   [Hexo 博客 Next 主题优化总结](http://www.shaoyance.com/2018/01/26/Hexo%E5%8D%9A%E5%AE%A2Next%E4%B8%BB%E9%A2%98%E4%BC%98%E5%8C%96%E6%80%BB%E7%BB%93/)
*   [为 NexT 主题添加文章阅读量统计功能](https://notes.doublemine.me/2015-10-21-%E4%B8%BANexT%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E9%98%85%E8%AF%BB%E9%87%8F%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD.html)
*   [2017 年最新基于 hexo 搭建个人免费博客——自定义页面样式一](http://www.cduyzh.com/hexo-settings-3/)
*   [Hexo 添加文章时自动打开编辑器](https://notes.doublemine.me/2015-06-29-Hexo%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E6%97%B6%E8%87%AA%E5%8A%A8%E6%89%93%E5%BC%80%E7%BC%96%E8%BE%91%E5%99%A8.html)
*   [next 主题下点击侧边栏头像回到博客首页](https://blog.yleao.com/2018/0901/hexo-next%E4%B8%BB%E9%A2%98%E4%B8%8B%E7%9A%84%E7%BE%8E%E5%8C%96.html#next%E4%B8%BB%E9%A2%98%E4%B8%8B%E7%82%B9%E5%87%BB%E4%BE%A7%E8%BE%B9%E6%A0%8F%E5%A4%B4%E5%83%8F%E5%9B%9E%E5%88%B0%E5%8D%9A%E5%AE%A2%E9%A6%96%E9%A1%B5)
*   [Google Fonts 已支持思源宋体！](https://reuixiy.github.io/beautiful/share/2018/12/11/noto-serif-sc-added-on-google-fonts.html)
*   [弃暗投明 - Hexo 更换 next 主题](https://www.bluelzy.com/articles/change_to_next_theme.html)
*   [hexo 博客 NEXT 主题美化](https://www.feiwuuz.com.cn/archives/5483aa06.html)
*   [在 hexo 博客中插入图片，音乐，视频](http://chant00.com/2015/11/04/%E5%9C%A8hexo%E5%8D%9A%E5%AE%A2%E4%B8%AD%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%EF%BC%8C%E9%9F%B3%E4%B9%90%EF%BC%8C%E8%A7%86%E5%B1%8F%EF%BC%8C%E5%85%AC%E5%BC%8F/)