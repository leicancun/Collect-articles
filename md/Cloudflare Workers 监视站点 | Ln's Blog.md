> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [weilining.cf](https://weilining.cf/118.html)

[](#参考 "参考")参考
--------------

[https://github.com/eidam/cf-workers-status-page](https://github.com/eidam/cf-workers-status-page)

[](#依赖 "依赖")依赖
--------------

```
cloudflare 账号
GitHub 账号
GitHub Secrets 配置
```

[](#开始 "开始")开始
--------------

### [](#一键部署cloudflare "一键部署cloudflare")一键部署 cloudflare

[![](https://camo.githubusercontent.com/1f3d0b4d44a2c3f12c78bd02bae907169430e04d728006db9f97a4befa64c886/68747470733a2f2f6465706c6f792e776f726b6572732e636c6f7564666c6172652e636f6d2f627574746f6e3f706169643d74727565)](https://deploy.workers.cloudflare.com/?url=https://github.com/eidam/cf-workers-status-page)

[Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/?url=https://github.com/eidam/cf-workers-status-page)

### [](#配置-GitHub-Action "配置 GitHub Action")配置 GitHub Action

**GitHub repository > Settings > Secrets**

Token 选`编辑 Cloudflare Workers`，区域资源包括所有，区域账号包括你自己账号。

```
CF_API_TOKEN afaljsdfjalsjd11 (https://dash.cloudflare.com/profile/api-tokens)
CF_ACCOUNT_ID d6265287978826049fad0ec9b2bb5111 (Workers 帐户 ID)
```

### [](#配置参数-config-yaml "配置参数 config.yaml")配置参数 config.yaml

在根文件

```
settings:
  title: 'Status Page'
  url: 'https://status-page.eidam.dev' 
  logo: logo-192x192.png 
  daysInHistogram: 90 
  collectResponseTimes: true 

  allmonitorsOperational: 'All Systems Operational'
  notAllmonitorsOperational: 'Not All Systems Operational'
  monitorLabelOperational: 'Operational'
  monitorLabelNotOperational: 'Not Operational'
  monitorLabelNoData: 'No data'
  dayInHistogramNoData: 'No data'
  dayInHistogramOperational: 'All good'
  dayInHistogramNotOperational: ' incident(s)' 

monitors:
  - id: blog-weilining-cf
    name: The weilining Blog
    url: 'https://blog.weilining.cf/' 
    method: GET
    expectStatus: 200
    
  - id: workers-cloudflare-com 
    name: workers.cloudflare.com
    description: 'You write code. They handle the rest.' 
    url: 'https://workers.cloudflare.com/' 
    method: GET 
    expectStatus: 200 
    followRedirect: false 

  - id: www-cloudflare-com
    name: www.cloudflare.com
    description: 'Built for anything connected to the Internet.'
    url: 'https://www.cloudflare.com'
    method: GET
    expectStatus: 200

  - id: blog-cloudflare-com
    name: The Cloudflare Blog
    url: 'https://blog.cloudflare.com/' 
    method: GET
    expectStatus: 200
```

### [](#Cloudflare完成设置 "Cloudflare完成设置")Cloudflare 完成设置

编辑完`config.yaml`，你的 `GitHub Action`便会跑起来，等几分钟即可完成`cloud flare`一键设置，然后进入到你的`Worker dash`，点第一个`Workers`即可进入监视

版权声明: 本博客所有文章除特别声明外，均采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议。转载请注明来自 [Ln's Blog](https://weilining.cf/)！