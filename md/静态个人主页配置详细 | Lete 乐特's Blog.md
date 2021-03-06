> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.lete114.top](https://blog.lete114.top/article/Hexo-MengD.html#%E9%9F%B3%E4%B9%90%E6%92%AD%E6%94%BE)

[](https://blog.lete114.top/article/Hexo-MengD.html#%E5%89%8D%E8%A8%80 "前言")前言
==============================================================================

问：为什么不直接手敲静态页面 (反正也就一个页面)？  
答：使用静态文件生成器方便管理，不需要修改源码就能修改样式和增加其他内容 (采用读取配置文件实现)

[](https://blog.lete114.top/article/Hexo-MengD.html#%E6%AD%A3%E6%96%87 "正文")正文
------------------------------------------------------------------------------

1.  克隆
    
    ```
    git clone https://github.com/lete114/hexo-theme-MengD.git MengD
    ```
    
2.  克隆后使用`cd MengD`进入`MengD`后执行以下命令
    
    ```
    npm install hexo --save
    npm install hexo-deployer-git --save
    ```
    
3.  相关命令
    
    ```
    hexo server # 本地预览(简写hexo s)
    hexo generate # 生成静态文件(简写hexo g)
    hexo clean # 清理文件缓存
    hexo deploy # 部署(简写hexo d)
    ```
    
    `hexo s`后在浏览器地址栏输入`http://localhost:4000/`即可本地预览  
    `hexo g`后根目录会多出`public`文件夹，里面就是生成出来的静态页面  
    `hexo clean`后系统将删除你的`public`文件夹 (一般很少使用)  
    `hexo d`后系统将`public`文件夹内的静态文件复制到`.deploy_git`文件夹内并部署到你的仓库  
    请留意你的根目录`_config.yml`配置文件内的配置是否填写
    
    ```
    # 你的域名地址
    url: https://lete114.top
    
    # 提交
    deploy:
        type: git
        repo:     # 提交的仓库地址
        branch: master
    ```
    

[](https://blog.lete114.top/article/Hexo-MengD.html#%E4%B8%BB%E9%A2%98%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6 "主题配置文件")主题配置文件
--------------------------------------------------------------------------------------------------------------------------

选取部分功能进行分析

#### [](https://blog.lete114.top/article/Hexo-MengD.html#%E8%87%AA%E5%AE%9A%E4%B9%89js%E3%80%81css "自定义js、css")自定义 js、css

必须以以下格式进行自定义引入 (注意缩进)

```
# 如下
# - https://xxx.com/css/css.css
# - https://xxx.com/js/js.js
# - css/css.css
# - js/js.js
css:
  - https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free/css/all.min.css
  - css/Lete.css
js:
  - https://xxx.com/js/js.js
  - js/js.js
```

#### [](https://blog.lete114.top/article/Hexo-MengD.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9B%BE%E6%A0%87 "自定义图标")自定义图标

想自定义多套不同的 icon 图标，可以在上面自定义 css 处引入 icon 图标

```
# 自定义图标
iconfont: https://cdn.jsdelivr.net/gh/sviptzk/StaticFile_HEXO@master/butterfly/css/iconfont.min.css
# 图标大小
font_size: 1.6em
# Icon 图标
links:
  iconfont icon-youxiang: mailto:lete@lete114.top
  iconfont icon-github3: https://github.com/lete114
  iconfont icon-icon_doc_fill: https://blog.lete114.top
  iconfont icon-lianjie: https://blog.lete114.top/link/
  iconfont icon-csdn: https://me.csdn.net/Lott0419
  iconfont icon-zhihu: https://www.zhihu.com/people/lete114
```

#### [](https://blog.lete114.top/article/Hexo-MengD.html#%E7%99%BE%E5%BA%A6%E5%88%86%E6%9E%90 "百度分析")百度分析

填写问号后面的 key 就可以了  
![](https://cdn.jsdelivr.net/gh/lete114/lete114.github.io@latest/img/HomePage/1.png)

#### [](https://blog.lete114.top/article/Hexo-MengD.html#404%E9%A1%B5%E9%9D%A2%E9%85%8D%E7%BD%AE "404页面配置")404 页面配置

<table><thead><tr><th>属性</th><th>值</th><th>说明</th></tr></thead><tbody><tr><td>sec</td><td>30</td><td>多少秒后返回首页</td></tr><tr><td>text_color</td><td>#e58a8a</td><td>读秒字体颜色，可填 Hex 值，也可以填颜色单词</td></tr><tr><td>text</td><td>404！页面君找不到这个网页！！</td><td>404 页面文字描述</td></tr><tr><td>background</td><td>#fff</td><td>404 背景颜色，可填 Hex 值、颜色单词、图片地址</td></tr><tr><td>border_color</td><td>#7986cb</td><td>返回首页按钮边框颜色</td></tr><tr><td>font_color</td><td>#80bdab</td><td>返回首页按钮文字颜色</td></tr></tbody></table>

```
## 404页面
error_404:
  # 多少秒后返回首页
  sec: 30
  # 读秒字体颜色
  text_color: '#e58a8a'
  # 404文字描述
  text: '404！页面君找不到这个网页！！'
  # 自定义背景
  # bg_img: url(https://cdn.jsdelivr.net/gh/lete114/CDN2/img/wei_er_li_te/3.jpg)
  # bg_img: '#fff'
  # bg_img: 'white'
  background: url(https://cdn.jsdelivr.net/gh/lete114/CDN2/img/wei_er_li_te/3.jpg)
  # 鼠标移到返回首页按钮
  # 返回首页边框颜色
  border_color: '#7986cb'
  # 返回首页字体颜色
  font_color: '#80bdab'
```

#### [](https://blog.lete114.top/article/Hexo-MengD.html#%E9%9F%B3%E4%B9%90%E6%92%AD%E6%94%BE "音乐播放")音乐播放

<table><thead><tr><th>属性</th><th>说明</th></tr></thead><tbody><tr><td>autoplay</td><td>自动播放</td></tr><tr><td>loop</td><td>循环播放</td></tr><tr><td>src</td><td>音频地址</td></tr><tr><td>controls</td><td><code>[不推荐使用]</code> 显示控件</td></tr><tr><td>muted</td><td><code>[不推荐使用]</code> 静音</td></tr><tr><td>preload</td><td><code>[不推荐使用]</code> 音频在页面加载时进行加载，并预备播放。如果使用 “autoplay”，则忽略该属性</td></tr></tbody></table>

```
music:
  field: 404
  ### autoplay=自动播放 | loop=循环播放 | controls=显示控件 | muted=静音 | src=音频地址
  ### 不推荐：controls、muted、preload
  ### preload=音频在页面加载时进行加载，并预备播放。如果使用 "autoplay"，则忽略该属性
  property:
    autoplay
    loop
    src="https://656e-env-jxscvzag-1301289878.tcb.qcloud.la/music/zenyang.mp3"
```