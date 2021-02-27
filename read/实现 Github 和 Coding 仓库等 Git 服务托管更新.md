\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[www.cnblogs.com\](https://www.cnblogs.com/selier/p/9634418.html)

> 如何使 Github、Coding、Gitee 码云 同时发布更新，多个不同 Git 服务器之间同时管理部署发布提交

**_1_**|**_0_** **缘由**
======================

因为在 Github 上托管的静态页面访问加载速度较为缓慢，故想在 Coding 上再建一个静态页面的项目，方便国内国外访问的分流，使访问的稳定性更高。（此为契机，本文只讲两托管网站仓库的同步更新。Coding 静态页面自定义域名及国内外的 DNS 分流，设置比较简单，搜索一下有很多内容，而且设置过程中我也没碰到问题，就不再赘述）Coding 是国内一个类似 Github 的代码托管网站，同样有 git 的分布式版本控制功能。考虑到 Github 在国内访问的不稳定性，可以将需要管理的项目同时放到 Github 和 Coding 上。最终想要实现的想法为，本地仓库发生更改后能同时更新到 Github 和 Coding 的仓库内。

**_2_**|**_0_** **两个方法**
========================

**_2_**|**_1_** **导入 Github 项目至 Coding**
----------------------------------------

将 Github 上的项目直接导入 Coding，以 Github 下项目仓库 `user_name/repo_name` 为例

1、复制该仓库的 SSH 密钥

[![](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912134825497-1979546688.png)](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912134825497-1979546688.png)

2、在 Coding 上新建一个项目仓库，输入完项目名称 `user_name/repo_name` （仓库名可以和 GitHub 上的不同），然后点击导入仓库，并选择版本控制仓库的类型为 Git，然后将刚才复制的 SSH 密钥粘贴到下图的文本框内，等待导入完成。

[![](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912134908376-1914227133.png)](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912134908376-1914227133.png)

**_2_**|**_2_** **同时更新到 Github 和 Coding**
-----------------------------------------

1、在已有的本地仓库（没有可以从 Github 下载）内找到隐藏的 `.git` 文件夹，打开

2、再打开 `config` 文件

[![](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912135338258-1921236937.png)](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912135338258-1921236937.png)

3、添加如下设置：即设置远端仓库的 url，并命名为 origin

```
\[remote "origin"\]
        url = git@github.com:用户名/仓库名.git
        url = git@git.coding.net:用户名/仓库名.git
        url = git@git.oschina.net:用户名/仓库名.git  # 码云
```

[![](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912135422434-599727150.png)](https://images2018.cnblogs.com/blog/1469487/201809/1469487-20180912135422434-599727150.png)

4、更改仓库内容后，在终端内输入

```
cd .../repo\_name  #定位至本地仓库目录
git add .
git commit -m "commit info"
git push origin  #默认push至远端仓库origin的master分支下
```

这样即可做到对两个托管仓库进行同时更新。

\_\_EOF\_\_

![](https://gitee.com/selierlin/cnblogs-theme/raw/master/img/blog_logo.gif)本文作者：**[Selier](https://www.cnblogs.com/selier/p/9634418.html)**  
本文链接：[https://www.cnblogs.com/selier/p/9634418.html](https://www.cnblogs.com/selier/p/9634418.html)  
关于博主：评论和私信会在第一时间回复。或者[直接私信](https://msg.cnblogs.com/msg/send/selier)我。  
版权声明：本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-nd/4.0/ "BY-NC-SA") 许可协议。转载请注明出处！  
声援博主：如果您觉得文章对您有帮助，可以点击文章右下角**【[推荐](javascript:void(0);)】**一下。您的鼓励是博主的最大动力！