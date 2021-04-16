> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [kuroha.vip](https://kuroha.vip/hexo/hexo_update.html#%E9%BC%A0%E6%A0%87%E5%8F%B3%E9%94%AE%E8%8F%9C%E5%8D%95-GalMenu)

  

Hexo 3.9.0 + NexT 7.2.0 => Hexo 5.1.0 + NexT 8.0.0
==================================================

发表于 2020-08-28 更新于 2021-02-05 分类于 [Hexo](/categories/Hexo/)  
本文字数： 13k 阅读时长 ≈ 12 分钟 一个 warning 引发的惨案!

[](#🏳‍🌈惨案 "🏳‍🌈惨案")🏳‍🌈惨案
=============================

一个 Warning 引发的惨案!

[](#升级方式 "升级方式")升级方式
====================

全新安装, 因为我不会升级啊~~😂

[](#安装-Git "安装 Git")安装 Git
--------------------------

进入 [Git 官方网站](https://git-scm.com/) 下载安装.

可以使用 `git --version` 进行验证, 出现版本号就说明成功了.

[](#安装-Nodejs "安装 Nodejs")安装 Nodejs
-----------------------------------

进入 [Nodejs 官方网站](https://nodejs.org/en/) 下载安装.

尽量选择安装长期支持版本 (LTS), 最新发布版可能会有警告, 甚至有错误发生!

可以使用 `node -v` 和 `npm -v` 进行验证, 出现版本号就说明成功了.

[](#安装-Hexo "安装 Hexo")安装 Hexo
-----------------------------

安装 Hexo 之前, 设置 Hexo 的安装位置. 具体见我的另一篇博客: [Hexo + Github Pages 搭建个人博客](https://kuroha.vip/hexo/hexo_blog.html) 这里不再赘述!

安装 Hexo: **`npm install hexo-cli -g`**

[](#创建本地博客 "创建本地博客")创建本地博客
--------------------------

1.  新建文件夹, 放置本地博客, 名称随意. `F:\WorkSpace\Hexo`
    
2.  初始化本地博客, 在 Git Bash Here 中输入: `hexo init`
    

[**注**] **此步骤需要耗费较长一段时间, 我大概用了 25 分钟! 慢慢等吧!**

> `hexo init` 是这次升级遇到的第一个大坑, 忘记了这个要执行好长一段时间, 好几次自己等不耐烦了, 直接 `Ctrl + C` 了! 😂

3.  安装默认依赖包, 在 Git Bash Here 中输入: `npm install`

[**注**] 在上一步中大部分的依赖其实已经安装了, 这里只是安装一小部分, 所以很快!

4.  生成静态文件, 在 Git Bash Here 中输入: `hexo generate`
    
5.  开启服务, 在 Git Bash Here 中输入 `hexo server`
    

[](#部署-Hexo "部署 Hexo")部署 Hexo
-----------------------------

1.  安装 Hexo deploy 插件, 在 Git Bash Here 中输入: `npm install hexo-deployer-git --no-optional`
    
2.  在站点配置文件中配置:
    

```
deploy:
  type: git
  repo: git@github.com:KurohaKirito/KurohaKirito.github.io.git
  branch: master
```

[**注**] repo 仓库的地址: 有 SSH 和 HTTPS 两种格式, 推荐选择 SSH 格式, 如果选择 Https 格式, 每次发布时都必须输入账号密码, 不嫌麻烦的可以用!

[](#安装-NexT-主题 "安装 NexT 主题")安装 NexT 主题
--------------------------------------

> 这里是第二个大坑, 最新版的 NexT 的仓库已经换地址了, 我还傻乎乎地用之前的地址, 唉...😔

*   2014-2017 => [https://github.com/iissnan/hexo-theme-next](https://github.com/iissnan/hexo-theme-next)
    
*   2018-2019 => [https://github.com/theme-next/hexo-theme-next](https://github.com/theme-next/hexo-theme-next)
    
*   2020-2020 => [https://github.com/next-theme/hexo-theme-next](https://github.com/next-theme/hexo-theme-next)
    

> 新版的 NexT 推荐使用 `npm install hexo-theme-next --no-optional` 进行安装, 作为一个 node_module 存在! 安装之后路径为: node_module/hexo-theme-next.

> 新版的 NexT 推荐用户不要修改主题目录下的配置文件, 而是在站点根目录下新建一个 **_config[. 主题名称].yml** 文件, 作为新的主题配置文件.

[![](https://kuroha.vip/images/hexo_update/next_theme_config.png)](/images/hexo_update/next_theme_config.png "next_theme_config")

[next_theme_config](/images/hexo_update/next_theme_config.png "next_theme_config")

可以先从 node_module/hexo-theme-next 文件夹中复制一份配置文件出来, 然后按照规则重命名, 最后修改其中的设置即可!

[](#自定义站点配置文件 "自定义站点配置文件")自定义站点配置文件
===================================

[](#主题 "主题")主题
--------------

修改 theme 的值为 next, 这里的名字要和之前新建主题配置文件时使用的名称一致!

[](#博客网址样式 "博客网址样式")博客网址样式
--------------------------

```
permalink: :title.html
```

[](#关闭-quot-半角字符自动转换全角字符-quot "关闭 "半角字符自动转换全角字符"")关闭 "半角字符自动转换全角字符"
-------------------------------------------------------------------

```
marked:
  smartypants: false
```

[](#生成站点地图-谷歌版 "生成站点地图 (谷歌版)")生成站点地图 (谷歌版)
------------------------------------------

1.  安装依赖 `hexo-generator-sitemap`, 命令: `npm install hexo-generator-sitemap --no-optional`, 之后生成网站时, 便会自动在根目录生成一个 `sitemap.xml` 文件!
    
2.  在 source 文件夹下新建文本文件: `robots.txt`, 并写入以下内容:
    

```
User-agent: *
Disallow:
Sitemap: https://kuroha.vip/sitemap.xml
```

*   *   `User-agent` : 定义以下配置对哪些搜索引擎生效.
*   *   `Allow` : 允许抓取的内容.
*   *   `Disallow` : 不允许抓取的内容.
*   *   `Sitemap` : 站点地图的存放地址.

重新发布之后, 便可以将站点地图提交给 Google Search 了!

[](#自定义主题配置文件 "自定义主题配置文件")自定义主题配置文件
===================================

配置文件中只需要改改设置就可以出现效果的就不提了, 说一下注意事项:

[](#开启自定义配置 "开启自定义配置")开启自定义配置
-----------------------------

取消自定义配置文件的注释, 并且要在对应的路径下创建对应的文件.

[](#开启标签-分类-关于菜单 "开启标签, 分类, 关于菜单")开启标签, 分类, 关于菜单
------------------------------------------------

取消相应的设置选项后, 必须在 `source` 文件夹下创建相应的路径, 并创建相应的 markdown 文件, 文件中的内容虽然很简单, 但是也必须添加! `comments : false` 可以使当前页面禁用评论系统.

### [](#分类 "分类")分类

```
---
type: "categories"
comments: false
---
```

### [](#标签 "标签")标签

```
---
type: "tags"
comments: false
---
```

[](#设置-Favicon-图标 "设置 Favicon 图标")设置 Favicon 图标
-----------------------------------------------

在 favicon 属性后设置路径之后, 必须在相应的路径下创建图片, 否则找不到文件会报错! 设置侧边栏头像时同理.

[](#添加预计阅读时间功能 "添加预计阅读时间功能")添加预计阅读时间功能
--------------------------------------

需要安装依赖: [hexo-word-counter](https://github.com/next-theme/hexo-word-counter)

`npm install hexo-word-counter --no-optional`

[**注**] 所有需要安装依赖才能出现效果的, 安装完依赖并设置好之后, 必须清理缓存重新生成才会生效!

[**注**] 某些特效需要关闭新版 NexT 中的 Pjax

[](#关闭最受欢迎文章功能 "关闭最受欢迎文章功能")关闭最受欢迎文章功能
--------------------------------------

NexT 中有这么一个设置: related_posts, 可以当作 "最近受欢迎的文章", "相关博客" 或者 "推荐阅读" 使用, 但是由于其依赖有点过时, 推荐关闭此功能!

[](#代码高亮风格设置 "代码高亮风格设置")代码高亮风格设置
--------------------------------

如果使用 `Prism` 进行代码高亮渲染, 并且选择较高级的一些效果, 需要安装依赖.

`npm install prism-themes --no-optional`

并且要在 **站点配置文件** 中将 highlight 设为 false, prismjs 设为 true.

```
highlight:
  enable: false
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: true
  preprocess: true
  line_number: true
  tab_replace: ''
```

最后在 **主题配置文件** 的 prism 后设置使用的渲染风格.

[](#本地搜索 "本地搜索")本地搜索
--------------------

需要安装依赖: [hexo-generator-searchdb](https://github.com/next-theme/hexo-generator-searchdb)

`npm install hexo-generator-searchdb --no-optional`

[](#音乐播放器-APlayer "音乐播放器 APlayer")音乐播放器 APlayer
-----------------------------------------------

> APlayer 源码地址: [APlayer](https://github.com/MoePlayer/APlayer)

新建目录: `source/js/aplayer`, 下载并解压源码, 将 `dist` 文件夹中的四个文件复制到 `source/js/aplayer` 中.

返回 `source/js` 文件夹, 新建一个 `fixedAplayer.js` 文件, 输入以下代码:

```
const ap = new APlayer({
    container: document.getElementById('aplayer'),
    fixed: true,
    autoplay: false,
    audio: [
      {
        name: '歌曲的名字',
        artist: '歌手',
        url: '音乐文件的地址',
        cover: '封面图片的地址',
      }
    ]
});
```

之后在 `source/_data/body-end.njk` 中添加:

```
<!--APlayer 吸底式音乐播放功能-->
{% if theme.aplayer_fixed %}
    <link rel="stylesheet" href="/js/aplayer/APlayer.min.css">
    <div></div>
    <script type="text/javascript" src="/js/aplayer/APlayer.min.js"></script>
    <script type="text/javascript" src="/js/fixedAplayer.js"></script>
{% endif %}
```

最后在 **主题配置文件** 中写入 `aplayer_fixed: true`.

[](#视频播放器-DPlayer "视频播放器 DPlayer")视频播放器 DPlayer
-----------------------------------------------

> DPlayer 源码地址: [DPlayer](https://github.com/MoePlayer/DPlayer)

新建目录: `source/js/dplayer`, 下载并解压源码, 将 `dist` 文件夹中的四个文件复制到 `source/js/dplayer` 中.

在待添加视频博客的所需位置中添加以下代码:

```
<div></div>
<script src="/js/dplayer/DPlayer.min.js"></script>

<script>
const dp_update = new DPlayer({
    container: document.getElementById('dplayer'),
    screenshot: true,
    video:
    {
        url: '/video/hexo_update/hexo_update.mp4', //视频文件
        pic: '/video/hexo_update/hexo_update.jpg', //视频封面
    },
});
</script>
```

[](#自定义单行代码段样式 "自定义单行代码段样式")自定义单行代码段样式
--------------------------------------

打开 `source/_data/styles.styl` 文件, 添加对 `Code` 标签的自定义配置即可. 下面是我博客使用的配置.

```
// 单行代码块 的自定义样式
code {
    margin: 0px 0px;             // 外边距
    border: 2px solid #00000099; // 边框厚度, 边框样式, 边框颜色
    border-radius: 0px;          // 边框圆润度
    color: #d0104c;              // 代码颜色
}
```

[](#添加捉小猫游戏 "添加捉小猫游戏")添加捉小猫游戏
-----------------------------

1.  下载捉小猫游戏源文件并解压, 之后将解压好的文件夹 `source` 和博客目录下的 `source` 文件夹合并. [Catch The Cat](https://od.lk/d/NzNfMjczNjY3MThf/catch_the_cat.7z)
    
2.  在主题配置文件的 menu 处添加新菜单项: 捉小猫! 仅需两步, 大功告成!
    

```
menu:
  捉小猫: /catch_the_cat/ || fa fa-cat
```

[](#鼠标右键菜单-GalMenu "鼠标右键菜单 GalMenu")鼠标右键菜单 GalMenu
--------------------------------------------------

1.  下载 GalMenu 源文件并解压, 之后将解压好的文件夹 `galmenu` 放到博客的 `source/js` 文件夹下. [GalMenu 下载链接](https://od.lk/d/NzNfMjczNjY3MThf/catch_the_cat.7z) 解压密码: `https://kuroha.vip/`
    
2.  在主题配置文件 `_config.next.yml` 中添加配置.
    

```
galmenu:
  enable: true # 动漫菜单
  audio: true # 菜单音效
```

3.  在 `source/_data/body-end.njk` 文件中添加配置.
    
    [**注**] 在这里可以自定义菜单项名称, 而且在 audio 标签中可以自定义音效文件名称, 建议不要修改路径. 修改名称后记得一定要在 `source/js/galmenu/audio` 文件夹中放入自定义的音效资源.
    

```
<!--动漫菜单-->
{% if theme.galmenu.enable %}
    <div>
        <div>
            <div>
                <a href="/">首页</a>
                <a href="javascript:history.go(1);">前进</a>
                <a href="javascript:$('html,body').animate({scrollTop:0},500);">顶部</a>
                <a href="javascript:location.reload();">刷新</a>
                <a href="/about/">留言</a>
                <a href="javascript:history.go(-1);">后退</a>
            </div>
            {% if theme.galmenu.audio %}
                <audio src="../js/galmenu/audio/sao-menu.wav"></audio>
            {% endif %}
        </div>
    </div>
    <script type="text/javascript">
        var items = document.querySelectorAll('.menuItem');
        for (var i = 0, l = items.length; i < l; i++) {
            items[i].style.left = (50 - 35 * Math.cos(- 0.5 * Math.PI - 2 * (1 / l) * i * Math.PI)).toFixed(4) + "%";
            items[i].style.top = (50 + 35 * Math.sin(- 0.5 * Math.PI - 2 * (1 / l) * i * Math.PI)).toFixed(4) + "%"
        }
    </script>
    <script>
        window.jQuery || document.write('<script src="../js/galmenu/js/jquery.min.js"><\/script>')
    </script>
    <script src="../js/galmenu/js/GalMenu.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            $('body').GalMenu({'menu': 'GalDropDown'})
        });
    </script>
{% endif %}
```

3.  在 `source/_data/head.njk` 文件内添加 CSS 引用.
    
    [**注**] 在这个 CSS 文件中可以修改菜单图片的文件名, 建议不要修改路径. 修改名称后记得一定要在 `source/js/galmenu/img` 文件夹中放入自定义的图片资源.
    

```
<!--动漫菜单-->
{% if theme.galmenu.enable %}
    <link rel="stylesheet" href="../js/galmenu/css/GalMenu.css">
{% endif %}
```

至此大功告成!

[](#鼠标单击之心形图案特效 "鼠标单击之心形图案特效")鼠标单击之心形图案特效
-----------------------------------------

在 `source/js` 下创建 `love.js` 文件, 内容具体见我的另一篇博客: [Hexo + NexT 主题美化 (NexT v7.2.0)](https://kuroha.vip/hexo/next_theme_beautify.html) 这里不再赘述!

之后在 `source/_data/body-end.njk` 中添加:

```
<!--心形图案效果-->
{% if theme.love %}
  <script type="text/javascript" src="/js/love.js"></script>
{% endif %}
```

最后在 **主题配置文件** 中写入 `love: true`.

[](#鼠标单击之烟花爆炸特效 "鼠标单击之烟花爆炸特效")鼠标单击之烟花爆炸特效
-----------------------------------------

1.  下载 `fireworks.js` 文件到 `source/js` 文件夹下
    
2.  在 `source/_data/body-end.njk` 中添加:
    

```
<!--烟花爆炸特效-->
{% if theme.fireworks %}
    <canvas></canvas>
    <script type="text/javascript" src="/js/fireworks.js"></script>
{% endif %}
```

3.  在 **主题配置文件** 中写入 `fireworks: true`.

**下载地址:** [fireworks.7z](https://od.lk/d/NzNfMjUzMDkxMjdf/fireworks.7z), 解压密码是: `https://kuroha.vip/`.

[**注**] 都读到这里了, 我想你肯定早就知道了, 想要获取文章中提到的所有资源文件, 只要 F12 就可以了! 😂 当然我还是提供了下载地址的...

[](#页面标题欺诈 "页面标题欺诈")页面标题欺诈
--------------------------

在 `source/js` 下创建 `crash_cheat.js` 文件, 内容具体见我的另一篇博客: [Hexo + NexT 主题美化 (NexT v7.2.0)](https://kuroha.vip/hexo/next_theme_beautify.html) 这里不再赘述!

之后在 `source/_data/body-end.njk` 中添加:

```
<!--崩溃欺骗-->
{% if theme.crashcheat %}
  <script type="text/javascript" src="/js/crash_cheat.js"></script>
{% endif %}
```

最后在 **主题配置文件** 中写入 `crashcheat: true`.

[](#球形标签云 "球形标签云")球形标签云
-----------------------

球形标签云其实就是用这个插件 [TagCanvas](https://www.goat1000.com/tagcanvas.php) 实现的, 点击进入官网.

进入官网后下载 [tagcanvas.js](https://www.goat1000.com/tagcanvas.js) 文件, 也可以直接在左面我给出的链接那里 "右键 => 链接另存为", 保存到: `source\js` 目录下. 需要的就是这一个 `tagcanvas.js` 文件!

打开 `source/js` 文件夹中再新建一个 `tagcloud.js` 文件, 写入以下内容:

```
window.onload = function () {
    try {
        TagCanvas.Start('my3DTags', 'tags',
            {
                textFont: 'Georgia,Optima',
                textColour: null,
                outlineColour: 'black',
                weight: true,
                reverse: true,
                depth: 0.8,
                maxSpeed: 0.05,
                bgRadius: 1,
                freezeDecel: true
            });
    }
    catch (e) {
        document
            .getElementById('myTags')
            .style
            .display = 'none';
    }
};
```

[**题外话**] 新版的 NexT 推荐用户不要再修改主题目录中的任何文件, 虽然我是一个前端纯小白, 但是我也在尽力去遵守这条约定, 但是我发现如果我想要实现这个标签云, 就必须修改主题目录中的文件! 如果有人知道可以不修改主题目录中的文件便可以实现相同的效果, 请务必告知, 十分感谢!

打开文件 `node_modules\hexo-theme-next\layout\page.njk`, 在这个 `<div>` 的前面加上如下代码:

```
{# 球形云标签 #}
<div>
  <canvas width="720" height="720">
  </canvas>
</div>
<div>
  <ul>
    {{ tagcloud({
        min_font   : 16,
        max_font   : 35,
        amount     : 999,
        color      : true,
        start_color: 'black',
        end_color  : 'green'
      })
    }}
  </ul>
</div>
<script type="text/javascript" src="/js/tagcanvas.js"></script>
<script type="text/javascript" src="/js/tagcloud.js"></script>
{# 普通云标签 #}
</script>
```

最后在 **主题配置文件** 中写入 `crashcheat: true`.`tagcanvas: true`.

> [**注**] 球形标签云也可以使用 Hexo 的插件 `hexo-tag-cloud` 来实现, 其实最终都是依赖于 `tagcanvas.js` 文件的, 而且我尝试 `hexo-tag-cloud` 后发现我不会改效果...😂 所以还是用了之前的老方法!
> 
> 另外, 执行上面的操作后, 球形标签云和普通标签云是同时存在的, 如果只想要显示球形标签云, 把后面那个 `普通云标签` 的 `div` 标签注释掉就行了. 就像这样:

```
{# 普通云标签 #}
{# <div>
    {{ tagcloud({
      min_font: theme.tagcloud.min,
      max_font: theme.tagcloud.max,
      amount  : theme.tagcloud.amount,
      orderby : theme.tagcloud.orderby,
      order   : theme.tagcloud.order,
      class   : 'tag-cloud'
      })
    }}
  </div> #}
```

[](#粒子时钟 "粒子时钟")粒子时钟
--------------------

下载文件 [clock.js](https://kuroha.vip/js/clock.js), 可以直接在链接上 "右键 => 链接另存为", 放到 `source/js/` 路径下.

之后在 `source/_data/sidebar.njk` 中添加:

```
{# 粒子时钟 #}
{% if theme.clock %}
    <div>
        <canvas>您的浏览器不支持 Canvas, 请更换浏览器!</canvas>
        <script type="text/javascript" src="/js/clock.js"></script>
    </div>
{% endif %}
```

最后在 **主题配置文件** 中写入 `clock: true`.

[](#站点运行时间 "站点运行时间")站点运行时间
--------------------------

下载文件 [website_runtime.js](https://kuroha.vip/js/website_runtime.js), 可以直接在链接上 "右键 => 链接另存为", 放到 `source/js/` 路径下.

之后在 `source/_data/footer.njk` 中添加:

```
{# 站点已运行时间 #}
{% if theme.websiteruntime %}
    <div></div>
    <script type="text/javascript" src="/js/website_runtime.js"></script>
{% endif %}
```

最后在 **主题配置文件** 中写入 `websiteruntime: true`.

[](#萌萌的看板娘 "萌萌的看板娘")萌萌的看板娘
--------------------------

*   第一种: `hexo-helper-live2d` 优点: 有声音, 缺点: 无法换装, 无法换模型, 响应事件少.

使用方法见官方网址: [hexo-helper-live2d](https://github.com/EYHN/hexo-helper-live2d)

*   第二种: `live2d-widget` 优点: 能换装, 能切换模型, 响应事件多, 缺点: 无声音, 配置较复杂. (现在可能已经有声音了)

使用方法见官方网址: [live2d-widget](https://github.com/stevenjoezhang/live2d-widget)

*   第三种: `live2d_demo` 优点: 能换装, 能切换模型, 响应事件多, 缺点: 无声音, 配置较复杂. (现在可能已经有声音了)

使用方法见官方网址: [live2d_demo](https://github.com/fghrsh/live2d_demo)

我是用的是第 3 种 **live2d_demo**

1.  下载 `live2d_demo`: [live2d_demo](https://od.lk/d/NzNfMjUyNDc1NTJf/live2d_demo.7z), 解压密码是: `https://kuroha.vip/`
    
2.  解压之后放到 `source/js/` 目录下, 完成这一步之后, 在 `source/js/live2d_demo/` 目录下应该有 9 个文件.
    
3.  在 `source/_data/body-end.njk` 文件的最后添加:
    
    ```
    <!--萌萌看板娘-->
    {% if theme.live2d_demo %}
        <script type="text/javascript" src="/js/live2d_demo/jquery-ui.js"></script><!-- 实现拖动效果，需引入 JQuery UI -->
        <script type="text/javascript" src="/js/live2d_demo/autoload.js"></script><!-- 使用 autoload.js 自动引入看板娘 -->
    {% endif %}
    ```
    
4.  最后在 **主题配置文件** 中写入 `live2d_demo: true`, 启用看板娘!
    

[**注**]

1.  要定制自己的看板娘, 可以修改 `autoload.js` 中的参数配置, 还可以在 `waifu-tips.json` 中修改对话, 这两处的配置足够定制自己独特的看板娘了!
    
2.  经过以上操作如果还是不能达到效果, 请检查 `autoload.js` 中的路径设置是否正确! (虽然我已经配置好了, 可以直接拿来用, 不过既然出问题了, 就自己检查一下吧!)
    

[](#aplayer-音乐效果展示 "aplayer 音乐效果展示")aplayer 音乐效果展示
==================================================

  绯色之空 - 川田真美  00:00 / 00:00         

1.  1 绯色之空 川田真美
2.  2 光るなら Goose house

[](#dplayer-视频效果展示 "dplayer 视频效果展示")dplayer 视频效果展示
==================================================

<video src="https://kuroha.vip/video/hexo_update/hexo_update.mp4" control></video>

设置弹幕颜色                  设置弹幕类型   顶部    滚动    底部      0:00 / 01:40     速度  洗脑循环   显示弹幕   海量弹幕   弹幕透明度 0.5 0.75 正常 1.25 1.5 2   00:57 [x] Player version Player FPS Video type Video url Video resolution Video duration [视频统计信息](javascript:void(0);) [关于作者](https://diygod.me) [DPlayer v1.26.0](https://github.com/MoePlayer/DPlayer) 

咕噜咕噜~ 赞赏 ![](https://kuroha.vip/images/donate/alipay.png)

支付宝

*   **本文作者：** Kuroha
*   **本文链接：** [https://kuroha.vip/hexo/hexo_update.html](https://kuroha.vip/hexo/hexo_update.html "Hexo 3.9.0 + NexT 7.2.0 => Hexo 5.1.0 + NexT 8.0.0")
*   **版权声明：** 本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/zh_CN) 许可协议。转载请注明出处！

欢迎关注我的其它发布渠道

[Twitter](https://twitter.com/KurohaKirito) [Telegram](https://t.me/KurohaKirito) [WeChat](/images/followme/wechat.png) [RSS](/atom.xml)

[Hexo](/tags/Hexo/) [正则表达式](/program/regular_expression.html "正则表达式") [Oracle 全拼和首字母查询](/oracle/oracle_trigger.html "Oracle 全拼和首字母查询")