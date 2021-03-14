> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.naibabiji.com](https://blog.naibabiji.com/tutorial/wordpress-sheng-ji-jiao-cheng.html)

WordPress 后台提示有新版本可以更新了，在实际情况中，往往会碰到自动更新 WordPress 失败的情况，奶爸建网站笔记这里跟大家分享下 WordPress 手动更新的几种方法。

**文章目录** [隐藏](#) [1. 自动更新 WordPress](#zi_dong_geng_xinWordPress) [2. 手动更新 WordPres 报错](#shou_dong_geng_xinWordPres_bao_cuo) [3. 手动升级 WordPress 的方法](#shou_dong_sheng_jiWordPress_de_fang_fa) [3.1. 方法一：下载离线包手动更新](#fang_fa_yi_xia_zai_li_xian_bao_shou_dong_geng_xin) [3.2. 方法二：使用插件更新](#fang_fa_er_shi_yong_cha_jian_geng_xin) [3.3. 方法三：使用代码 + 压缩包更新](#fang_fa_san_shi_yong_dai_maya_suo_bao_geng_xin) [3.4. 方法四、宝塔面板手动更新 WordPress 教程](#fang_fa_si_bao_ta_mian_ban_shou_dong_geng_xinWordPress_jiao_cheng) [3.5. 方法五、通过 ssh 命令手动更新 WordPress](#fang_fa_wu_tong_guossh_ming_ling_shou_dong_geng_xinWordPress)

自动更新 WordPress
--------------

自动更新 WordPress 很简单，直接后台点击更新按钮就可以了。如果你使用的是国外的虚拟主机，通常都不需要你点更新按钮，当有新版本后系统会自动为你更新到新版版本。

当然也可能你的虚拟主机商没有给你开启自动更新功能，所以你自己点击一次更新按钮就可以了。

但是国内的服务器因为网络问题，通常就会出现更新失败的情况，这个时候我们就需要手动更新来解决这个问题了。

手动更新 WordPres 报错
----------------

如果自动更新 WordPress 失败，那么就只能手动更新了，最常见的更新 WordPress 失败提示就是 “另一更新正在进行”

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557324276-naibabiji.com_2019-05-08_21-42-12.jpg)

碰到这个提示，你去网上搜索，基本上的解决办法都是让你去数据库删除一个 core_updater.lock 的表文件。

网上基本上的方法都是让你进入网站数据库（通过 phpmyadmin 或者 ssh 如如命令方式）

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557324404-naibabiji.com_2019-05-08_21-45-19.jpg)

在 wp_options 表里面搜索 core_updater.lock，可以找到一项数值。然后删除它再重新更新就行了。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557324405-naibabiji.com_2019-05-08_21-45-37.jpg)

但是，这个方法针对国内主机并不是 100% 管用，因为国内主机访问 [WordPress](https://blog.naibabiji.com/an-zhuang-wordpress "查看更多“查看更多WordPress”的文章") 服务器的速度并不稳定，很可能下载不成功，导致升级失败，所以这个时候你就需要手动给 WordPress 升级了。

另外**国内服务器自动更新失败了还容易出现白屏或者报错的情况**。

这个时候你只需要重新手动更新一次就能解决问题了。

手动升级 WordPress 的方法
------------------

### 方法一：下载离线包手动更新

你可以自己下载新版版本的 WordPress 安装包，然后自己手动更新。

新版版的 WordPress 离线安装包下载可以参考此文：[WordPress 新版中文简体版本地下载](https://blog.naibabiji.com/files/wordpress-xia-zai.html)

下载完毕后，**手动更新 WordPress 的方法为**：

*   ①. 解压下载的安装包，删除里面的 wp-content 文件夹；
*   ②. 用 FTP 删除**服务器上的** wp-admin 和 wp-includes 两个文件夹；
*   ③. 把本地剩余的文件上传到服务器覆盖所有文件；
*   ④. 登录 WordPress 网站后台，看是否有更新数据库的请求，有就更新，无就已经更新完毕。

1、把下载下来的压缩包解压，然后进入 [WordPress](https://blog.naibabiji.com/an-zhuang-wordpress "查看更多“查看更多WordPress”的文章") 文件夹里面，删掉 wp-content 文件夹。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557324850-naibabiji.com_2019-05-08_21-53-54.jpg)

2、然后使用 FTP 软件连接到服务器，进入你网站根目录，删除 wp-admin 和 wp-includes 两个文件夹。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557324875-naibabiji.com_2019-05-08_21-52-40.jpg)

3、然后把剩下的文件全部上传到服务器上面，覆盖掉原来的文件，再进入 WordPress 网站后台，如果需要更新数据库会提醒你，点击更新即可，不需要更新数据库，那么这次[手动更新 WordPress](https://blog.naibabiji.com/tutorial/wordpress-sheng-ji-jiao-cheng.html) 就完成了。

### 方法二：使用插件更新

**更新：**插件可以直接使用 [WP Downgrade](https://blog.naibabiji.com/tutorial/wp-downgrade.html)，可以任意[安装新老版本的 WP](https://blog.naibabiji.com/tutorial/wp-downgrade.html)。

我爱水煮鱼博主写了一个中文下载镜像的插件，插件会自动在你升级中文版本 WordPress 的时候把下载镜像切换到插件里面指定的网址，升级完毕后禁用插件即可。

**插件代码如下：**

```
<?php
/*
Plugin Name: WPJAM 中文下载镜像
Plugin URI: https://blog.wpjam.com/project/wpjam-basic/
Description: WPJAM 中文下载镜像
Version: 1.0
Author: Denis
Author URI: http://blog.wpjam.com/
*/
add_filter('site_transient_update_core', function($value){
	foreach ($value->updates as &$update) {
		if($update->locale == 'zh_CN'){
			$update->download	= 'http://www.xintheme.cn/download/wordpress-zh_CN.zip';
			$update->packages->full	= 'http://www.xintheme.cn/download/wordpress-zh_CN.zip';
		}
	}

	return $value;
});
```

**插件使用方法：**

把上面的代码保存为一个 php 文件，然后上传到服务器的 wp-content/plugins 目录下，后台启用插件再点击更新按钮即可。

你也可以直接[点击这里下载](https://blog.naibabiji.com/wp-content/uploads/2019/11/wpjam-download.zip)奶爸保存好的插件文件，直接通过网站后台上传 zip 压缩包安装插件启用并更新。

**插件注意事项：**

插件里面提供的下载地址速度并不快（可能更新时会下载超时导致失败），你可以自己把安装包传到你自己服务器后修改链接实现快速下载。

另外，现在国内开发者开发的 [wp china yes](https://blog.naibabiji.com/files/wp-china-yes.html) 和 [kill 429](https://blog.naibabiji.com/files/kill-429.html) 这两款插件也可以帮助你实现后台自动更新的功能。

### 方法三：使用代码 + 压缩包更新

这个方法来自龙笑天下博客，和方法二类似，看上去似乎更加简单便捷，同样可以**解决** **429 Too Many Requests 错误**，具体使用方法如下:

1.  下载 WordPress 安装包文件，改名为 wordpress.zip
2.  上传 wordpress.zip 到你网站根目录
3.  复制下面的代码到主题函数文件
4.  后台点击更新
5.  更新完毕，删除函数代码

```
/**
 * 临时更改WordPress程序包地址以便WP在线更新成功 - 龙笑天下
 * https://www.ilxtx.com/how-to-update-wordpress-successfully.html
 */
function lxtx_site_transient_update_core( $value ){
    foreach ($value->updates as &$update) {
        $update->download = home_url( 'wordpress.zip' );
        $update->packages->full = home_url( 'wordpress.zip' );
    }
    return $value;
}
add_filter('site_transient_update_core', 'lxtx_site_transient_update_core');
```

如果你不会添加代码到主题函数文件里面可以使用下面这款插件帮忙。

[安全添加代码到 functions.php 文件的方法：Code Snippets](https://blog.naibabiji.com/tutorial/wordpress-code-snippets.html)

### [![](https://img.wordpressjc.com/wp-content/uploads/2019/11/429toomanyrequest.png?_upt=89b0def51573846113)](https://img.wordpressjc.com/wp-content/uploads/2019/11/429toomanyrequest.png?_upt=89b0def51573846113)

### 方法四、宝塔面板手动更新 WordPress 教程

首先进入宝塔面板后台（[宝塔面板忘记后台登录网址怎么办](https://blog.naibabiji.com/tutorial/zhao-hui-bao-ta-hou-tai-wang-zhi.html)）

从左边导航栏的【文件】进入你网站根目录，然后点击远程下载，[下载新版的 WordPress 安装包](https://blog.naibabiji.com/files/wordpress-xia-zai.html)。

直接点击确定。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325563-naibabiji.com_2019-05-08_22-19-25.jpg)

下载完毕后，在下载下来的压缩包上点击解压。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325564-naibabiji.com_2019-05-08_22-20-05.jpg)

解压保持默认，直接点击解压按钮。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325566-naibabiji.com_2019-05-08_22-21-02.jpg)

选中 wp-admin 和 wp-includes 文件夹，然后删除。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325567-naibabiji.com_2019-05-08_22-21-40.jpg)

点击 WordPreess 文件夹进入，删除里面的 wp-content 文件夹（其实这个文件夹里面就是几个默认主题和默认插件，你不是用的默认主题这一步删不删影响不大）

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325568-naibabiji.com_2019-05-08_22-22-19.jpg)

然后全选 [WordPress](https://blog.naibabiji.com/an-zhuang-wordpress "查看更多“查看更多WordPress”的文章") 文件夹里面的内容，选择【剪切】

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325774-naibabiji.com_2019-05-08_22-22-47.jpg)

回到你网站根目录，粘贴所有即可。

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557325576-naibabiji.com_2019-05-08_22-23-16.jpg)

然后访问后台查看，用宝塔面板手动更新 WordPress 的教程就结束了。

### 方法五、通过 ssh 命令手动更新 WordPress

通过 ssh 命令操作起来也简单，不过新手可能不是很熟练，操作的要好谨慎。

下面已 LNMP 一键包安装的环境演示，具体命令如下：

```
cd /home/wwwroot/website
```

上面的 website 替换成你自己网站的文件夹。

```
wget https://wordpress.org/latest.zip
unzip latest.zip
rm -rf wp-admin
rm -rf wp-includes
cd wordpress
rm -rf wp-content
mv -f * ..
```

上面的命令就把 WordPress 升级好了，直接去后台看结果就行。

但是，你可能会在以后使用中碰到下图这个问题

![](https://img.wordpressjc.com/wp-content/uploads/2019/05/1557326447-naibabiji.com_2019-05-08_21-58-45.jpg)

在下次自动升级 WordPress 或者安装插件的时候提示 “要执行请求的操作，WordPress 需要访问您网页服务器的权限。 请输入您的 FTP 登录凭据以继续。 如果您忘记了您的登录凭据（如用户名、密码），请联系您的网站托管商。”

这是因为我们 ssh 升级 WordPress 的时候用的 root 账号，而网站是 www 用户，所以我们需要使用下面的命令更改权限。（命令接着上面的命令操作）

```
cd ..
chomd -R 755 *
chown -R www:www *
```

好了，这篇手动升级 wordPress 的教程就结束了，应该是全网最全的关于 WordPress 升级的教程了。

**2.4** / **5** ( **19** votes )