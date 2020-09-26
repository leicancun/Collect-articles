\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.lete114.top\](https://blog.lete114.top/article/upyun-cdn-config.html#%E5%89%8D%E8%A8%80)

[](#前言 "前言")前言
==============

为什么我要写这篇文章？因为网上的教程不行，看了也不懂，重点没有说明清楚  
导致很多人没弄清楚，到头来还是自己摸索出来的 (在说自己)  
看了本片文章，少走弯路

[](#准备工作 "准备工作")准备工作
--------------------

1\. 又拍云  
2\. 域名  
3\. 域名已备案  
4\. 一双手和一个小脑袋

准备两个二级域名  
加速域名: test1.lete114.top  
回源域名: test2.lete114.top  
(如果你的网站是 Github Pages 的话可以使用 xxxx.github.io 当作回源域名)  
(我这里为了方便演示，就使用 test1 和 test2，test1 就是相当于本站的 blog.lete114.top)  
[![](https://upimage.alexhchu.com/2020/08/15/30dbbdc63c685.png)](https://upimage.alexhchu.com/2020/08/15/30dbbdc63c685.png)

[](#创建-CDN-服务 "创建 CDN 服务")创建 CDN 服务
-----------------------------------

这里的加速域名我 test 后面少打了个 1  
源站证书校验就不要开启了，如果开启的话源站与的 ssl 证书与又拍云证书不符合，就会拒接访问  
[![](https://i.erosouko.pub/2020/08/15/1d972303e71fc.png)](https://i.erosouko.pub/2020/08/15/1d972303e71fc.png)

test1.lete114.top 域名 `CNAME` 解析到 `lete-test.b0.aicdn.com`  
test2.lete114.top 域名 `CNAME` 解析到 `lete114.github.io`  
[![](https://upimage.alexhchu.com/2020/08/15/79dd1d57c19c6.png)](https://upimage.alexhchu.com/2020/08/15/79dd1d57c19c6.png)

[](#其他配置 "其他配置")其他配置
--------------------

### [](#缓存控制 "缓存控制")缓存控制

资源路径输入 `*.*` 表示全站缓存，缓存时间看个人喜好（我选择 2 小时）

补充：缓存配置是为了不必要的资源消耗，设置缓存配置后，两小时内又拍云不会到源站抓取资源，节省了 CDN 流量  
如果未设置缓存配置的话，每次有人打开你的网站，又拍云都要到源站去抓取资源

[![](https://upimage.alexhchu.com/2020/08/15/b7ba0d54c0fb2.png)](https://upimage.alexhchu.com/2020/08/15/b7ba0d54c0fb2.png)

### [](#性能优化 "性能优化")性能优化

`开启`页面压缩

自动去除页面文件中非必要的字符（空白、注释等），自动压缩文件大小，加快传输速度。

`开启`重定向跟随

CDN 节点回源请求，若源站响应 301/302 状态码，则直接跳转获取资源，不会返回 301/302 给终端用户，免去了用户再次向 301/302 后的 URL 发起请求的连接时间，从而加快用户访问速度。

### [](#HTTPS "HTTPS")HTTPS

`开启` TLS 1.3

TLS 1.3 是一种全新的加密协议，它既能提高终端用户的访问速度，又能增强安全性

`开启`最低 TLS 版本 选择 1.0

`开启` HTTP/2

### [](#访问控制 "访问控制")访问控制

`开启` CC 防护

针对网络安全领域中的 CC 攻击而进行的一种应用层攻击防护，针对匹配的 URI 进行页面校验，来决定是放行还是直接拦截。

`开启` WAF 保护

WAF 也即 Web Application Firewall，能有效拦截跨站攻击、SQL 注入和其他代码执行等多种攻击方式。

### [](#成本控制 "成本控制")成本控制

`开启` WebP 自适应

智能判断浏览器是否支持 WebP，来决定返回 WebP 格式图片还是原图，从而减少网络传输消耗。

### [](#页脚添加又拍云 "页脚添加又拍云")页脚添加又拍云

打开主题配置文件找到 `custom_text:` 添加  
如果你没有页脚文字描述的话可以吧前面的 `<br>` 去掉

yml

```
<br><a href="https://www.upyun.com/?utm\_source=lianmeng&utm\_medium=referral" target="\_blank" rel="noopener"><img src="https://cdn.jsdelivr.net/gh/lete114/CDN/upyun/%E5%8F%88%E6%8B%8D%E4%BA%91\_logo5.png" align="absmiddle" width="60px" height="30px">提供加速服务</a>
```

如有任何问题，可以在评论区留言