> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [pwner.cn](https://pwner.cn/posts/90e45981.html)

🎨上次（2019 年 6 月初）因为重装 Windows 系统的缘故，需要重新部署本地的环境并与 Github 的仓库进行连接，因为当时正处于期末复习阶段，于是为了省事直接选择备份博客文章后全部重新部署本地环境，而且更换了 Hexo 主题的版本，第一次（2019 年 4 月底）安装 Hexo 的时候使用的貌似是 5.X 的版本，

### [](#2020-11新增 "2020.11新增")2020.11 新增

#### [](#修改行高 "修改行高")修改行高

`source\css\_variables\base.styl`

#### [](#修改宽度 "修改宽度")修改宽度

`themes\next\source\css\_variabes\pisces.styl`

在当时魔改的过程中发现该版本无法完美添加代码复制的按钮，于是在第二次部署的时候特意更换了 7.1.1 版本的，测试代码复制按钮通过以后就开始魔改其他的配置了。直到前不久… 我刚刚发现… 一个问题… 对于强迫症患者来说是一个致命的问题 —— 分类页面的格式变成了这样子😑

[![](https://ae01.alicdn.com/kf/Hce540c0c54a84128af459b6fbea27d68R.png)](https://ae01.alicdn.com/kf/Hce540c0c54a84128af459b6fbea27d68R.png)

于是我百方求助，有人建议我修改 CSS 样式，但是因为对 CSS 不够熟悉，也是无从下手……😵

在尝试了一个上午的时间不更换版本修复这个 bug 无果，下午我果断调整方向，直接选择更换主题版本。令人惊喜的是，更换版本到 6.6.0 以后竟然完美解决了这个问题。😎果然还是那句话，重装解决 99% 的问题。

**以下记录这次更换版本后的各种魔改操作，以便日后复查**

[x] 1.~HEXO 版本更换成最新的~，避免各种功能不兼容问题（代码复制按钮等）。

### [](#添加代码复制按钮 "添加代码复制按钮")添加代码复制按钮

在主题配置文件中启用 `copy_button` 即可

```
copy_button:
  enable: true
  # Show text copy result
  show_result: true
```

### [](#修改文章内超链接样式 "修改文章内超链接样式")修改文章内超链接样式

定位到 `themes/next/source/css/_custom/custom.styl`

添加以下代码

```
.post-body p a {
	color: #0593d3;
	border-bottom: none;
	&:hover {
		color: #0477ab;
		text-decoration: underline;
	}
}
```

### [](#修改阅读全文按钮样式 "修改阅读全文按钮样式")修改阅读全文按钮样式

定位到 `themes/next/source/css/_custom/custom.styl`

添加以下代码

```
.post-button {
    margin-top: 30px;
    text-align: center;
}

.post-button .btn {
    color: #fff;
    font-size: 15px;
    background: #5c5c5c;
    border-radius: 16px;
    line-height: 2;
    padding: 0 20px;
    transition: 0.2s ease-out;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
    
}

.post-button a{
  margin: 0 8px 8px 0 !important;
  border-bottom: 1px solid #666;
  border: none;
}

.btn:hover, .post-button .btn:hover {
    border-color: #222;
    color: #222;
    background: #fff;
    
}
```

### [](#修改主题页面布局为圆角 "修改主题页面布局为圆角")修改主题页面布局为圆角

在 `/themes/next/source/css/_variables` 处找到 `custom.styl` 添加如下代码（以 `Gemini` 风格为例）：

```
// Variables of Gemini scheme
// =================================================

@import "Pisces.styl";

// Settings for some of the most global styles.
// --------------------------------------------------
$body-bg-color                    = #eee

// Borders.
// --------------------------------------------------
$box-shadow-inner                 = 0 2px 2px 0 rgba(0,0,0,.12), 0 3px 1px -2px rgba(0,0,0,.06), 0 1px 5px 0 rgba(0,0,0,.12)
$box-shadow                       = 0 2px 2px 0 rgba(0,0,0,.12), 0 3px 1px -2px rgba(0,0,0,.06), 0 1px 5px 0 rgba(0,0,0,.12), 0 -1px .5px 0 rgba(0,0,0,.09)

$border-radius-inner              = initial
$border-radius                    = initial
$border-radius-inner            = 15px 15px 15px 15px;
$border-radius                  = 15px;
```

### [](#引用块样式修改 "引用块样式修改")引用块样式修改

定位到 `themes\next\source\css\ _custom\ _custom.styl` 添加如下代码：

```
//引用块样式
code {
    color: #1ABC9C;
    background: #fbf7f8;
    margin: 2px;
}

// 引用块？边框的自定义样式
.highlight, pre {
    margin: 5px 0;
    padding: 5px;
    border-radius: 3px;
}
.highlight, code, pre {
    border: 1px solid #d6d6d6;
}
```

### [](#引用块设置换行 "引用块设置换行")引用块设置换行

定位到 `themes\next\source\css\_common\scaffolding\base.styl`，找到 `blockquote` 样式，进行如下修改：

```
blockquote {
  margin: 0;
  padding: 0;
  word-break: break-all;
}
```

### [](#设置头像边框为圆形框-amp-鼠标悬停头像旋转 "设置头像边框为圆形框&鼠标悬停头像旋转")设置头像边框为圆形框 & 鼠标悬停头像旋转

定位到 `themes\next\source\css\_common\components\sidebar\sidebar-author.styl`，作如下修改

```
.site-author-image {
  display: block;
  margin: 0 auto;
  padding: $site-author-image-padding;
  max-width: $site-author-image-width;
  height: $site-author-image-height;
  border: $site-author-image-border-width solid $site-author-image-border-color;
  border-radius: 60%;
  transition: 2.5s all;  
}

.site-author-image:hover {
    transform: rotate(360deg);
}
```

### [](#首页添加Github标签 "首页添加Github标签")首页添加 Github 标签

定位到 `themes\next\layout\layout.swig`，在 `<div></div>` 下方添加对应颜色的代码

黑色：

```
<a href="https://your-url" aria-label="View source on GitHub"><svg width="80" height="80" viewBox="0 0 250 250" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor"></path></svg></a><style>.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}</style>
```

绿色：

```
<a href="https://your-url" aria-label="View source on GitHub"><svg width="80" height="80" viewBox="0 0 250 250" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor"></path></svg></a><style>.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}</style>
```

### [](#文章永久链接 "文章永久链接")文章永久链接

使用如下命令安装 `hexo-abbrlink` 插件：

```
sudo npm install hexo-abbrlink --save
```

  在站点配置文件下进行如下修改：

```
url: https://pwner.cn
root: /
permalink: posts/:abbrlink.html
permalink_defaults:
abbrlink:
  alg: crc32  # 算法：crc16(default) and crc32
  rep: hex    # 进制：dec(default) and hex
```

### [](#文章内页二级分类样式逻辑优化 "文章内页二级分类样式逻辑优化")文章内页二级分类样式逻辑优化

定位到 `themes\next\layout\_macro\post.swig`，文件里有

```
{% if post.categories and post.categories.length and theme.post_meta.categories %}
            <span >
            {% if theme.post_meta.created_at or theme.post_meta.updated_at %}
              <span>|</span>
            {% endif %}
              <span>
                <i></i>
              </span>
              {% if theme.post_meta.item_text %}
                <span>{{ __('post.in') }}</span>
              {% endif %}
              {% for cat in post.categories %}
                <span itemprop="about" itemscope itemtype="http://schema.org/Thing">
                  <a href="{{ url_for(cat.path) }}" itemprop="url" rel="index">
                    <span itemprop="name">{{ cat.name }}</span>
                  </a>
                </span>

                {% set cat_length = post.categories.length %}
                {% if cat_length > 1 and loop.index !== cat_length %}
                  {{ __('symbol.comma') }}
                {% endif %}
              {% endfor %}
            </span>
          {% endif %}
```

这一段就是相应的代码

可以看出来

```
<span>
    <i></i>
</span>
```

这一部分是分类的小图标

```
<span itemprop="about" itemscope itemtype="http://schema.org/Thing">
    <a href="{{ url_for(cat.path) }}" itemprop="url" rel="index">
        <span itemprop="name">{{ cat.name }}</span>
    </a>
</span>
```

这一部分是生成链接

```
{% if cat_length > 1 and loop.index !== cat_length %}
    {{ __('symbol.comma') }}
{% endif %}
```

这一部分就是产生分隔符号 (如果多余一个分类并且当前循环不是最后一个)

这个就是 “,” 把它修改成即可

即可。

### [](#使用使用压缩博文页面，优化访问速度 "使用使用压缩博文页面，优化访问速度")使用使用压缩博文页面，优化访问速度

在站点根目录下安装 hexo-neat

```
npm install hexo-neat --save
```

为站点配置文件添加相关配置，添加如下内容到站点配置文件`_config.yml` 的末尾就可以。

```
# hexo-neat
# 博文压缩
neat_enable: true
# 压缩html
neat_html:
  enable: true
  exclude:
# 压缩css  
neat_css:
  enable: true
  exclude:
    - '**/*.min.css'
# 压缩js
neat_js:
  enable: false
  mangle: false
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/jquery.fancybox.pack.js'
    - '**/index.js'
```

此处因为笔者的不问博文开启了加密，所以为了避免出现 bug，就选择不压缩 JS 文件，当然如果你想压缩 JS 文件，也可以通过配置参数将其开启。

压缩前的页面代码包含很多空行

[![](https://p.pstatp.com/origin/dc100002a270ca75e56a)](https://p.pstatp.com/origin/dc100002a270ca75e56a)

压缩后的网页代码

[![](https://ae01.alicdn.com/kf/H77221494a58b4760b822af9ef27b6386c.png)](https://ae01.alicdn.com/kf/H77221494a58b4760b822af9ef27b6386c.png)

### [](#文章添加置顶和加精功能 "文章添加置顶和加精功能")文章添加置顶和加精功能

笔者是通过安装第三方插件来实现文章的置顶功能的，当然也可以通过修改文件配置来实现（参考：[解决 Hexo 博客文章置顶问题](https://zhwhong.cn/2017/03/23/deal-with-hexo-article-top-problem/)），但是会比直接使用插件略显繁琐。

执行以下命令安装插件

```
$ npm uninstall hexo-generator-index --save
$ npm install hexo-generator-index-pin-top --save
```

在需要**置顶**的文章的 `Front-matter` 中加上 `top: true` 或者 `top: 任意数字`，例如：

```
title: 漫步者TWS1蓝牙耳机开箱
copyright: true
categories:

- 硬件派
  abbrlink: d05fae9e
  date: 2019-09-27 19:36:13
  top: 100
  tags:
```

其中，`top` 的值越大，文章排序越靠前。

到这里，已经实现了文章排序显示的问题。当然，为了更直观地表达该文章是置顶的，还需要给文章添加 “置顶” 的标签。

打开 `/themes/next/layout/_macro/` 目录下的 `post.swig` 文件，在 `<div>` 的第一个 `<span>` 标签下，插入如下代码：

```
{% if post.top %}    
	<i></i>    
	<font color=7D26CD>置顶</font>    
	<span>|</span>
{% endif %}
```

同理，可以设置**精华文章**标签的添加：

1、在 `/themes/next/layout/_macro/` 路径，找到 `post.swig`，在前文`置顶`功能后边，加上如下代码：

```
{% if post.essential%}     
	<span>         
		<i>精华</i>     
	</span>     
<span>|</span> {% endif %}
```

2、在 `themes/next/source/css/_custom/custom.styl` 中，增加如下样式：

```
.jingping{  
	background : #00a8c3;  
	padding:2px 4px 2px 4px;  
	color: #fff;
}
```

3、在需要设置精华的文章 `Front-matter` 中，加入如下代码

到此就完成了精华文章的设置。

### [](#添加最近文章列表 "添加最近文章列表")添加最近文章列表

首先在主题配置文件添加以下关键字

```
recent_posts:
  enable: true
  search: true
  post: false
  sidebar: false
  icon: history
  title: 近期文章
  layout: block
```

#### [](#侧栏 "侧栏")侧栏

在 `next/layout/_macro/sidebar.swig` 中的 `if theme.links` 对应的 `endif` 后面。

```
{% if theme.recent_posts.enable and theme.recent_posts.sidebar %}
  <div class="links-of-blogroll motion-element {{ "links-of-blogroll-" + theme.recent_posts.layout  }}">
   <div>
     <i class="fa fa-history fa-{{ theme.recent_posts.icon | lower }}" aria-hidden="true"></i>
     {{ theme.recent_posts.title }}
   </div>
   <ul>
     {% set posts = site.posts.sort('-date') %}
     {% for post in posts.slice('0', '3') %}
       <li>
         <a href="{{ url_for(post.path) }}" title="{{ post.title }}" target="_blank">{{ post.title }}</a>
       </li>
     {% endfor %}
   </ul>
 </div>
{% endif %}
```

#### [](#搜索结果处添加 "搜索结果处添加")搜索结果处添加

找到路径 `H:\hexo\themes\hexo-theme-next\layout\_partials\search` 下 `localsearch.swig` 文件  
把 `` 修改成以下内容（这里显示 15 篇）

```
<div>
  {% if theme.recent_posts.enable and theme.recent_posts.search %}
    <div>
     <div>
       <i class="fa fa-{{ theme.recent_posts.icon }}" aria-hidden="true"></i>
       {{ theme.recent_posts.title }}
     </div>
     <ul>
       {% set posts = site.posts.sort('-date') %}
       {% for post in posts.slice('0', '15') %}
         <li>
           <a href="{{ url_for(post.path) }}" title="{{ post.title }}" target="_blank">{{ post.title }}</a>
         </li>
       {% endfor %}
     </ul>
    </div>
  {% endif %}
</div>
```

#### [](#文章尾部添加 "文章尾部添加")文章尾部添加

把代码加在 `H:\hexo\themes\hexo-theme-next\layout\_macro\post.swig` 里的相应位置（我加在 tags 后）

```
{% if not is_index and theme.recent_posts.enable and theme.recent_posts.post %}
  <div>
   <div>
     <i class="fa fa-{{ theme.recent_posts.icon }}" aria-hidden="true"></i>
     {{ theme.recent_posts.title }}
   </div>
   <ul>
     {% set posts = site.posts.sort('-date') %}
     {% for post in posts.slice('0', '5') %}
         <a href="{{ url_for(post.path) }}" title="{{ post.title }}" target="_blank">{{ post.title }}</a> 
     {% endfor %}
   </ul>
  </div>
{% endif %}
```

#### [](#其他 "其他")其他

可尝试将 `-date` 改为 `-update`

### [](#常见的音乐的两种语法 "常见的音乐的两种语法")常见的音乐的两种语法

#### [](#使用HTML直接添加网易云音乐 "使用HTML直接添加网易云音乐")使用 HTML 直接添加网易云音乐

```
<div>
    <iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=280 height=86 src="//music.163.com/outchain/player?type=2&id=33911781&auto=1&height=66">
    </iframe>
</div>
```

#### [](#Hexo专用写法 "Hexo专用写法")Hexo 专用写法

```
{% aplayer "送别" "李叔同" "https://resource.pwner.cn/music/songbie.mp3" "https://s2.ax1x.com/2019/09/13/nrrMUU.png" "autoplay" %}
```

### [](#PDF插入的语法 "PDF插入的语法")PDF 插入的语法

```
{% pdf https://www.pwner.cn/123.pdf %}
```

#### [](#侧边栏目录设置成自动全部展开 "侧边栏目录设置成自动全部展开")侧边栏目录设置成自动全部展开

`themes/next/source/css/_common/components/sidebar/sidebar-toc.styl`，修改

```
.post-toc .nav .nav-child { display: none; }
```

为

```
.post-toc .nav .nav-child { display: block; }
```

#### [](#其他修改记录： "其他修改记录：")其他修改记录：

[x] 添加友链页面

[x] 添加本地搜索插件

[x] 侧边栏头像设置成圆形（6.7.0 默认为圆形头像）并开启光标悬停转动

[x] 侧边栏添加 Github/E-mail 按钮

[x] 添加站点地图和 RSS

[x] 底部文字修改，添加建站计时，添加站点统计

[x] 文章地址切换成永久链接，以利于搜索引擎抓取

[x] 页面压缩优化，改善访问体验

[x] 单击图片放大功能 Fancybox 插件（2.0）

[x] 显示浏览进度并显示在左侧边栏

[x] 添加打赏二维码

[x] SEO 优化（包括站点 Notfollow 设置）

[x] 添加 Valine 评论系统

[x] 优化了 SEO 设置：①主题配置文件添加了 `baidu_site_verification`②开启主题配置文件中的 `disable_baidu_tranformation`③主题配置文件开启 `index_with_subtitle`④主题配置文件开启 `exturl`（会导致自定义的超链文字样式失效）

[x] 开启了数学公式渲染：①主题配置文件中启用：`math: enable: true`②根据提示，默认配置是需要在文章的 `Front Matter` 中启用设置才能正常渲染的。为了尽可能确保设置的可靠性，建议不开启全局。③如果图方便，建议在 post 模板中的 `Front Matter` 添加 `mathjax: true` 设置项，防止今后使用其渲染公式时忘记设置。

[x] [添加了通知功能](https://www.dp2px.com/2018/10/14/hexo-notify/)，可以在主题配置文件中进行通知内容的配置

[x] [将文章侧边目录设置成自动全部展开](https://vonsdite.github.io/posts/6c0dbfd2.html)