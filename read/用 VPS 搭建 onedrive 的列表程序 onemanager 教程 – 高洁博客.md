> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.ba74.com](https://www.ba74.com/774.html)

onemanager 是 2019 年新出的一款 onedrive 列表程序，与其他列表程序不同地方在于，可以直接从列表网管理文件，包括新建、删除、编辑等。

今天给大家介绍一下，在 vps 上安装 onemanager 的流程。这里推荐直接使用宝塔进行安装配置。安装宝塔，以及 lnmp 环境的过程就不做表述了，如果这块也有不明白的，请具体查看宝塔官网教程。

1、在宝塔里新建站点，跟搭建普通站点一样，填写域名，申请 SSL（非必须），删除站点默认文件。

2、从 github 下载最新的源码 https://github.com/qkqpttgf/OneManager-php/releases，然后上传到网站根目录并解压，将解压的文件移动到站点根目录。

3、设置伪静态，复制粘贴如下代码：rewrite ^(.*) /index.php?/$1 last;

4、根目录下 config.php 设置权限为 666，如图所示：

![](http://inews.gtimg.com/newsapp_ls/0/12200174233/0)

5、访问网站首页，即可进行配置了，如图：

![](http://inews.gtimg.com/newsapp_ls/0/12200178273/0)

6、语言选择简体中文，来到了设置管理员密码的界面，点击 确认重写（伪静态）功能启用，然后输入您要设置的管理员密码，点击确定。稍等一会儿，左上角会出现管理的字样，鼠标移动过去，点击设置，进入后台，如图：

[![](https://www.ba74.com/wp-content/uploads/2020/08/20200802080610100-1024x523.png)](https://www.ba74.com/wp-content/uploads/2020/08/20200802080610100.png)

7、passfile 这个建议设置下，这样后边才能加密某些文件夹，建议随便敲打一些字母作为文件名，比如 sdjasfjsdk.txt；theme 这个，根据自己的喜好来，有的 theme 没有管理文件的功能，有的有，其他一些设置选项，按照需求来，设置完毕之后，点一下那个设置两个字保存。最下面的是添加 onedrive 盘，点击之后，如图：

[![](https://www.ba74.com/wp-content/uploads/2020/08/2020080208064581.png)](https://www.ba74.com/wp-content/uploads/2020/08/2020080208064581.png)

8、标签和显示名称自己根据自己的实际情况填写，主要是针对多盘用户，用作区分使用。下面主要说下挂盘的方法步骤，如果您的盘是国际版，也就是例如 A1、国外 edu 等获取的，那么需要选择 MS：国际版（商业版与个人版）；如果是世纪互联，比如买的 yiyi 的，请选择 CN：世纪互联版，不管是什么版，都建议使用自己申请的应用 ID 与机密，不用 OneManager 默认的，主要是因为 api 有使用限制，一定时间内调用的次数有限，用的人多了难免出问题。下面说下如何申请自己的 api，如果是国际版，请访问 [https://portal.azure.com，如果是世纪互联版，请访问 https://portal.azure.cn，登录自己要注册自己的 api 的账号。下面我就以国际版为例：](https://www.ba74.com/go?url=https://portal.azure.com%EF%BC%8C%E5%A6%82%E6%9E%9C%E6%98%AF%E4%B8%96%E7%BA%AA%E4%BA%92%E8%81%94%E7%89%88%EF%BC%8C%E8%AF%B7%E8%AE%BF%E9%97%AEhttps://portal.azure.cn%EF%BC%8C%E7%99%BB%E5%BD%95%E8%87%AA%E5%B7%B1%E8%A6%81%E6%B3%A8%E5%86%8C%E8%87%AA%E5%B7%B1%E7%9A%84api%E7%9A%84%E8%B4%A6%E5%8F%B7%E3%80%82%E4%B8%8B%E9%9D%A2%E6%88%91%E5%B0%B1%E4%BB%A5%E5%9B%BD%E9%99%85%E7%89%88%E4%B8%BA%E4%BE%8B%EF%BC%9A)

![](http://inews.gtimg.com/newsapp_ls/0/12200193842/0)

9、登录之后，找到 Azure Active Directory 并进入，然后点击左侧的 应用注册

![](http://inews.gtimg.com/newsapp_ls/0/12200196497/0)

然后选择 新注册，应用名称随便，但是建议写简明好记的，比如 onemanager，具体填写和选择的请按照下图，其中重定向 URL 地址为 [https://scfonedrive.github.io/](https://www.ba74.com/go?url=https://scfonedrive.github.io/)

![](http://inews.gtimg.com/newsapp_ls/0/12200202373/0)

注册完之后，复制记录下客户端 ID，备用，然后点击左侧的 证书和密码

![](http://inews.gtimg.com/newsapp_ls/0/12200210185/0)

新增客户端密码，说明随便写，截止期限，选择 从不，然后点击添加，然后一定把这个刚生成的秘钥保存下来，这个只显示一次，以后就看不到了，如果忘了，只能重新生成一个。

然后点击左侧的 API 权限，添加权限，点击 Microsoft Graph，然后点击里面的 委托的权限，找到里面的 Files 类别里的 Files.ReadWrite.All，勾选之后点击添加权限，然后刷新，最后如图所示

[![](https://www.ba74.com/wp-content/uploads/2020/08/2020080208120964-1024x423.png)](https://www.ba74.com/wp-content/uploads/2020/08/2020080208120964.png)

[![](https://www.ba74.com/wp-content/uploads/2020/08/2020080208122845-1024x477.png)](https://www.ba74.com/wp-content/uploads/2020/08/2020080208122845.png)

最后将刚才记录的应用程序 ID 和秘钥，粘贴到 onemanager 程序里，然后确定即可，有的时候可能第一次添加失败，没关系，删除这个盘，重新添加一次即可。

免责声明：本站的资源均来自于互联网，仅为资源共享、学习参考之目的，其版权均归原作者及其网站所有，如有侵权请留言联系。