\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.lete114.top\](https://blog.lete114.top/article/Valine-LeanCloud-Config.html#%E4%BF%AE%E6%94%B9Valine%E8%AF%84%E8%AE%BA%E5%8C%BA%E6%A0%B7%E5%BC%8F)

[](#前言 "前言")前言
==============

之前写了一篇 `LeanCloud`+`Yilia` 的文章👉 [https://blog.lete114.top/article/addee0b6.html](https://blog.lete114.top/article/addee0b6.html)

我觉得还不够详细，而且之前写的没有 `Qmsg酱` (QQ 评论提醒)、`Server酱` (微信评论提醒)

特此写了这篇更详细的，堪称`保姆级`别的教程了

废话不多说教程开始

[](#创建LeanCloud应用 "创建LeanCloud应用")创建 LeanCloud 应用
-------------------------------------------------

注册我就不多说了，有手有脑都会

`注意：`一定要选择国际版，如果你选择的是`华北`或者`华东`的话，Valine 后台评论管理是需要备案才能绑定的

### [](#打开LeanCloud "打开LeanCloud")打开 LeanCloud

官网：[https://console.leancloud.app/#/app](https://console.leancloud.app/#/app)  
注册登陆后长这样  
[![](https://files.alexhchu.com/2020/07/09/086f260f08bd1.png)](https://files.alexhchu.com/2020/07/09/086f260f08bd1.png)  
点击下边的`创建应用`填写应用昵称点击`创建`即可  
[![](https://files.alexhchu.com/2020/07/09/f602176a3bfa9.png)](https://files.alexhchu.com/2020/07/09/f602176a3bfa9.png)

### [](#打开创建的应用 "打开创建的应用")打开创建的应用

选择`云引擎`–> `设置`–> `云引擎域名` (`强调这个就是LeancLoud的后台地址`输入自己喜欢的一个的前缀)  
后台地址后面加上 `/sign-up` 就可以注册  
例如：[https://letetest.avosapps.us/sign-up](https://letetest.avosapps.us/sign-up)

[![](https://files.alexhchu.com/2020/07/09/d80705b6f31c5.png)](https://files.alexhchu.com/2020/07/09/d80705b6f31c5.png)  
当然如果你有自己的域名也可以选择绑定自己的域名，选择`设置`–> `域名绑定`–> `云引擎域名`  
[![](https://files.alexhchu.com/2020/07/09/45386e2aa682f.png)](https://files.alexhchu.com/2020/07/09/45386e2aa682f.png)

### [](#自定义环境变量 "自定义环境变量")自定义环境变量

选择`云引擎`–> `设置`–> `添加自定义环境变量`

<table><thead><tr><th>变量名</th><th>示例</th><th>说明</th></tr></thead><tbody><tr><td>SITE_NAME</td><td>Lete 乐特个人博客</td><td><code>[必填]</code> 网站名称</td></tr><tr><td>SITE_URL</td><td><a href="https://blog.lete114.top" data-pjax-state="" one-link-mark="yes">https://blog.lete114.top</a></td><td><code>[必填]</code> 网站地址</td></tr><tr><td>SMTP_USER</td><td><a href="mailto:admin@lete114.top" data-pjax-state="" one-link-mark="yes">admin@lete114.top</a></td><td><code>[必填]</code> 邮箱地址</td></tr><tr><td>SMTP_PASS</td><td>123456789</td><td><code>[必填]</code> 邮箱授权码<br>(部分邮箱服务商默认开启 SMTP)<br>(如果没有授权码可直接填写邮箱密码)</td></tr><tr><td>SMTP_SERVICE</td><td>QQ</td><td><code>[必填]</code> 邮箱服务商<a target="_blank" rel="noopener" href="https://nodemailer.com/smtp/well-known/#supported-services" one-link-mark="yes">查询相关详细</a></td></tr><tr><td>SENDER_NAME</td><td>Lete 乐特</td><td><code>[必填]</code> 寄件人名称</td></tr><tr><td>TEMPLATE_NAME</td><td>rainbow</td><td><code>[必填]</code> 设置提醒邮件的主题<br>看下方有主题模板</td></tr><tr><td>ADMIN_URL</td><td><a target="_blank" rel="noopener" href="https://letetest.leanapp.cn" one-link-mark="yes">https://letetest.leanapp.cn</a></td><td><code>[可选]</code> 后台管理地址</td></tr><tr><td>SCKEY</td><td>SCU100890xxxxxx293e1xxx9dbfe82axxxx2dc</td><td><code>[可选]</code> server 酱的 SCKEY (微信提醒)</td></tr><tr><td>QMSG_KEY</td><td>fdexxxx42a1xxx28f16d5xxxxa00</td><td><code>[可选]</code> Qmsg 酱的密钥</td></tr><tr><td>QQ</td><td>123456789</td><td><code>[可选]</code>Qmsg 酱发送的 qq，不填为全部<br>支持多个，用英文逗号分隔即可</td></tr><tr><td>QQ_SHAKE</td><td>true</td><td><code>[可选]</code> 填写代表发送 QQ 戳一戳</td></tr><tr><td>INFO</td><td><code>&lt;p style='color:red'&gt;test&lt;p&gt;</code></td><td><code>[可选]</code> 自定义信息输出，支持 HTML 代码<br>LeanCloud 控制台日志信息输出</td></tr><tr><td>FAVICON</td><td><a target="_blank" rel="noopener" href="https://cdn.jsdelivr.net/gh/lete114/lete114.github.io/img/favicon.ico" one-link-mark="yes">https://cdn.jsdelivr.net/gh/lete114/lete114.github.io/img/favicon.ico</a></td><td>[可选] 网页 favicon 图标</td></tr><tr><td>TO_EMAIL</td><td><a href="mailto:admin@lete114.top" data-pjax-state="" one-link-mark="yes">admin@lete114.top</a></td><td><code>[可选]</code> 博主通知收件地址，默认使用 <code>SMTP_USER</code></td></tr><tr><td>SPAM_WORDS</td><td>检测的内容，如：单号，物流</td><td><code>[可选]</code> 需要对屏蔽的关键词，关键词用半角逗号分隔</td></tr><tr><td>MAIN_COLOR</td><td>#ff9191</td><td><code>[可选]</code> 仅针对 custom2 模板主题的主要颜色</td></tr><tr><td>MAIN_IMG</td><td><a target="_blank" rel="noopener" href="https://cdn.jsdelivr.net/gh/lete114/CDN/BoBoPic/22.jpg" one-link-mark="yes">https://cdn.jsdelivr.net/gh/lete114/CDN/BoBoPic/22.jpg</a></td><td><code>[可选]</code> 仅针对 custom2 模板主题的头图</td></tr></tbody></table>

邮箱主题模板

<table><thead><tr><th>主题</th><th>说明</th></tr></thead><tbody><tr><td>default</td><td>默认主题</td></tr><tr><td>rainbow</td><td>原版的 rainbow</td></tr><tr><td>custom1</td><td>基于🎉<a target="_blank" rel="noopener" href="https://pbas.club/" one-link-mark="yes">梨花町の肾兄さん</a>🎉的模板</td></tr><tr><td>custom2</td><td>对 custom1 的改进版</td></tr></tbody></table>

参考：[https://blog.hclonely.com/posts/409d3090/](https://blog.hclonely.com/posts/409d3090/)  
参考：[https://www.antmoe.com/posts/2380732b/](https://www.antmoe.com/posts/2380732b/)

### [](#参考我博客的自定义环境变量 "参考我博客的自定义环境变量")参考我博客的自定义环境变量

[![](https://files.alexhchu.com/2020/07/08/e5a374ff70a50.png)](https://files.alexhchu.com/2020/07/08/e5a374ff70a50.png)

### [](#部署 "部署")部署

选择`云引擎`–> `部署`–> `部署项目`–>`Git部署`–> `配置Git`–> `填写下方任意一个地址`–> `保存`–> `生产环境`–> `部署`  
个人定制：[https://github.com/lete114/Valine-Admin-Server.git](https://github.com/lete114/Valine-Admin-Server.git)  
小康：[https://github.com/sviptzk/Valine-Admin-Server.git](https://github.com/sviptzk/Valine-Admin-Server.git)

### [](#创建定时任务 "创建定时任务")创建定时任务

1.  定时检查 24 小时内漏发的邮件通知  
    生产环境选择 `resend_mails`  
    选择 `Cron表达式`时间自己调整 `0 0 1 * * *`
    
2.  自动唤醒  
    生产环境选择 `self_wake`  
    选择 `Cron表达式`时间自己调整 `0 0/60 0 * * ?`
    

[![](https://files.alexhchu.com/2020/07/09/634817487f104.png)](https://files.alexhchu.com/2020/07/09/634817487f104.png)

### [](#设置安全域名 "设置安全域名")设置安全域名

这里设置的是你博客的地址，你博客有多少个地址就填多少个地址，不然评论显示 403  
[![](https://files.alexhchu.com/2020/07/15/4c5c5fa169478.png)](https://files.alexhchu.com/2020/07/15/4c5c5fa169478.png)

[](#申请Qmsg酱 "申请Qmsg酱")申请 Qmsg 酱
-------------------------------

1.  打开官网  
    官网：~[https://qmsg.zendee.cn/](https://qmsg.zendee.cn/)~  
    目前 Qmsg 已关闭新用户注册  
    点击登陆 (我选择的是 QQ 登陆)  
    [![](https://files.alexhchu.com/2020/07/09/77df6bb65c01e.png)](https://files.alexhchu.com/2020/07/09/77df6bb65c01e.png)
    
2.  添加 QQ  
    可填写多个  
    [![](https://files.alexhchu.com/2020/07/09/7770a7ebdb44d.png)](https://files.alexhchu.com/2020/07/09/7770a7ebdb44d.png)
    
3.  点击右上角文档  
    把 `send` 后面的 `key` 复制到 `LeanCloud` 的 `QMSG_KEY` 环境变量后保存即可  
    [![](https://files.alexhchu.com/2020/07/09/d762276c062d1.png)](https://files.alexhchu.com/2020/07/09/d762276c062d1.png)
    

[](#申请Server酱 "申请Server酱")申请 Server 酱
-------------------------------------

和 Qmsg 类似，`注册` —> `登陆` —> `发送消息` —> 就可以得到 `SCKEY` 代码了  
官网：[http://sc.ftqq.com/3.version](http://sc.ftqq.com/3.version)  
[![](https://i.erosouko.pub/2020/08/12/cb1913acb505a.png)](https://i.erosouko.pub/2020/08/12/cb1913acb505a.png)

[](#Valine-配置 "Valine 配置")Valine 配置
-----------------------------------

1.  打开 `C:\Hexo-Blog\themes\Butterfly\_config.yml`
    
    `注意：`下方步骤由 `Butterfly` 主题独有，如果你是其他主题请自行查看主题源码
    
    找到 \`# comments\` 修改 \`valine\` 的 js 地址以下选其一 个人定制：https://cdn.jsdelivr.net/gh/lete114/CDN2/js/Valine-Lete3.2.js HCLonely 魔改版：https://cdn.jsdelivr.net/gh/HCLonely/Valine@latest/dist/Valine.min.js yml
    
    ```
    \# comments
    blueimp\_md5: https://cdn.jsdelivr.net/npm/blueimp-md5/js/md5.min.js
    gitalk: https://cdn.jsdelivr.net/npm/gitalk@latest/dist/gitalk.min.js
    gitalk\_css: https://cdn.jsdelivr.net/npm/gitalk/dist/gitalk.min.css
    valine: https://cdn.jsdelivr.net/gh/lete114/CDN2/js/Valine-Lete3.2.js
    disqusjs: https://cdn.jsdelivr.net/npm/disqusjs@1/dist/disqus.js
    disqusjs\_css: https://cdn.jsdelivr.net/npm/disqusjs@1/dist/disqusjs.css
    utterances: https://utteranc.es/client.js
    ```
    
2.  再次找到 `valine` 添加 `master` 和 `friends`
    
    yml
    
    ```
    \# valine
    # https://valine.js.org
    valine:
      enable: true # if you want use valine,please set this value is true
      master: 2a77xxx15437xxxd7f4442e2 # 你邮箱的md5加密(百度md5在线加密)
      friends: ed5xxxcfe547babab7xxx6893b # 你朋友的邮箱md5加密
      appId: qvkfTxxxxxACiF4lscUxxxYXbMMI # leancloud application app id
      appKey: WOUxxx5Pmtwxxxrog # leancloud application app key
      notify: true # valine mail notify (true/false) Deprecated in v1.4.0+
      verify: false # valine verify code (true/false) Deprecated in v1.4.0+
      pageSize: 10 # comment list page size
      avatar: monsterid # gravatar style https://valine.js.org/#/avatar
      lang: zh-CN # i18n: zh-CN/zh-TW/en/ja
      placeholder: 建议使用QQ邮箱，评论头像采用QQ头像 #评论框占位符
      guest\_info: nick,mail,link #valine comment header info
      recordIP: false # Record reviewer IP
      serverURLs: # This configuration is suitable for domestic custom domain name users, overseas version will be automatically detected (no need to manually fill in)
      emojiCDN:  # emoji CDN
      enableQQ: true # enable the Nickname box to automatically get QQ Nickname and QQ Avatar
      requiredFields: nick,mail # required fields nick/mail/link
      bg: # valine background
      count: true # dispaly comment count in top\_img
    ```
    
3.  随后到 `C:\Hexo-Blog\themes\Butterfly\layout\includes\comments\valine.pug` 添加
    
    Code
    
    ```
    window.valine = new Valine({
      el:'#vcomment',
      master:'#{theme.valine.master}',
      friends:'#{theme.valine.friends}',
      appId: '#{theme.valine.appId}',
      appKey: '#{theme.valine.appKey}',
      #省略....
    ```
    
4.  添加自定义表情包 `[可选]`  
    打开 `C:\Hexo-Blog\themes\Butterfly\layout\includes\comments\valine.pug`
    
    Code
    
    ```
    window.valine = new Valine({
      el:'#vcomment',
      master:'#{theme.valine.master}',
      friends:'#{theme.valine.friends}',
      #省略....
      enableQQ: #{theme.valine.enableQQ},
      requiredFields: requiredFields,
      emojiMaps: {
                "1":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/1.gif",
                "001":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/001.png",
                "002":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/002.png",
                "003":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/003.png",
                #省略....
                "0104":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/104.jpg",
                "0105":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/105.jpg",
                "0106":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/106.gif"
            }
    });
    ```
    
5.  valine.pug 文件夹的全部内容展示
    
    Code
    
    ```
    \- let emojiMaps = '""'
    if site.data.valine
      - emojiMaps = JSON.stringify(site.data.valine)
    
    #vcomment.vcomment
    script(src=url\_for(theme.CDN.valine))
    script.
      var requestSetting = function (from,set) {
        var from = from
        var setting = set.split(',').filter(function(item){
        return from.indexOf(item) > -1
        });
        setting = setting.length == 0 ? from :setting;
        return setting
      }
    
      var guestInfo = requestSetting(\['nick','mail','link'\],'#{ theme.valine.guest\_info }')
      var requiredFields = requestSetting(\['nick','mail'\],'#{ theme.valine.requiredFields }')
    
      window.valine = new Valine({
        el:'#vcomment',
        master:'#{theme.valine.master}',
        friends:'#{theme.valine.friends}',
        appId: '#{theme.valine.appId}',
        appKey: '#{theme.valine.appKey}',
        placeholder: '#{theme.valine.placeholder}',
        avatar: '#{theme.valine.avatar}',
        meta: guestInfo,
        pageSize: '#{theme.valine.pageSize}',
        lang: '#{theme.valine.lang}',
        recordIP: #{theme.valine.recordIP},
        serverURLs: '#{theme.valine.serverURLs}',
        emojiCDN: '#{theme.valine.emojiCDN}',
        emojiMaps: !{emojiMaps},
        enableQQ: #{theme.valine.enableQQ},
        requiredFields: requiredFields,
        emojiMaps: {
                  "1":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/1.gif",
                  "001":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/001.png",
                  "002":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/002.png",
                  "003":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/003.png",
                  "004":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/004.png",
                  "005":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/005.png",
                  "006":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/006.png",
                  //- 图片过多，我这里就省略了
                  "0103":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/103.jpg",
                  "0104":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/104.jpg",
                  "0105":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/105.jpg",
                  "0106":"https://cdn.jsdelivr.net/gh/lete114/CDN/emoji/106.gif"
              }
      });
    ```
    

  
表情包效果图  
[![](https://files.alexhchu.com/2020/07/09/f4b93f91f5db6.png)](https://files.alexhchu.com/2020/07/09/f4b93f91f5db6.png)

### [](#修改Valine评论区样式 "修改Valine评论区样式")修改 Valine 评论区样式

1.  打开 `C:\Hexo-Blog\themes\Butterfly\_config.yml`  
    找到 `theme_color:` 修改 `main:` 颜色即可
    
    yml
    
    ```
    theme\_color:
       enable: true
       main: "#e58a8a" # 文章颜色
       paginator: "#00c4b6" # 分页器的颜色
       button\_hover: "#e58a8a" # 鼠标移动到按钮上的显示的颜色
       text\_selection: "#00c4b6" # 选择文字的背景颜色
       link\_color: "#99a9bf" # 链接颜色
       meta\_color: "#858585"
       hr\_color: "#e58a8a" # 小剪刀颜色、小摩托颜色
       code\_foreground: "#F47466" # 代码\`code\`的颜色
       code\_background: "rgba(27, 31, 35, .05)" # 代码\`code\`的背景颜色
       toc\_color: "#00c4b6"
       blockquote\_padding\_color: "#e58a8a" # >  >> >>> 描述颜色
       blockquote\_background\_color: "#49b1f5"
    ```
    
      
    Valine 评论区效果图  
    [![](https://files.alexhchu.com/2020/07/09/348648393708f.png)](https://files.alexhchu.com/2020/07/09/348648393708f.png)
    
2.  如果你的主题不是 butterfly 主题的话  
    可以写一个 css 样式覆盖掉默认样式
    
    css
    
    ```
    /\*回复按钮颜色\*/
    #vcomment .vat {
        color: rgb(0, 0, 0);
        font-size: 0.7125rem;
        padding: 0px 0.8rem;
        border-width: 1px;
        border-style: solid;
        border-color: rgb(0, 0, 0);
        border-image: initial;
        border-radius: 5px;
        transition: all 0.3s ease 0s;
    }
    /\*提交评论按钮颜色\*/
    #vcomment button {
        background-color: rgb(0, 0, 0);
        color: rgb(255, 255, 255);
        font-size: 0.7rem;
        padding: 0.3rem 0.8rem;
        border-color: rgb(255, 255, 255);
        transition: all 0.3s ease 0s;
    }
    
    /\*如果你还想修改鼠标移动到【回复】按钮或者【提交】按钮显示的颜色就修改\*/
    /\*
    #vcomment .vat:hover {
        color: rgb(0, 0, 0);
        font-size: 0.7125rem;
        padding: 0px 0.8rem;
        border-width: 1px;
        border-style: solid;
        border-color: rgb(0, 0, 0);
        border-image: initial;
        border-radius: 5px;
        transition: all 0.3s ease 0s;
    }
    \*/
    ```
    
    最后在 `</body>` 前引用 css 就可以了