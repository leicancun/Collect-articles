\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[yangchaoyi.vip\](https://yangchaoyi.vip/posts/520520/#正文)

[](#阅读须知 "阅读须知")阅读须知
--------------------

> 注意，本篇博客并不是从零手把手教你去搭博客，那样会很花费时间去写一篇文档，况且从零搭建的博客一搜也是一大把，太多重复的内容就没必要继续写了。因此，对于不知道怎么搭建的伙伴，我会提供我搭建时用到的学习资料，任意选一篇按着教程搭建就好了。另外，本篇博客教程内容主要是记载本站美化 DIY 方面，更多后续内容将会更新在本站内 [https://yangchaoyi.vip](https://yangchaoyi.vip/) 教程内容可复制引用，但请加一个参考链接，谢谢！

[](#关于博客是否开源 "关于博客是否开源")关于博客是否开源
--------------------------------

因为本站博客也是最近重新搭建起来的，还有一些优化和功能也在完善。当然，我也会朝着开源方向发展，但**具体什么时候公开博客源码，这还不确定，还需要一段时间准备**。因为选择去开源的话还需要修改很多信息内容，有些隐私以及安全部分需要进行修改，也需要进行版本发布等等。这些都需要一段时间去准备的。

但你也**不用因为看到这里就觉得这篇文章没有价值了**，我们搭建博客嘛，在于搭的过程，是一个不断迭代的过程，本篇会开源自己当前主题美化教程，你按着教程来，一样可以拥有自己风格的博客。

[](#博客源码开放 "博客源码开放")博客源码开放
--------------------------

\====== 更新！吼吼吼 ========

目前是已经在做开源的准备了，当然还有一些优化项和功能增加后续在慢慢更新，请小伙伴们关注[本仓库](https://github.com/Chocolate1999/hexo-blog-lionkk)，点个 star 即可，然后记得关注`readme`的动态更新，添加的特性与教程都会与代码同步更新。为了回馈开源，这不是生成后的网页文件，是您可以直接使用的源码，您只需要把博客相关信息换成您自己的就可以部署了，对于新手或者不懂编程的小伙伴来说，简直是福音，极大简化了您构建博客的工作量和复杂度，每个人都可以下载并修改成自己喜欢样式！如果你有修改想法，欢迎 PR！最后，我们还是给这个开源小项目取个名字吧，由于本人狮子座（单身，苦笑），而且微信公众号名字也是取名：`小狮子前端Vue`，由于并不是自己开发的主题，起名就不添加`theme`了，那就叫 `hexo-blog-lionkk`。<<<<< [源代码下载](https://github.com/Chocolate1999/hexo-blog-lionkk) >>>>>

**简单使用方法：**

`star` 本项目仓库 ^ o ^  
安装 [Git](https://git-scm.com/downloads), 安装 [nodeJS](https://nodejs.org/en/)  
你可以直接`fork`一份源码到你的仓库，`clone`到本地  
在本地博客仓库运行`npm i`命令安装依赖包  
修改配置信息，改成自己的信息  
运行命令`hexo clean`（清除生成文件），`hexo g`（生成网页）， `hexo s`（本地预览），`hexo d`（部署）

有什么问题可以在文章最后评论区**留言和讨论**，当然，欢迎点击文章最后的打赏按键，请博主一杯冰阔乐，笑～

> 最后，如果项目和教程对你有所帮助或者你看见了还算比较喜欢，欢迎给我 star，谢谢您！

[](#前言 "前言")前言
--------------

在本科大二下学期的时候，因为参与了学校 `acm` 选拔，获得了参与蓝桥杯比赛的名额，又或者说是门票吧 [推荐阅读：关于我的大学 ACM 江湖](https://yangchaoyi.vip/posts/24659/#%E5%BC%95%E8%A8%80) ，从那个时候开始，我就开始写起了博客，因为学校一位老师的成就，我就选择了 `CSDN` 这个平台，从那个时候到现在，我几乎每个月都会写博客，到现在已经是一种习惯了。我习惯性的将我所学记录并且分享开源，自己遇到的 `bug` 记录下来，让看到博客的伙伴少走点坑。[必读文章：【长文总结】2020 从零到博客专家 过去的我，现在的我，将来的我](https://yangchaoyi.vip/posts/37335/)

一晃大学就快结束了，我也成功获得了 `CSDN博客专家` 荣誉称号。到了大三，也是到了确定自己方向时刻了，考虑之后，选择走前端，成为一个前端程序员。于是呢，我就想着自己 `DIY` 一个属于自己的博客，有一个比较漂亮的页面，或许能激发阅读兴趣呢？

本博客基于`Hexo`，所以首先要了解一下我们搭建博客所要用到的框架。`Hexo`是高效的静态网站生成框架，它基于`Node.js`，快速，简单且功能强大，是搭建博客的首选框架。大家可以进入 [hexo](https://hexo.io/zh-cn/) 官网进行详细查看，因为`Hexo`的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。通过`Hexo`，你可以直接使用`Markdown`语法来撰写博客。相信很多小伙伴写工程都写过`README.md`文件吧，对，就是这个格式的！写完后只需两三条命令即可将生成的网页上传到`github`或者`coding`等代码管理托管平台，然后别人就可以浏览你的博客网页啦。是不是很简单？你无需关心网页源代码的具体生成细节，只需要用心写好你的博客文章内容就行了。

> 简单总结：Hexo, 产品成熟，使用简单，功能强大，有丰富的各种插件资源；但，像发布后台、站内搜索，评论系统类似诉求，虽然有对应的工具，但也需要自己折腾下，后续我们一步一步介绍。

本站目前的主题是 `hexo-theme-butterfly` ，在此之前呢，使用过 `hexo-theme-matery`主题来建站。因此本教程更多的是介绍`hexo-theme-butterfly`，至于我为什么选择更换这个主题呢？读者可以对比一下它和 `csdn` 呢，是不是有点相像，既有了原本的界面，页面又更加美观一点，简直喜欢的不要不要的~

本教程暂时分为五个部分：

*   第一部分： `hexo-theme-matery`主题搭建介绍
*   第二部分： `hexo-theme-butterfly`主题搭建美化 DIY 教程
*   第三部分：分享本站所用的学习资料以及本篇文章所参考的文章
*   第四部分：彩蛋（暂时没想到好的标题，给点神秘感 hhh）
*   第五部分：总结

[](#第一部分-matery主题搭建介绍 "第一部分 matery主题搭建介绍")第一部分 matery 主题搭建介绍
------------------------------------------------------------

### [](#阅读须知-1 "阅读须知")阅读须知

由于更换了主题，但是域名并没有更换，因此下文界面链接可能失效了，但是附上了相关图片介绍，尽管本文并不是详细介绍 `matery`主题搭建过程，但是在文章内容部分也是提供了一些 dalao 搭建资料，小伙伴们可以参考他们的搭建过程。当然，如果你和我一样，选择`butterfly`主题，可以跳过第一部分，直接去第二部分即可。

### [](#前言-1 "前言")前言

原本是计划刷题继续提升自己的，奈何看了一个 b 站 up 主的关于搭建个人博客的视频，其中有提到对于计算机的我们来说，有一个属于自己的博客是挺重要的，不仅能作为自己的记录，而且还能写进自己简历，丰富大学生活等等。

于是，我就折腾了大概 10 多天左右，从一开始搭建 hexo 博客

[搭建个人博客 Hexo 框架 （自制）](https://blog.csdn.net/weixin_42429718/article/details/104239306)

到使用了 yila 主题，但做着做着发现原来主题上面还有升级版的主题，我看到了 yilia 主题的升级版 yelee 主题，于是花了 3 天左右的时间按照教程快速开发了一个个人主页如下图：

[Hexo yilia 主题 搭建个人主页【整合目录】](https://blog.csdn.net/weixin_42429718/article/details/104264485)

[可以进去瞧一瞧，传送门](http://yangchaoyi1021.cn/)

[![](https://img-blog.csdnimg.cn/20200218165557659.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200218165557659.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

当然，关于 yilia 主题，挺适合刚入门 hexo 的伙伴。

这篇博客是我用 yilia 主题常用的，推荐阅读

[Hexo yilia 主题一揽子使用方案](https://blog.csdn.net/lynnbest/article/details/79845944)

然后就是我上面那个图关于 yelee 主题，下面就是官方文档，按照教程来的话，最多一周就能快速拥有一个自己的博客了

[yelee 主题使用说明（官方文档）](http://moxfive.xyz/yelee/new-features.html)

### [](#我的主题 "我的主题")我的主题

然而，最后我搭建选择的主题呢，以上都不是, 我采用的是 hexo-theme-matery

以下就是原主题相关特性，大家可以简单看一看

主题特性:

*   `简单漂亮`，`文章内容美观易读`
*   Material Design 设计
*   `响应式设计`，博客在桌面端、平板、手机等设备上均能很好的展现
*   首页`轮播文章`及每天动态切换 Banner 图片
*   `瀑布流式`的博客文章列表（文章无特色图片时会有 24 张漂亮的图片代替）
*   `时间轴式`的归档页
*   词云的标签页和雷达图的分类页
*   `丰富的关于我`页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
*   可自定义的数据的`友情链接`页面
*   支持文章置顶和文章打赏
*   支持 `MathJax`
*   TOC 目录
*   可设置复制文章内容时追加`版权信息`
*   可设置阅读文章时做`密码验证`
*   Gitalk、Gitment、Valine 和 Disqus `评论模块`（推荐使用 Gitalk）
*   集成了`不蒜子统计`、`谷歌分析`（Google Analytics）和`文章字数统计`等功能
*   支持在首页的音乐播放和视频播放功能

### [](#简单概述 "简单概述")简单概述

显然，看完了特性也还不知道会是啥样，那就整点图？？？

[![](https://img-blog.csdnimg.cn/2020021621451031.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/2020021621451031.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

什么？看完图，还想直接上手体验，好，满足你

[超逸の博客——传送门](https://yangchaoyi.vip/)

好了，到此结束…

### [](#我的搭建过程 "我的搭建过程")我的搭建过程

显然，我也是一个小白，花了一周的时间才有了现在这样个人博客，我就简述一下我的零基础搭建过程：

配置 hexo 环境——创建好了第一个 hexo 框架——尝试学习 yilia 主题

发现了 yelee 主题，果断重新写——三天就搭建了一个测试版，不断优化压缩（gulp,cdn 等等）

成功搭建了一个个人博客（喜悦，成就感）——从大佬的友链里面发现了更大佬，界面非常美观——赶紧按着大佬教程从零再码一次（因为有了之前的基础，开发也还算挺快的）

又是三天成型，有了测试版——域名备案——解决在国内访问速度慢的原因

github+coding 双部署——添加各种插件（豆瓣，天气，看板娘等）——测试访问速度

最后，开发完毕！

[嘿！ 传送门](https://yangchaoyi.vip/)

### [](#学习资料合集（重点在这！） "学习资料合集（重点在这！）")学习资料合集（重点在这！）

前面还是稍微扯了一点个人总结，下面我将分享，我这一周来查阅的资料。

当然，只分享真正能解决问题的博客，我查阅的资料很多很多，下面是一些我遇到的问题以及一些优秀的大佬整理的超详细搭建教程：

### [](#搭建全教程（真大佬写的，超详细） "搭建全教程（真大佬写的，超详细）")搭建全教程（真大佬写的，超详细）

洪卫大佬写的教程，我就是跟着他的教程开发的，首推！

[Hexo+Github 博客搭建完全教程](https://sunhwee.com/posts/6e8839eb.html)

[![](https://img-blog.csdnimg.cn/2020021817392216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/2020021817392216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

下面这位大佬总共写了四篇，这里我就链接了他的第一篇，剩下几篇去主页找找就好了，和上面洪卫大佬主题风格不一样，而且还专门写了一篇 pwa，真是好心人！不过我更喜欢这位大佬的主题颜色，所以我结合了洪卫和 sitoi 大佬的博客搭建教程！

[基于 Hexo GitHub 从零开始搭建个人博客](https://sitoi.cn/posts/6666.html)

[![](https://img-blog.csdnimg.cn/20200218173853770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200218173853770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
下面是过客~ 励心大佬的超详细版搭建教程，后面才发现，我很多问题是在这篇文章中解决的！关于解决 github 访问速度问题，部署在 coding 和码云上等等，总之，这位大佬干货分享满满，我看完简直要感动哭了，居然如此详细，终于解决了我的 bug！！！

[Hexo+github 搭建博客 (超级详细版，精细入微)](https://yafine-blog.cn/posts/4ab2.html)

[![](https://img-blog.csdnimg.cn/20200218174037293.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200218174037293.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

### [](#关于我搭建过程问题解决 "关于我搭建过程问题解决")关于我搭建过程问题解决

（以下问题不分先后，能够解决你的问题那就很好了，如果不能解决你的问题，请在评论区留言，看到了立即回复您，然后更新博客）

### [](#入门必看 "入门必看")入门必看

[Hexo yilia 主题 搭建个人主页【整合目录】](https://blog.csdn.net/weixin_42429718/article/details/104264485)

### [](#修改主题颜色（调整自己喜欢的背景颜色） "修改主题颜色（调整自己喜欢的背景颜色）")修改主题颜色（调整自己喜欢的背景颜色）

在主题文件的 `/source/css/matery.css`文件中，搜索 `.bg-color`来修改背景颜色：

```
.bg-color {
    background-image: linear-gradient(to right, #1f4d71 0%, #71bbb6 100%);
    opacity: 0.9;
    
}
```

### [](#相关插件 "相关插件")相关插件

[每日诗词 api](https://www.jinrishici.com/#)

[Hitokoto（一言）api](https://hitokoto.cn/)

[给 hexo 博客添加天气插件的网站](https://cj.weather.com.cn/plugin/pc)

[hexo 博客添加一级分类相册功能](https://liyangzone.com/2019/07/22/hexo%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0%E4%B8%80%E7%BA%A7%E5%88%86%E7%B1%BB%E7%9B%B8%E5%86%8C/)

[Tidio 聊天机器人插件](https://www.tidio.com/panel/bots/manage/898302)

[基于 Hexo GitHub 从零开始搭建个人博客（四）：让你的博客完美支持 PWA](https://sitoi.cn/posts/49115.html#toc-heading-1)

[Matery 主题安装豆瓣插件](https://ciweigg2.github.io/2019/11/02/matery-zhu-ti-an-zhuang-dou-ban-cha-jian/)

### [](#优化加速 "优化加速")优化加速

[利用 Gulp 来压缩你的 Hexo 博客](https://leaferx.online/2017/06/16/use-gulp-to-minimize/)

[国内 Github 访问加速](https://blog.sky03.cn/posts/29055.html)

[静态博客访问优化之终极解决方案](https://blog.sky03.cn/posts/1663.html)

[Hexo 进阶之各种优化](https://blog.sky03.cn/posts/42790.html#toc-heading-4)

[hexo 使用 katex 引擎 (markdown 渲染加速)](https://blog.csdn.net/appleyuchi/article/details/92795620)

[使用 Jsdelivr CDN 加速博客访问速度](https://yafine-blog.cn/posts/ee35.html)

[SEO 优化](https://blog.sky03.cn/posts/42790.html#toc-heading-18)

### [](#部署相关 "部署相关")部署相关

[如何申请阿里云免费 SSL 证书（可用于 https 网站）并下载下来](https://www.cnblogs.com/qiao20/p/11274726.html)

[为自定义域名的 Hexo 博客升级到 Https 网站](https://blog.csdn.net/qq_37683287/article/details/91559605)

[Hexo 博客系列（六）：部署到七牛](http://www.isetsuna.com/hexo/deploy-qiniu/)

[（站长工具）ping 服务器，网站测速](http://ping.chinaz.com/)

[coding 国内部署——传送门](https://coding.net/)

[Hexo 博客部署到码云和 Coding（提高国内访问速度）](https://yafine-blog.cn/posts/51fb.html)

### [](#其它 "其它")其它

[定制个人 logo 强大网站](https://www.logosc.cn/)

[不蒜子官网（如果统计无效，多半是链接失效了，去获取最新的）](http://ibruce.info/2015/04/04/busuanzi/)

[使用 PicGo+Github 搭建免费图床](https://yafine-blog.cn/posts/eb3a.html)

最后，我们压缩完后，有些指令不能用简称了，以下是我部署时常用指令

```
hexo clean
hexo g -s
hexo server
gulp
hexo deploy
```

### [](#总结 "总结")总结

我的博客基本上算是开发完毕了，实现了代码压缩 + CDN 优化 + 国内外双部署

还未完成的部分：备份源码 + SEO 优化，但这些是可选项，后续再花点时间折腾一下就好了，感谢你能看到这篇文章，觉得不错的话，记得点个赞，加个关注！

（如果以上内容能够解决你的问题那就很好了，如果不能解决你的问题，请在评论区留言，看到了立即回复您，然后更新博客，欢迎您的加入！）

[](#第二部分-butterfly-主题搭建美化DIY教程 "第二部分 butterfly 主题搭建美化DIY教程")第二部分 butterfly 主题搭建美化 DIY 教程
----------------------------------------------------------------------------------------

### [](#阅读须知-2 "阅读须知")阅读须知

> 在本文开头就有说明，在此再说明一下，并不是从零搭建 butterfly，只提供相关美化 DIY 教程，主要针对新手，每一步都算比较详细，所以可能会显得比较啰嗦，所以建议基础比较好小伙伴根据目录选择自己感兴趣的部分跳着看，不要文章没看，上来先喷一下！谢谢⊙o⊙

#### [](#Butterfly-主题 "Butterfly 主题")Butterfly 主题

编辑博客根目录 `/themes/Butterfly/layout/includes/footer.pug`文件，

第一步，将以下内容

```
©${theme.since} - ${nowYear} By ${config.author}
```

改为

```
©${theme.since} - ${nowYear + ' '} <i></i> ${config.author}
```

第二步，将以下内容

```
©${nowYear} By ${config.author}
```

改为

```
©${nowYear + ' '} <i></i> ${config.author}
```

将以下内容添加到 `<head></head>` 标签内：

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/HCLonely/images@master/others/heartbeat.min.css">
```

具体放置位置，可以参考下图：  
[![](https://img-blog.csdnimg.cn/20200420132925497.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200420132925497.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
这样，就有一颗跳动的心 ❤啦 ✿✿ヽ (°▽°) ノ✿  
[![](https://img-blog.csdnimg.cn/20200420132948247.png)](https://img-blog.csdnimg.cn/20200420132948247.png)

#### [](#其他主题 "其他主题")其他主题

将`<i></i>`添加到需要显示的位置

同上第 2 步

### [](#添加访客地图 "添加访客地图")添加访客地图

前往 [clustrmaps](https://clustrmaps.com/) 网站注册一个帐号

找到 `Free Tools`下面的 `Website Widget`, 点击 `Get Map Widget`

输入你的博客网址，点击`Next`

根据你自己的喜好选择样式`Map widget`或 `Globe Widget`（本人使用后者）

找到如下代码，记住 `src (****** 的部分)`:

```
<script type="text/javascript" src="\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*">
```

在 `themes\Butterfly\layout\includes\widget`文件夹新建`card_map.pug`文件，文件内容如下：

```
.card-widget.card-map
  .card-content
    .item-headline
      i.fa.fa-globe-asia(aria-hidden="true")
      span= \_p('aside.card\_map')
    script#clstr\_globe(type="text/javascript" defer="defer" src="此处填入你自己的代码")
```

编辑 `themes\Butterfly\layout\includes\widget\index.pug`文件，在你想要显示的位置插入以下代码：

```
if theme.aside.card\_map
        !=partial('includes/widget/card\_map', {}, {cache:theme.fragment\_cache})
```

具体放置位置，可以参考下图：  
[![](https://img-blog.csdnimg.cn/20200419190844832.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419190844832.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
编辑 `butterfly.yml` 文件，在 `card_webinfo` 下面添加一行`card_map: true`

[![](https://img-blog.csdnimg.cn/20200419191112811.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419191112811.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
如果没有图标的话，就将 `fontawesome v5`版本开启

```
\# fontawesome圖標
# 默認使用的是 fontawesome v4版本的圖標
fontawesome\_v5:
  enable: true
```

编辑 `themes\Butterfly\languages\zh-CN.yml`文件 (请根据你的网站语言选择)，找到 **card\_announcement: 公告** , 在下面添加一行 **card\_map: 访客地图** (后面的文本可自定义)

[![](https://img-blog.csdnimg.cn/20200419191159352.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419191159352.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
如果不想显示，直接把 `butterfly.yml`文件的`card_map: true` 改为 `card_map: false` 即可

### [](#添加Pixiv-日榜 "添加Pixiv 日榜")添加 Pixiv 日榜

在 `themes\Butterfly\layout\includes\widget`文件夹新建 `card_pixiv.pug`文件，文件内容如下：

注意：最后三行要保持空格间距一样（直接复制下面代码即可）

```
.card-widget.card-pixiv
 .card-content
  .item-headline
    i.fa.fa-image(aria-hidden="true")
    span= \_p('aside.card\_pixiv')
    iframe(src="https://cloud.mokeyjay.com/pixiv" frameborder="0" )
```

[https://cloud.mokeyjay.com/pixiv](https://cloud.mokeyjay.com/pixiv) 使用的是[超能小紫](https://www.mokeyjay.com/)提供的服务，也可以自行搭建，搭建方式请看[这里](https://www.mokeyjay.com/archives/1063)

编辑 `themes\Butterfly\layout\includes\widget\index.pug` 文件，在你想要显示的位置插入以下代码：

```
if theme.aside.card\_pixiv
        !=partial('includes/widget/card\_pixiv', {}, {cache:theme.fragment\_cache})
```

具体放置位置，参考下图：  
[![](https://img-blog.csdnimg.cn/20200419183941492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419183941492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

编辑 `butterfly.yml`文件，在 `card_webinfo` 下面添加一行 `card_pixiv: true`

可以通过搜索关键词 `aside`，找到对应位置添加  
[![](https://img-blog.csdnimg.cn/20200419184046471.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419184046471.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
编辑 `themes\Butterfly\languages\zh-CN.yml`文件 (请根据你的网站语言选择)，找到 **card\_announcement: 公告** , 在下面添加一行 **card\_pixiv: Pixiv 日榜 Top50**(后面的文本可自定义)

如果不想显示，直接把 `butterfly.yml`文件的 `card_pixiv: true`改为 `card_pixiv: false`即可

### [](#添加日历 "添加日历")添加日历

安装 `hexo-generator-calendar` 插件

```
cnpm install --save git:
```

下载 `calendar.js`和 `languages.js` 文件，保存到 `themes\Butterfly\source\js` 目录

*   [calendar.js](https://github.com/pengloo53/Hexo-theme-light_cn/blob/master/source/js/calendar.js) 下载地址
*   [languages.js](https://github.com/pengloo53/Hexo-theme-light_cn/blob/master/source/js/languages.js) 下载地址

编辑`calendar.js` 文件，在文件最后`}(jQuery));`之前添加:

```
$(document).ready(function () {
    $('#calendar').aCalendar('zh-CN');
});
```

具体位置参考下图：  
[![](https://img-blog.csdnimg.cn/20200419193746630.png)](https://img-blog.csdnimg.cn/20200419193746630.png)

编辑 `butterfly.yml` 文件，以下两个你 `butterfly.yml`文件里有哪个就用那个，不要都用！选择一个即可

*   在 `CDN_USE->js` 下面添加如下内容（本人采用这种方式）：

```
\- /js/calendar.js
- /js/languages.js
```

具体位置参考下图：  
[![](https://img-blog.csdnimg.cn/20200419193929972.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419193929972.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

*   在 `inject->bottom`下面添加如下内容（如果用了上述方法就不要用了）：

```
\- <script src="/js/calendar.js"></script>
- <script src="/js/languages.js"></script>
```

新建 `calendar.styl`文件，保存到 `themes\Butterfly\source\css\_layout` 目录下

[源文件传送门](https://raw.githubusercontent.com/pengloo53/Hexo-theme-light_cn/master/source/css/_partial/calendar.styl)

原下载处使用会有 bug，你可以直接复制如下我改好的代码即可

```
#calendar
  a
    text-decoration none

.cal-head
  margin-bottom: 15px
  position relative
  height 20px
  padding 8px 6px 2px 6px

.cal-prev,.cal-next
  position absolute
  top 9px
  width 16px
  height 18px
  padding 3px 4px
  border 1px solid transparent
  color #333
  outline 0

.cal-prev
  left 8px
  &:before
    border-right 9px solid #333

.cal-next
  right 8px
  &:before
    border-left 9px solid #333

.cal-prev:before,.cal-next:before
  content ''
  display block
  width 0
  height 0
  border-top 5px solid transparent
  border-bottom 5px solid transparent

.cal-title
  width 120px
  margin 0 auto
  color #333
  font bold 14px/18px Arial
  text-align center
  a
    border 1px solid transparent
    color #9f9f9f

.cal,
.cal th,
.cal td
  border 1px solid #d1d1d1

.cal
  display: table
  border-collapse separate
  border-spacing 0
  border-width 1px 0 0 1px
  table-layout fixed
  width 100%
  margin 0
  th
    background #9f9f9f
    color #fff
    border-width 0 1px 1px 0
    font-weight 700
  td
    border-width 0 1px 1px 0
  tbody
    a
      background-color #007acc
      color #fff
      display block
      font-weight 700
    .cal-today
      background-color #66ecfd
      color #fff
  .cal-gray
    color #bbb8b8

\[data-theme='dark'\] .cal .cal-gray
  color #505050

.cal th,
.cal td
  font-weight normal
  line-height 2.5625
  padding 0
  text-align center

\[data-theme='dark'\] .cal .cal-foot
  color #9f9f9f

.cal .cal-foot
  color #2ca6cb

.cal-title a:hover,
.cal-prev:hover,
.cal-next:hover,
.cal .cal-foot:hover,
.cal .cal-foot:focus,
.cal tbody a:hover,
.cal tbody a:focus
  background-color #686868
  color #fff
  cursor pointer
```

在`themes\Butterfly\layout\includes\widget` 文件夹新建`card_calendar.pug` 文件，文件内容如下：

```
.card-widget.card-calendar
  .card-content
    .item-headline
      i.far.fa-calendar-alt(aria-hidden="true")
      span= \_p('aside.card\_calendar')
    div.widget-wrap
    div#calendar.widget
```

编辑`themes\Butterfly\layout\includes\widget\index.pug` 文件，在你想要显示的位置插入以下代码：

```
if theme.aside.card\_calendar
        !=partial('includes/widget/card\_calendar', {}, {cache:theme.fragment\_cache})
```

具体位置参考下图：  
[![](https://img-blog.csdnimg.cn/20200419194253473.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419194253473.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

编辑 `butterfly.yml`文件，在 `card_webinfo`下面添加一行`card_calendar: true`

[![](https://img-blog.csdnimg.cn/2020041919435677.png)](https://img-blog.csdnimg.cn/2020041919435677.png)

编辑`themes\Butterfly\languages\zh-CN.yml`文件 (请根据你的网站语言选择)，找到 **card\_announcement: 公告** , 在下面添加一行 **card\_calendar: 日历** (后面的文本可自定义)

[![](https://img-blog.csdnimg.cn/20200419194436425.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200419194436425.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

如果不想显示，直接把 `butterfly.yml`文件的`card_calendar: true`改为`card_calendar: false` 即可

### [](#添加哔哩哔哩番剧页面插件 "添加哔哩哔哩番剧页面插件")添加哔哩哔哩番剧页面插件

#### [](#安装 "安装")安装

```
npm install hexo-bilibili-bangumi --save
```

#### [](#更新 "更新")更新

```
npm install hexo-bilibili-bangumi --update --save
```

#### [](#配置 "配置")配置

将下面的配置写入站点的配置文件`_config.yml`里 (不是主题的配置文件)。

```
bangumi:
  enable: true 
  vmid: 
  title: '追番列表'
  quote: '生命不息，追番不止！'
  show: 1
  loading: '/img/bangumi-loading.gif'
```

**配置介绍**

*   enable: 是否启用
*   vmid: 哔哩哔哩番剧页面的 vmid(uid), 如何获取？
*   title: 该页面的标题
*   quote: 写在页面开头的一段话，支持 html 语法
*   show: 初始显示页面：0: 想看 , 1: 在看 , 2: 看过，默认为 1
*   loading: 图片加载完成前的 loading 图片

#### [](#使用 "使用")使用

前往你的 Hexo 博客的根目录

输入如下命令

```
hexo new page bangumis
```

找到`source/bangumis/index.md`这个文件

修改这个文件，添加 `type: "bangumis"`：

```
\---
title: bangumis
date: 2018-01-05 00:00:00
type: "bangumis"
---
```

防止请求次数过多插件不再自动获取番剧数据，所以请根据自己的需要在 `hexo generate 或 hexo deploy` 之前使用`hexo bangumi -u` 命令更新番剧数据！

删除数据命令:

```
hexo bangumi -d
```

#### [](#获取-uid "获取 uid")获取 uid

登录哔哩哔哩后前往 [https://space.bilibili.com/](https://space.bilibili.com/) 页面，网址最后的一串数字就是 uid

**效果展示**  
[![](https://img-blog.csdnimg.cn/2020042013115126.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/2020042013115126.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

### [](#添加卡通人物（看板娘） "添加卡通人物（看板娘）")添加卡通人物（看板娘）

输入如下命令获取 live2d：

```
npm install --save hexo-helper-live2d
```

输入以下命令，下载相应的模型，将 `haruto` 更换成你想要的模型名称即可（本人就选 haruto），更多模型选择请[点击此处](https://github.com/xiazeyu/live2d-widget-models)，各个模型的预览请[访问原作者的博客](https://huaji8.top/post/live2d-plugin-2.0/)

```
npm install live2d-widget-model-haruto
```

打开站点目录下的 `_config.yml`文件，添加如下代码：

```
live2d:
	enable: true
	scriptFrom: local
	model: 
		use: live2d-widget-model-haruto #模型选择
	display: 
		position: right  #模型位置
		width: 150       #模型宽度
		height: 300      #模型高度
	mobile: 
		show: false      #是否在手机端显示
```

执行 `hexo g` & `hexo s`，查看页面，发现就会多一个卡通人物啦 ✿✿ヽ (°▽°) ノ✿

[![](https://img-blog.csdnimg.cn/20200420075033482.png)](https://img-blog.csdnimg.cn/20200420075033482.png)

参考：

[Hexo 博客优化之博客美化系列（持续更新）](https://blog.csdn.net/qq_36759224/article/details/85420403)

### [](#地址栏添加-abbrlink "地址栏添加 abbrlink")地址栏添加 abbrlink

**背景：**

不想要 2020/xx/xx/xxx/xx 这样比较长的说明，想要简短一点的。

**解决：**

安装 `hexo-abbrlink` 插件

```
npm install hexo-abbrlink
```

编辑 站点的 `_config.yml`文件，找到 `permalink` , 改成 **permalink: posts/:abbrlink/**

具体位置，可以参考下图：

[![](https://img-blog.csdnimg.cn/20200420073332447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200420073332447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
最后，在你写的文章 front 部分，添加自定义 `abbrlink` 即可。  
[![](https://img-blog.csdnimg.cn/20200420073353594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200420073353594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
地址栏变化，成功 ✿✿ヽ (°▽°) ノ✿  
[![](https://img-blog.csdnimg.cn/20200420073441986.png)](https://img-blog.csdnimg.cn/20200420073441986.png)

### [](#Gallery-相册图库 "Gallery 相册图库")Gallery 相册图库

一个图库集合。

写法

```
<div>
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```

*   name：图库名字
*   description：图库描述
*   link：连接到对应相册的地址
*   img-url：图库封面的地址

例如：

```
<div>
{% galleryGroup '壁纸' '收藏的一些壁纸' '/Gallery/wallpaper' https:
{% galleryGroup '漫威' '关于漫威的图片' '/Gallery/marvel' https:
{% galleryGroup 'OH MY GIRL' '关于OH MY GIRL的图片' '/Gallery/ohmygirl' https:
</div>
```

[![](https://cdn.jsdelivr.net/gh/jerryc127/CDN/img/20191226003414.png)](https://cdn.jsdelivr.net/gh/jerryc127/CDN/img/20191226003414.png)

### [](#豆瓣插件（movie、book、game） "豆瓣插件（movie、book、game）")豆瓣插件（movie、book、game）

#### [](#安装-1 "安装")安装

```
npm install hexo-douban --save
```

在最外层站点 `_config.yml` （⚠️ 注意：不是主题的配置文件）添加如下内容

```
\# 豆瓣
douban:
  user: 211251422
  builtin: true
  book:
    title: '好书推荐'
    quote: '读书好，好读书，读好书'
  movie:
    title: '电影'
    quote: '那些在电影院看过的电影'
  timeout: 10000
```

*   user: 你的豆瓣 ID。打开豆瓣，登入账户，然后在右上角点击 ” 个人主页 “，这时候地址栏的 URL 大概是这样：[https://www.douban.com/people/xxxxxx/](https://www.douban.com/people/xxxxxx/) ，其中的”xxxxxx” 就是你的个人 ID 了。
*   builtin: 是否将生成页面的功能嵌入 hexo s 和 hexo g 中，默认是 false ，另一可选项为 true 。
*   title: 该页面的标题。
*   quote: 写在页面开头的一段话, 支持 html 语法。
*   timeout: 爬取数据的超时时间，默认是 10000ms，如果在使用时发现报了超时的错 (ETIMEOUT) 可以把这个数据设置的大一点。  
    如果只想显示某一个页面 (比如 movie)，那就把其他的配置项注释掉即可

#### [](#配置-config-文件 "配置 config 文件")配置 config 文件

在你的主题的 `butterfly.yml` 文件中配置以下内容，如下：

```
\# 如果你有使用hexo-douban，可配置這個
douban:
   meta: true
   movies\_img: https:
   books\_img: https:
#   games\_img:
```

#### [](#使用-1 "使用")使用

前往你的 Hexo 博客的根目录

输入如下命令

```
hexo new page books
```

找到`source/books/index.md`这个文件

修改这个文件，添加 `type: "books"`：

```
\---
title: 书单
date: 2020-04-19 12:58:56
type: "books"
---
```

同理，对于电影页面

前往你的 Hexo 博客的根目录

输入如下命令

```
hexo new page movies
```

找到`source/movies/index.md`这个文件

修改这个文件，添加 `type: "movies"`：

```
\---
title: 电影
date: 2020-04-19 12:58:56
type: "movies"
---
```

### [](#友链界面加入自定义文字 "友链界面加入自定义文字")友链界面加入自定义文字

具体效果如下：  
[![](https://img-blog.csdnimg.cn/20200424114754770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424114754770.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

#### [](#配置-1 "配置")配置

第一步，在`themes/Butterfly/layout/flink.pug` 文件内加入如下代码：

```
p(style="font-size:14px;font-weight:bold")= theme.PS
hr
h2= theme.require\_headline
ul
  li= theme.requirement1
  li= theme.requirement2
  li= theme.requirement3
  li= theme.requirement4
  li= theme.requirement5
  li= theme.requirement6
hr
h2= theme.myInfo
ul
  li= theme.info1
  li= theme.info2
  li= theme.info3
  li= theme.info4
```

具体位置请参考下图：  
[![](https://img-blog.csdnimg.cn/20200424124244315.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424124244315.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
第二步，在`source/_data/butterfly.yml` 内加入如下代码（位置随意）：

> 这里提供我的模板，当然你需要修改成为你自己的风格。

```
\# 友链界面美化
PS: PS：欢迎交换友链，以下是相关注意事项。
require\_headline: A Few Requirements
requirement1: 本站不参与商业性网站、下载站、视频站等
requirement2: HTTP和HTTPS均可，不强制性要求小绿锁，但是只有一个IP或者带端口的不接受哦
requirement3: 网站要有维护，定期或不定期均可，线下朋友请忽略这一条
requirement4: 申请友链在评论区留言即可，但需先添加本站友链（申请格式如下文所述）
requirement5: 有一定数量的原创文章，建站一周以上（大佬可以无视以上要求）
requirement6: 如果你想联系我，在About页面中有我的相关联系方式
myInfo: My Blog Info
info1: 'name: 超逸の技术博客'
info2: 'link: https://yangchaoyi.vip/'
info3: 'avatar: https://cdn.jsdelivr.net/gh/Chocolate1999/cdn/img/avatar.png'
info4: 'descr: 不是只会写业务代码の前端攻城狮'
```

### [](#友链链接区块加入一行小字 "友链链接区块加入一行小字")友链链接区块加入一行小字

具体效果图如下所示：

[![](https://img-blog.csdnimg.cn/20200424124816463.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424124816463.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

#### [](#配置-2 "配置")配置

第一步，在`themes/Butterfly/layout/flink.pug` 文件内加入如下代码：

```
h4= i.cdescr
```

具体位置，请参考如下：

[![](https://img-blog.csdnimg.cn/20200424124920612.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424124920612.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
第二步，此后我们在`source/_data/link.yml` 中就可以多加一栏变量了，例如：  
[![](https://img-blog.csdnimg.cn/20200424124947577.png)](https://img-blog.csdnimg.cn/20200424124947577.png)

### [](#跳过-hexo-的渲染 "跳过 hexo 的渲染")跳过 hexo 的渲染

或许你会问这个到底有啥用呢？来两张图你就知道了：

[![](https://img-blog.csdnimg.cn/20200424150921963.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424150921963.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
[![](https://img-blog.csdnimg.cn/20200424151000759.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424151000759.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

[Xuexi’s Blog：【参考】Hexo 大结局](https://xiabor.com/2020/04/21/hexo3/#%E5%A6%82%E4%BD%95%E8%B7%B3%E8%BF%87hexo%E7%9A%84%E6%B8%B2%E6%9F%93)

参考了如上博客后，我就增加了这两个界面，因为我们部署到 `github pages` 其实就是静态页面，你明白了 hexo 渲染机制后，你可以做的界面就会更多了，比如有些大佬博客会加入一些游戏，例如`2048`，`3D魔方`等等，这些我后续考虑再加进去。

你所需要的就是找到开源的静态页面，添加进去，然后跳过`hexo`渲染即可。

### [](#友链样式美化 "友链样式美化")友链样式美化

本次更新新增呼吸灯效果，`github`源码仓库已同步更新。  
[![](https://img-blog.csdnimg.cn/20200426160609547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200426160609547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
实现效果步骤如下：

将`themes/Butterfly/layout/flink.pug` 原本的文件内容删去，直接负责替换如下内容：

```
#page
  .flink#article-container
    each i in site.data.link
      h2= i.class\_name
      .post-cards
        .md-links
          each item in i.link\_list
            .md-links-item(style= item.color ? \`--primary-color:${item.color};border-width:${item.width};border-style:${item.style};animation: ${item.custom} ${item.time} infinite alternate; background:${item.background}\` : 'border-width:0px;border-style:solid;animation: link\_custom 0s infinite alternate;background:0')
              a.customcolor(href=item.link  title=item.name target="\_blank" rel=item.remove ? "external nofollow" : "" style=item.namecolor ? \`--namecolor:${item.namecolor}\` : '')
                if theme.lazyload.enable
                  img.lazyload(data-src=item.avatar onerror=\`this.onerror=null;this.src='\` + url\_for(theme.lodding\_bg.flink) + \`'\` alt=item.name,style=item.rotate ? \`--primary-rotate:${item.rotate};--autotime:${item.autotime};\` : '--primary-rotate:0deg' class=item.autorotate ? \`${item.autorotate}\` : '')
                else
                  img(src=item.avatar onerror=\`this.onerror=null;this.src='\` + url\_for(theme.lodding\_bg.flink) + \`'\` alt=item.name )
                .md-links-title= item.name 
                .md-links-des= item.descr
    != page.content
  if page.comments !== false
    include includes/comments/index.pug
```

在主题配置文件 `source/_data/butterfly.yml` 添加如下样式

```
https:
```

具体位置，你可以搜索用`ctrl+f`键搜索`css`，添加进去。  
[![](https://img-blog.csdnimg.cn/20200426160933761.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200426160933761.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
当然，如果你是`clone` 的 `dev` 分支，最新版本的话，可以这样引入 `css`：

具体位置，你可以搜索用`ctrl+f`键搜索`inject`，可以直接覆盖你之前的代码或者添加进去都可以。

```
\# inject
# 插入代码到头部</head>之前 和 尾部</body>之前
inject:
  head:
  # - <link rel="stylesheet" href="xxxxx">
    - <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/sviptzk/HexoStaticFile@master/Hexo/css/flink.min.css">
```

各种参数说明（可自行搭配）如下：

```
\# 边框大小 默认为0 
width: 0px
# 边框样式 默认 solid
style: solid
# 边框颜色 默认淡蓝色 #49b1f5
color: "#0078e7"
# 自动旋转 可选值 flash（闪现） link\_custom（单色呼吸灯） link\_custom1（彩色呼吸灯）
custom: link\_custom1
# 动画时长设定，默认为0
time: 4s
# name的颜色
namecolor: "#ff9191"
# descr的颜色
descolor: "#ff9191"
# 背景颜色
background: 0
# 鼠标悬停旋转角度
rotate: 360deg
# 自动旋转 latuo左旋转 rauto右旋转
autorotate: "lauto"
# 旋转的周期（时长）
autotime: 2s
#移除此链接的权重 0为否 非0为移除
remove: 0
```

参考：[小康博客：Hexo 关于 Butterfly 的一些小修改](https://www.antmoe.com/posts/1dc865d0/index.html)

### [](#添加全局吸底APlayer "添加全局吸底APlayer")添加全局吸底 APlayer

#### [](#第一步 "第一步")第一步

打开 `themes\Butterfly\layout\includes\head.pug`

结尾加一句

```
include ./third-party/aplayer.pug
```

[![](https://img-blog.csdnimg.cn/20200519114724631.png)](https://img-blog.csdnimg.cn/20200519114724631.png)

#### [](#第二步 "第二步")第二步

然后在`themes\Butterfly\layout\includes\third-party\`里面新建一个文件叫 `aplayer.pug` , 内容如下

```
if theme.aplayer && theme.aplayer.enable
	.aplayer(data-id=theme.aplayer.id data-server=theme.aplayer.server data-type=theme.aplayer.type data-fixed=theme.aplayer.fixed data-mini=theme.aplayer.mini data-listFolded=theme.aplayer.listFolded data-order=theme.aplayer.order data-preload=theme.aplayer.preload)
	each item in theme.aplayer.css
		link(rel='stylesheet', href=item)
	each item in theme.aplayer.js
		script(src=item)
```

#### [](#第三步 "第三步")第三步

然后打开`butterfly.yml`(如果你没有启用的话, 就打开`source/_data/butterfly.yml`) 加入以下内容

```
##侧边栏歌单
aplayer:
  enable: true
  js:
    - https:
    - https:
  css:
    - https:
  id: 2693598459
  server: netease 
  type: playlist
  fixed: 'true'
  order: random
  preload: none
  listFolded: 'false'
```

#### [](#解决与TOC冲突问题 "解决与TOC冲突问题")解决与 TOC 冲突问题

然后重新生成就可以看到 `aplayer`了, 这里的 id 是我的网易云歌单号, 可以修改成别的.  
但是浏览 `Page` 时会发现 `aplayer` 会和 `TOC`(怎么又是它) 的切换按钮重合  
打开 `themes\Butterfly\source\css\_global\index.styl`  
修改第 61 行

[![](https://img-blog.csdnimg.cn/20200519114915192.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200519114915192.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)  
最后，大功告成 ✿✿ヽ (°▽°) ノ✿  
[![](https://img-blog.csdnimg.cn/2020051911514933.png)](https://img-blog.csdnimg.cn/2020051911514933.png)

参考：  
Author: [Pscgylotti](http://home.ustc.edu.cn/~pscgylotti/blogs/2020/05/09/butterfly/)

### [](#后续内容 "后续内容")后续内容

**须知：** 由于`CSDN` 对于长文章更新会有人工审核，因此不断更新迭代的话可能会有些许麻烦，有时可能文章会失效，所以目前你所看到的内容其实不是最新版本的，所有后续更新内容都会持续更新在本站内，[https://yangchaoyi.vip](https://yangchaoyi.vip/)

[](#第三部分-分享本站所用的学习资料以及本篇文章所参考的文章 "第三部分 分享本站所用的学习资料以及本篇文章所参考的文章")第三部分 分享本站所用的学习资料以及本篇文章所参考的文章
--------------------------------------------------------------------------------------------

### [](#阅读须知-3 "阅读须知")阅读须知

> 本篇内容以及本站博客搭建都是参考了许许多多的文章，因此可能有些内容遗漏掉您的文章注明出处，您可以在本篇内容底部评论留言，收到消息，我会立即更新文章出处，为您带来打扰实在不好意思。

### [](#butterfly主题添加功能 "butterfly主题添加功能")butterfly 主题添加功能

[GamerNoTitle：【参考】友链界面加入更多的自定义文字](https://bili33.top/2020/03/19/butterfly-customize/#%E5%8F%8B%E9%93%BE%E7%95%8C%E9%9D%A2%E5%8A%A0%E5%85%A5%E6%9B%B4%E5%A4%9A%E7%9A%84%E8%87%AA%E5%AE%9A%E4%B9%89%E6%96%87%E5%AD%97)

[Kp Zhang：为本博客添加新特性记录](https://zkpeace.com/2020/02/17/%E4%B8%BA%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0%E6%96%B0%E7%89%B9%E6%80%A7%E8%AE%B0%E5%BD%95/#%E6%B5%8F%E8%A7%88%E5%99%A8%E6%8E%A8%E9%80%81)

### [](#dalao文档 "dalao文档")dalao 文档

[JerryC：Butterfly 作者文档](https://jerryc.me/categories/Butterfly%E6%96%87%E6%AA%94/)

[洪卫の博客：Hexo+Github 博客搭建完全教程](https://sunhwee.com/posts/6e8839eb.html#toc-heading-4)

[HCLonely Blog：Hexo 博客 DIY](https://blog.hclonely.com/posts/57bd67ce/)

### [](#配置Valine-Admin-邮件回复提醒 "配置Valine Admin 邮件回复提醒")配置 Valine Admin 邮件回复提醒

[赵俊的博客：【参考】Hexo 优化 — Valine 扩展之邮件通知](http://www.zhaojun.im/hexo-valine-admin/)

[Xuexi’s Blog：【参考】配置 Valine Admin 邮件回复提醒](https://xiabor.com/2019/12/28/valine-admin/#valine%E7%9A%84%E9%82%AE%E4%BB%B6%E6%8F%90%E9%86%92)

[](#第四部分-彩蛋 "第四部分 彩蛋")第四部分 彩蛋
-----------------------------

biubiubiu~ 让我猜猜你是不是看了前文说是有彩蛋，直接跳到这里来看了，如果被我猜中的话，请评论如下内容：`我上当了！`

哈哈哈，好了，整点正常点的，正如上文所说，一时间也想不到好的标题，就整个有吸引力的 hhh

**关于本站**

本站源代码开放，同时也欢迎小伙伴们交换友链，具体说明可在 [友链页](https://yangchaoyi.vip/link/) 查看。

上文说了很多，都是关于如何搭建博客，怎样美化，但是一点也没介绍我的`博客文化`，现在就简单介绍一下吧：

首先，我的博客建立之初心还是以学习目的的，并且是与下面 `笔记仓库` 和我的 `CSDN内容` 进行绑定的，后续我都会将优质内容码上去。

[传送门：小狮子前端の学习笔记](https://github.com/Chocolate1999/Front-end-learning-to-organize-notes)  
[![](https://img-blog.csdnimg.cn/20200424154115206.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)](https://img-blog.csdnimg.cn/20200424154115206.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70)

截止到 20 年 4 月 24 日，已经有了 18 个 star（不包括自己 hh），里面多是前端学习整理的笔记，也是选择开源，**因为知识与技术是开源的，但是学习与消化知识是靠的自己。**

我相信，我的这个笔记仓库定会影响一部分人，能让一部分前端甚至普通程序员受益颇多，学习是一辈子都要坚持的事情。坚持下来的人一定很酷~

看到这里的你，应该是比较优秀的了，因为本文多多少少还是些许啰嗦了点，毕竟要写一篇搭建文档嘛，**一个项目的好不好，很大部分就取决你的文档写的够不够优秀。** 因为项目出了 bug，好的文档能够让你事半功倍，而且一份详细的文档，对于二次开发与优化也是极有帮助的！

另外，博主建了一个关于算法的群：ACM/LeetCode/Codeforces 群号：1044593736

**To acmer:**

欢迎各位 acmer 入群，在这里你可以讨论算法，约 cf，讨论面试题，或者你也可以分享转发优质内容，但与学习无关的请勿打扰。群文件已上传部分学习资料，后续会一直补充。加油，少年！

继续补充：从一开始本群只有 10 人不到，到现在快突破 100 人了。从群里没有人冒泡，到现在开始讨论 cf、leetcode、代码等，也算是看到了成长吧，我觉得是一件比较有成就感的事情！很多入群的伙伴，或许是看了我之前写的关于 ACM 江湖的文章，亦或是成为 CSDN 博客专家之路的文章。不管如何，你依旧是曾经那个追风的少年，加油！

最后，来几一句觉得不错的名言吧：

算法改变世界，算法创造未来！

[](#第五部分-总结 "第五部分 总结")第五部分 总结
-----------------------------

一口气没想到就到了总结时刻了，每次总结我都是草草的结束了，但这次来点正式一点的。（这次总结一定要超过 200 字！手动狗头）

### [](#正文 "正文")正文

**神奇の沟通**

*   沟通是 **传递** 沟通是 **交流**
*   沟通是 **分享** 沟通是 **智慧**
*   沟通是 **友谊** 沟通是 **力量**

“ **认识自我、超越自我** “ 是沟通的最高境界

*   当你在项目中感觉所要学习的人和事越来越多时，说明你在 **成长** 。
*   当你感觉要责怪的人和事越来越少时，说明你在 **成熟** 。
*   当你在项目中不断获得了友谊和朋友时，说明你将取得项目的 **成功** 。

人们能够记住的东西有如下规律：

*   **听到**的内容的 5%
*   **读过**的内容的 10%
*   **见过**的内容的 30%
*   **讨论过**的内容的 50%
*   **亲自做**的内容的 75%
*   **教给别人**所做过的事情的 90%

因此，我觉得我如果把我学过的知识开源也是一件有意义的事情，你读完本篇文章后，你学会了搭建博客，你得到了好处，我呢，因为这篇文档，也让自己受益颇多，将知识梳理的同时，也对这件事情记忆深刻了，这难道不是双赢的局面嘛。所以，赶快给本仓库点个 star 吧，[传送门：小狮子前端の学习笔记](https://github.com/Chocolate1999/Front-end-learning-to-organize-notes)。请博主一杯冰阔乐，笑～

本篇博客介绍就到此结束了，完结，撒花✿✿ヽ (°▽°) ノ✿，后续更新内内容的话，上文也有提及过，会更新到 [https://yangchaoyi.vip](https://yangchaoyi.vip/) 里，到时候会置顶的，打开应该就能看到啦~

有什么问题可以在文章最后评论区留言和讨论，当然，你有更加优秀的文章或者新花样，都可以提出来，热烈欢迎~

> 最后，如果项目和教程对你有所帮助或者你看见了还算比较喜欢，欢迎给我 star，谢谢您！