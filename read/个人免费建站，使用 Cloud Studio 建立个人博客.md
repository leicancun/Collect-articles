> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/73998745)

**使用腾讯云 Cloud Studio 免费建立一个个人博客（由于 Cloud Studio 已经升级，该方法可能已经失效）**

前言：对于通过 Github Pages 来建立一个静态网站，相信这是目前大家最常见到免费建站，但是仅通过 Github Pages 建立一个网站是静态的，Jekyll 和 Hexo 是最常用的静态博客，而且他们都是开源项目。使用 Cloud Studio 最大的优点就是一件部署功能，可以部署一个小型的动态博客，这里使用 WordPress 为例。

准备：这边唯一可能需要付费的就是一个域名，现在一些新顶级域名的价格也不高。以及注册 Cloud Studio 账号。

步骤：
---

![](https://pic1.zhimg.com/v2-673085d7519194efd037bc9a65a23660_r.jpg)

创建一个 Cloud Studio 账号，新建工作空间

![](https://pic1.zhimg.com/v2-22339a3cbd659cc96debcd672d986360_r.jpg)

选择 PHP 运行环境，当然新注册的账号需要新建项目

![](https://pic3.zhimg.com/v2-4c2192c8c26eb129fb99e41e4ba842ca_r.jpg)

现在我们先通过终端安装一个软件，搭建过程中会使用到。腾讯云使用的是 Ubuntu 16.04 LTS，以下命令可以直接使用。相关命令：

```
sudo apt-get update #获取镜像更新
sudo apt-get install unzip #安装unzip

```

![](https://pic3.zhimg.com/v2-248d96faac53c35cda96170717290f42_r.jpg)

由于不支持文件夹上传和超过 10M 的文件上传，这边提供两个方法。首先是在 WordPress 官网获取压缩包，解压，重新打包成两个小于 10M 的压缩包，上传，通过 unzip 命令解压。第二种方法是，通过官网获取压缩包的下载链接，使用 wget 命令获取，然后再使用 unzip 命令解压。相关命令：

```
wget https://wordpress.org/latest.zip #获取WordPress安装包,链接自己找
unzip WordPress.zip #解压安装包，包名自行修改

```

![](https://pic2.zhimg.com/v2-ec13f9cd9b9b05401dea475101657669_r.jpg)![](https://pic3.zhimg.com/v2-b80a897af27f46eccaeac4bc1f012726_r.jpg)

自此，所有的工作的开始了。在部署前我们需要删除一些代码，这是 WordPress 的一个 bug, 不处理的话可能会导致通过 WordPress 仪表盘编辑 PHP 文件时报错。找到目录下的 / wp-admin/includes/file.php 文件，删除 492 行到 599 行的命令。

```
if ( $is_active && 'php' === $extension ) {    #部分代码

```

![](https://pic4.zhimg.com/v2-8e1226c35dade0ae9ac3e165376983d7_r.jpg)

过版本里的提交会推送之后，就可以开始一键部署了。一键部署会分配一个域名，当然也可以绑定自己的域名。绑定域名在一键部署里有，通过将域名 CNAME 解析到网站空间。

![](https://pic4.zhimg.com/v2-fd74df48d34f6670479020382960f69b_r.jpg)

访问测试域名或者绑定的域名，显示图中的页面说明步骤很顺利。在一键部署的资源管理里可以看到数据库的连接信息。这里为我们提供了一个 128M 的网站空间和数据库空间。

![](https://pic3.zhimg.com/v2-1c4f576fcf15b74aa6941b8f8b5e94da_r.jpg)![](https://pic3.zhimg.com/v2-cf1c052a7ec53e1dba6971967713f452_r.jpg)![](https://pic2.zhimg.com/v2-56712a766a524de63e4f621e47eec851_r.jpg)

填写数据库连接信息之后即可完成安装，由于这是个测试网站，在完成教程后就删除，所有这里就不打码了。

![](https://pic3.zhimg.com/v2-d62c16f42bcc935be28a7f4bd1bc583a_r.jpg)![](https://pic2.zhimg.com/v2-0fb70d58d0c682afa0a2092e84ef960d_r.jpg)

至此网站就成功部署了，关于 WordPress 的操作就自行完成了。

![](https://pic3.zhimg.com/v2-718bbec8778f29fb35ed537fd6206466_r.jpg)

关于删除自豪的采用 WordPress 的方法，仪表盘 - 外观 - 编辑 - footer.php 文件，删除图中所示代码即可。是否删除自行判断。

相关事项：
-----

1.  在 Cloud Studio 里修改网站文件，每次都需要重新部署才会更新到网站空间里。
2.  由于网站空间较小，建议配合七牛云的 CDN 来使用，对于一个小网站，对象存储免费的空间都足够使用。
3.  使用 Cloud Studio 来部署 WordPress，请查看 WordPress 的相关版权文件。
4.  欢迎转载，转载请注明出处。