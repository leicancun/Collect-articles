> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [rocpeak.gitee.io](https://rocpeak.gitee.io/2019/11/10/%E6%90%AD%E5%BB%BA%20Hexo%20%E5%8D%9A%E5%AE%A2/)

本教程基于 Windows：

[![](https://s1.ax1x.com/2020/07/03/NO5zhd.png)](https://s1.ax1x.com/2020/07/03/NO5zhd.png "Windows规格.png")

[Windows 规格. png](https://s1.ax1x.com/2020/07/03/NO5zhd.png "Windows规格.png")

**建议：安装 node 前先安装好 git，利用 Git Bash Here 可以完美替换 cmd**

理由：它是一个非常好的命令行哈，完美兼容 Linux 与 win 命令

[Git 安装配置教程](https://blog.csdn.net/u013295518/article/details/78746007)

[](#基础准备 "基础准备")基础准备[](#基础准备)
=============================

[](#安装环境 "安装环境")安装环境[](#安装环境)
-----------------------------

到 [官网](https://nodejs.org/en/) 下载并安装 node.js LTS 版本

[![](https://s1.ax1x.com/2020/07/03/NO5Ih9.png)](https://s1.ax1x.com/2020/07/03/NO5Ih9.png "nodejs版本.png")

[nodejs 版本. png](https://s1.ax1x.com/2020/07/03/NO5Ih9.png "nodejs版本.png")

安装完成后打开 cmd 命令提示符输入以下命令查看 node.js 和 npm 的版本

```
node -v
npm -v
```

[![](https://s1.ax1x.com/2020/07/03/NOIKcq.png)](https://s1.ax1x.com/2020/07/03/NOIKcq.png "查看node与npm的版本.png")

[查看 node 与 npm 的版本. png](https://s1.ax1x.com/2020/07/03/NOIKcq.png "查看node与npm的版本.png")

[](#安装包管理器 "安装包管理器")安装包管理器[](#安装包管理器)
-------------------------------------

由于国内镜像源安装很慢，所以先利用 npm (包管理器) 安装 cnpm，命令如下：

```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

[](#安装hexo博客框架 "安装hexo博客框架")安装 hexo 博客框架[](#安装hexo博客框架)
-------------------------------------------------------

```
cnpm install -g hexo-cli
```

安装完成后查看版本

```
hexo -v
```

[![](https://s1.ax1x.com/2020/07/03/NOIMj0.png)](https://s1.ax1x.com/2020/07/03/NOIMj0.png "查看hexo的版本.png")

[查看 hexo 的版本. png](https://s1.ax1x.com/2020/07/03/NOIMj0.png "查看hexo的版本.png")

[](#基本命令 "基本命令")基本命令[](#基本命令)
-----------------------------

```
node -v        // 查看node版本
npm -v         // 查看包管理器版本
shdo hexo init // 初始化博客
hexo n         // 新建帖子
hexo clean     // 清理
hexo g         // 生成
hexo s         // 启动本地博客
hexo d         // 部署到远端
```

[](#创建专属博客的文件夹 "创建专属博客的文件夹")创建专属博客的文件夹[](#创建专属博客的文件夹)
-----------------------------------------------------

也就是博客的根目录，整个博客都基于这个文件夹

cd 到硬盘理想的位置，文件夹命名随意 (建议规范命名)

```
mkdir blog
```

进入博客根目录

```
cd blog
```

初始化博客

```
sudo hexo init
```

初始化完成后会提示：Start bloggers with Hexo！

[](#启动博客 "启动博客")启动博客[](#启动博客)
-----------------------------

```
hexo s
```

用浏览器打开本地主机的博客地址，按 `Ctrl + C` 停止本地博客

[http://localhost:4000](http://localhost:4000/)

新建一篇文章

```
hexo n "文章名称"
```

打开编辑文章：盘符:/……/blog/source/_posts/“你的文章名称. md”

建议使用 Typora 软件来编辑 md 文件

编辑完成后保存退出并回到博客的根目录

清理博客，然后生成新的博客

```
hexo clean
hexo g
```

再次启动博客就可以看到刚刚编辑的文章了

本地博客这样就完成啦！也没有多少条命令哈哈

嗯，一切都这么简单，优雅…

[](#部署到远端 "部署到远端")部署到远端[](#部署到远端)
---------------------------------

GitHub (免费 (访问速度不理想))

登录 GitHub (没有请先免费注册 [https://github.com](https://github.com/))

新建一个仓库 (用于存放 git 推上来的博客资源文件)

*** 该仓库的命名要求：/ 你 GitHub 的昵称. github.io**

后续就可以用 `https://你GitHub的昵称.github.io` 访问博客了

[](#安装git插件 "安装git插件")安装 git 插件[](#安装git插件)
-------------------------------------------

```
cnpm install --save hexo-deployer-git
```

**在根目录下打开 `_config.yml` 配置文件**

**在 # Deployment (部署方式) 下设定部署到远端的地址**

```
deploy:
  type: git
  repo: 这里的地址为你刚才新建的仓库地址
  branch: master
```

修改完配置文件后保存退出 (vim 命令：按 Esc 退出编辑模式进入命令模式后，`:wq`)

[](#把博客推送到远端 "把博客推送到远端")把博客推送到远端[](#把博客推送到远端)
---------------------------------------------

第一次推送需要登录 GitHub 账号及密码

```
hexo d      // 部署到远端服务器
hexo g -d   // 生成博客并部署到远端
```

然后你就可以在仓库看到那些关于博客生成的资源文件了

用 https:// 你 GitHub 的昵称. github.io 就可以让别人访问你的博客了

从此以后你就可以利用 md 文档编写你的博客了

[](#更换主题 "更换主题")更换主题[](#更换主题)
-----------------------------

从 GitHub 克隆 yilia 主题到本地

```
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
git clone https://github.com/theme-next/hexo-theme-next.git themes/next
```

**更改根目录配置文件的主题参数**

修改 hexo 根目录下的 `_config.yml` 文件

```
theme: yilia
```

[](#日常三步走 "日常三步走")日常三步走[](#日常三步走)
---------------------------------

```
hexo clean  // 清理
hexo g      // 生成
hexo s      // 启动本地博客
```

[](#深入修改样式 "深入修改样式")深入修改样式[](#深入修改样式)
=====================================

[](#自定义样式文件 "自定义样式文件")自定义样式文件[](#自定义样式文件)
-----------------------------------------

**新建 customize_main.0cf68a.css 样式文件**

用途：用于覆盖 `main.0cf68a.css` 样式文件里与自定义样式重复的默认样式

应用：主题文件目录下的`_config.yml` 中添加

```
# 启动自定义样式文件
customize: true
```

打开 `E:\Projects\blog\themes\yilia\layout\_partial\head.ejs` 文件

**在 `<%- partial('css') %>` 行后面添加如下代码**

```
<% if (theme.customize){ %>
    <link href="//cdn.bootcss.com/animate.css/3.5.0/animate.min.css" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="/./customize_main.0cf68a.css">
<% } %>
```

**这样子网页就会加载自定义的样式文件，并覆盖默认样式里与自定义重复的样式**

也就是必须先加载默认样式文件后再加载自定义样式文件，才能达到覆盖的效果

**注意：在以下样式代码中 customize_main.0cf68a.css 文件的样式会覆盖 main.0cf68a.css 文件的样式**

[](#添加来必力评论系统 "添加来必力评论系统")添加来必力评论系统[](#添加来必力评论系统)
-------------------------------------------------

注册登录来必力官网，安装来必力系统，

在 `E:\Projects\blog\themes\yilia\layout\_partial\post` 目录下新建 `livere.ejs` 文件后打开粘贴

copy 下来的安装代码：

```
<!-- 来必力City版安装代码 -->
<div data-id="city" data-uid="<%=theme.livere_uid%>">
  <script type="text/javascript">
   (function(d, s) {
       var j, e = d.getElementsByTagName(s)[0];
       if (typeof LivereTower === 'function') { return; }
       j = d.createElement(s);
       j.src = 'https://cdn-city.livere.com/js/embed.dist.js';
       j.async = true;
       e.parentNode.insertBefore(j, e);
   })(document, 'script');
  </script>
<noscript> 为正常使用来必力评论功能请激活JavaScript </noscript>
</div>
<!-- City版安装代码已完成 -->
```

打开 `E:\Projects\blog\themes\yilia` 目录下的 `_config.yml` 主题配置文件

**在评论的区域加入来必力评论系统的 ID**

```
#0、来必力
livere_uid: MTAyMC80NzI1OS8yMzc1OQ
```

[](#来必力评论系统优化 "来必力评论系统优化")来必力评论系统优化[](#来必力评论系统优化)
-------------------------------------------------

解决方案：

打开 `E:\Projects\blog\themes\yilia\layout\_partial\article.ejs` 文件

在第 `<% if (!index && post.comments){ %>` 行后添加如下代码：

```
<div>
  <!-- 来必力评论系统 -->
  <% if (theme.livere){ %>
    <%- partial('post/livere', {
      key: post.slug,
      title: post.title,
      url: config.url+url_for(post.path)
    }) %>
  <% } %>      
</div>
```

打开 `E:\Projects\blog\themes\yilia\source\customize_main.0cf68a.css` 自定义样式文件

**为来必力系统添加 CSS 样式：**

```
/* 来必力样式代码 */
.comment-area-customize {
  line-height: 1.8em;
  padding-right: 7.6923%;
  padding-left: 7.6923%;
  margin: 0 30px;
  background-color: #FFF;
  overflow: hidden;
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  border-radius: 18px;
}
/* 来必力背景过渡 */
 .comment-area-customize {
  background: hsla(0, 0%, 100%, .3);
}
/* 移动端来必力样式 */
@media screen and (max-width: 800px) {
  .comment-area-customize {
    margin: auto;
    background-color: #FFF;
  }
  .mid-col.show .comment-area-customize {
    background: hsla(0, 0%, 100%, .3)
  }
}
```

[](#文章类型标签优化 "文章类型标签优化")文章类型标签优化[](#文章类型标签优化)
---------------------------------------------

**把标签位置迁移到文章标题下方：**

打开 `E:\Projects\blog\themes\yilia\layout\_partial\article.ejs` 文件

在

```
<!-- 文章标题与文章日期 -->
<%- partial('post/title', {class_name: 'article-title'}) %>
<% if (!post.noDate){ %>
  <%- partial('post/date', {class_name: 'archive-article-date', date_format: null}) %>
<% } %>
```

代码块的下方添加如下代码：

```
<!-- 把下方的文章标签代码连同样式一并上移到文章标题的下方 -->
<div>
  <%if(post.top){%>
    <div>
      <i></i>
      <a>置顶</a>
    </div>
  <% } %>
  <%- partial('post/tag') %>
  <%- partial('post/category') %>
</div>
```

然后删除该文件下方的标签代码。

打开 `E:\Projects\blog\themes\yilia\source\customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章类型标签优化 */
.article-info-index.article-info-customize {
  margin: 10px 0;
  min-height: 20px;
}
/* 文章类型标签移动端优化 */
@media screen and (max-width: 800px) {
  .article-info-index.article-info-customize {
    margin: 10px 0 20px;
    min-height: 20px;
  }
}
/* 标签tag开关微调 */
.tools-col .tools-section .search-tag.tagcloud .search-switch input:after {
  top: 104%;
  left: 3px;
  width: 11px;
  height: 11px;
  background-color: #64BD63;
}
.tools-col .tools-section .search-tag.tagcloud .search-switch input:checked:after {
  left: 28px;
  width: 12px;
  height: 12px;
}
/* 标签云背景优化 */
.tools-col .tools-section .search-tag.tagcloud .article-tag-list {
  border-radius: 8px;
}
/* 标签云选中文章鼠标悬停背景圆角优化 */
.tools-col .tools-section .search-ul .search-li:hover {
  background: hsla(0, 0%, 100%, .2);
  border-radius: 8px;
}
/* 隐藏标签云文章分割线 */
.tools-col .tools-section .search-ul .search-li {
  margin: 0 30px 0 10px;
  padding: 10px 10px;
  border-bottom: 0 dotted #dcdcdc;
}
@media screen and (max-width: 800px) {
  .tools-col .tools-section .search-ul .search-li {
    margin: 0 20px 0 10px;
  }
}
```

[](#干掉文章标题前的小黑块 "干掉文章标题前的小黑块")干掉文章标题前的小黑块[](#干掉文章标题前的小黑块)
---------------------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 干掉文章标题前的小黑块 */
.article-header {
  border-left: none;
  padding: 30px 7.6923% 15px;
}
```

[](#展开全文按钮优化 "展开全文按钮优化")展开全文按钮优化[](#展开全文按钮优化)
---------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 展开全文按钮优化 */
.article-more-link {
  float: left;
}
.article-more-link a {
  background: rgba(77, 77, 77, 0.2);
  color: #999999;
  border-radius: 18px;
}
.mid-col.show .article .article-more-link a {
  background: rgba(77, 77, 77, 0.1);
  color: #999999;
}
.article-more-link a:hover {
  color: #FFFFFF;
  background: #39C7F7
}
.mid-col.show .article .article-more-link a:hover {
  color: #FFFFFF;
  background: #39C7F7
}
```

[](#文章标题优化 "文章标题优化")文章标题优化[](#文章标题优化)
-------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章标题行距优化 */
a.article-title:hover {
  color: #39C7F7;
}
.article-entry h1 {
  text-align: center;
  font-weight: 500;
  margin-top: 2em;
}
.article-entry h2, .article-entry h3, .article-entry h4, .article-entry h5, .article-entry h6 {
  margin-top: 40px;
  margin-bottom: 0;
  color: #574c4c;
  font-weight: 500;
}
```

[](#文章日期优化 "文章日期优化")文章日期优化[](#文章日期优化)
-------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章日期优化 */
.archive-article-date {
  margin-right: 0;
}
.archive-article-date:hover {
  color: #39C7F7;
}
.archive-article-inner .article-meta .archive-article-date {
  cursor: pointer;
}
.archive-article-date:hover time {
  color: #39C7F7;
}
```

[](#文章文本行距优化 "文章文本行距优化")文章文本行距优化[](#文章文本行距优化)
---------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章文本行距优化 */
.article-entry p,
.article-entry table {
  line-height: 1.8em;
  margin: .5em 0;
}
```

[](#文章归档框圆角化 "文章归档框圆角化")文章归档框圆角化[](#文章归档框圆角化)
---------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章归档框圆角化 */
.article {
  border: 0;
  /*overflow: hidden;*/
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  border-radius: 18px;
}
.archives-wrap {
  background: rgba(255, 255, 255, 0.5);
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  /*border-radius: 18px;*/
}
.archives-wrap:first-child {
  margin-top: 30px;
  border-radius: 18px 18px 0 0;
}
.archives-wrap:last-child {
  margin-bottom: 80px;
  border-radius: 0 0 18px 18px;
}
```

[](#文章行内代码块优化 "文章行内代码块优化")文章行内代码块优化[](#文章行内代码块优化)
-------------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章行内代码块优化 */
.article-entry li code, .article-entry p code {
  padding: 3px 3px;
  margin: 0 3px;
  background: rgba(57, 199, 247, 0.4);
  border: none;
  border-radius: 5px;
  word-wrap: break-word;
  font-size: 14px;
  font-family: "DejaVu Sans Mono", Menlo, Monaco, Andale Mono, Microsoft YaHei, lucida console, Courier New, monospace;
}
.mid-col.show .article-entry li code, .mid-col.show .article-entry p code {
  background: rgba(57, 199, 247, 0.2);
}
```

[](#文章代码块优化 "文章代码块优化")文章代码块优化[](#文章代码块优化)
-----------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章代码块优化 */
.article-entry .highlight {
  border-radius: 8px;
  transition: all .2s ease-in;
}
.article-entry .highlight .line {
  color: #fff;
  min-height: 19px;
  overflow-x: auto;
  white-space: pre;
  font-family: "DejaVu Sans Mono", Menlo, Monaco, Andale Mono, Microsoft YaHei, lucida console, Courier New, monospace;
}
.article-entry pre {
  background: none;
}
.article-entry .highlight {
  background: rgba(39, 40, 34, .7);
}
.article-entry .highlight:hover {
  background: rgba(39, 40, 34, 1);
}
.mid-col.show .article-entry .highlight {
  background: rgba(39, 40, 34, .3);
}
.mid-col.show .article-entry .highlight:hover {
  background: rgba(39, 40, 34, 1);
}
/* 禁止代码块行号被鼠标选中 */
.gutter pre {
  moz-user-select: -moz-none;
  -moz-user-select: none;
  -o-user-select:none;
  -khtml-user-select:none;
  -webkit-user-select:none;
  -ms-user-select:none;
  user-select:none;
}
/* 代码块行号右边框填充 */
.article-entry .highlight .gutter pre {
  color: #999;
  padding-right: 10px;
  border-right: 1px solid #999;
}
.article-entry .highlight .code pre {
  padding-left: 10px;
}
/* 行号颜色 */
.article-entry .highlight .gutter pre .line {
  color: #999;
  text-shadow: 0 1px #444;
}
/* 代码块样式之评论：黄色 */
pre .comment {
  color:#ffec8b
}
/* 代码块样式之类的参数、函数的关键字、关键字：蓝色 */
pre .class .params, pre .function .keyword, pre .keyword, pre .literal {
  color:#66d9ef
}
/* 代码块样式之css的属性值、函数名、参数、标签：白色 */
pre .css .value, pre .doctype, pre .function, pre .params, pre .tag {
  color:#ccc
  /* color:#66d9ef; */
}
/* 代码块样式之HTML或者xml的头部元素：红色(颜色较浅) */
pre .meta{
  color:#f78da1;
}
/* 代码块样式之HTML的标签：红色 */
pre .tag .name {
  /* color:#dc3958; */
  color:#ff6481;
}
/* 代码块样式之：色 */
pre .at_rule, pre .at_rule .keyword, pre .css~* .tag, pre .preprocessor, pre .preprocessor .keyword, pre .title{
  color:#fa9400
}
/* 代码块样式之属性、类、函数的title：绿色 */
pre .attr,pre .attribute, pre .built_in, pre .class, pre .css~* .class, pre .function .title {
  color:#a6e22e
}
/* 代码块样式之字符串、属性值：猪肝色 */
pre .string, pre .value {
  color:#e6db74
}
/* 代码块样式之数字：粉红色 */
pre .number {
  color:#ffe4b5
}
pre .css~* .id, pre .id {
  color:#fd971f
}
```

[](#文章代码块复制功能 "文章代码块复制功能")文章代码块复制功能[](#文章代码块复制功能)
-------------------------------------------------

在 `hexo` 的根目录下的 `themes\yilia\source\js` 中新建 `clipboard_use.js` 如下:

注意：按钮中的字体图标需引入 `Font Awesome` 图标库，详见 Font Awesome 中文网

```
$(".highlight").wrap("<div class='code-wrapper' style='position:relative'></div>");
/*页面载入完成后，创建复制按钮*/
!function (e, t, a) {
  /* code */
  var initCopyCode = function () {
    var copyHtml = '';
    copyHtml += '<button data-clipboard-snippet="">';
    copyHtml += '  <i></i><span>复制</span>';
    copyHtml += '</button>';
    $(".highlight .code").before(copyHtml);
    var clipboard = new ClipboardJS('.btn-copy', {
      target: function (trigger) {
        return trigger.nextElementSibling;
      }
    });
    clipboard.on('success', function (e) {
      e.trigger.innerHTML = "<i class='fa fa-check' style='color:green'></i><span style='color:green'>复制成功</span>"
      setTimeout(function () {
        e.trigger.innerHTML = "<i class='fa fa-clipboard'></i><span>复制</span>"
      }, 1000)
      e.clearSelection();
    });
    clipboard.on('error', function (e) {
      e.trigger.innerHTML = "<i class='fa fa-exclamation' style='color:red'></i><span style='color:red'>复制失败</span>"
      setTimeout(function () {
        e.trigger.innerHTML = "<i class='fa fa-clipboard'></i><span>复制</span>"
      }, 1000)
      e.clearSelection();
    });
  }
  initCopyCode();
}(window, document);
```

在 `hexo` 的根目录下的 `themes\yilia\layout\layout.ejs` 文件的 `</body>` 前引入

```
<!-- 代码块复制功能 -->
<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/clipboard@2.0.4/dist/clipboard.js"></script>
<script type="text/javascript" src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script type="text/javascript" src="/js/clipboard_use.js"></script>
```

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章代码块复制功能 */
.btn-copy {
  display: inline-block;
  cursor: pointer;
  background-color: #eee;
  background-image: linear-gradient(#fcfcfc, #eee);
  border: 1px solid #d5d5d5;
  border-radius: 3px;
. -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  -webkit-appearance: none;
  font-size: 13px;
  font-weight: 700;
  line-height: 20px;
  color: #333;
  -webkit-transition: opacity .3s ease-in-out;
  -o-transition: opacity .3s ease-in-out;
  transition: opacity .3s ease-in-out;
  padding: 2px 6px;
  position: absolute;
  right: 5px;
  top: 5px;
  opacity: 0;
}
.btn-copy span {
  margin-left: 5px;
}
.highlight:hover .btn-copy {
  opacity: 1;
}
```

参考：[https://www.yansheng.xyz/article/e9d1b881.html](https://www.yansheng.xyz/article/e9d1b881.html)

[](#文章字体优化 "文章字体优化")文章字体优化[](#文章字体优化)
-------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 文章字体优化 */
body, button, input, select, textarea {
  font-family: "DejaVu Sans Mono", lucida grande, lucida sans unicode, lucida, helvetica, Hiragino Sans GB, Microsoft YaHei, WenQuanYi Micro Hei, sans-serif;
}
```

[](#文章超链接优化 "文章超链接优化")文章超链接优化[](#文章超链接优化)
-----------------------------------------

```
/* 文章超链接优化 */
/* 文章中的超链接,鼠标悬浮特效 */
.article-entry a{
  display: inline-block;
  position: relative;
  color: #08c;
}
/* 鼠标悬浮时，变色 */
.article-entry a:hover {
  color: #d7191a;
  transition: .4s ease-in-out;
}
/* 鼠标悬浮时，变色, 赞赏按钮例外 */
.article-entry a:hover .tooltip-item {
  color: #fff;
}
/* 鼠标悬浮时，下划线从中间向两边延伸 */
.article-entry a:hover::after {
  transform: scaleX(1);
  /* 旋转，与transform连用；这里作用：鼠标悬浮时，底部的下划线从中间扩散到两边。
     bottom right :左到右出现，左到右消失（需配合上面的::after）*/
  transform-origin: bottom center;
}
/* 鼠标移开后，下划线从两边向中间消失 */
.article-entry a::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: .1rem;
  bottom: 0;
  left: 0;
  background-color: #08c;
  /* 详见：https://www.w3school.com.cn/cssref/pr_transform-origin.asp,
     旋转，与transform连用；这里作用：鼠标移开后，底部的下划线从中间开始消失 */
  transform-origin: bottom center;
  transition: transform .3s ease-out;
}
/* 赞赏超链接例外 */
.page-reward a::after {
  content: none;
}
```

[](#文章图片优化 "文章图片优化")文章图片优化[](#文章图片优化)
-------------------------------------

```
/* 文章图片优化 */
.article img {
  display:block;
  margin-left: auto;
  margin-right:auto;
  opacity: .7;
  border-radius: 8px;
  transition: all .2s ease-in;
}
.mid-col.show .article img {
  opacity: 0.3;
  transition: all .2s ease-in;
}
.mid-col.show .article img:hover {
  opacity: 1;
}
/* 文章图片全屏时降低遮罩 */
.pswp__bg {
  opacity: .8!important;
}
/* 文章赞赏二维码区域优化 */
.reward-box-item .reward-img {
  opacity: 1;
}
.page-reward .reward-type {
  color: #fff;
}
.tooltip-top .tooltip:hover .tooltip-text {
  border-radius: 8px;
}
.tooltip-top .tooltip-text {
  transition: all .3s ease-in-out;
}
```

[](#左列个人主页优化 "左列个人主页优化")左列个人主页优化[](#左列个人主页优化)
---------------------------------------------

**干掉头像上方的颜色方块**

打开 `E:\Projects\blog\themes\yilia\layout\_partial\left-col.ejs` 文件

注释或者删除如下这行代码：

```
<!-- 注释了头像上方的颜色方块
<div style="background: <%= theme.style && theme.style.header ? theme.style.header : defaultBg %>"></div>
-->
```

**主页随笔取消换行**

注释或者删除如下这行代码的 `<li>` 标签：

```
<!-- 主页随笔取消换行 -->
<!--<li>--><a href="<%- url_for(theme.menu[i]) %>"><%= i %></a><!--</li>-->
```

**个人主页样式优化**

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* 左列个人主页优化 */
.left-col {
  margin: 30px 0;
  height: 91.5%;
  /* overflow: hidden; */
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  border-radius: 0 18px 18px 0;
}
/*左列背景过渡到透明*/
.left-col.show {
  background: hsla(0, 0%, 0%, .0);
  box-shadow: 0 0 0 0 rgba(0, 0, 0, .0);
  margin: 30px auto;
  border-radius: 0;
}
/* 头像优化 */
.left-col .intrude-less {
  margin: 12% auto 0;
}
.left-col #header .profilepic {
  border: 0 solid #fff;
  -webkit-box-shadow: 0 0 0 2px rgba(255,255,255,0.5), 0px 2px 20px 3px rgba(0,0,0,0.25);
  box-shadow: 0 0 0 2px rgba(255,255,255,0.5), 0px 2px 20px 3px rgba(0,0,0,0.25);
}
/* 头像跃动 */
.left-col #header .profilepic:hover {
  -webkit-animation: jello 1s;
  animation: jello 1s;
}
/* 移动端头像优化 */
@media screen and (max-width: 800px) {
  .profilepic {
    width: 100px;
    height: 100px;
    margin: 15px auto 30px;
    border: 0 solid #fff;
    -webkit-box-shadow: 0 0 0 2px rgba(255,255,255,0.5), 0px 2px 20px 3px rgba(0,0,0,0.25);
    box-shadow: 0 0 0 2px rgba(255,255,255,0.5), 0px 2px 20px 3px rgba(0,0,0,0.25);
  }
  /* 头像跃动 */
  .profilepic:hover {
    -webkit-animation: jello 1s;
    animation: jello 1s;
  }
}
/*
!*头像旋转360°，鼠标离开后又转回来，代码如下:*!
.left-col #header .profilepic img {
  !* 控制旋转速度时间*!
  -webkit-transition: -webkit-transform 1.0s ease-out;
  -moz-transition: -moz-transform 1.0s ease-out;
  transition: transform 1.0s ease-out;
}
.left-col #header .profilepic img:hover {
  !* 鼠标经过360% *!
  -webkit-transform: rotateZ(360deg);
  -moz-transform: rotateZ(360deg);
  transform: rotateZ(360deg);
}
*/
/* 个人描述字体粗细 */
.left-col #header .header-subtitle {
  font-weight: 300;
}
/* 所有文章 友链 关于我 */
.left-col #header a {
    font-weight: 300;
}
.left-col #header .header-smart-menu a:after {
    content: "";
}
/* 主页随笔自动居中 */
.left-col #header .header-menu {
margin: auto;
}
/* 主页随笔移动端按钮高亮并增大头像背景高度 */
@media screen and (max-width: 800px) {
  .header-menu li a:hover {
    color: #FFFFFF;
    background: #39C7F7
  }
  #mobile-nav .overlay {
    height: 150px;
  }
}
/* 跳转到站外按钮高亮 */
#header .header-nav .social a.github:hover {
  background: #000000;
  border: 1px solid #000000;
}
#header .header-nav .social a.weibo:hover {
  background: #E6162D;
  border: 1px solid #E6162D;
}
#header .header-nav .social a.rss:hover {
  background: #FF6600;
  border: 1px solid #FF6600;
}
#header .header-nav .social a.zhihu:hover {
  background: #0E88EB;
  border: 1px solid #0E88EB;
}
```

[](#移动端三点式菜单页面优化 "移动端三点式菜单页面优化")移动端三点式菜单页面优化[](#移动端三点式菜单页面优化)
-------------------------------------------------------------

```
/* 移动端三点式菜单页面优化 */
@media screen and (max-width: 800px) {
  /* 菜单页面宽度 */
  .tools-col .tools-section, .tools-col .tools-wrap {
    width: 333px;
  }
  /* 搜索按钮偏移 */
  .tools-col .tools-section .search-wrap, .tools-col .tools-wrap .search-wrap {
    width: 292px;
  }
  /* 搜索边框偏移 */
  .tools-col .tools-section .search-wrap .search-ipt {
    width: 293px;
  }
  /* 标签余量归零 */
  .tools-col .tools-section .search-tag.tagcloud, .tools-col .tools-wrap .search-tag.tagcloud {
     margin-right: 0;
  }
  /* 标签提示符tag:偏移 */
  .tools-col .tools-section .search-tag.tagcloud .search-tag-wording {
    margin: 4px 69px 0 0;
  }
  /* 标签按钮偏移 */
  .tools-col .tools-section .search-tag.tagcloud .search-switch input {
    width: 34px;
  }
}
```

[](#增大移动端文章间隔 "增大移动端文章间隔")增大移动端文章间隔[](#增大移动端文章间隔)
-------------------------------------------------

```
/* 增大移动端文章间隔 */
@media screen and (max-width: 800px) {
  .article {
    margin: 20px 0;
  }
}
```

[](#添加公众号 "添加公众号")添加公众号[](#添加公众号)
---------------------------------

打开 `E:\Projects\blog\themes\yilia\_config.yml` 文件

将 menu 拆分为如下：

```
menu:  
  主页: /
menu1:  
  公众号:
menu2:  
  相册: /404/index.html
```

打开 `E:\Projects\blog\themes\yilia\layout\_partial\left-col.ejs` 文件

主页相册的更改：

```
<nav>
  <ul>
    <% for (var i in theme.menu){ %>
      <a href="<%- url_for(theme.menu[i]) %>"><%= i %></a>
    <%}%>
    <% for (var i in theme.menu1){ %>
      <a href="#"><%= i %></a>
      <div><img src="/img/lessroc.jpg" alt="公众号"></div>
    <%}%>
    <% for (var i in theme.menu2){ %>
      <a href="<%- url_for(theme.menu2[i]) %>"><%= i %></a>
    <%}%>
  </ul>
</nav>
```

打开 `E:\Projects\blog\themes\yilia\layout\_partial\mobile-nav.ejs` 文件

移动端主页相册的更改：

```
<nav>
  <ul style="width: <%= ulWidth %>">
    <% var divide = 100 / count + '%' %>
    <% for (var i in theme.menu){ %>
      <li style="width: <%= divide %>"><a href="<%- url_for(theme.menu[i]) %>"><%= i %></a></li>
    <%}%>
    <% var divide = 100 / count + '%' %>
    <% for (var i in theme.menu1){ %>
      <li style="width: <%= divide %>"><a href="#"><%= i %></a></li>
      <div><img src="/img/lessroc.jpg" alt="公众号"></div>
    <%}%>
    <% var divide = 100 / count + '%' %>
    <% for (var i in theme.menu2){ %>
      <li style="width: <%= divide %>"><a href="<%- url_for(theme.menu2[i]) %>"><%= i %></a></li>
    <%}%>
  </ul>
</nav>
```

打开 `E:\Projects\blog\themes\yilia\source\customize_main.0cf68a.css` 样式文件

为以上更改添加样式：

```
/* 公众号 */
.show_img {
  padding-bottom: 5px;
}
.hide_img {
  position: absolute;
  z-index: 9999;
  display: block;
  width: 50px;
  margin: auto 40px;
  -webkit-box-shadow: none;
  box-shadow: none;
  transition: all .2s ease-in;
}
.hide_img:hover,
.show_img:hover + .hide_img,
.left-col.show .show_img:hover + .hide_img,
.left-col.show .hide_img:hover {
  display: block;
  width: 77%;
  margin: auto -22px;
  border-radius: 18px;
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
}
.show_img:hover + .hide_img img,
.hide_img img {
  transition: all .2s ease-in;
  background-color: rgba(255, 255, 255, 0);
}
.show_img:hover + .hide_img img,
.hide_img img:hover {
  border-radius: 18px;
  background-color: rgba(255, 255, 255, 1);
}
/* 左列弹出过渡 */
.left-col.show .hide_img {
  margin: auto 60px;
  width: 0;
  transition: all .2s ease-in;
}
/*.left-col.show .show_img {
  padding-bottom: 0;
}*/
/* 公众号移动端过渡 */
@media screen and (max-width: 800px) {
  .hide_image {
    display: block;
    z-index: 9999;
    position: absolute;
    width:  0;
    margin: -19px auto;
    transition: all .2s ease-in;
  }
  .show_image:hover + .hide_image {
    display: block;
    width: 60px;
    margin: -48px auto;
    transition: all .2s ease-in;
    -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
    box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  }
}
```

[](#解决文章图片显示异常 "解决文章图片显示异常")解决文章图片显示异常[](#解决文章图片显示异常)
-----------------------------------------------------

设置站点配置_config.yml:

将 `post_asset_folder: false` 改为 `post_asset_folder: true`  
安装插件: npm install [https://github.com/CodeFalling/hexo-asset-image](https://github.com/CodeFalling/hexo-asset-image) – save

[](#单击上浮爱心 "单击上浮爱心")单击上浮爱心[](#单击上浮爱心)
-------------------------------------

页面点击出现爱心的实现  
在 `\blog\themes\yilia\source` 里新建一个 `love.js` 文件，加入如下代码：

```
!function (e, t, a) {
  function n() {
    c(".heart{width: 10px;height: 10px;position: fixed;background: #f00;transform: rotate(45deg);-webkit-transform: rotate(45deg);-moz-transform: rotate(45deg);}.heart:after,.heart:before{content: '';width: inherit;height: inherit;background: inherit;border-radius: 50%;-webkit-border-radius: 50%;-moz-border-radius: 50%;position: fixed;}.heart:after{top: -5px;}.heart:before{left: -5px;}"), o(), r()
  }

  function r() {
    for (var e = 0; e < d.length; e++) d[e].alpha <= 0 ? (t.body.removeChild(d[e].el), d.splice(e, 1)) : (d[e].y--, d[e].scale += .004, d[e].alpha -= .013, d[e].el.style.cssText = "left:" + d[e].x + "px;top:" + d[e].y + "px;opacity:" + d[e].alpha + ";transform:scale(" + d[e].scale + "," + d[e].scale + ") rotate(45deg);background:" + d[e].color + ";z-index:99999");
    requestAnimationFrame(r)
  }

  function o() {
    var t = "function" == typeof e.onclick && e.onclick;
    e.onclick = function (e) {
      t && t(), i(e)
    }
  }

  function i(e) {
    var a = t.createElement("div");
    a.className = "heart", d.push({
      el: a,
      x: e.clientX - 5,
      y: e.clientY - 5,
      scale: 1,
      alpha: 1,
      color: s()
    }), t.body.appendChild(a)
  }

  function c(e) {
    var a = t.createElement("style");
    a.type = "text/css";
    try {
      a.appendChild(t.createTextNode(e))
    } catch (t) {
      a.styleSheet.cssText = e
    }
    t.getElementsByTagName("head")[0].appendChild(a)
  }

  function s() {
    return "rgb(" + ~~(255 * Math.random()) + "," + ~~(255 * Math.random()) + "," + ~~(255 * Math.random()) + ")"
  }

  var d = [];
  e.requestAnimationFrame = function () {
    return e.requestAnimationFrame || e.webkitRequestAnimationFrame || e.mozRequestAnimationFrame || e.oRequestAnimationFrame || e.msRequestAnimationFrame || function (e) {
      setTimeout(e, 1e3 / 60)
    }
  }(), n()
}(window, document);
```

接着在 \blog\themes\yilia\layout_partial\footer.ejs 的最后面加入如下代码：

```
<script type="text/javascript" src="/love.js"></script>
```

[](#添加文章目录 "添加文章目录")添加文章目录[](#添加文章目录)
-------------------------------------

为了方便查看每篇文章的目录结构，可以定位到想看的地方，特地找了下如何实现这个功能。

### [](#添加-CSS-样式 "添加 CSS 样式")添加 CSS 样式[](#添加-CSS-样式)

打开 `themes\yilia\source` 目录新建 `article_directory.css` 文件后面添加如下代码：

```
/* 文章目录样式 */
/*
#container .show-toc-btn, #container .toc-article1 {
  display: block;
}
*/

.toc-article1 {
  /*display: none;*/
  top: 15%;
  z-index: 100;
  background: rgba(255, 255, 255, .7);
  border: 1px solid #ccc;
  max-width: 0;
  min-width: 0;
  max-height: 0;
  overflow-y: auto;
  font-size: 14px;
  padding: 10px;
  border-right: none;
  position: fixed;
  right: 40px;
  margin-right: 0;
  opacity: 0;
  transition: all .3s ease;
  border-radius: 18px 0 0 18px;
  text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.2);
  -webkit-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  -moz-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  -ms-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  -o-box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, 0.16), 0 2px 10px 0 rgba(0, 0, 0, 0.12);
}

.show-toc-btn:hover + .toc-article1,
.toc-article1:hover {
  max-width: 500px;
  min-width: 150px;
  max-height: 500px;
  overflow-y: auto;
  opacity: 1;
}

@media screen and (max-width: 800px) {
  .toc-article1 {
    top: 22.6%;
    right: 0;
  }
}

.toc-article1 .toc-close {
  font-weight: 700;
  font-size: 20px;
  cursor: pointer;
  float: right;
  color: #ccc
}

.toc-article1 .toc-close {
  top: 130px;
  width: 25px;
  height: 150px;
  margin: -10px -10px auto;
}

.toc-article1 .toc-close:hover {
  color: #000
}

.toc-article1 .toc {
  font-size: 14px;
  padding: 0;
  line-height: 20px
}

.toc-article1 .toc .toc-number {
  color: #333
}

.toc-article .toc .toc-text:hover,
.toc-article1 .toc .toc-text:hover {
  /*text-decoration: underline;*/
  color: #2a6496
}

.toc-article1 li {
  list-style-type: none
}

.toc-article1 .toc-level-1 {
  margin: 4px 0
}

@-moz-keyframes cd-bounce-1 {
  0% {
    opacity: 0;
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
  60% {
    opacity: 1;
    -o-transform: scale(1.01);
    -webkit-transform: scale(1.01);
    -moz-transform: scale(1.01);
    -ms-transform: scale(1.01);
    transform: scale(1.01)
  }
  100% {
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
}

@-webkit-keyframes cd-bounce-1 {
  0% {
    opacity: 0;
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
  60% {
    opacity: 1;
    -o-transform: scale(1.01);
    -webkit-transform: scale(1.01);
    -moz-transform: scale(1.01);
    -ms-transform: scale(1.01);
    transform: scale(1.01)
  }
  100% {
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
}

@-o-keyframes cd-bounce-1 {
  0% {
    opacity: 0;
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
  60% {
    opacity: 1;
    -o-transform: scale(1.01);
    -webkit-transform: scale(1.01);
    -moz-transform: scale(1.01);
    -ms-transform: scale(1.01);
    transform: scale(1.01)
  }
  100% {
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
}

@keyframes cd-bounce-1 {
  0% {
    opacity: 0;
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
  60% {
    opacity: 1;
    -o-transform: scale(1.01);
    -webkit-transform: scale(1.01);
    -moz-transform: scale(1.01);
    -ms-transform: scale(1.01);
    transform: scale(1.01)
  }
  100% {
    -o-transform: scale(1);
    -webkit-transform: scale(1);
    -moz-transform: scale(1);
    -ms-transform: scale(1);
    transform: scale(1)
  }
}

.show-toc-btn {
  display: block;
  top: 15%;
  z-index: 10;
  width: 35px;
  height: 120px;
  min-height: 14px;
  overflow: hidden;
  padding: 10px;
  letter-spacing: 10px;
  border: 1px solid #ddd;
  border-right: none;
  position: fixed;
  right: 40px;
  text-align: center;
  background-color: #f9f9f9;
  border-radius: 18px 0 0 18px;
  transition: all .3s ease;
}

.show-toc-btn .btn-bg {
  margin-top: 2px;
  display: block;
  width: 16px;
  height: 14px;
  background: url(http://7xtawy.com1.z0.glb.clouddn.com/show.png) no-repeat;
  -webkit-background-size: 100%;
  -moz-background-size: 100%;
  background-size: 100%
}

.show-toc-btn .btn-text {
  color: #999;
  font-size: 12px
}

/*.show-toc-btn:hover .btn-bg {
  background-position: 0 -16px
}

.show-toc-btn:hover .btn-text {
  font-size: 14px;
  !*color: #ea8010;*!
  !*color: #0088CC;*!
  color: #FFFFFF;
  !* background: #39C7F7 *!
}

.show-toc-btn:hover {
  background: #39C7F7
}*/

.toc-article1 li ol, .toc-article1 li ul {
  margin-left: 23px;
}

.toc-article1 ol, .toc-article1 ul {
  margin: 5px 0;
}

/* 移动端文章导航 */
@media screen and (max-width: 800px) {
  .show-toc-btn {
    top: 150px;
    right: 0;
    width: 10px;
    padding: 0;
  }

  .show-toc-btn .btn-text {
    font-size: 9px;
  }

  /*.show-toc-btn:hover .btn-text {
    font-size: 9px;
  }*/

  .toc-article1 {
    top: 150px;
    right: -5px;
    border-radius: 18px 0 0 18px;
  }

  .toc-article1 .toc-close {
    top: 130px;
    width: 25px;
    height: 150px;
    margin: -10px -10px auto;
  }

  .toc-article1 .toc-close:hover {
    color: #000;
  }
}
```

### [](#修改-aside-ejs-文件 "修改 aside.ejs 文件")修改 aside.ejs 文件[](#修改-aside-ejs-文件)

打开 `themes\yilia\layout\_partial` 文件夹下的 `aside.ejs` 文件，在 `</aside>` 前一行加入如下内容（注意位置）

```
<!-- 目录内容 -->
<% if (!index && post.toc){ %>
  <p onmouseenter="showToc();" onmouseleave="showBtn();">
    <!-- <span></span> -->
    <span>文章目录</span>
  </p>
  <div onmouseleave="showBtn();" onmouseenter="showToc();">
    <!--<span title="隐藏导航">×</span>-->
    <strong>文章目录</strong>
    <%- toc(post.content) %>
  </div>
  <script type="text/javascript">
    function showToc(){
      var toc_article = document.getElementById("toc-article1")
      var show_toc_btn = document.getElementById("show-toc-btn")
      // toc_article.setAttribute("style","display:block")
      // show_toc_btn.setAttribute("style","display:none")
      show_toc_btn.style.opacity = "0"
      // toc_article.style.marginRight = "0"
    }
    function showBtn(){
      var toc_article = document.getElementById("toc-article1")
      var show_toc_btn = document.getElementById("show-toc-btn")
      // toc_article.setAttribute("style","display:none");
      // show_toc_btn.setAttribute("style","display:block");
      show_toc_btn.style.opacity = "1"
      // toc_article.style.marginRight = "-350px"
    }
  </script>
<% } %>
<!-- 目录内容结束 -->
```

然后若想要文章显示目录，在每篇文章开头加入：`toc: true` 即可

本目录与 hexo 自带的目录功能无关

[](#添加彩带 "添加彩带")添加彩带[](#添加彩带)
-----------------------------

### [](#彩带1-鼠标点击自动替换彩带 "彩带1.鼠标点击自动替换彩带")彩带 1. 鼠标点击自动替换彩带[](#彩带1-鼠标点击自动替换彩带)

新建 `\yilia\source\js\ribbon.js` 文件，添加以下代码：

```
/**
 * Copyright (c) 2016 hustcc
 * License: MIT
 * Version: v1.0.1
 * GitHub: https://github.com/hustcc/ribbon.js
**/
/*jshint -W030 */
! function() {
  function attr(node, attr, default_value) {
    return Number(node.getAttribute(attr)) || default_value;
  }

  // get user config
  var scripts = document.getElementsByTagName('script'),
    script = scripts[scripts.length - 1]; // 当前加载的script
  config = {
    z: attr(script, "zIndex", -1), // z-index
    a: attr(script, "alpha", 0.6), // alpha
    s: attr(script, "size", 90), // size
  };

  var canvas = document.createElement('canvas'),
    g2d = canvas.getContext('2d'),
    pr = window.devicePixelRatio || 1,
    width = window.innerWidth,
    height = window.innerHeight,
    f = config.s,
    q, t,
    m = Math,
    r = 0,
    pi = m.PI*2,
    cos = m.cos,
    random = m.random;
  canvas.width = width * pr;
  canvas.height = height * pr;
  g2d.scale(pr, pr);
  g2d.globalAlpha = config.a;
  canvas.style.cssText = 'opacity: ' + config.a + ';position:fixed;top:0;left:0;z-index: ' + config.z + ';width:100%;height:100%;pointer-events:none;';
  // create canvas
  document.getElementsByTagName('body')[0].appendChild(canvas);

  function redraw() {
    g2d.clearRect(0, 0, width, height);
    q = [{x: 0, y: height * 0.7 + f}, {x: 0, y: height * 0.7 - f}];
    while(q[1].x < width + f) draw(q[0], q[1]);
  }
  function draw(i, j) {
    g2d.beginPath();
    g2d.moveTo(i.x, i.y);
    g2d.lineTo(j.x, j.y);
    var k = j.x + (random()*2-0.25)*f, n = line(j.y);
    g2d.lineTo(k, n);
    g2d.closePath();
    r -= pi / -50;
    g2d.fillStyle = '#'+(cos(r)*127+128<<16 | cos(r+pi/3)*127+128<<8 | cos(r+pi/3*2)*127+128).toString(16);
    g2d.fill();
    q[0] = q[1];
    q[1] = {x: k, y: n};
  }
  function line(p){
    t = p + (random() * 2 - 1.1) * f;
    return (t > height || t < 0) ? line(p) : t;
  }

  document.onclick = redraw;
  document.ontouchstart = redraw;
  redraw();
}();
```

打开 `\yilia\layout\layout.ejs` 文件，在 `<%- partial('_partial/viewer') %>` 后添加以下代码：

```
<!-- 彩带1.点击自动替换彩带 -->
<% if (theme.ribbon){ %>
  <!-- <script src="https://g.joyinshare.com/hc/ribbon.min.js" type="text/javascript"></script> -->
  <script type="text/javascript" src="/js/ribbon.js"></script>
<% } %>
```

打开 `\yilia\_config.yml` 文件，添加以下代码：

```
# https://github.com/hustcc/ribbon.js
# 彩带1.点击自动替换彩带
ribbon: true
```

### [](#彩带2-自动飘动 "彩带2.自动飘动")彩带 2. 自动飘动[](#彩带2-自动飘动)

新建 `\yilia\source\js\ribbon_flow.js` 文件，添加以下代码：

```
(function (name, factory) {
  if (typeof window === "object") {
    window[name] = factory()
  }
})("Ribbons", function () {
  var _w = window,
    _b = document.body,
    _d = document.documentElement;
  var random = function () {
    if (arguments.length === 1) {
      if (Array.isArray(arguments[0])) {
        var index = Math.round(random(0, arguments[0].length - 1));
        return arguments[0][index]
      }
      return random(0, arguments[0])
    } else if (arguments.length === 2) {
      return Math.random() * (arguments[1] - arguments[0]) + arguments[0]
    }
    return 0
  };
  var screenInfo = function (e) {
    var width = Math.max(0, _w.innerWidth || _d.clientWidth || _b.clientWidth || 0),
      height = Math.max(0, _w.innerHeight || _d.clientHeight || _b.clientHeight || 0),
      scrollx = Math.max(0, _w.pageXOffset || _d.scrollLeft || _b.scrollLeft || 0) - (_d.clientLeft || 0),
      scrolly = Math.max(0, _w.pageYOffset || _d.scrollTop || _b.scrollTop || 0) - (_d.clientTop || 0);
    return {
      width: width,
      height: height,
      ratio: width / height,
      centerx: width / 2,
      centery: height / 2,
      scrollx: scrollx,
      scrolly: scrolly
    }
  };
  var mouseInfo = function (e) {
    var screen = screenInfo(e),
      mousex = e ? Math.max(0, e.pageX || e.clientX || 0) : 0,
      mousey = e ? Math.max(0, e.pageY || e.clientY || 0) : 0;
    return {
      mousex: mousex,
      mousey: mousey,
      centerx: mousex - screen.width / 2,
      centery: mousey - screen.height / 2
    }
  };
  var Point = function (x, y) {
    this.x = 0;
    this.y = 0;
    this.set(x, y)
  };
  Point.prototype = {
    constructor: Point,
    set: function (x, y) {
      this.x = x || 0;
      this.y = y || 0
    },
    copy: function (point) {
      this.x = point.x || 0;
      this.y = point.y || 0;
      return this
    },
    multiply: function (x, y) {
      this.x *= x || 1;
      this.y *= y || 1;
      return this
    },
    divide: function (x, y) {
      this.x /= x || 1;
      this.y /= y || 1;
      return this
    },
    add: function (x, y) {
      this.x += x || 0;
      this.y += y || 0;
      return this
    },
    subtract: function (x, y) {
      this.x -= x || 0;
      this.y -= y || 0;
      return this
    },
    clampX: function (min, max) {
      this.x = Math.max(min, Math.min(this.x, max));
      return this
    },
    clampY: function (min, max) {
      this.y = Math.max(min, Math.min(this.y, max));
      return this
    },
    flipX: function () {
      this.x *= -1;
      return this
    },
    flipY: function () {
      this.y *= -1;
      return this
    }
  };
  var Factory = function (options) {
    this._canvas = null;
    this._context = null;
    this._sto = null;
    this._width = 0;
    this._height = 0;
    this._scroll = 0;
    this._ribbons = [];
    this._options = {
      colorSaturation: "80%",
      colorBrightness: "60%",
      colorAlpha: 0.65,
      colorCycleSpeed: 6,
      verticalPosition: "center",
      horizontalSpeed: 150,
      ribbonCount: 5,
      strokeSize: 5,
      parallaxAmount: -0.5,
      animateSections: true
    };
    this._onDraw = this._onDraw.bind(this);
    this._onResize = this._onResize.bind(this);
    this._onScroll = this._onScroll.bind(this);
    this.setOptions(options);
    this.init()
  };
  Factory.prototype = {
    constructor: Factory,
    setOptions: function (options) {
      if (typeof options === "object") {
        for (var key in options) {
          if (options.hasOwnProperty(key)) {
            this._options[key] = options[key]
          }
        }
      }
    },
    init: function () {
      try {
        this._canvas = document.createElement("canvas");
        this._canvas.style["display"] = "block";
        this._canvas.style["position"] = "fixed";
        this._canvas.style["margin"] = "0";
        this._canvas.style["padding"] = "0";
        this._canvas.style["border"] = "0";
        this._canvas.style["outline"] = "0";
        this._canvas.style["left"] = "0";
        this._canvas.style["top"] = "0";
        this._canvas.style["width"] = "100%";
        this._canvas.style["height"] = "100%";
        this._canvas.style["z-index"] = "-1";
        this._onResize();
        this._context = this._canvas.getContext("2d");
        this._context.clearRect(0, 0, this._width, this._height);
        this._context.globalAlpha = this._options.colorAlpha;
        window.addEventListener("resize", this._onResize);
        window.addEventListener("scroll", this._onScroll);
        document.body.appendChild(this._canvas)
      } catch (e) {
        console.warn("Canvas Context Error: " + e.toString());
        return
      }
      this._onDraw()
    },
    addRibbon: function () {
      var dir = Math.round(random(1, 9)) > 5 ? "right" : "left",
        stop = 1000,
        hide = 200,
        min = 0 - hide,
        max = this._width + hide,
        movex = 0,
        movey = 0,
        startx = dir === "right" ? min : max,
        starty = Math.round(random(0, this._height));
      if (/^(top|min)$/i.test(this._options.verticalPosition)) {
        starty = 0 + hide
      } else if (/^(middle|center)$/i.test(this._options.verticalPosition)) {
        starty = this._height / 2
      } else if (/^(bottom|max)$/i.test(this._options.verticalPosition)) {
        starty = this._height - hide
      }
      var ribbon = [],
        point1 = new Point(startx, starty),
        point2 = new Point(startx, starty),
        point3 = null,
        color = Math.round(random(0, 360)),
        delay = 0;
      while (true) {
        if (stop <= 0) break;
        stop--;
        movex = Math.round((Math.random() * 1 - 0.2) * this._options.horizontalSpeed);
        movey = Math.round((Math.random() * 1 - 0.5) * (this._height * 0.25));
        point3 = new Point();
        point3.copy(point2);
        if (dir === "right") {
          point3.add(movex, movey);
          if (point2.x >= max) break
        } else if (dir === "left") {
          point3.subtract(movex, movey);
          if (point2.x <= min) break
        }
        ribbon.push({
          point1: new Point(point1.x, point1.y),
          point2: new Point(point2.x, point2.y),
          point3: point3,
          color: color,
          delay: delay,
          dir: dir,
          alpha: 0,
          phase: 0
        });
        point1.copy(point2);
        point2.copy(point3);
        delay += 4;
        color += this._options.colorCycleSpeed
      }
      this._ribbons.push(ribbon)
    },
    _drawRibbonSection: function (section) {
      if (section) {
        if (section.phase >= 1 && section.alpha <= 0) {
          return true
        }
        if (section.delay <= 0) {
          section.phase += 0.02;
          section.alpha = Math.sin(section.phase) * 1;
          section.alpha = section.alpha <= 0 ? 0 : section.alpha;
          section.alpha = section.alpha >= 1 ? 1 : section.alpha;
          if (this._options.animateSections) {
            var mod = Math.sin(1 + section.phase * Math.PI / 2) * 0.1;
            if (section.dir === "right") {
              section.point1.add(mod, 0);
              section.point2.add(mod, 0);
              section.point3.add(mod, 0)
            } else {
              section.point1.subtract(mod, 0);
              section.point2.subtract(mod, 0);
              section.point3.subtract(mod, 0)
            }
            section.point1.add(0, mod);
            section.point2.add(0, mod);
            section.point3.add(0, mod)
          }
        } else {
          section.delay -= 0.5
        }
        var s = this._options.colorSaturation,
          l = this._options.colorBrightness,
          c = "hsla(" + section.color + ", " + s + ", " + l + ", " + section.alpha + " )";
        this._context.save();
        if (this._options.parallaxAmount !== 0) {
          this._context.translate(0, this._scroll * this._options.parallaxAmount)
        }
        this._context.beginPath();
        this._context.moveTo(section.point1.x, section.point1.y);
        this._context.lineTo(section.point2.x, section.point2.y);
        this._context.lineTo(section.point3.x, section.point3.y);
        this._context.fillStyle = c;
        this._context.fill();
        if (this._options.strokeSize > 0) {
          this._context.lineWidth = this._options.strokeSize;
          this._context.strokeStyle = c;
          this._context.lineCap = "round";
          this._context.stroke()
        }
        this._context.restore()
      }
      return false
    },
    _onDraw: function () {
      for (var i = 0, t = this._ribbons.length; i < t; ++i) {
        if (!this._ribbons[i]) {
          this._ribbons.splice(i, 1)
        }
      }
      this._context.clearRect(0, 0, this._width, this._height);
      for (var a = 0; a < this._ribbons.length; ++a) {
        var ribbon = this._ribbons[a],
          numSections = ribbon.length,
          numDone = 0;
        for (var b = 0; b < numSections; ++b) {
          if (this._drawRibbonSection(ribbon[b])) {
            numDone++
          }
        }
        if (numDone >= numSections) {
          this._ribbons[a] = null
        }
      }
      if (this._ribbons.length < this._options.ribbonCount) {
        this.addRibbon()
      }
      requestAnimationFrame(this._onDraw)
    },
    _onResize: function (e) {
      var screen = screenInfo(e);
      this._width = screen.width;
      this._height = screen.height;
      if (this._canvas) {
        this._canvas.width = this._width;
        this._canvas.height = this._height;
        if (this._context) {
          this._context.globalAlpha = this._options.colorAlpha
        }
      }
    },
    _onScroll: function (e) {
      var screen = screenInfo(e);
      this._scroll = screen.scrolly
    }
  };
  return Factory
});
new Ribbons({
  colorSaturation: "60%",
  colorBrightness: "50%",
  colorAlpha: 0.5,
  colorCycleSpeed: 5,
  verticalPosition: "random",
  horizontalSpeed: 200,
  ribbonCount: 3,
  strokeSize: 0,
  parallaxAmount: -0.2,
  animateSections: true
});
```

打开 `\yilia\layout\layout.ejs` 文件，在 `<%- partial('_partial/viewer') %>` 后添加以下代码：

```
<!-- 彩带2.自动飘动 -->
<% if (theme.ribbon_flow){ %>
  <!-- <script src="https://g.joyinshare.com/hc/piao.js" type="text/javascript"></script> -->
  <script type="text/javascript" src="/js/ribbon_flow.js"></script>
<% } %>
```

打开 `\yilia\_config.yml` 文件，添加以下代码：

```
# 彩带2.自动飘动
ribbon_flow: true
```

### [](#增加彩带可见度 "增加彩带可见度")增加彩带可见度[](#增加彩带可见度)

```
/* 全局背景半透明，提高彩带可见区域 */
/*#container {
  background: rgba(234, 234, 234, .5);
}*/
/* 文章外部背景关闭 */
.mid-col {
  background: none;
}
/* 内容背景半透明，提高彩带可见区域 */
.left-col,
.article {
  background: rgba(255, 255, 255, .5);
}
```

[](#Firefox滚动条优化 "Firefox滚动条优化")Firefox 滚动条优化[](#Firefox滚动条优化)
--------------------------------------------------------------

打开 `customize_main.0cf68a.css` 文件添加自定义的样式代码：

```
/* Firefox滚动条优化 */
*, id, class {
  scrollbar-width: thin;
  scrollbar-color: #999 #eee;
}
```