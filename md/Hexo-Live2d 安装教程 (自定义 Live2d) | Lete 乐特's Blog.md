\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.lete114.top\](https://blog.lete114.top/article/Live2d-Config.html#%E5%89%8D%E8%A8%80)

[](#前言 "前言")前言
==============

使用自己的 Live2d 看板娘

每次看别人博客或者网站的时候，别人网站都有好看的看板娘，即使安装了 `helper-live2d` 但提供的 Live2d 太少了  
那么如何使用自定义的 Live2d 呢？  
看网上很多教程都是乱七八糟的，看也看不懂，自己研究了一下，成功了！  
分享出来，让更多人少踩坑，这里我以`紫罗兰永恒花园`的`薇尔莉特·伊芙加登`小姐姐的 Live2d 模型作为演示，结束后会奉上几个好看的模型  
如果你有好看的模型可以与我分享 (好东西要学会分享)[![](https://blog.lete114.top/img/Live2d-Config/xixi.png)](/img/Live2d-Config/xixi.png)

[](#安装 "安装")安装
--------------

使用 `helper-live2d` 的 Live2d 插件 [https://github.com/EYHN/hexo-helper-live2d](https://github.com/EYHN/hexo-helper-live2d)

bash

```
npm install --save hexo-helper-live2d
```

### [](#配置 "配置")配置

安装成功后，在 hexo 根目录的`_config.yml` 添加如下配置 (可以写在主题配置文件里)

1.  基础配置
    
    yml
    
    ```
    \# Live2D
    ## https://github.com/EYHN/hexo-helper-live2d
    live2d:
      enable: true # 开启live2d
      # enable: false
      scriptFrom: local # 默认
      pluginRootPath: live2d/ # 插件在站点上的根目录(相对路径)
      pluginJsPath: lib/ # 脚本文件相对与插件根目录路径
      pluginModelPath: assets/ # 模型文件相对与插件根目录路径
      # scriptFrom: jsdelivr # jsdelivr CDN
      # scriptFrom: unpkg # unpkg CDN
      # scriptFrom: https://cdn.jsdelivr.net/npm/live2d-widget@3.x/lib/L2Dwidget.min.js # 你的自定义 url
      tagMode: false # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中
      debug: false # 调试, 是否在控制台输出日志
      model:
        use: live2d-widget-model-wanko # npm-module package name
        # use: wanko # 博客根目录/live2d\_models/ 下的目录名
        # use: ./wives/wanko # 相对于博客根目录的路径
        # use: https://cdn.jsdelivr.net/npm/live2d-widget-model-wanko@1.0.5/assets/wanko.model.json # 你的自定义 url
    ```
    
2.  进阶配置  
    看如下配置在`基础配置`的基础上进行添加相应的配置
    
    yml
    
    ```
    live2d:
      enable: true # 是否开启live2d
      scriptFrom: local ## 脚本从本地引入
      pluginRootPath: live2dw/ # 模型根目录(指hexo g后生成public\\live2dw文件名)
      pluginJsPath: lib/ # 依赖js的文件夹名(public\\live2dw\\lib)
      pluginModelPath: assets/ # 模型存放目录(public\\live2dw\\assets)
      tagMode: false # 标记模式(未知) 
      log: false # 日志
      model: # 模型
        use: live2d-widget-model-wanko # 使用的模型名称
      display: # 显示
        position: right # 显示在右边(left显示在左边)
        width: 150 # 宽度
        height: 300 # 高度
      mobile:
        show: true # 手机端是否显示
      react:
        opacity: 0.7 # 透明度
    ```
    
    下面是我在`基础配置`的基础上添加的几个属性
    
    yml
    
    ```
    \# Live2D
    ## https://github.com/EYHN/hexo-helper-live2d
    live2d:
      enable: true # 开启live2d
      # enable: false
      scriptFrom: local # 默认
      pluginRootPath: live2d/ # 插件在站点上的根目录(相对路径)
      pluginJsPath: lib/ # 脚本文件相对与插件根目录路径
      pluginModelPath: assets/ # 模型文件相对与插件根目录路径
      # scriptFrom: jsdelivr # jsdelivr CDN
      # scriptFrom: unpkg # unpkg CDN
      # scriptFrom: https://cdn.jsdelivr.net/npm/live2d-widget@3.x/lib/L2Dwidget.min.js # 你的自定义 url
      tagMode: false # 标签模式, 是否仅替换 live2d tag标签而非插入到所有页面中
      debug: false # 调试, 是否在控制台输出日志
      display:
         position: left
      mobile:
         show: false   
      model:
         scale: 1.2
         use: weier
    ```
    
3.  高级配置  
    建议小白可以不必理会，高玩请随意，官方 API 地址：[L2Dwidget | live2d-widget.js](https://l2dwidget.js.org/docs/class/src/index.js~L2Dwidget.html#instance-method-init)
    

### [](#使用模型 "使用模型")使用模型

1.  自定义模型  
    使用自己下载好的模型  
    在 hexo 根目录新建 `live2d_models` 文件夹，然后把模型放进去，最后在 `live2d` 配置里的 `model:` 下的 `use:` 输入模型文件夹名  
    在我提供的 `live2d` 的压缩包里有几个模型，这里我以`薇尔莉特·伊芙加登`进行演示
    
    > 将`薇尔莉特·伊芙加登`复制到刚从新建的 `live2d_models` 文件夹内，然后重命名为 `weier`(当然这个名字是你自定义的)，然后进入 `weier` 文件夹，里面有个 `14.json` 文件，将他重命名为 `weier.model.json` 其他文件无需修改，最后在 `live2d` 配置里的 `model:` 下的 `use:` 输入模型文件夹名 (weier)
    
    yml
    
    ```
    model:
         use: weier
    ```
    
2.  使用 `npm install {packagename}` 安装模型如下
    
    bash
    
    ```
    npm install live2d-widget-model-wanko
    ```
    
    目前有如下模型[模型样式](https://huaji8.top/post/live2d-plugin-2.0/)  
    `live2d-widget-model-chitose`  
    `live2d-widget-model-epsilon2_1`  
    `live2d-widget-model-gf`  
    `live2d-widget-model-haru/01` (use `npm install --save live2d-widget-model-haru`)  
    `live2d-widget-model-haru/02` (use `npm install --save live2d-widget-model-haru`)  
    `live2d-widget-model-haruto`  
    `live2d-widget-model-hibiki`  
    `live2d-widget-model-hijiki`  
    `live2d-widget-model-izumi`  
    `live2d-widget-model-koharu`  
    `live2d-widget-model-miku`  
    `live2d-widget-model-ni-j`  
    `live2d-widget-model-nico`  
    `live2d-widget-model-nietzsche`  
    `live2d-widget-model-nipsilon`  
    `live2d-widget-model-nito`  
    `live2d-widget-model-shizuku`  
    `live2d-widget-model-tororo`  
    `live2d-widget-model-tsumiki`  
    `live2d-widget-model-unitychan`  
    `live2d-widget-model-wanko`  
    `live2d-widget-model-z16`
    

### [](#模型下载地址 "模型下载地址")模型下载地址

[https://656e-env-jxscvzag-1301289878.tcb.qcloud.la/live2dModel.zip](https://656e-env-jxscvzag-1301289878.tcb.qcloud.la/live2dModel.zip)