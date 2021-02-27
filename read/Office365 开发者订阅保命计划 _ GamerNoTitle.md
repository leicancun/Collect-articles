\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[bili33.top\](https://bili33.top/2020/04/27/Office365-Renew-Project/)

上次有一篇[文章](/2019/08/30/Office365/)教大家怎么白嫖了 Office365 E3 Subscription for Developers（现在是 E5），近期我重新申请了一次（之前的过期了），在这里教大家怎么增大微软续费的机会

只是增大机会，并不是一定会续费！！！

我已经续费成功一次了，截图在底部

### [](#自建网盘法 "自建网盘法")自建网盘法

Office365 的 E5 订阅附带了 5T 的 Onedrive（如果你是 1T 可以去 [Onedrive 后台](https://admin.onedrive.com/?v=StorageSettings)进行调整）

这里我推荐使用 [Oneindex](https://github.com/qupb/oneindex)，使用方便

只需要自己找一个服务器搭建，使用自己的账号获取 API 的 ID 和 KEYS 绑定即可，记得多用，怎么部署不多说

### [](#E5Sub-bot法 "E5Sub_bot法")E5Sub\_bot 法

如果你有服务器也可以自己搭建，项目地址在这里 [https://github.com/iyear/E5SubBot](https://github.com/iyear/E5SubBot)

怎么搭建就去看官方文档，这里说一下没有服务器怎么弄

我们先打开 Telegram，在搜索栏搜索 [@E5Sub\_bot](https://t.me/e5subbot)，打开以后在输入框搜索 / bind

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Start.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Start.png)

接着我们点击应用注册后面的那个链接，你也可以直接点击[这里](https://apps.dev.microsoft.com/?deepLink=%2Fquickstart%2FgraphIO%3FpublicClientSupport%3Dfalse%26appName%3De5sub%26redirectUrl%3Dhttp%3A%2F%2Flocalhost%2Fe5sub%26allowImplicitFlow%3Dfalse%26ru%3Dhttps%253A%252F%252Fdeveloper.microsoft.com%252Fen-us%252Fgraph%252Fquick-start%253FappID%253D_appId_%2526appName%253D_appName_%2526redirectUrl%253Dhttp%253A%252F%252Flocalhost%253A8000%2526platform%253Doption-windowsuniversal)

打开后登陆自己的 Office 账户，把显示的应用机密保存下来

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Secret.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Secret.png)

接着点下面那个蓝色的按钮，返回快速启动

往下拉网页，看到有个 APP ID(or Client ID)，我们把下面框框内的 UUID 找个地方复制粘贴临时保存一下

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-UUID.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-UUID.png)

然后我们回到 Telegram，输入刚刚的 UUID 和 Secret 秘钥，需要按照提供的格式进行输入

会返回一个带有链接的对话框给我们，我们点击授权用户后面的点击直达

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Bind.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Bind.png)

弹出来一个登录界面，登录完成后，复制地址栏里面的网址，粘贴到 Telegram 的对话框内就可以了

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Refresh-Token.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Refresh-Token.png)

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Reply.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Reply.png)

这样我们就绑定成功了，接下来就不管它，它会自己进行 API 的调用，每小时调用一次，并且会给我们反馈结果

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Result.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/E5Sub-Result.png)

### [](#自动续订程序法 "自动续订程序法")自动续订程序法

这是一个由其他大佬开发的网页端的程序，并且所有的操作都是在他的服务器上的，本地服务器不需要跑任何东西。我们打开 [https://e5.qyi.io/user/login?redirect=%2Fuser%2Fhome](https://e5.qyi.io/user/login?redirect=%2Fuser%2Fhome)

打开可能有点慢，请耐心等待。打开后点击中间的 Github 图标使用 Github 进行登录，进入主界面

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-start.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-start.png)

然后先把这个网页放在一边，打开 [Azure](https://portal.azure.com/)，在上面搜索[应用注册](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)，打开后，我们点击左上角的`新注册`，名称随便填，下面的受支持的账户类型选择第三个，URI 我们填写`https://e5.qyi.io/outlook/auth2/receive`，一定要填正确，否则是无法使用的！

进入页面后，我们复制上面显示的`应用程序（客户端）ID`，以供备用，接着我们点击左边的证书和密码，创建我们这个程序的密码

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-Azure-Secret.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-Azure-Secret.png)

在右边选择新客户端密码，描述随便填，密码我们选择从不过期，然后新建，把给我们的密码保存下来备用

接着点到 API 权限，点击添加权限，选择 Microsoft Graph，然后选择右边的应用程序权限，勾选`Mail.Read`、`Mail.ReadBasic`、`Mail.ReadBasic.All`、`Mail.ReadWrite`即可，剩下那个`Mail.Send`不用选择，勾选后确定，点击添加权限右边的`代表xxx授予管理员同意`，一定要点，否则无法正常运行

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-Azure-Permission.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/qyi-Azure-Permission.png)

接着返回刚刚的那个网页，ID 和机密填进去，然后点保存，接着点授权，一定要点授权，否则不会正常运行！

### [](#Github-Action法 "Github Action法")Github Action 法

这里我们使用的是一个 Github 项目 [AutoApiSecret](https://github.com/wangziyingwen/AutoApiSecret)，进入这个项目我们先把它 fork 一份到自己的账户下

同样，我们还是要先注册一个应用，获取应用 ID 和应用机密，怎么注册看[自动续订程序法](#自动续订程序法)

唯一不同的是，我们需要的权限变为以下权限：

`Files.Read.All` `Files.ReadWrite.All` `Sites.Read.All` `Sites.ReadWrite.All`

`User.Read.All` `User.ReadWrite.All` `Directory.Read.All` `Directory.ReadWrite.All`

`Mail.Read` `Mail.ReadWrite` `MailboxSettings.Read` `MailboxSettings.ReadWrite`

勾选完下面的权限保存，别忘了要点允许！！！

我们使用 rclone 来获取我们的 refresh\_token，你可以点击这里下载 [rclone](http://file.heimu.ltd/rclone.exe)

在命令行里，输入

bash

```
rclone authorize "onedrive" "之前保存的应用id" "之前保存的应用秘钥"
```

来打开登录窗口，在窗口内登录后，在命令行里面找到`refresh_token:`并把后面的内容直到`,"expiry"`的部分复制下来备用

接着我们回到我们的仓库，打开里面的 1.txt 文件，把刚刚获取的 refresh\_token 贴进去

打开仓库设置，点击 Secret，我们添加两个东西

第一个是`CONFIG_ID`，里面的内容写为`id=r'你的应用id'`，第二个是`CONFIG_KEY`，里面的内容写作`secret=r'你的应用机密'`

接着打开仓库里面的 1.txt，把你的 refresh\_token 贴进去

打开右上角自己头像下的 Settings，选到 Developer Settings，再点到 Personal access tokens，在这里我们新建一个 token，名字随便填，但是权限我们需要勾一下内容

`admin:repo_hook` `repo` `workflow`

然后保存即可，回到我们的仓库，点击顶上的 Action，如果你没有开过 Action，那么这里会需要让你打开同意条例来打开 Action，打开后，我们给自己的这个仓库点个 Star，来手动触发我们的 Action

在 Action 界面我们可以看到我们的 Workflow 是否运行正常，如果运行后打绿色的勾就说明成功了，这个时候就不需要再管它了，直接把这个仓库放着就好了，每一小时就会自动调用一次 API，达到微软要求的开发（伪）目的

### [](#题外话 "题外话")题外话

我今天重新开了一个 E5 的订阅，反正看看能撑多久

[![](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/Success-Renewed.png)](https://cdn.jsdelivr.net/gh/GamerNoTitle/Picture-repo-v1@master/img/Office365-Renew-Project/Success-Renewed.png)

续费成功图