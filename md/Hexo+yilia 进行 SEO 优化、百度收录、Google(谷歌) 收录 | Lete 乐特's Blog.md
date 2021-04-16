\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.lete114.top\](https://blog.lete114.top/article/b6c07012.html#%E5%89%8D%E8%A8%80)

### [](#前言 "前言")前言

> **SEO（Search Engine Optimization）**：汉译为搜索引擎优化。
> 
> > 个人搭建的博客没有基于任何知名的平台如：CSDN，知乎，简书，博客园等，，那么在搜索引擎被收录的可能就微乎其微特别是百度，百度对于新站不是特别友好，我的个人博客提交给百度一个多月了，只抓取，不收录，一个月也就抓个两三次，自从对网站进行了 SEO 优化后，百度有了很大的反义，不过还是只抓取不收录，两个月过去了，只收录我个人博客的一个首页，相比于谷歌，当天提交，当天收录。

> **那么如何提高被收索引擎收录的几率呢？**
> 
> > 1.  先对自己网站进行优化
> > 2.  其次就是 SEO 优化

[![](https://cdn.jsdelivr.net/gh/lete114/CDN@3.0/BoBoPic/02.jpg)](https://cdn.jsdelivr.net/gh/lete114/CDN@3.0/BoBoPic/02.jpg)

### [](#网站优化 "网站优化")网站优化

想要收索引擎重视，就得先对自己网站或者博客进行优化、如：标题标签、Meta 描述、Meta 关键字、XML 网站地图、Robots.txt、网站图标、自定义 404 页面、加载时间 (速度)、以及网站结构

##### [](#Head-头部优化 "Head 头部优化")Head 头部优化

打开路径：`\Hexo\themes\yilia\layout\_partial\head.ejs`  
自己看，我就不多说了，自行修改相应信息内容

html

```
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

    <meta http-equiv="Content-Language" content="zh" />
    <meta http-equiv="content-language" content="zh-CN">
    <meta >
    <meta >
    <meta 我相信我可以，但我又一直在路上，所以我有无限的可能！" />
    <meta property="site\_name" content="Lete乐特个人博客" />

    <!-- Open Graph -->
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://lete114.now.sh/index.html">
    <meta property="og:title" content="Lete乐特个人博客" />
    <meta property="og:site\_name" content="Lete乐特个人博客" />
    <meta property="og:description" content="我相信我可以，但我又一直在路上，所以我有无限的可能！" />
    <meta property="og:locale" content="zh-CN">
    <meta >
    <meta >
    <meta 我相信我可以，但我又一直在路上，所以我有无限的可能！">
    <link rel="icon" href="img/favicon.ico">
    <link rel="dns-prefetch" href="https://lete114.now.sh">
```

##### [](#配置Robots-txt文件 "配置Robots.txt文件")配置 Robots.txt 文件

Robots 是站点与 spider 沟通的重要渠道，站点通过 robots 文件声明本网站中不想被搜索引擎收录的部分或者指定搜索引擎只收录特定的部分。

> > 可以用我写好的，修改自己的相应配置即可，如有更高的需求可以前往 —>[robots.txt 文件的格式](https://ziyuan.baidu.com/college/courseinfo?id=267&page=12#h2_article_title30)

bash

```
\# 允许所有用户代理的浏览器爬虫进行访问（爬取数据）
User-agent: \*

# 不允许访问的内容
Disallow: /fonts/
Disallow: /img/
Disallow: /js/
Disallow: /css/
Disallow: /\*.js
Disallow: /\*.css

Sitemap: http://lete114.github.io/sitemap.xml
Sitemap: http://lete114.github.io/baidusitemap.xml
Sitemap: http://lete114.gitee.io/sitemap.xml
Sitemap: http://lete114.gitee.io/baidusitemap.xml
Sitemap: http://lete114.now.sh/sitemap.xml
Sitemap: http://lete114.now.sh/baidusitemap.xml


Sitemap: https://lete114.github.io/sitemap.xml
Sitemap: https://lete114.github.io/baidusitemap.xml
Sitemap: https://lete114.gitee.io/sitemap.xml
Sitemap: https://lete114.gitee.io/baidusitemap.xml
Sitemap: https://lete114.now.sh/sitemap.xml
Sitemap: https://lete114.now.sh/baidusitemap.xml
```

##### [](#自定义404-html页面 "自定义404.html页面")自定义 404.html 页面

随便网上找个自己新欢的 404.html 页面把他丢到 `\Hexo\themes\yilia\source` 文件夹下即可，下面是我的 404.html 页面  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/Sundry/404.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/Sundry/404.png)

##### [](#博客-网站-加载速度-时间 "博客(网站)加载速度(时间)")博客 (网站) 加载速度 (时间)

可以看看我的这篇文章内容：[https://lete114.now.sh/article/2aa315b1.html](https://lete114.now.sh/article/2aa315b1.html)

##### [](#补充 "补充")补充

可以前往这个网站测试自己的博客有那先需要优化的地方：[http://seo.cjzzc.com/](http://seo.cjzzc.com/)  
整个 60 分及格就好了，因为百度也是 60 分[![](https://cdn.jsdelivr.net/gh/moezx/cdn@3.1.9/img/Sakura/images/smilies/icon_huaji.gif)](https://cdn.jsdelivr.net/gh/moezx/cdn@3.1.9/img/Sakura/images/smilies/icon_huaji.gif)  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/07.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/07.png)  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/08.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/08.png)

### [](#百度收录 "百度收录")百度收录

> 1.  百度搜索框内输入 `site:你的域名`如：`site:lete114.now.sh` 后点击提交链接或者直接 [https://zhanzhang.baidu.com](https://zhanzhang.baidu.com)  
>     
> 2.  (这一步需要的截图图片过多，会影响博客加载速度，请按照文字进行) 注册一个百度账号，登陆，点击`用户中心` —> `添加网站` —> `输入域名` (建议选择 https)—> `设置站点领域` (随意选择适合自己网站（博客）的)—> `选择验证方式`，建议使用文件验证 (验证后可删除)—> 点击`下载验证文件`，下载后丢到 `\Hexo\themes\yilia\source` 文件夹下即可 —>`hexo g` 和 `hexo d` 上传 github 后，稍等 `2分钟`后点击`完成验证` , 验证成功后可以点击顶部的`搜索服务`

[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/01.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/01.png)

##### [](#选择链接提交方式 "选择链接提交方式")选择链接提交方式

> 1.  手动提交：一次性提交链接给百度，可以使用此种方式。
> 2.  自动提交（虽然这种方式各有千秋，但是百度推荐全用上，全面一点！）：
>     
>     > 2.1 主动推送（实时）：最为快速的提交方式，推荐您将站点当天新产出链接立即通过此方式推送给百度，以保证新链接可以及时被百度收录。  
>     > 2.2 自动推送：最为便捷的提交方式，请将自动推送的 JS 代码部署在站点的每一个页面源代码中，部署代码的页面在每次被浏览时，链接会被自动推送给百度。可以与主动推送配合使用。  
>     > 2.3 sitemap：您可以定期将网站链接放到 sitemap 中，然后将 sitemap 提交给百度。百度会周期性的抓取检查您提交的 sitemap，对其中的链接进行处理，但收录速度慢于主动推送。
>     

##### [](#设置推送 "设置推送")设置推送

**站长平台：[https://ziyuan.baidu.com](https://ziyuan.baidu.com)**

前提：注册百度，添加站点、验证站点。

验证成功就能在，百度找到你的网站了，百度搜索框输入：如 `site:lete114.now.sh`，但百度没有那么快，可能需要一两个星期甚至一个月 (谷歌的话当天就可以收入，或者明天)。

##### [](#主动推送 "主动推送")主动推送

百度站长工具，然后在`（标题栏）收索服务--->普通收录--->资源提交--->主动推送(实时)`。  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/03.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/03.png)

添加插件 hexo-baidu-url-submit

该插件 github 网址：[https://github.com/huiwang/hexo-baidu-url-submit](https://github.com/huiwang/hexo-baidu-url-submit)

首先，在 Hexo 根目录下右键选择 Git，输入：`npm install hexo-baidu-url-submit --save` 安装插件

##### [](#配置“百度主动推送” "配置“百度主动推送”")配置 “百度主动推送”

然后，同样在根目录下，把以下内容配置到`_config.yml` 文件中:

bash

```
\# 百度主动推送
baidu\_url\_submit:
  count: 100 ## 提交最新的100个链接
  host: lete114.now.sh ## 在百度站长平台中注册的域名
  token: Your token ## 请注意这是你百度站长平台主动推送的的秘钥， 所以请不要把博客源代码发布在公众仓库里!
  path: baidu\_urls.txt ## 文本文档的地址， 新链接会保存在此文本文档里
```

最后，加入新的 deploy (可以参考一下我的`_config.yml` 文件)

bash

```
\# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
   - type: git
     repo: 
           github: https://github.com/lete114/lete114.github.io.git
           gitee: https://gitee.com/lete114/lete114.git
     branch: master
   - type: baidu\_url\_submitter
# 百度主动推送
baidu\_url\_submit:
  count: 100 ## 提交最新的一个链接
  host: lete114.now.sh ## 在百度站长平台中注册的域名
  token: Ulo7QFTjgAAzLqB9 ## 请注意这是您的秘钥， 所以请不要把博客源代码发布在公众仓库里!
  path: baidu\_urls.txt ## 文本文档的地址， 新链接会保存在此文本文档里
```

##### [](#如何进行推送 "如何进行推送")如何进行推送

执行 `hexo d` 的时候，新的连接就会被推送了。如下图

[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/10.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/10.png)

重新生成后，我们可以发现在 `public\` 目录下生成有 `baidu_urls.txt` 里面的就是推送的链接。

##### [](#自动推送 "自动推送")自动推送

1\. 在配置 `\Hexo\themes\yilia\_config.yml` 中开启功能：

bash

```
\# 开启百度站长平台自动推送(https://ziyuan.baidu.com/linksubmit/index)
# 页面被访问了，就会被推送过去。
baidu\_push: true
```

2\. 在 `\Hexo\themes\yilia\layout\_partial\` 目录下新建 `baidu-push.ejs`

html

```
<% if (theme.baidu\_push){ %>
<!-- 开启百度站长平台自动推送 -->
<script>
  (function () {
    var bp = document.createElement('script');
    var curProtocol = window.location.protocol.split(':')\[0\];
    if (curProtocol === 'https') {
      bp.src = 'https://zz.bdstatic.com/linksubmit/push.js';
    } else {
      bp.src = 'http://push.zhanzhang.baidu.com/push.js';
    }
    var s = document.getElementsByTagName("script")\[0\];
    s.parentNode.insertBefore(bp, s);
  })();
</script>
<% } %>
```

3\. 在 `\Hexo\themes\yilia\layout\_partial\head.ejs` 的 `</head>` 前引入脚本：

html

```
<!--百度自动推送-->
<%- partial('baidu-push') %>
</head>
```

##### [](#百度sitemap提交 "百度sitemap提交")百度 sitemap 提交

**我们使用 hexo generator-baidu-sitemap 这个插件**

**github：[https://github.com/coneycode/hexo-generator-baidu-sitemap](https://github.com/coneycode/hexo-generator-baidu-sitemap)**

安装 `hexo generator-baidu-sitemap` 插件

bash

```
\# if your hexo version is 2.x.x, you should install as follow:
# 如果你的hexo版本是2.x.x，你应该安装如下
$ npm install hexo-generator-baidu-sitemap@0.0.8 --save

# if version is 3.x.x, you should install as follow:
# 如果版本是3.x.x，你应该安装如下
$ npm install hexo-generator-baidu-sitemap --save
```

然后在 Hexo 的`_config.yml` 里面配置一下：

bash

```
baidusitemap:
  path: baidusitemap.xml
```

`hexo g` 后，会在 `public\` 目录下生成站点文件 `baidusitemap.xml`。  
之后去百度站长平台提交一下 sitemap 的路径就好，如：lete114.now.sh/baidusitemap.xml，感觉这个没多大用，可能是我博客有问题吧。

##### [](#效果 "效果")效果

在站长平台可以看到链接提交数量，如：  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/04.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/04.png)  
[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/02.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/02.png)

### [](#Google收录 "Google收录")Google 收录

##### [](#添加网站、验证 "添加网站、验证")添加网站、验证

登录 Google 账号，打开搜索控制台：[https://search.google.com/search-console](https://search.google.com/search-console) ，添加你的网站，需要验证网站，它那里会提供几种验证方式，依然推荐使用 HTML 文件验证，下载 HTML 文件，将文件丢到 `\Hexo\themes\yilia\source` 文件夹下即可，然后点击验证。`（验证后可删除）`  
验证成功不是当天就是明天就能再 Google 找到你的网站了，谷歌搜索输入如 `site:lete114.now.sh`

##### [](#谷歌sitemap提交 "谷歌sitemap提交")谷歌 sitemap 提交

提交 sitemap，上面使用的是百度的 sitemap 也可以，如果 Google 识别不了，可以使用通用 sitemap 生成器 hexo-generator-sitemap：[https://github.com/hexojs/hexo-generator-sitemap](https://github.com/hexojs/hexo-generator-sitemap)

bash

```
npm install hexo-generator-sitemap --save
```

配置 Hexo 的`_config.yml`

bash

```
sitemap:
    path: sitemap.xml
```

执行 `hexo g` 重新生成，会在 `public` 目录下生成 `sitemap.xml` 文件，发布后，就可以在 google 控制台提交这个 sitemap 了。

##### [](#效果-1 "效果")效果

[![](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/09.png)](https://cdn.jsdelivr.net/gh/lete114/CDN/SEO/09.png)

### [](#补充-1 "补充")补充

SEO 只负责提交网站的索引量、访问量，具体数据可以通过添加百度分析和 google 分析来参看。可参考：[hexo+yilia 添加百度统计和 Google 统计](https://www.yansheng.xyz/article/eda67a25.html)

由于我对 SEO 优化也不是很了解，有哪里写的不对或者是有问题希望大家能够指出，请在评论区留言