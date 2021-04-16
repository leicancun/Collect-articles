> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zealot.top](https://zealot.top/Hexo-Github%E6%90%AD%E5%BB%BA%E8%87%AA%E5%B7%B1%E7%9A%84%E5%8D%9A%E5%AE%A22.html)

[](#前言 "前言")前言
--------------

我这篇文章主要是讲解以 next 主题的各项具体设置，让自己的博客更加美化。（网上有很多关于 Next 主题的配置方法，我主要是把网上找到的各个设置做个汇总吧）

NexT 是一款简洁优雅且易于使用的主题，配置比较简单，只需要稍微修改配置文件即可，功能也比较全，分类、归档、标签显示明了，让人一看就知道干嘛的。

### [](#设置侧边栏设置圆形可旋转头像 "设置侧边栏设置圆形可旋转头像")设置侧边栏设置圆形可旋转头像

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo14.gif)](http://xmzcl.vicp.net:8089/images/blog_hexo14.gif)

设置方法：

找到生成的 Hexo 目录`themes/next/source/css_common/components/sidebar`下的`sidebar-author.styl`，将里面的 css 样式内容全部替换为：  

```
.site-author-image {
  margin: 0 auto;
  padding: $site-author-image-padding;
  max-width: $site-author-image-width;
  height: $site-author-image-height;
  border: $site-author-image-border-width solid $site-author-image-border-color;

  border-radius: 50%;
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  transition: 1.4s all;
}

.site-author-image:hover {
    -webkit-transform: rotate(360deg);
    -moz-transform: rotate(360deg);
    -ms-transform: rotate(360deg);
    -transform: rotate(360deg);
}

.site-author-name {
  margin: $site-author-name-margin;
  text-align: $site-author-name-align;
  color: $site-author-name-color;
  font-weight: $site-author-name-weight;
}

.site-description {
  margin-top: $site-description-margin-top;
  text-align: $site-description-align;
  font-size: $site-description-font-size;
  color: $site-description-color;
}
```

### [](#添加动态背景 "添加动态背景")添加动态背景

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo15.gif)](http://xmzcl.vicp.net:8089/images/blog_hexo15.gif)

设置方法：

打开生成的 Hexo 目录`themes/next/layout/_layout.swig`文件，  
在`</body>`上面添加代码 (注意不要放在`</head>`的后面)  

```
{% if theme.canvas_nest %}
<script type="text/javascript"
color="0,0,255" opacity='0.7' zIndex="-2" count="99" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```

配置项说明  
`color ：线条颜色, 默认: '0,0,0'；三个数字分别为(R,G,B)`  
`opacity: 线条透明度（0~1）, 默认: 0.5`  
`count: 线条的总数量, 默认: 150`  
`zIndex: 背景的z-index属性，css属性用于控制所在层的位置, 默认: -1`

然后打开主题配置文件，修改`canvas_nest`为`true`  

```
canvas_nest: true
```

### [](#点击出现桃心效果 "点击出现桃心效果")点击出现桃心效果

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo16.gif)](http://xmzcl.vicp.net:8089/images/blog_hexo16.gif)

设置方法：

在网址输入如下  
[http://7u2ss1.com1.z0.glb.clouddn.com/love.js](http://7u2ss1.com1.z0.glb.clouddn.com/love.js)  
然后将里面的代码 copy 一下，新建`love.js`文件并且将代码复制进去，然后保存。  
将`love.js`文件放到路径`themes/next/source/js/src`里面，然后打开`themes/next/layout/_layout.swig`文件, 在末尾（在前面引用会出现找不到的 bug）  
添加以下代码：  

```
<!-- 页面点击小红心 -->
<script type="text/javascript" src="/js/src/love.js"></script>
```

### [](#添加RSS "添加RSS")添加 RSS

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo17.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo17.jpg)

设置方法：  
执行以下命令安装 RSS 插件

```
npm install hexo-generator-feed --save
```

编辑网站根目录下的`_config.yml`，添加以下代码开启  

```
plugin:
- hexo-generator-feed
feed:
type: atom
path: atom.xml
limit: 20
```

### [](#字数统计 "字数统计")字数统计

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo19.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo19.jpg)

设置方法：  
安装统计插件

```
npm i --save hexo-wordcount
```

NexT 主题默认已经集成了文章【字数统计】、【阅读时长】统计功能，如果我们需要使用，只需要在主题配置文件`themes/next/_config.yml`中打开`wordcount`统计功能即可。如下所示：

```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true         # 单篇 字数统计
  min2read: true          # 单篇 阅读时长
  totalcount: false       # 网站 字数统计
  separated_meta: true
```

显示文字  
打开`post.swig`文件，路径：`themes/next/layout/_macro/post.swig`

修改【字数统计】，找到如下代码：

`<span title="{{ __('post.wordcount') }}">`  
`{{ wordcount(post.content) }}`  
`</span>`

添加`字`到`{{ wordcount(post.content)}}` 后面，修改后为：

`<span title="{{ __('post.wordcount') }}">`  
`{{ wordcount(post.content) }} 字`  
`</span>`

同理，我们修改【阅读时长】，修改后如下：

`<span title="{{ __('post.min2read') }}">`  
`{{ min2read(post.content) }} 分钟`  
`</span>`

### [](#修改-代码块自定义样式 "修改``代码块自定义样式")修改 `` 代码块自定义样式

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo20.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo20.jpg)

设置方法：  
打开`themes/next/source/css/_custom/custom.styl`, 向里面加入：(颜色可以自己定义)

```
// Custom styles.
code {
    color: #ff7600;
    background: #fbf7f8;
    margin: 2px;
}
// 大代码块的自定义样式
.highlight, pre {
    margin: 5px 0;
    padding: 5px;
    border-radius: 3px;
}
.highlight, code, pre {
    border: 1px solid #d6d6d6;
}
```

### [](#博文置顶 "博文置顶")博文置顶

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo21.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo21.jpg)

设置方法：  
首先安装插件：

```
npm uninstall hexo-generator-index --save
npm install hexo-generator-index-pin-top --save
```

然后在需要置顶的文章的`Front-matter`中加上`top: true`即可。比如下面这篇文章：

[![](http://xmzcl.vicp.net:8089/images/blog_hexo22.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo22.jpg)

置顶功能就完成了。

不过置顶的文章显示在最上面之后，如果没有明确的置顶标志，是不是感觉有点怪怪的呢？

设置置顶标志  
打开：`themes/next/layout/_macro`目录下的`post.swig`文件，定位到`<div>`标签下，插入如下代码：  

```
{% if post.top %}
  <i></i>
  <font color=7D26CD>置顶</font>
  <span>|</span>
{% endif %}
```

### [](#结尾添加“本文结束”标记 "结尾添加“本文结束”标记")结尾添加 “本文结束” 标记

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo23.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo23.jpg)

设置方法：  
在路径`themes/next/layout/_macro`中新建`passage-end-tag.swig`文件, 并添加以下内容：

```
<div>
    {% if not is_index %}
        <div>
            -------------本文结束
            <i></i>
            感谢您的阅读-------------
        </div>
    {% endif %}
</div>
```

接着打开`themes/next/layout/_macro/post.swig`文件，在`post-body`之后，`post-footer`之前添加如下代码,(大概在 350 行左右的位置)：  

```
<div>
  {% if not is_index %}
    {% include 'passage-end-tag.swig' %}
  {% endif %}
</div>
```

然后打开主题配置文件`_config.yml`, 在末尾添加：  

```
# 文章末尾添加“本文结束”标记
passage_end_tag:
  enabled: true
```

### [](#修改结尾-标签 "修改结尾#标签")修改结尾`#`标签

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo24.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo24.jpg)

设置方法：  
修改模板`themes/next/layout/_macro/post.swig`搜索`rel=”tag”`，将后面的`#`换成

```
<i></i>
```

### [](#修改文章内链接文本样式 "修改文章内链接文本样式")修改文章内链接文本样式

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo25.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo25.jpg)

设置方法：  
修改文件`themes/next/source/css/_common/components/post/post.styl`，在末尾添加如下`css`样式，：

```
// 文章内链接文本样式
.post-body p a{
  color: #0593d3;
  border-bottom: none;
  border-bottom: 1px solid #0593d3;
  &:hover {
    color: #fc6423;
    border-bottom: none;
    border-bottom: 1px solid #fc6423;
  }
}
```

其中选择`.post-body`是为了不影响标题，选择`p`是为了不影响首页 “阅读全文” 的显示样式, 颜色可以自己定义。

### [](#主页文章添加阴影效果 "主页文章添加阴影效果")主页文章添加阴影效果

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo26.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo26.jpg)

设置方法：  
打开`themes/next/source/css/_custom/custom.styl`, 在里面加入：

```
// 主页文章添加阴影效果
 .post {
   margin-top: 60px;
   margin-bottom: 60px;
   padding: 25px;
   -webkit-box-shadow: 0 0 5px rgba(202, 203, 203, .5);
   -moz-box-shadow: 0 0 5px rgba(202, 203, 204, .5);
  }
```

### [](#添加站内搜索 "添加站内搜索")添加站内搜索

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo27.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo27.jpg)

设置方法：  
安装`hexo-generator-searchdb`插件

```
npm install hexo-generator-searchdb --save
```

编辑`_config.yml`站点配置文件，新增以下内容到任意位置：  

```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

编辑`themes/next/_config.yml` 主题配置文件，启用本地搜索功能, 将`local_search:`下面的`enable:`的值，改成`true`  

```
# Local search
local_search:
  enable: true
```

### [](#首页不显示全文-只显示预览 "首页不显示全文(只显示预览)")首页不显示全文 (只显示预览)

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo28.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo28.jpg)

设置方法：  
打开主题配置文件`/themes/next/_config.yml`，将`auto_excerpt`下面的`enable:`的值，改成`true`

```
# Automatically Excerpt. Not recommand.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
enable: true
length: 150
```

除了这个方法，还有一个更灵活的方法，直接在编辑的文章中添加`<!--more-->`标记。这样只会显示`<!--more-->`标记之前的那部份。

### [](#添加顶部加载条 "添加顶部加载条")添加顶部加载条

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo17.gif)](http://xmzcl.vicp.net:8089/images/blog_hexo17.gif)

设置方法：  
打开`themes/next/_config.yml`主题配置文件，将`pace:`的值, 改成`true`  
还可以将`pace_theme:`的值，改成相应的名字, 变更不同样式的加载条。  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo29.png)](http://xmzcl.vicp.net:8089/images/blog_hexo29.png)

### [](#添加到百度统计 "添加到百度统计")添加到百度统计

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo30.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo30.jpg)

设置方法：  
首先你要去[百度统计](http://tongji.baidu.com/)注册个账号。

将安装代码复制到 github 上的`index.html`文件里面的`</head>`前面（大约在 150 行左右）  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo33.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo33.jpg)

[![](http://xmzcl.vicp.net:8089/images/blog_hexo32.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo32.jpg)

然后复制百度统计的`KEY`  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo31.png)](http://xmzcl.vicp.net:8089/images/blog_hexo31.png)

编辑文件`themes/next/_config.yml`，将`Baidu Analytics ID`下面的`baidu_analytics:`的值设置成百度统计的`KEY`

```
# Baidu Analytics ID
baidu_analytics: #百度统计的KEY
```

### [](#侧边栏推荐阅读 "侧边栏推荐阅读")侧边栏推荐阅读

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo34.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo34.jpg)

设置方法：  
编辑文件`themes/next/_config.yml`，找到`# Blog rolls`修改成下面的样子就 OK 了。(links 里面写你想要的链接):

```
# Blog rolls
links_icon: link
links_title: 推荐阅读
#links_layout: block
links_layout: inline
links:
  优设: http://www.uisdc.com/
  廖雪峰: https://www.liaoxuefeng.com/
  Web前端导航: http://www.alloyteam.com/nav/
  前端书籍资料: http://www.36zhen.com/t?id=3448
  百度前端技术学院: http://ife.baidu.com/
  google前端开发基础: http://wf.uisdc.com/cn/
```

### [](#生成sitemap文件 "生成sitemap文件")生成 sitemap 文件

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo35.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo35.jpg)

设置方法：  
首先安装相关插件：

```
npm install hexo-generator-sitemap --save
npm install hexo-generator-baidu-sitemap --save
npm install hexo-generator-seo-friendly-sitemap --save
```

注：根据个人喜欢选择合适插件即可

接着修改主题配置文件`themes/next/_config.yml`, 找到`menu:`将下面`sitemap`前面的`#`号去掉，再添加`baidusitemap: /baidusitemap.xml`  

```
menu:
  ......
  sitemap: /sitemap.xml    # 站点地图
  baidusitemap: /baidusitemap.xml
```

### [](#添加联系方式 "添加联系方式")添加联系方式

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo36.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo36.jpg)

设置方法：  
修改`themes/next/_config.yml`站点配置文件，找到`# Social Links`, 将`social:`下面对应的 ·`#`号去掉。

```
# Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, globe icon will be loaded.
social:
  GitHub: https://github.com/xmzcl || github
  E-Mail: mailto:18976787@qq.com || envelope
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype

social_icons:
  enable: true
  icons_only: false
  transition: false
```

注释：seoial_icons 节点中后面的值是 [http://fontawesome.io/icons/](http://fontawesome.io/icons/) 中提供的图标的名称。之后其他链接如推特，微博等都可自行增减。

### [](#添加打赏功能 "添加打赏功能")添加打赏功能

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo37.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo37.jpg)

设置方法：  
打开`themes/next/_config.yml`站点配置文件，找到`# Reward`把`wechatpay:`和`alipay:`前面的`#`号删除。然后将自己的二维码文件`wechatpay.jpg`、`alipay.jpg`图片放入`themes/next/source/images`中即可。

```
# Reward
reward_comment: 坚持原创技术分享，您的支持将鼓励我继续创作！
wechatpay: /images/wechatpay.jpg
alipay: /images/alipay.jpg
#bitcoin: /images/bitcoin.png
```

### [](#文章加密访问 "文章加密访问")文章加密访问

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo18.gif)](http://xmzcl.vicp.net:8089/images/blog_hexo18.gif)

设置方法：  
打开`themes/next/layout/_partials/head.swig`文件。  
在`<meta {{ theme.android_chrome_color }}">`下面插入代码：

```
<script>
    (function () {
        if ('{{ page.password }}') {
            if (prompt('请输入文章密码') !== '{{ page.password }}') {
                alert('密码错误！');
                if (history.length === 1) {
                    location.replace("http://xxxxxxx.xxx"); // 这里替换成你的首页
                } else {
                    history.back();
                }
            }
        }
    })();
</script>
```

然后在需要加密的文章头上添加`password:`标签字段，后面跟上你要设置的密码。如下图：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo38.png)](http://xmzcl.vicp.net:8089/images/blog_hexo38.png)

### [](#博客加上萌萌的宠物 "博客加上萌萌的宠物")博客加上萌萌的宠物

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo40.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo40.jpg)

设置方法：  
首先安装 live2d 插件

```
npm install -save hexo-helper-live2d
```

然后在在 hexo 的`_config.yml`主站配置文件中结尾处添加下面这些代码：  

```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  model:
    use: live2d-widget-model-wanko
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```

然后刷新一下 hexo 就可以看到效果了.  

```
hexo clean && hexo s
```

**下面这段是出于原创:**  
萌萌宠物网上找了好多资料, 发现没有一个能说清楚 live2d 是怎么配置和更换宠物的. 所以我在这里给大伙写一下我的经验.  
如果要变更宠物需要先安装他的插件包, 代码如下: [想知道有哪些宠物可以点这里](https://www.jianshu.com/p/832b3706cebe)  

```
npm install live2d-widget-model-z16
```

然后在`use: live2d-widget-model-wanko`这串代码中将`live2d-widget-model-wanko`变成你安装的宠物名字, 如刚才装的`live2d-widget-model-z16`  
再刷新一下 hexo 就可以看到效果了.  
`width:150`和`height:300`这二个是代表宠物的宽度和高度. 你可以自行设置. 也是要刷新 hexo 才可以看到效果.  
如果在手机上观看博客, 萌宠可能会影响观看. 将`mobile:`下面的`show:`的值`true`改成`false`之后, 在手机上就不会显示萌宠了.  

```
mobile:
   show: true
```

### [](#自定义鼠标样式 "自定义鼠标样式")自定义鼠标样式

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo41.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo41.jpg)

设置方法：  
打开`themes/next/source/css/_custom/custom.styl`, 在里面添加如下代码：

```
// 鼠标样式
  * {
      cursor: url("http://om8u46rmb.bkt.clouddn.com/sword2.ico"),auto!important
  }
  :active {
      cursor: url("http://om8u46rmb.bkt.clouddn.com/sword1.ico"),auto!important
  }
```

其中 url 里面必须是 ico 图片，ico 图片可以上传到网上，然后获取外链，复制到 url 里就行了。

小技巧：二个 ICO 图标可以设置成一大一小。这样点击起来，就会有动画效果了。

### [](#修改主题宽度 "修改主题宽度")修改主题宽度

设置原因：  
因为 next 默认的主题宽度觉得有点窄，想把他改宽一点, 比较好看. 所以就有了下面这个方法  
设置方法：  
在`themes/next/source/css/_schemes/Picses/_layout.styl`文件末尾添加如下代码:  

```
// 以下为新增代码！！
header{ width: 70% !important; }
header.post-header {
  width: auto !important;
}
.container .main-inner { width: 70%; }
.content-wrap { width: calc(100% - 260px); }

.header {
  +tablet() {
    width: auto !important;
  }
  +mobile() {
    width: auto !important;
  }
}

.container .main-inner {
  +tablet() {
    width: auto !important;
  }
  +mobile() {
    width: auto !important;
  }
}

.content-wrap {
  +tablet() {
    width: 100% !important;
  }
  +mobile() {
    width: 100% !important;
  }
}
```

### [](#显示阅读百分比 "显示阅读百分比")显示阅读百分比

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo44.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo44.jpg)

设置方法：  
打开`themes/next/_config.yml`主题配置文件, 找到`# Scroll percent label in b2t button`将`scrollpercent:`的值, 改成`true`

```
# Scroll percent label in b2t button
  scrollpercent: true
```

### [](#点击爆炸效果 "点击爆炸效果")点击爆炸效果

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo45.png)](http://xmzcl.vicp.net:8089/images/blog_hexo45.png)

设置方法：  
首先在`themes/next/source/js/src`里面建一个叫`fireworks.js`的文件，代码如下：

```
{% if theme.fireworks %}
   <canvas ></canvas> 
   <script type="text/javascript" src="//cdn.bootcss.com/animejs/2.2.0/anime.min.js"></script> 
   <script type="text/javascript" src="/js/src/fireworks.js"></script>
{% endif %}
```

再打开`themes/next/_config.yml`主题配置文件，在文件最后添加：  

```
# Fireworks
fireworks: true
```

### [](#隐藏网页底部-powered-By-Hexo-强力驱动 "隐藏网页底部 powered By Hexo / 强力驱动")隐藏网页底部 powered By Hexo / 强力驱动

设置方法：  
打开`themes/next/layout/_partials/footer.swig`，使用

隐藏符号之间的代码即可，或者直接将这段代码删除。  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo46.png)](http://xmzcl.vicp.net:8089/images/blog_hexo46.png)

### [](#设置分页显示 "设置分页显示")设置分页显示

设置方法  
打开`_config.yml`主站配置文件, 找到`index_generator:`, 设置成如下代码:  

```
index_generator:
  path: ''
  per_page: 6
  order_by: -date

archive_generator:
  per_page: 20
  yearly: true
  monthly: true

tag_generator:
  per_page: 10
```

说明:`index_generator:`是设置主页显示多少篇文章开始分页,`archive_generator:`是设置归档主页显示多少篇文章开始分页,`tag_generator:`是指底分页条显示多少个分页的链接.

### [](#取消Coding跳转页 "取消Coding跳转页")取消 Coding 跳转页

设置效果：  
取消下面这个跳转页面.  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo45.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo45.jpg)

设置方法：  
打开`themes/next/layout/_partials/footer.swig`文件。将下面的代码添加到如下图的位置.  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo47.png)](http://xmzcl.vicp.net:8089/images/blog_hexo47.png)

```
{% if theme.footer.powered and theme.footer.theme.enable %}
  <span>|</span>
{% endif %}

  <span>Hosted by <a href="https://pages.coding.me" >Coding Pages</a></span>
```

然后在 Coding 网站上, 勾选已放置 Hosted by Coding Pages  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo48.png)](http://xmzcl.vicp.net:8089/images/blog_hexo48.png)

### [](#加入valine在线评论 "加入valine在线评论")加入 valine 在线评论

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo46.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo46.jpg)

设置方法：  
首先要先去 [LeanCloud](https://leancloud.cn/) 注册一个帐号. 然后再创建一个应用.  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo48.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo48.jpg)

进入应用 -> 设置 -> 应用 key, 获取你的 appid 和 appkey 如图所示：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo47.jpg)](http://xmzcl.vicp.net:8089/images/blog_hexo47.jpg)

拿到`appid`和`appkey`之后，打开`themes/next/_config.yml`主题配置文件，查找`valine`，填入`appid` 和 `appkey`  
我的配置:

```
valine:
  enable: true
  appid:  your app id
  appkey: your app key
  notify: false # mail notifier , https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: ヾﾉ≧∀≦)o来啊，快活啊! 
  guest_info: nick,mail,link
  pageSize: 10
```

最后！记得在 Leancloud -> 设置 -> 安全中心 -> Web 安全域名 把你的域名加进去．

刷新一下~ 是不是就能看到评论框了？

### [](#压缩博客 "压缩博客")压缩博客

设置方法：  
运行下面的命令安装插件：  

```
npm install gulp -g
npm install gulp-minify-css gulp-uglify gulp-htmlmin gulp-htmlclean gulp --save
```

然后在博客根目录下新建一个`gulpfile.js`的文件, 输入下面的代码：  

```
var gulp = require('gulp');
var minifycss = require('gulp-minify-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
// 压缩 public 目录 css
gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss())
        .pipe(gulp.dest('./public'));
});
// 压缩 public 目录 html
gulp.task('minify-html', function() {
  return gulp.src('./public/**/*.html')
    .pipe(htmlclean())
    .pipe(htmlmin({
         removeComments: true,
         minifyJS: true,
         minifyCSS: true,
         minifyURLs: true,
    }))
    .pipe(gulp.dest('./public'))
});
// 压缩 public/js 目录 js
gulp.task('minify-js', function() {
    return gulp.src('./public/**/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 执行 gulp 命令时执行的任务
gulp.task('default', [
    'minify-html','minify-css','minify-js'
]);
```

对生成博客进行压缩就执行`hexo g && gulp`，就会根据`gulpfile.js`的配置，对博客进行压缩了。  

小技巧： linux 下可以, 将下面的代码添加到`~/.bashrc`文件的结尾。

代码：

```
alias up='hexo clean && hexo g && hexo d' #部署到网上
alias upg='hexo clean && hexo g && gulp && hexo d' #压缩后部署到网上
```

添加完后，刷新`~/.bashrc`文件。  

```
source ~/.bashrc
```

这样部署时只需要输入`up`或者`upg`就可以实现部署了，不用打那么多字了。

### [](#实现fork-me-on-github "实现fork me on github")实现 fork me on github

设置效果：  
[![](http://xmzcl.vicp.net:8089/images/blog_hexo39.png)](http://xmzcl.vicp.net:8089/images/blog_hexo39.png)

设置方法：  
点击[这里](https://github.com/blog/273-github-ribbons)或者[这里](http://tholman.com/github-corners)挑选自己喜欢的样式， 复制代码：

粘贴刚才复制的代码到`themes/next/layout/_layout.swig`文件中, 放在`<div></div>`的下面，并把 href 改为你的 github 地址

[![](http://xmzcl.vicp.net:8089/images/blog_hexo40.png)](http://xmzcl.vicp.net:8089/images/blog_hexo40.png)

### [](#显示文章热度 "显示文章热度")显示文章热度

设置效果：  
[![](http://host.zealot.top:8089/images/blog_hexo42.png)](http://host.zealot.top:8089/images/blog_hexo42.png)

设置方法：  
next 主题集成 leanCloud，打开`themes/next/layout/_macro/post.swig`, 在画红线的区域添加`℃`

[![](http://host.zealot.top:8089/images/blog_hexo43.png)](http://host.zealot.top:8089/images/blog_hexo43.png)  
打开，`themes/next/languages/zh-Hans.yml`, 将画红框的改为`热度`.

[![](http://host.zealot.top:8089/images/blog_hexo44.png)](http://host.zealot.top:8089/images/blog_hexo44.png)

打开`themes/next/_config.yml`找到`leancloud_visitors`, 将`enable:`改成`true`, 再填上自己的`app_id`和`app_key`。[不懂怎么看 app_id 和 app_key 的可以点这里!](#加入valine在线评论)  

```
leancloud_visitors:
  enable: true
  app_id: #你自己的id
  app_key: #你自己的key
```

### [](#hexo载入动画效果 "hexo载入动画效果")hexo 载入动画效果

设置方法：  
编辑`themes/netx/_config.yml`找到`motion`, 将`enable`的值，改成`true`  

```
# Use velocity to animate everything.
motion:
  enable: true
  async: false
  transition:
    # Transition variants:
    # fadeIn | fadeOut | flipXIn | flipXOut | flipYIn | flipYOut | flipBounceXIn | flipBounceXOut | flipBounceYIn | flipBounceYOut
    # swoopIn | swoopOut | whirlIn | whirlOut | shrinkIn | shrinkOut | expandIn | expandOut
    # bounceIn | bounceOut | bounceUpIn | bounceUpOut | bounceDownIn | bounceDownOut | bounceLeftIn | bounceLeftOut | bounceRightIn | bounceRightOut
    # slideUpIn | slideUpOut | slideDownIn | slideDownOut | slideLeftIn | slideLeftOut | slideRightIn | slideRightOut
    # slideUpBigIn | slideUpBigOut | slideDownBigIn | slideDownBigOut | slideLeftBigIn | slideLeftBigOut | slideRightBigIn | slideRightBigOut
    # perspectiveUpIn | perspectiveUpOut | perspectiveDownIn | perspectiveDownOut | perspectiveLeftIn | perspectiveLeftOut | perspectiveRightIn | perspectiveRightOut
    post_block: fadeIn #主页载入效果
    post_header: bounceRightIn #文章标题载入效果
    post_body: slideDownIn
    coll_header: bounceLeftIn
    # Only for Pisces | Gemini.
    sidebar: bounceLeftIn #侧边栏载入效果
```

`#`号里都是载入效果，有时间可以自己多试一试！

### [](#建立md模板 "建立md模板")建立 md 模板

你是在站点文件夹根目录用`hexo new <title>`新建的文章，那么其实它就是将文章的模版文件`~/scaffolds/post.md`复制了一份到`~/blog/source/_posts/`下，所以这也意味着：

你可以直接通过在`~/blog/source/_posts/`下新建. md 结尾的文件来写新的文章。  
你可以通过自定义文章的模版文件，从而每次命令行新建的文章都会有你自定义的内容。  
下面是我的`post.md`内容  

```
title: {{ title }}
date: {{ date }}

categories:
/* 分类，支持多级，比如：
- technology
- computer
- computer-aided-art
*/

tags:
/* 标签
** 多个可以这样写
- 标签1
- 标签2
- 标签3
*/

description:
/* 文章的描述，在每篇文章标题下方显示
*/

comments:
/* 是否开启评论
** 默认值是 true
** 要关闭写 false
*/

photos:
/* Gallery support，用来支持画廊 / 相册，用法如下：
- photo_url_1
- photo_url_2
- photo_url_3
*/

link:
/* 文章的外部链接
*/

top: true
/* 文章置顶
** true就是开启，flase就是关闭置顶。
*/

password:
/* 文章密码，参考本文"1.20.文章加密访问"
** 需配置好，否则请勿添加！
*/
```

### [](#在博文中添加版权信息 "在博文中添加版权信息")在博文中添加版权信息

设置效果：  
[![](http://host.zealot.top:8089/images/hexo100.png)](http://host.zealot.top:8089/images/hexo100.png)

设置方法：  
在目录`themes/next/layout/_macro/`下建立`my-copyright.swig`文件, 填入下面的代码：  

```
{% if page.copyright %}
<div>
  <script src="//cdn.bootcss.com/clipboard.js/1.5.10/clipboard.min.js"></script>

  <!-- JS库 sweetalert 可修改路径 -->
  <script src="https://cdn.bootcss.com/jquery/2.0.0/jquery.min.js"></script>
  <script src="https://unpkg.com/sweetalert/dist/sweetalert.min.js"></script>
  <p><span>本文标题:</span><a href="{{ url_for(page.path) }}">{{ page.title }}</a></p>
  <p><span>文章作者:</span><a href="/" title="访问 {{ theme.author }} 的个人博客">{{ theme.author }}</a></p>
  <p><span>发布时间:</span>{{ page.date.format("YYYY年MM月DD日 - HH:mm") }}</p>
  <p><span>最后更新:</span>{{ page.updated.format("YYYY年MM月DD日 - HH:mm") }}</p>
  <p><span>原始链接:</span><a href="{{ url_for(page.path) }}" title="{{ page.title }}">{{ page.permalink }}</a>
    <span  title="点击复制文章链接"><i data-clipboard-text="{{ page.permalink }}"  aria-label="复制成功！"></i></span>
  </p>
  <p><span>许可协议:</span><i></i> <a rel="license" href="https://creativecommons.org/licenses/by-nc-nd/4.0/" target="_blank" title="Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)">署名-非商业性使用-禁止演绎 4.0 国际</a> 转载请保留原文链接及作者。</p>
</div>
<script>
    var clipboard = new Clipboard('.fa-clipboard');
    $(".fa-clipboard").click(function(){
      clipboard.on('success', function(){
        swal({
          title: "",
          text: '复制成功',
          icon: "success",
          showConfirmButton: true
          });
	});
    });
</script>
{% endif %}
```

在目录`themes/next/source/css/_common/components/post/`下建立`my-post-copyright.styl`  

```
.my_post_copyright {
  width: 85%;
  max-width: 45em;
  margin: 2.8em auto 0;
  padding: 0.5em 1.0em;
  border: 1px solid #d3d3d3;
  font-size: 0.93rem;
  line-height: 1.6em;
  word-break: break-all;
  background: rgba(255,255,255,0.4);
}
.my_post_copyright p{margin:0;}
.my_post_copyright span {
  display: inline-block;
  width: 5.2em;
  color: #b5b5b5;
  font-weight: bold;
}
.my_post_copyright .raw {
  margin-left: 1em;
  width: 5em;
}
.my_post_copyright a {
  color: #808080;
  border-bottom:0;
}
.my_post_copyright a:hover {
  color: #a3d2a3;
  text-decoration: underline;
}
.my_post_copyright:hover .fa-clipboard {
  color: #000;
}
.my_post_copyright .post-url:hover {
  font-weight: normal;
}
.my_post_copyright .copy-path {
  margin-left: 1em;
  width: 1em;
  +mobile(){display:none;}
}
.my_post_copyright .copy-path:hover {
  color: #808080;
  cursor: pointer;
}
```

修改`themes/next/layout/_macro/post.swig`, 在代码  

```
<div>
  {% if not is_index %}
    {% include 'passage-end-tag.swig' %}
  {% endif %}
</div>
```

之前添加下面的代码：  

```
<div>
      {% if not is_index %}
        {% include 'my-copyright.swig' %}
      {% endif %}
</div>
```

[![](http://host.zealot.top:8089/images/hexo101.png)](http://host.zealot.top:8089/images/hexo101.png)

修改`themes/next/source/css/_common/components/post/post.styl`文件，在最后一行增加：  

```
@import "my-post-copyright"
```

然后保存退出。

在需要增加版权信息显示的博文抬头，添加`copyright: true`。如下图：

[![](http://host.zealot.top:8089/images/hexo102.png)](http://host.zealot.top:8089/images/hexo102.png)

### [](#按文章更新时间排序 "按文章更新时间排序")按文章更新时间排序

这个功能我单独写了一篇文章，请访问下面的链接了解。

[利用 vim 实现 HEXO 文章按更新时间自动排序](https://zealot.top/%E5%88%A9%E7%94%A8vim%E5%AE%9E%E7%8E%B0HEXO%E6%96%87%E7%AB%A0%E6%8C%89%E6%9B%B4%E6%96%B0%E6%97%B6%E9%97%B4%E6%8E%92%E5%BA%8F.html#more)

### [](#美化右侧滚动条 "美化右侧滚动条")美化右侧滚动条

设置效果：

[![](http://xmzcl.vicp.net:8089/images/hexostyle001.png)](http://xmzcl.vicp.net:8089/images/hexostyle001.png)

设置方法：  
打开`themes\next\source\css\_custom\custom.styl`文件，将下面的代码添加进去。  

```
//设置滚动条的样式
//参考https://segmentfault.com/a/1190000003708894
::-webkit-scrollbar {
      width: 5px;
      height: 5px;

}
//滚动槽
::-webkit-scrollbar-track {
      background: #eee;

}
//滚动条滑块
::-webkit-scrollbar-thumb {
      border-radius: 5px;
        background-color: #ccc;

}
::-webkit-scrollbar-thumb:hover {
      background-color: rgb(247, 149, 51);

}
```

### [](#优化选择的文字样式 "优化选择的文字样式")优化选择的文字样式

设置效果：  
[![](http://host.zealot.top:8089/images/hexostyle002.png)](http://host.zealot.top:8089/images/hexostyle002.png)

设置方法：  
打开`themes\next\source\css\_custom\custom.styl`文件，将下面的代码添加进去。  

```
::selection {
      background-color: rgb(255, 241, 89);
        color: #555;

}
```

### [](#valine评论实现邮箱提醒 "valine评论实现邮箱提醒")valine 评论实现邮箱提醒

这个功能我单独写了一篇文章，请访问下面的链接了解。

[Hexo 博客之 valine 评论实现邮箱提醒的方法](https://zealot.top/Hexo%E5%8D%9A%E5%AE%A2%E4%B9%8Bvaline%E8%AF%84%E8%AE%BA%E5%AE%9E%E7%8E%B0%E9%82%AE%E7%AE%B1%E6%8F%90%E9%86%92%E7%9A%84%E6%96%B9%E6%B3%95.html#more)

未完待续…….