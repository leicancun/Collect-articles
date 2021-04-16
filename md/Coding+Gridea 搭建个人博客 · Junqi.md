\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[junqifu.github.io\](https://junqifu.github.io/article/81d814de/)

[![](https://junqifu.github.io/article/81d814de/10.jpg)](https://junqifu.github.io/article/81d814de/10.jpg "我的首页")  

先看结果，让你知道我在做什么

这是我网站的首页，链接在这里👉[Junqi-Notes](http://junqifu.xyz/)

[![](https://junqifu.github.io/article/81d814de/11.jpg)](https://junqifu.github.io/article/81d814de/11.jpg "我的文章页")  
T06040001

[](#1-先了解Gridea是什么？ "1.先了解Gridea是什么？")1\. 先了解 Gridea 是什么？[](#1-先了解Gridea是什么？)
-----------------------------------------------------------------------------

Gridea 官方网址在这里👉[Gridea](https://gridea.dev/)

为什么要用 Gridea（静态博客写作客户端）？如果是新手的话，还没用过 hexo 等，可自动忽略本条  
我开始用 hexo + Github 编写博客，当然仅供自己日常记录 [hexo](https://hexo.io/zh-cn/) 只能将本地编辑好的 [Markdown](https://baike.baidu.com/item/markdown/3245829?fr=aladdin) 文件推送到 Github，并且每次推送新的文章都需要重复 hexo 三连，hexo 配置和主题的设置也是超级复杂的，so 你懂的作为一个懒人，我想有没有一个东西能够实现编辑 Markdown 文件后一键推送至 [GitHub](https://github.com/) 或者其他 Pgae 上并且使用和操作都非常便捷呢？ 于是我找到了 [Gridea](https://gridea.dev/)

> 相信你应该基本了解什么是 [Gridea](https://gridea.dev/) 了，下面就开始实际操作吧！

[](#2-安装与本地预览 "2.安装与本地预览")2\. 安装与本地预览[](#2-安装与本地预览)
---------------------------------------------------

安装就很简单了，官网下载安装包，Gridea 目前支持 windows、Linux、Mac  
[![](https://junqifu.github.io/article/81d814de/4.jpg)](https://junqifu.github.io/article/81d814de/4.jpg "Gridea官网")

安装完成后，点击预览就可以在浏览器查看效果了  
[![](https://junqifu.github.io/article/81d814de/12.jpg)](https://junqifu.github.io/article/81d814de/12.jpg "Gridea主页")

可以在主题中修改主题的样式，Gridea 客户端内置了四个主题，目前来说 Gridea 主题样式还是比较单一没有 hexo 的多  
而且在个性化上主题上没有 hexo 那么多插件可以选择（本人觉得就单单说平常写写日志文章来说够了）  
[![](https://junqifu.github.io/article/81d814de/13.jpg)](https://junqifu.github.io/article/81d814de/13.jpg "Gridea主题市场")

[![](https://junqifu.github.io/article/81d814de/14.jpg)](https://junqifu.github.io/article/81d814de/14.jpg "Gridea客户端主题设置")

到目前为止，其实完全可以开始写你的日记了，在文章页面，新建一个文档，编辑完成后预览就 OK 了  
如果你想把你的笔记放到云端存储，同时希望分享给其人你的笔记，那就继续观看下面的文档吧

[](#3-coding-配置 "3.coding 配置")3.coding 配置[](#3-coding-配置)
---------------------------------------------------------

1.  [Coding](https://dev.tencent.com/production) 简介
    
    ```
    最适合研发团队的项目协作工具
    CODING 个人版包含了任务、Wiki、文件等功能。支持多成员协作，并且深度集成了代码仓库的操作与状态。
    代码托管功能除了提供高性能远端 Git 仓库外，还支持代码审查、Bug 跟踪和一键部署等功能，
    真正符合研发团队的工作模式。
    ```
    

> 需要注意的是，不要注册到 Coding 企业版去了，在 coding 企业版中，Coding Pages 是没有，个人版在这里👉[Coding 个人版](https://dev.tencent.com/production)

[![](https://junqifu.github.io/article/81d814de/6.jpg)](https://junqifu.github.io/article/81d814de/6.jpg "Coding官网")

2.  注册登录认证一套手续后，就可以新建仓库了  
    [![](https://junqifu.github.io/article/81d814de/15.jpg)](https://junqifu.github.io/article/81d814de/15.jpg "Coding新建项目")  
    新建项目需要注意一点的是，建议项目名称和项目路径名称一致，注意勾选上公开源代码和启用 README.md
3.  项目新建完成后可以开启 Page 服务👇  
    [![](https://junqifu.github.io/article/81d814de/16.jpg)](https://junqifu.github.io/article/81d814de/16.jpg "Coding开启Page")  
    进入页面之后勾选同意服务协议，一键开启就 OK 了
4.  设置访问令牌  
    [![](https://junqifu.github.io/article/81d814de/17.jpg)](https://junqifu.github.io/article/81d814de/17.jpg "Coding开启Page")  
    设置访问令牌，记录下设置完成后的 token 值，后面需要用到
5.  目前位置 Coding 配置就完成了

> ps：还需要注意一点是把本地的 SSH 公钥设置一下，如果你用过 GitHub 那就参照着来就行 参考信息[如何配置 SSH 公钥访问 git 仓库？](https://coding.net/help/doc/git/ssh-key.html)  
> [![](https://junqifu.github.io/article/81d814de/18.jpg)](https://junqifu.github.io/article/81d814de/18.jpg "Coding开启Page")

[](#4-Gridea本地基础配置 "4.Gridea本地基础配置")4.Gridea 本地基础配置[](#4-Gridea本地基础配置)
----------------------------------------------------------------------

我的配置页  
[![](https://junqifu.github.io/article/81d814de/1.jpg)](https://junqifu.github.io/article/81d814de/1.jpg "Gridea基础配置")  
说一下基本的配置信息  
域名就是 Gridea Page 访问的域名，见下图👇  
[![](https://junqifu.github.io/article/81d814de/19.jpg)](https://junqifu.github.io/article/81d814de/19.jpg "Gridea基础配置")  
仓库就是你的仓库名了  
分支一般默认是 master  
仓库用户名和邮箱就不多说了  
Token 就是你上面保存的访问令牌的 Token 值  
至于 CNAME ，如果你想要更改 CodingPage 域名换成你自己的域名就在这里设置，现在先留着空，不用管  
接下来直接点击检测远程连接看看是否成功，报错的话就需要重新检查一下你填写的上述内容是否正确  
（Gridea 客户端在这里的优化也不是很好，没有详细的错误提示信息，只能自己一项一项测试错误在哪里）  
如果显示链接成功就可以点击保存，在左下角找到同步按钮，一键同步完成了！！

现在你可在 Coding 中查看自己的仓库是否有内容提交，有的话，就可以直接访问你的 CodingPage 页面，内容就会直接呈现了

> 文章没看懂？有没有视频？视频链接在这里！[Suremotoo](https://www.bilibili.com/video/av54298548)

> ps: 网站域名设置和评论设置见下篇文章，目前就写到此处，有疑问欢迎评论和发邮件至 1769459858@qq.com

### [](#教程适用：GitHub、Git-有部分基础 "教程适用：GitHub、Git 有部分基础")教程适用：GitHub、Git 有部分基础[](#教程适用：GitHub、Git-有部分基础)

[](#结尾 "结尾")结尾[](#结尾)
---------------------

学习不是一件简单的事情，如果你没有计划和安排，一切都是浮云