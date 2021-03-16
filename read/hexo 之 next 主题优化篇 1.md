> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [juejin.cn](https://juejin.cn/post/6844904053818785805#heading-5) 这篇博客完成的时候已经是现在了，首先给大家拜个晚年，祝大家新年快乐！ 好的还是不好的都已经过去了，希望大家不要为旧的忧伤浪费新的眼泪。

上一篇博客介绍了如何搭建 `hexo` 环境，最近放假在家有时间 (而且为了安全更不能出门) 可以更博，所以打算将环境优化篇内容完成，做一个简单的总结（是不是转的有点快 ^_^）!

主题优化最重要的一部分内容就是修改 `_config.yml` 文件，我们把它叫站点配置文件，在我们的 `themes` 目录下还有一个名称是 `_config.yml` 文件，我们把它叫做主题配置文件，注意进行区分。

更换 `next` 主题
============

下载主题
----

下载地址：[next 最新版本地址](https://github.com/theme-next/hexo-theme-next)

我们进入 `hexo` 的博客目录，然后将 `next` 仓库克隆至 `themes` 目录下：

```
$ cd Blog
$ git clone https://github.com/theme-next/hexo-theme-next.git themes/next
复制代码
```

这个时候就已经将 `next` 这一主题仓库克隆至 `themes` 文件夹的 `next` 目录内，直接打开文件夹也可以看到。

修改站点配置文件
--------

我们打开站点配置文件 `_config.yml` (Blog 目录下) ，找到 `theme`，修改为 `next` 即可:

```
theme: next
复制代码
```

只需要修改这一处就可以更换主题，记住需要重启服务器主题才能生效。

主题配置文件概览
========

缓冲及其他设置
-------

想要优化主题，我们首先要熟悉的一个就是主题配置文件 `_config.yml` (不是站点配置文件)，下面就详细的介绍这个文件的内容 (其实我们通过文件各部分的英文说明都能明白各部分的作用，建议大家在配置之前还是先通读一遍)

首先是总体的设置，这一部分基本可以不用理会，默认就好

```
# If false, merge configs from `_data/next.yml` into default configuration (rewrite).
# If true, will fully override default configuration by options from `_data/next.yml` (override). Only for NexT settings.
# And if true, all config from default NexT `_config.yml` must be copied into `next.yml`. Use if you know what you are doing.
# Useful if you want to comment some options from NexT `_config.yml` by `next.yml` without editing default config.
override: false # 默认 false 即可

# Console reminder if new version released.
reminder: false # 控制台是否提醒新版本的更新，false

# Allow to cache content generation. Introduced in NexT v6.0.0.
cache:
  enable: true # 允许缓存，true

# Remove unnecessary files after hexo generate.
minify: false # 是否在 hexo 生成之后删除不必要的文件，false

# Define custom file paths.
# Create your custom files in site directory `source/_data` and uncomment needed files below.
custom_file_path: # 常用的文件路径
  #head: source/_data/head.swig
  #header: source/_data/header.swig
  #sidebar: source/_data/sidebar.swig
  #postMeta: source/_data/post-meta.swig
  #postBodyEnd: source/_data/post-body-end.swig
  #footer: source/_data/footer.swig
  #bodyEnd: source/_data/body-end.swig
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl
复制代码
```

站点基本信息配置
--------

```
# 网站图标设置，不是个人头像，个人头像设置是在侧边栏设置部分 
# 设置分为不同的浏览器不同的设备以及不同的大小都可以分别进行设置，根据自己的喜好选择就行
favicon: 
  small: /images/favicon-16x16-next.png
  medium: /images/favicon-32x32-next.png
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml

# 网站的页脚设置部分
footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
  #since: 2015  # 网站的建站时间，如果不写就是你自己建站的时间

  # Icon between year and copyright info.
  icon: # 这里的icon是页脚建站时间和网站名字之间的图标，默认是 `user`图标
    # Icon name in Font Awesome. See: https://fontawesome.com/v4.7.0/icons/
    # `heart` is recommended with animation in red (#ff0000).
    name: user #图标名称
    # If you want to animate the icon, set it to true.
    animated: false # 是否是动画，默认
    # Change the color of icon, using Hex Code.
    color: "#808080" # 颜色，16进制

  # If not defined, `author` from Hexo `_config.yml` will be used.
  copyright: # 文章版权设置部分

  powered:
    # Hexo link (Powered by Hexo).
    enable: true # 是否显示 hexo链接，如果不想显示设置为false即可
    # Version info of Hexo after Hexo link (vX.X.X).
    version: true # 是否显示版本号，如果不想显示设置为false即可

  theme: # 这一部分是设置在页脚是否显示主题提供商和版本号，false即可
    # Theme & scheme info link (Theme - NexT.scheme).
    enable: true
    # Version info of NexT after scheme info (vX.X.X).
    version: true

  # Beian ICP and gongan information for Chinese users. See: http://www.beian.miit.gov.cn, http://www.beian.gov.cn
  beian: #这一部分设置网站备案，如果还没有备案就不需要填写
    enable: false
    icp:
    # The digit in the num of gongan beian.
    gongan_id:
    # The full num of gongan beian.
    gongan_num:
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url:

# Creative Commons 4.0 International License.
# See: https://creativecommons.org/share-your-work/licensing-types-examples
# Available values of license: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
# You can set a language value if you prefer a translated version of CC license, e.g. deed.zh
# CC licenses are available in 39 languages, you can find the specific and correct abbreviation you need on https://creativecommons.org
creative_commons: # 文章版权说明，这一部分比较重要，也是值得说明的一部分
  license: by-nc-sa # 版权说明
  sidebar: false # 侧边栏就不需要版权了，false
  post: false # 文章需要搬去哪说明，修改为true
  language: # 语言可以不用设置，因为在站点配置文件中已经设置好了
复制代码
```

选择框架
----

```
# 根据自己的喜好选择框架，可以挨个尝试，但我自己还是更喜欢这个默认框架 `Muse`
# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------
# Schemes
scheme: Muse
#scheme: Mist
#scheme: Pisces
#scheme: Gemini
复制代码
```

菜单栏设置
-----

```
# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# When running the site in a subdirectory (e.g. yoursite.com/blog), remove the leading slash from link value (/archives -> archives).
# External url should start with http:// or https://
menu: # 选择自己需要显示的菜单，其他不需要的注释即可
  home: / || home # 主页
  #about: /about/ || user # 关于
  #tags: /tags/ || tags # 标签
  #categories: /categories/ || th # 分类
  archives: /archives/ || archive # 归档
  #schedule: /schedule/ || calendar # 日历
  #sitemap: /sitemap.xml || sitemap 
  #commonweal: /404/ || heartbeat # 404界面

# Enable / Disable menu icons / item badges.
menu_settings: # 菜单栏设置
  icons: true # 是否显示图标
  badges: false 
复制代码
```

> 注: 在使用的时候直接设置就好，但是并不会起作用，因为我们还要为菜单创建一个新的界面，例如使用命令 hexo new page about 创建 about 界面，然后点击 about 才会跳出。

侧边栏设置
-----

```
# ---------------------------------------------------------------
# Sidebar Settings
# See: https://theme-next.org/docs/theme-settings/sidebar
# ---------------------------------------------------------------

sidebar:
  # Sidebar Position.
  position: left # 侧边栏位置，默认在左侧
  #position: right

  # Manual define the sidebar width. If commented, will be default for:
  # Muse | Mist: 320
  # Pisces | Gemini: 240
  #width: 300 # 定义侧边栏的宽度，一般默认300就挺好

  # Sidebar Display (only for Muse | Mist), available values:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
  display: post # post指的是默认的是在文章界面自动展开
                # always在所有的页面都默认展开
                # hide 是在所有的页面都默认隐藏
                # remove 完全移除侧边栏

  # Sidebar padding in pixels.
  padding: 18 # 侧边栏填充像素大小，可忽略
  # Sidebar offset from top menubar in pixels (only for Pisces | Gemini).
  offset: 12 # 侧边栏距离顶部菜单的距离(单位像素)
  # Enable sidebar on narrow view (only for Muse | Mist).
  onmobile: false # 在移动设备是否显示菜单栏，仅仅针对 Muse 和 Mist主题有效

# Sidebar Avatar
avatar: # 个人头像设置
  # Replace the default image and set the url here.
  url: #/images/avatar.gif
  # If true, the avatar will be dispalyed in circle.
  rounded: false # 是否是圆形显示
  # If true, the avatar will be rotated with the cursor.
  rotated: false # 鼠标放置头像上可以旋转

# Posts / Categories / Tags in sidebar.
site_state: true # 侧边栏头像下是否显示文章、分类和标签设置

# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimiter is the target permalink, value after `||` delimiter is the name of Font Awesome icon.
social: # 友情链接，直接添加自己的社会链接即可，||前面是地址，||后面是图标
  #GitHub: https://github.com/yourname || github
  #E-Mail: mailto:yourname@gmail.com || envelope
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
  #RSS: /atom.xml || rss

social_icons: # 友链的图标，默认就好
  enable: true
  icons_only: false
  transition: false

# Blog rolls
links_settings: # 友链的设置
  icon: link    # 图标link
  title: Links # 链接名称，可以修改为：友情链接
  # Available values: block | inline
  layout: block # 友链的布局: 块 或 行

links: # 上面是设置，这里是添加链接，title + 链接
  #Title: http://yoursite.com

# Table of Contents in the Sidebar
# Front-matter variable (unsupport wrap expand_all).
toc: # 文章标题设置，这一部分默认设置即可
  enable: true # 是否显示文章标题
  # Automatically add list number to toc.
  number: true # 标题是否自动编号
  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: false # 如果题目过长，是否换行
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: false # 是否显示所有等级的标题
  # Maximum heading depth of generated toc.
  max_depth: 6 # 接受生成的标题的最大深度

# A button to open designated chat widget in sidebar.
# Firstly, you need enable the chat service you want to activate its sidebar button.
chat: # 打开chat服务的按钮，首先你需要激活一个  chat 服务，这里可以不用设置，没有实用价值
  enable: false # 关闭在线聊天服务即可
  #service: chatra
  #service: tidio
  icon: comment # Icon name in Font Awesome, set false to disable icon.
  text: Chat # Button text, change it as you wish.
复制代码
```

文章设置
----

```
# ---------------------------------------------------------------
# Post Settings
# See: https://theme-next.org/docs/theme-settings/posts
# ---------------------------------------------------------------

# Automatically excerpt description in homepage as preamble text.
excerpt_description: true # 在主页显示预览文本

# Read more button
# If true, the read more button will be displayed in excerpt section.
read_more_btn: true # 是否显示 阅读更多 按钮

# Post meta display settings
post_meta: # 文章显示设置，这里建议默认
  item_text: true # 是否显示文章内容
  created_at: true # 是否显示创建时间
  updated_at:      # 是否显示更新时间
    enable: true
    another_day: true
  categories: true # 是否显示分类

# Post wordcount display settings
# Dependencies: https://github.com/theme-next/hexo-symbols-count-time
symbols_count_time: # 预计阅读时间和文章字数统计，需要安装插件，具体的设参考上面的链接，但我不建议设置(太繁琐)
  separated_meta: true
  item_text_post: true
  item_text_total: false
  awl: 4
  wpm: 275

# Use icon instead of the symbol # to indicate the tag at the bottom of the post
tag_icon: false # 文章底部默认的标签是 # 号，建议改为 true

# Reward (Donate) # 打赏设置
# Front-matter variable (unsupport animation).
reward_settings:
  # If true, reward will be displayed in every article by default.
  enable: false # 时候开启打赏服务
  animation: false # 是否添加动画
  #comment: Donate comment here.

reward: # 此处是贴上自己的收款码，收款码放置在 images 目录下，然后在此处添加链接
  #wechatpay: /images/wechatpay.png
  #alipay: /images/alipay.png
  #bitcoin: /images/bitcoin.png

# Related popular posts
# Dependencies: https://github.com/tea3/hexo-related-popular-posts
related_posts: # 是否开启相关文章推荐，不建议开启
  enable: false
  title: # Custom header, leave empty to use the default one
  display_in_home: false
  params:
    maxCount: 5
    #PPMixingRate: 0.0
    #isDate: false
    #isImage: false
    #isExcerpt: false

# Post edit
# Dependencies: https://github.com/hexojs/hexo-deployer-git
post_edit: 
  enable: false
  url: https://github.com/user-name/repo-name/tree/branch-name/subdirectory-name # Link for view source
  #url: https://github.com/user-name/repo-name/edit/branch-name/subdirectory-name # Link for fork & edit

# Show previous post and next post in post footer if exists
# Available values: left | right | false
post_navigation: left # 上一篇/下一篇文章导航，选择项有 left/right/false
复制代码
```

用户界面设置
------

```
# ---------------------------------------------------------------
# Custom Page Settings
# See: https://theme-next.org/docs/theme-settings/custom-pages
# ---------------------------------------------------------------

# TagCloud settings for tags page.
tagcloud: # 标签云界面
  # All values below are same as default, change them by yourself.
  min: 12 # Minimun font size in px
  max: 30 # Maxium font size in px
  start: "#ccc" # Start color (hex, rgba, hsla or color keywords)
  end: "#111" # End color (hex, rgba, hsla or color keywords)
  amount: 200 # Amount of tags, change it if you have more than 200 tags

# Google Calendar
# Share your recent schedule to others via calendar page.
calendar: # 日程表界面
  calendar_id: <required> # Your Google account E-Mail
  api_key: <required>
  orderBy: startTime
  offsetMax: 24 # Time Range
  offsetMin: 4 # Time Range
  showDeleted: false
  singleEvents: true
  maxResults: 250
复制代码
```

主题框架设置
------

```
# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Set the text alignment in posts / pages.
text_align: # 文本对齐方式，默认居中 justify 即可
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
  desktop: justify
  mobile: justify

# Reduce padding / margin indents on devices with narrow width.
mobile_layout_economy: false # 移动端是否窄化布局，默认即可

# Android Chrome header panel color ($brand-bg / $headband-bg => $black-deep).
android_chrome_color: "#222" # 安卓chrome浏览器颜色，默认即可

# Hide sticky headers and color the menu bar on Safari (iOS / macOS).
safari_rainbow: false # safari浏览器,默认即可

# Custom Logo (Do not support scheme Mist)
custom_logo: #/uploads/custom-logo.jpg  # 用户 logo ，默认即可

codeblock: # 代码块设置
  # Code Highlight theme
  # Available values: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
  highlight_theme: normal  # 代码高亮主题，有 normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic 几种选择
  # Add copy button on codeblock
  copy_button: # 代码块中的复制按钮
    enable: false # 建议 true
    # Show text copy result.
    show_result: false # 是否显示复制成功/复制失败信息，建议 true
    # Available values: default | flat | mac
    style: # 代码块的风格，其中有mac风格，自己可以选择尝试一下，但我还是觉得默认的 normal 可以

back2top: # 返回页面顶部按钮
  enable: true # 建议开启
  # Back to top in sidebar.
  sidebar: false # 在侧边栏就不建议了，默认false即可
  # Scroll percent label in b2t button.
  scrollpercent: false # 显示滚动的百分比，根据个人喜好

# Reading progress bar
reading_progress: # 阅读进度条，这里建议默认
  enable: false
  # Available values: top | bottom
  position: top
  color: "#37c6c0"
  height: 3px

# Bookmark Support
bookmark: # 书签，如果开启，则下一次使用的时候就会从你上次浏览的地方显示，改为 true 即可
  enable: false
  # Customize the color of the bookmark.
  color: "#222"
  # If auto, save the reading progress when closing the page or clicking the bookmark-icon.
  # If manual, only save it by clicking the bookmark-icon.
  save: auto

# `Follow me on GitHub` banner in the top-right corner.
github_banner: # 在右上角的 github 图标处，点击进入自己的github账户，建议自己有开源的项目可以开启，也是一个宣传自己的机会
  enable: false
  permalink: https://github.com/yourname
  title: Follow me on GitHub
复制代码
```

字体设置部分
------

```
# ---------------------------------------------------------------
# Font Settings
# See: https://theme-next.org/docs/theme-settings/#Fonts-Customization
# ---------------------------------------------------------------
# Find fonts on Google Fonts (https://www.google.com/fonts)
# All fonts set here will have the following styles:
#   light | light italic | normal | normal italic | bold | bold italic
# Be aware that setting too much fonts will cause site running slowly
# ---------------------------------------------------------------
# To avoid space between header and sidebar in scheme Pisces / Gemini, Web Safe fonts are recommended for `global` (and `title`):
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------

font: # 这一部分是字体设置，如果字体是false，即表示不适用外部字体，使用的是 next 主题默认字体
      # 如果对默认字体感到不合适，可以修改，选择自己找到的字体库，添加链接就可,但是要确保能够访问，
      # 比如谷歌字体库在大陆就无法访问，即使你使用科学上网可以获得资源，但是不能保证你的访问用户能够顺利看到，
      # 关于字体的详细设置请看下面的字体设置篇
  enable: false

  # Uri of fonts host, e.g. //fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # Global font settings used for all elements inside <body>.
  global:
    external: true
    family: Lato
    size:

  # Font settings for site title (.site-title).
  title:
    external: true
    family:
    size:

  # Font settings for headlines (<h1> to <h6>).
  headings:
    external: true
    family:
    size:

  # Font settings for posts (.post-body).
  posts:
    external: true
    family:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
复制代码
```

第三方插件
-----

### 数学公式加持

```
# ---------------------------------------------------------------
# Third Party Plugins & Services Settings
# See: https://theme-next.org/docs/third-party-services/
# You may need to install dependencies or set CDN URLs in `vendors`
# There are two different CDN providers by default:
#   - jsDelivr (cdn.jsdelivr.net), works everywhere even in China
#   - CDNJS (cdnjs.cloudflare.com), provided by cloudflare
# ---------------------------------------------------------------

# Math Formulas Render Support
math: # 数学公式插件，显示数学公式的插件，仅设置为 true 还不行，需要下载依赖插件
      # 可以选择两个引擎 mathjax / katex
  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front-matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support.
  mathjax:
    enable: false
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: false

  # hexo-renderer-markdown-it-plus (or hexo-renderer-markdown-it with markdown-it-katex plugin) required for full Katex support.
  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false

# Easily enable fast Ajax navigation on your website.
# Dependencies: https://github.com/theme-next/theme-next-pjax
pjax: false

# FancyBox is a tool that offers a nice and elegant way to add zooming functionality for images.
# For more information: https://fancyapps.com/fancybox
fancybox: false

# A JavaScript library for zooming images like Medium.
# Do not enable both `fancybox` and `mediumzoom`.
# For more information: https://github.com/francoischalifour/medium-zoom
mediumzoom: false

# Vanilla JavaScript plugin for lazyloading images.
# For more information: https://github.com/ApoorvSaxena/lozad.js
lazyload: false

# Pangu Support
# For more information: https://github.com/vinta/pangu.js
pangu: false

# Quicklink Support
# For more information: https://github.com/GoogleChromeLabs/quicklink
# Front-matter (unsupport home archive).
quicklink:  # 快链，我还没有尝试过，可以自己试试
  enable: false

  # Home page and archive page can be controlled through home and archive options below.
  # This configuration item is independent of `enable`.
  home: false
  archive: false

  # Default (true) will initialize quicklink after the load event fires.
  delay: true
  # Custom a time in milliseconds by which the browser must execute prefetching.
  timeout: 3000
  # Default (true) will enable fetch() or falls back to XHR.
  priority: true

  # For more flexibility you can add some patterns (RegExp, Function, or Array) to ignores.
  # See: https://github.com/GoogleChromeLabs/quicklink#custom-ignore-patterns
  ignores:
复制代码
```

### 评论功能

```
# ---------------------------------------------------------------
# Comments Settings
# See: https://theme-next.org/docs/third-party-services/comments
# ---------------------------------------------------------------
# next 主题支持几个评论插件 disqus | disqusjs |gitalk | livere | changyan(china) | valine(china) | 
# 而且同时支持多个评论系统
# 具体的请看我所配置 valine 方法
# Multiple Comment System Support
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: changyan | disqus | disqusjs | gitalk | livere | valine
  active:
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any navs, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2

# Disqus
disqus:
  enable: false
  shortname:
  count: true
  #post_meta_order: 0

# DisqusJS
# Alternative Disqus - Render comment component using Disqus API.
# Demo: https://suka.js.org/DisqusJS/
# For more information: https://github.com/SukkaW/DisqusJS
disqusjs:
  enable: false
  # API Endpoint of Disqus API (https://disqus.com/api/).
  # Leave api empty if you are able to connect to Disqus API. Otherwise you need a reverse proxy for it.
  # For example:
  # api: https://disqus.skk.moe/disqus/
  api:
  apikey: # Register new application from https://disqus.com/api/applications/
  shortname: # See: https://disqus.com/admin/settings/general/

# Changyan
changyan:
  enable: false
  appid:
  appkey:
  #post_meta_order: 0

# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
  enable: false
  appid: # Your leancloud application appid
  appkey: # Your leancloud application appkey
  notify: false # Mail notifier
  verify: false # Verification code
  placeholder: Just go go # Comment box placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
  language: # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  recordIP: false # Whether to record the commenter IP
  serverURLs: # When the custom domain name is enabled, fill it in here (it will be detected automatically by default, no need to fill in)
  #post_meta_order: 0

# LiveRe comments system
# You can get your uid from https://livere.com/insight/myCode (General web site)
livere_uid: # <your_uid>

# Gitalk
# For more information: https://gitalk.github.io, https://github.com/gitalk/gitalk
gitalk:
  enable: false
  github_id: # GitHub repo owner
  repo: # Repository name to store issues
  client_id: # GitHub Application Client ID
  client_secret: # GitHub Application Client Secret
  admin_user: # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # Gitalk's display language depends on user's browser or system environment
  # If you want everyone visiting your site to see a uniform language, you can set a force language value
  # Available values: en | es-ES | fr | ru | zh-CN | zh-TW
  language:
复制代码
```

### 文章评价功能

```
# ---------------------------------------------------------------
# Post Widgets & Content Sharing Services
# See: https://theme-next.org/docs/third-party-services/post-widgets
# ---------------------------------------------------------------
# next 主题支持两个评估系统： Widgetpack Rating 和 AddThis
# Star rating support to each article.
# To get your ID visit https://widgetpack.com
rating: # rating 插件设置
  enable: false
  id:     # <app_id>
  color:  fc6423

# AddThis Share. See: https://www.addthis.com
# Go to https://www.addthis.com/dashboard to customize your tools.
add_this_id: # AddThis 插件设置
复制代码
```

### 文章统计和分析功能

```
#  next 主题支持许多的统计和分析插件，用于统计站点浏览量文章浏览数等等
# 包括有 google_analytics baidu_analytics cnzz leancloud firesrtore 以及最常使用的卜算子
# 这一部分只需要现在是干什么的就可以，具体的配置过程见下一篇博客

# ---------------------------------------------------------------
# Statistics and Analytics
# See: https://theme-next.org/docs/third-party-services/statistics-and-analytics
# ---------------------------------------------------------------

# Google Analytics 谷歌统计设置
google_analytics: 
  tracking_id: # <app_id>
  # By default, NexT will load an external gtag.js script on your site.
  # If you only need the pageview feature, set the following option to true to get a better performance.
  only_pageview: false

# Baidu Analytics # 百度统计设置
baidu_analytics: # <app_id>

# Growingio Analytics
growingio_analytics: # <project_id>

# CNZZ count CNZZ的设置
cnzz_siteid:

# Show number of visitors of each article.
# You can visit https://leancloud.cn to get AppID and AppKey.
# AppID and AppKey are recommended to be the same as valine's for counter compatibility.
# Do not enable both `valine.visitor` and `leancloud_visitors`.
leancloud_visitors: # leancloud插件设置
  enable: false
  app_id: # <app_id>
  app_key: # <app_key>
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true
  betterPerformance: false

# Another tool to show number of visitors to each article.
# Visit https://console.firebase.google.com/u/0/ to get apiKey and projectId.
# Visit https://firebase.google.com/docs/firestore/ to get more information about firestore.
firestore: # firestore设置
  enable: false
  collection: articles # Required, a string collection name to access firestore database
  apiKey: # Required
  projectId: # Required

# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count: # 卜算子
  enable: false
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye

复制代码
```

### 站内搜索功能

```
# ---------------------------------------------------------------
# Search Services
# See: https://theme-next.org/docs/third-party-services/search-services
# ---------------------------------------------------------------

# next 主题支持两种站内搜索插件 algolia_search 和 local_search(比较常用);
# local_search 的具体配置见下一篇博客内容

# Algolia Search
# For more information: https://www.algolia.com
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: false
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false

# Swiftype Search API Key
swiftype_key:
复制代码
```

### 站内即时聊天功能

```
# ---------------------------------------------------------------
# Chat Services
# See: https://theme-next.org/docs/third-party-services/chat-services
# ---------------------------------------------------------------

# next 主题支持在线聊天服务，支持两个插件 charta 和 tidioA,这一部分自认为没有必要，所以我也没有配置

# Chatra Support
# See: https://chatra.io
# Dashboard: https://app.chatra.io/settings/general
chatra: # charta 插件设置
  enable: false
  async: true
  id: # Visit Dashboard to get your ChatraID
  #embed: # Unfinished experimental feature for developers. See: https://chatra.io/help/api/#injectto

# Tidio Support
# See: https://www.tidiochat.com
# Dashboard: https://www.tidiochat.com/panel/dashboard
tidio: # tidio 插件设置
  enable: false
  key: # Public Key, get it from dashboard. See: https://www.tidiochat.com/panel/settings/developer
复制代码
```

### 标签插件

```
# ---------------------------------------------------------------
# Tags Settings
# See: https://theme-next.org/docs/tag-plugins/
# ---------------------------------------------------------------

# 标签插件和 Front-matter 中的标签不同，它们是用于在文章中快速插入特定内容的插件。
# 这一部分的内容还是挺有意思的，可以尝试学习学习，具体的使用方法我会在后面的使用篇具体讲解;
# 现在详细的介绍以及效果演示可以看中文官方文档 (https://hexo.io/zh-cn/docs/tag-plugins)

# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  transition:
    tabs: false
    labels: true

# PDF tag, requires two plugins: pdfObject and pdf.js
# pdfObject will try to load pdf files natively, if failed, pdf.js will be used.
# The following `cdn` setting is only for pdfObject, because cdn for pdf.js might be blocked by CORS policy.
# So, you must install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# See: https://github.com/theme-next/theme-next-pdf
pdf:
  enable: false
  # Default height
  height: 500px

# Mermaid tag
mermaid:
  enable: false
  # Available themes: default | dark | forest | neutral
  theme: forest
复制代码
```

### 动画设置部分

```
# ---------------------------------------------------------------
# Animation Settings
# ---------------------------------------------------------------
# 这一部分主要是使用页面动画设置
# Use velocity to animate everything.
# For more information: http://velocityjs.org
motion: # 第一部分主要是使用 velocity 引擎实现的界面动态的效果，默认就好
        # 否则可能还需要学习一下 velocity
  enable: true
  async: false
  transition:
    # Transition variants:
    # fadeIn | flipXIn | flipYIn | flipBounceXIn | flipBounceYIn
    # swoopIn | whirlIn | shrinkIn | expandIn
    # bounceIn | bounceUpIn | bounceDownIn | bounceLeftIn | bounceRightIn
    # slideUpIn | slideDownIn | slideLeftIn | slideRightIn
    # slideUpBigIn | slideDownBigIn | slideLeftBigIn | slideRightBigIn
    # perspectiveUpIn | perspectiveDownIn | perspectiveLeftIn | perspectiveRightIn
    post_block: fadeIn
    post_header: slideDownIn
    post_body: slideDownIn
    coll_header: slideLeftIn
    # Only for Pisces | Gemini.
    sidebar: slideUpIn

# Progress bar in the top during page loading.
# Dependencies: https://github.com/theme-next/theme-next-pace
# For more information: https://github.com/HubSpot/pace
pace: # 文章加载时候显示的进度条，需要添加依赖(个人认为没有必要)
  enable: false
  # Themes list:
  # big-counter | bounce | barber-shop | center-atom | center-circle | center-radar | center-simple
  # corner-indicator | fill-left | flat-top | flash | loading-bar | mac-osx | material | minimal
  theme: minimal

# JavaScript 3D library.
# Dependencies: https://github.com/theme-next/theme-next-three
three: # javaScript 的3D库，同样需要添加依赖库文件，我也没有设置
  enable: false
  three_waves: false
  canvas_lines: false
  canvas_sphere: false

# Canvas-nest
# Dependencies: https://github.com/theme-next/theme-next-canvas-nest
# For more information: https://github.com/hustcc/canvas-nest.js
canvas_nest:
  enable: false
  onmobile: true # Display on mobile or not
  color: "0,0,255" # RGB values, use `,` to separate
  opacity: 0.5 # The opacity of line: 0~1
  zIndex: -1 # z-index property of the background
  count: 99 # The number of lines

# Canvas-ribbon
# Dependencies: https://github.com/theme-next/theme-next-canvas-ribbon
# For more information: https://github.com/zproo/canvas-ribbon
canvas_ribbon:
  enable: false
  size: 300 # The width of the ribbon
  alpha: 0.6 # The transparency of the ribbon
  zIndex: -1 # The display level of the ribbon
复制代码
```