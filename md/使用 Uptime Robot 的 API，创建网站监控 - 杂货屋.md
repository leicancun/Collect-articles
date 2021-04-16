> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [sword.studio](https://sword.studio/115.html)

本文最后更新于 2018 年 11 月 25 日， 已超过 823 天没有更新。 如果文章内容或图片资源失效，请留言反馈，我会及时处理，谢谢！

简介
--

Uptime Robot 是一个国外免费的网站 / 服务器在线率监控服务，每 5 分钟检查一次你设定的网站 / 服务，最多可以免费检查 50 个网站 / 服务。  
当你的网站宕机时，Uptime Robot 就会通过你资料里设置好的邮件或者短信通知你，需要注意的一点是 Uptime Robot 的短信服务不支持中国，想用的话可以通过 Google Voice 来接收。

源码搭建及使用
-------

监控使用可以参考以前的文章 [https://agint.me/14.html](https://sword.studio/go/aHR0cHM6Ly9hZ2ludC5tZS8xNC5odG1s)

这里说的主要是利用源码搭建自己的监控界面

项目地址：[https://github.com/HeadTalker/uptime-robot](https://sword.studio/go/aHR0cHM6Ly9naXRodWIuY29tL0hlYWRUYWxrZXIvdXB0aW1lLXJvYm90)

汉化版[下载](https://sword.studio/go/aHR0cHM6Ly9maWxlLmFnaW50Lm1lLyVFNiVCQSU5MCVFNyVBMCU4MS91cHRpbWUtcm9ib3QucmFy)

1、下载源码并解压到站点根目录。php 环境即可

2、获取 API，进入后台：[https://uptimerobot.com/dashboard.php#mySettings](https://sword.studio/go/aHR0cHM6Ly91cHRpbWVyb2JvdC5jb20vZGFzaGJvYXJkLnBocCNteVNldHRpbmdz) ，拉到最底部，API Settings 这块，如下图：  
[![](https://www.ituku.me/images/6MoA.png)](https://www.ituku.me/images/6MoA.png)

3、修改 /php 目录下的 config.php 文件，第 9 行 修改为自己的 API 改为自己的 API。

4、访问站点域名即可

演示地址： [http://status.cso.cx/](https://sword.studio/go/aHR0cDovL3N0YXR1cy5jc28uY3gv)

* * *

> 站点名称：Sword's Blog 杂货屋
> 
> 本文链接：[https://sword.studio/115.html](https://sword.studio/115.html)
> 
> 本博客所有文章除特别声明外，均采用[知识共享署名 - 非商业性使用 4.0 国际许可协议](https://sword.studio/go/aHR0cHM6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL2xpY2Vuc2VzL2J5LW5jLzQuMC9kZWVkLnpo) 进行许可  
> 
> 您可以自由的转载和修改，但请务必注明文章来源并且不可用于商业目的