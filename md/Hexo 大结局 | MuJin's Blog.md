> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [xiabor.com](https://xiabor.com/714f.html#如何在页脚养鱼)

Hexo 大结局——本篇作为折腾 hexo 的最后一篇，本文写完就再也不折腾 hexo 了。（不过可以折腾一下 Typecho,Hugo,WordPress）

[](#如何跳过hexo的渲染 "如何跳过hexo的渲染")如何跳过 hexo 的渲染
-------------------------------------------

查看官方文档页面跳过 hexo 的渲染主要有两种方式：

### [](#Front-matter "Front matter")Front matter

*   新建页面，然后将你的代码直接写入`index.md`中
    
*   在 Front matter 中添加`layout: false`，例如我的 [Sakura 樱花雨](https://xiabor.com/sakura)页面，此方法适用于单一的纯 HTML  
    css 页面。
    
    ```
    ---
    title: sakura
    date: 2019-11-29 16:59:51
    type: "sakura"
    layout: false
    ---
    ```
    
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421114708.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421114708.png)
    
    示例图
    

### [](#skip-render "skip_render")skip_render

*   如果页面含有复杂的 js，layout 的方式可能容易报错，因此利用 hexo 自带的`skip_render`
*   在根目录【**根目录**】的_config.yml，你可以看到`skip_render`，大致在 32 行。写入你想要的跳过渲染的路径，例如我的[烟花 - CodePen](https://xiabor.com/fireworks) 页面：

```
skip_render:
    - 'fireworks/*'
    - 'fireworks/**'

```

*   注意缩进和空格，解释一下：`'fireworks/*'`表示在目录`source/fireworks`下的文件全部跳过渲染，`'fireworks/**'`表示在目录`source/fireworks/文件夹`下的文件全部跳过渲染（例如页面的 js、css 在另一个文件夹中）。这里有点重复了，只为了你能看明白。
    
*   Hexo 最终是把`md`渲染为 HTML 页面，所以既然跳过渲染，那页面就只写入 HTML。如图，将新建页面的`index.md`直接改为 HTML（注意调整 css）  
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421115308.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421115308.png)
    
    文件示例图
    

### [](#可以混用 "可以混用")可以混用

*   都是跳过渲染，当然可以混用
    
*   例如我的[小圆点](https://xiabor.com/dot)页面，两种方法混用
    
*   修改 md 为 HTML，直接写入 HTML，并在 Front matter 中利用`layout: false`  
    跳过渲染  
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421121330.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/20200421121330.png)
    
    小圆点页面示例图
    
*   若采用第二种方法，在根目录【**根目录**】的_config.yml 添加
    
    ```
    skip_render:
        - 'dot/*'
        - 'dot/**'
    ```
    

### [](#文章中直接嵌入HTML "文章中直接嵌入HTML")文章中直接嵌入 HTML

*   既然 md 最终会被渲染为 HTML，那直接写 HTML 当然是可以的，但只能以文章形式展示，而不是新的页面
    
*   例如我在这嵌入一个颜色表，HTML 代码完整，前后换行留空即可
    
      <table><tbody><tr><th>颜色名</th><th>十六进制颜色值</th><th>颜色</th></tr><tr><td>SteelBlue</td><td>#4682B4</td><td>rgb(70, 130, 180)</td></tr><tr><td>Tan</td><td>#D2B48C</td><td>rgb(210, 180, 140)</td></tr><tr><td>Teal</td><td>#008080</td><td>rgb(0, 128, 128)</td></tr><tr><td>Thistle</td><td>#D8BFD8</td><td>rgb(216, 191, 216)</td></tr><tr><td>Tomato</td><td>#FF6347</td><td>rgb(255, 99, 71)</td></tr><tr><td>Turquoise</td><td>#40E0D0</td><td>rgb(64, 224, 208)</td></tr><tr><td>Violet</td><td>#EE82EE</td><td>rgb(238, 130, 238)</td></tr><tr><td>VioletRed</td><td>#D02090</td><td>rgb(208, 32, 144)</td></tr><tr><td>Wheat</td><td>#F5DEB3</td><td>rgb(245, 222, 179)</td></tr><tr><td>White</td><td>#FFFFFF</td><td>rgb(255, 255, 255)</td></tr><tr><td>WhiteSmoke</td><td>#F5F5F5</td><td>rgb(245, 245, 245)</td></tr><tr><td>Yellow</td><td>#FFFF00</td><td>rgb(255, 255, 0)</td></tr><tr><td>YellowGreen</td><td>#9ACD32</td><td>rgb(154, 205, 50)</td></tr></tbody></table>

[](#永久链接 "永久链接")永久链接
--------------------

### [](#默认链接 "默认链接")默认链接

默认的链接格式为

```
year/:month/:day/:title/
```

如果文章名是中文，由于编码生成的链接会很长，况且不利于 SEO

### [](#利用字段替换链接 "利用字段替换链接")利用字段替换链接

根据官方文档 [hexo.io/docs](https://hexo.io/zh-cn/docs/permalinks)，可以利用一个字段定义永久链接

<table><thead><tr><th>变量</th><th>描述</th></tr></thead><tbody><tr><td>:year</td><td>文章的发表年份（4 位数）</td></tr><tr><td>:month</td><td>文章的发表月份（2 位数）</td></tr><tr><td>:i_month</td><td>文章的发表月份（去掉开头的零）</td></tr><tr><td>:day</td><td>文章的发表日期 (2 位数)</td></tr><tr><td>:i_day</td><td>文章的发表日期（去掉开头的零）</td></tr><tr><td>:hour</td><td>文章发表时的小时 (2 位数)</td></tr><tr><td>:minute</td><td>文章发表时的分钟 (2 位数)</td></tr><tr><td>:title</td><td>文件名称</td></tr><tr><td>:post_title</td><td>文章标题</td></tr><tr><td>:id</td><td>文章 ID (not persistent across cache reset)</td></tr><tr><td>:category</td><td>分类。如果文章没有分类，则是 default_category 配置信息。</td></tr></tbody></table>

例如：在 front matter 中加入 id：xxxx

```
---
title: title
categories:
tags:
id: xxxx
---
```

在 hexo 根目录加入或修改 permalink

```
permalink: posts/:id.html/
permalink_defaults:
```

这样文章地址就会变为`https://xxx.com/posts/id.html`，无需插件也能设置永久链接。

### [](#abbrlink插件 "abbrlink插件")abbrlink 插件

*   项目地址：[hexo-abbrlink](https://github.com/rozbo/hexo-abbrlink)
    
*   安装插件
    

```
npm install hexo-abbrlink --save
```

*   在根目录`blog\scaffolds\post.md`中添加 abbrlink 字段（不加也行）
    
*   根目录 config.yml 下设置
    

```
permalink: posts/:abbrlink.html
abbrlink:
alg: crc32  
rep: hex    
permalink_defaults:
```

hexo clean 之后本地预览时便可重新生成永久链接，文章 front matter 会多一个 abbrlink 字段

永久链接格式为`https://xxx.com/posts/abbrlink.html`

*   插件参数

```
abbrlink:
alg: crc32  #support crc16(default) and crc32
rep: hex    #support dec(default) and hex

crc16 & hex
https://post.zz173.com/posts/66c8.html

crc16 & dec
https://post.zz173.com/posts/65535.html
crc32 & hex
https://post.zz173.com/posts/8ddf18fb.html

crc32 & dec
https://post.zz173.com/posts/1690090958.html
```

### [](#使用技巧 "使用技巧")使用技巧

*   虽然 abbrlink 是自动生成的，可以在文章的 front matter 自定义修改。
*   以前用了 hexo 默认链接`year/:month/:day/:title/`，安装插件插件后所有文章链接都会发生变化，那么评论怎么办？

_对于我这样的小破站，好不容易才有几条评论，就这样丢失了心有不甘啊_

想到了几个解决方案：

1.  既然可以自定义 abbrlink，那只要将根目录配置改为
    
    ```
    permalink: :abbrlink
    permalink_defaults:
    ```
    
    这样的话再把需要留下评论的页面 front matter 改回原来的链接格式`year/:month/:day/:title/`，**不仅仅是格式，日期名称也必须和原来保持一致**
    
2.  群友提示，如果像我一样用的 valine 评论，可以直接在 leancloud 后台修改 URL，valine 绑定的相对路径，哪怕更换域名，只要保证文章链接一致，评论便可保留。  
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/QQ%E6%88%AA%E5%9B%BE20200619095538.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/QQ%E6%88%AA%E5%9B%BE20200619095538.png)
    
    leancloud
    

### [](#常用链接格式 "常用链接格式")常用链接格式

<table><thead><tr><th>permalink</th><th>格式预览</th></tr></thead><tbody><tr><td>:abbrlink/</td><td>xxx.com/xxx</td></tr><tr><td>:abbrlink.html/</td><td>xxx.com/xxx.html</td></tr><tr><td>posts/:abbrlink.html/</td><td>xxx.com/posts/xxx.html</td></tr><tr><td>article/:abbrlink.html/</td><td>xxx.com/article/xxx.html</td></tr></tbody></table>

### [](#pinyin插件 "pinyin插件")pinyin 插件

*   将中文链接转拼音，安装插件
    
    ```
    npm i hexo-permalink-pinyin --save
    ```
    
*   在 Hexo 根目录下的 _config.yml 文件中，修改以下的配置项：
    
    ```
    permalink: article/:title.html
    permalink_pinyin:
    enable: true
    separator: '-'  
    permalink_defaults:
    ```
    
    永久链接格式为`https://xxx.com/posts/wen-zhang-ming.html`
*   实用性不是很好，如果标题文字很多，链接依然会很长。

[](#如何在页脚养鱼 "如何在页脚养鱼")如何在页脚养鱼
-----------------------------

效果就在页脚，是不是很想要？这里简述 butterfly 主题的引入方法，其他主题类似，实在不行建议更换 butterfly 主题

！！！不要修改源码，若已修改请恢复原样  
在主题配置的`inject`引入 js: [https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fishes.js](https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fishes.js) **即可**  

```
- <script src="https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fishes.js"></script>
```

调整页脚阴影透明度`themes\butterfly\source\css\_layout\footer.styl`

```
background-color: alpha($dark-black, .1)
```

文章页页脚宽度多余导致出现横向滚动条，新建`xxx.css`，添加以下 css 引入`inject`即可（若设置了全局背景去掉固定高度`height: 160px`引入即可）

```
/* 鱼塘固定宽度 */
canvas:not(#ribbon-canvas), #web_bg {
    margin-bottom: -0.5rem;
    display: block;
    width: 100%;
    height: 160px
}
```

修改源码实现方法（其它主题可参考此处）

1.  先将扒来的 code 转为 pug
    
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/Snipaste_2020-07-05_10-36-45.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/Snipaste_2020-07-05_10-36-45.png)
    
    htmltopug
    
      
    写进`\themes\butterfly\layout\includes\footer.pug`末尾
    
    ```
    #jsi-flying-fish-container.containerscript(src='js/fish.js')style.    @media only screen and (max-width: 767px){    #sidebar_search_box input[type=text]{width:calc(100% - 24px)}    }
    ```
    
2.  然后在`inject`引入 js: [https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fish.js](https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fish.js)
    
    ```
    - <script src="https://cdn.jsdelivr.net/gh/xiabo2/CDN@latest/fish.js"></script>
    ```
    
3.  引入之后效果如下，页脚太高，`themes\butterfly\source\css\_layout\footer.styl`调整下 css 即可 (补充：调整页脚阴影透明度为 0.1)  
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/fish.gif)](https://cdn.jsdelivr.net/gh/xiabor/img/i/fish.gif)
    
    页脚跳动的鱼
    
    ```
    #footer-wrapposition: absolutepadding: 1.2rem 1rem 1.4remcolor: $light-greytext-align: centerleft: 0right: 0top:0bottom: 0#footer  if hexo-config('footer_bg') != false    &:before    position: absolute    width: 100%    height: 100%    background-color: alpha($dark-black, .1)    content: ''
    ```
    
4.  另外，还是会出现报错，  
    [![](https://cdn.jsdelivr.net/gh/xiabor/img/i/fish20200702225229.png)](https://cdn.jsdelivr.net/gh/xiabor/img/i/fish20200702225229.png)
    
    报错
    
    引用 JS 报错 Uncaught ReferenceError: $ is not defined  
    原因一：未引用 jquery 库 jquery.min.js 文件，或者说路径错误；
    
    解决办法：  
    很简单，引用 jquery-X.X.X.min.js 这个 js 路径文件到当前页面即可。
    
    `<script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>`  
    建议将 js 保存到本地引用
    
    `<script src="你的路径/jquery.min.js"></script>`  
    原因二：忽略了 HTML 中`<script>`引入 jQuery 文件的顺序，要把 JQuery 库的引用放到第一个`<script>`引用前面，这样顺序执行后面的 js 文件才能识别 $。
    

（主题已经引入 jquery）调整了好久，还是没能解决报错，有人催更如何页脚养鱼就直接写出来了，报错交给各位解决吧。

版权声明: 本博客所有文章除特别声明外，均采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议。转载请注明来自 [MuJin's Blog](https://xiabor.com/)！

ღ喜欢记得五星好评哦~

* * *