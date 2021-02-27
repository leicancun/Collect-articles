\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[logi.im\](https://logi.im/script/unblocking-netease-music-without-perception.html)

得益于对网易云及其他音乐平台 API 的逆向，大佬们逐渐意识到，可以使用第三方音源替换网易源，从而实现解锁网易云付费和无版权歌曲的效果。此类插件最早兴起于 Android 的 Xposed 平台，几经转手，[音量增强器](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL2JpbjQ1Njc4OS9VbmJsb2NrMTYzTXVzaWNDbGllbnQtWHBvc2VkL3JlbGVhc2Vz) 终成集大成者，初版至今已有 3 年有余。然而随着各大音乐平台限制日益严格，加上作者精力有限，这一插件看起来即将淡出历史舞台，其继任者则是现今如日中天，专注于对接各大音源和网易云的 [UnblockNeteaseMusic](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL25vbmRhbmVlL1VuYmxvY2tOZXRlYXNlTXVzaWM=)。该项目基于 Nodejs，以通用代理形式向外提供服务，可运行于几乎所有操作系统，已衍生出 [路由](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL21heGxpY2hlbmcvbHVjaS1hcHAtdW5ibG9ja211c2lj)、[Xposed 插件](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL25pbmluZzM3Ny9VbmJsb2NrTXVzaWNQcm9fWHBvc2Vk) 等多种特定环境下的无感知使用形式。而我今天介绍的，则是 Windows 和 Android 平台下，相对无感知的使用方法。

Android
-------

Android 平台，可以使用 [Taichi](https://logi.im/go/aHR0cHM6Ly90YWljaGkuY29vbC96aC8=) 搭配 [UnblockMusicPro\_Xposed](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL25pbmluZzM3Ny9VbmJsb2NrTXVzaWNQcm9fWHBvc2VkL3JlbGVhc2Vz) 无感知解锁。

Windows
-------

Windows 7 如无法执行则需 [升级 Powershell](https://logi.im/go/aHR0cDovL2Jsb2cudnVlYWRtaW4ub3JnL2luZGV4LnBocC9hcmNoaXZlcy84OQ==) 到 3.0 以上，XP 不支持

### 安装代理

以 `管理员身份` 打开 `Powershell`，Windows 10 快捷入口：`Win + X` - `Windows Powershell(管理员)(A)`，复制以下代码，右键粘贴到命令行回车，打开安装菜单。

```
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force
Invoke-Expression -Command (Invoke-WebRequest -UseBasicParsing -Uri https://bit.ly/2PoNlad).Content

```

随后选择 `1` 即安装。安装完毕后选择 `3` 运行。如需添加开机自启，则执行 `7`。最后输入 `0` 退出。

```
\----------------------------
     网易云解锁安装脚本
            V0.02 2019.09.12
                @AUTHOR LOGI
----------------------------
0. 退出
1. 安装
2. 卸载
3. 运行
4. 停止
5. 更新
6. 局域网共享
7. 添加开机自启
8. 取消开机自启
----------------------------
请选择:

```

### 设置代理

打开网易云音乐 PC 客户端（非 UWP 版），进入 `设置` - `工具`。将 `Http 代理` 改为 `自定义代理、HTTP代理`，服务器地址为 `127.0.0.1`，端口是 `6666`，最后点击 `确定` 重启网易云。

![](https://img11.360buyimg.com/img/jfs/t1/51016/5/10241/41312/5d76dcdaE953ed117/3d8875e29b5584d2.jpg)

以上便是全部步骤，今后便可无感畅听大部分付费和无版权歌曲。如使用一段时间后无法解锁，则需要重新执行命令，选择 `5` 更新。

### 局域网共享

在代理运行的情况下，程序支持为局域网下其他设备提供代理，包括但不限于电脑、手机和平板等。下面以 Android 设备为例，其他设备的设置大体相同。

成功运行代理后，进入菜单 `6` 局域网共享，此时程序将显示本机 IP 和代理所在端口。

```
\----------------------------
      WIFI 手动代理配置
主机名：192.168.0.13
端  口：6666
----------------------------
请按任意键继续...

```

进入安卓手机的 `设置` - `WLAN` 设置。点击所连 WIFI 名称右侧的 `向右箭头`，进入详细设置。

将 `代理` 模式改为 `手动`，`主机名` 和 `端口` 根据上面获取到的信息填写。最后点击右上角的 `对号` 按钮保存。

![](https://img14.360buyimg.com/img/jfs/t1/77817/32/12791/128963/5da1b27eE7b71eee3/2780d4544c9a60e3.png)

根据 [作者说明](https://logi.im/go/aHR0cHM6Ly9naXRodWIuY29tL25vbmRhbmVlL1VuYmxvY2tOZXRlYXNlTXVzaWMvaXNzdWVzLzY1I2lzc3VlY29tbWVudC00OTM3MTg0Mzk=)，iOS 设备还需安装 CA 证书。首先点击 [该链接](https://logi.im/go/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL25vbmRhbmVlL1VuYmxvY2tOZXRlYXNlTXVzaWMvbWFzdGVyL2NhLmNydA==) 添加证书，随后在 `设置` > `通用` > `关于本机` > `证书信任设置` 下，手动开启证书，具体参考 [Apple 官方说明](https://logi.im/go/aHR0cHM6Ly9zdXBwb3J0LmFwcGxlLmNvbS96aC1jbi9IVDIwNDQ3Nw==)。

使用这种方式，一旦电脑关闭，设备将无法联网，必须将 WIFI 代理改回成 `无`，所以并非无感知解锁。

如有问题请在下方留言，文章转载请注明出处，详细交流请加下方群组！请大佬不要屏蔽文中广告，因为它将帮我分担服务器开支，如果能帮忙点击我将万分感谢。

[TG 大佬群](tg://resolve?domain=pubg2333) [QQ 大佬群](https://jq.qq.com/?_wv=1027&k=5RTZaWd) [QQ 追番群](https://jq.qq.com/?_wv=1027&k=5Yje1wK)