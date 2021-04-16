> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [geniucker.now.sh](https://geniucker.now.sh/2020/04/25/Hexo-NexT%E4%B8%BB%E9%A2%98%E8%87%AA%E5%AE%9A%E4%B9%89%E5%8F%8B%E9%93%BE%E9%A1%B5%E9%9D%A2/)

Next 主题可增加友链，在主题配置文件`_config.yml`中`links`下添加，展示效果（图片来自[北宸的小站](https://links.jianshu.com/go?to=https://www.liaofuzhan.com)）：  
![](https://cdn.jsdelivr.net/gh/geniucker/source/image/20200425-1-1.jpg)  
当链接变多以后，页面的排版很不美观，这时候就需要给友链新增一个单独的页面了。网上其他的方法大部分都涉及到对模板的改动, 会给日后的主题升级带来麻烦。本文的方法不涉及对模板的改动，但原理与网上的方法类似。**本方法适用于 NexT6.0.2 及以上（由于涉及到 styles.styl 等 Hexo 数据目录的操作）**

[](#新增links页面 "新增links页面")新增 links 页面
-------------------------------------

在博客目录下的控制台执行：

```
hexo new page links
```

在创建的`source\links\index.md`中添加如下内容（不删除原有内容，在最后添加）：

```
<div>
<div>
<div>
{% for link in site.data.links %}
<div>
  <a href="{{ link.site }}" target="_blank">
  <img src="{{ link.avatar }}"/></a>
  <div>
  <div><a href="{{ link.site }}" target="_blank">{{ link.name }}</a>
  <a href="{{ link.site }}"><span><i aria-hidden="true"></i> 关注</span></a></div>
  <div title="{{ link.info }}">{{ link.info }}</div>
  </div>
</div>
{% endfor %}
</div>
</div>
</div>
```

[](#修改-styles-styl-文件 "修改 styles.styl 文件")修改 styles.styl 文件
-----------------------------------------------------------

用文本编辑器打开`source\_data\styles.styl`文件（无则创建），在末尾添加如下内容（不删除原有内容）：

```
#links{
	margin-top: 5rem;
	.links-content{
		margin-top:1rem;
	}
	.link-navigation::after {
		content: " ";
		display: block;
		clear: both;
	}
	.card {
		width: 300px;
		font-size: 1.1em;
		padding: 10px 20px;
		border-radius: 4px;
		transition-duration: 0.15s;
		margin-bottom: 1rem;
		display:flex;
	}
	.card:nth-child(odd) {
		float: left;
	}
	.card:nth-child(even) {
		float: right;
		+mobile() {
			float: left;
		}
	}
	.card:hover {
		transform: scale(1.1);
		box-shadow: 0 2px 6px 0 rgba(0, 0, 0, 0.12), 0 0 6px 0 rgba(0, 0, 0, 0.04);
		background: rgba(68, 68, 68, 0.12)
	}
	.card a {
		border:none;
	}
	.card .ava {
		width: 3rem!important;
		height: 3rem!important;
		margin:0!important;
		margin-right: 1em!important;
		border-radius:50%
		transition: transform 1s ease-out;
	}
	.ava:hover {
			transform: rotateZ(360deg);
		}
	.card .card-header {
		font-style: italic;
		overflow: hidden;
		width: 236px;
	}
	.card .card-header a {
		font-style: normal;
		color: #2bbc8a;
		font-weight: bold;
		text-decoration: none;
	}
	.card .card-header a:hover {
		color: #d480aa;
		text-decoration: none;
	}
	.card .card-header .info {
		font-style:normal;
		color:#a3a3a3;
		font-size:14px;
		min-width: 0;
		text-overflow: ellipsis;
		overflow: hidden;
		white-space: nowrap;
	}
	span.focus-links{
		vertical-align:1px;
		font-style:normal;
		margin-left:10px;
		position:unset;
		left:0;
		padding:0 7px 0 5px;
		font-size:11px;
		border-color:#42c02e;
		border-radius:40px;
		line-height:24px;
		height:24px;
		color:#fff!important;
		background-color:#2bbc8a;
		display:inline-block
		}
	span.focus-links:hover{background-color:#318024}
}
```

在主题配置文件`_config.yml`的`custom_file_path`下取消`style: source/_data/styles.styl`的注释

[](#新建-links-yml-并配置友链 "新建 links.yml 并配置友链")新建 links.yml 并配置友链
--------------------------------------------------------------

在`source\_data`下新建 links.yml 文件并用文本编辑器打开，添加如下内容：

```
- name: Geniucker 
  avatar: https://cdn.jsdelivr.net/gh/geniucker/source/avatar.jpg 
  site: https://geniucker.js.org 
  info: 崇尚技术 
- name: cyc's blog
  avatar: https://q1.qlogo.cn/g?b=qq&nk=2516803593&s=640
  site: https://cyc2004.baklib.com
  info: 暂无介绍~
```

这里添加了两条友链，若添加多条方法类似

在主题配置文件`_config.yml`中`menu`下添加：

```
友情链接: /links/ || link
```

NexT7.8.0 以后为：

```
友情链接: /links/ || fa fa-link
```

在主页的菜单即可看到友情链接

![](https://cdn.jsdelivr.net/gh/geniucker/source/image/20200425-1-2.jpg)  
我的[友情链接页面](https://geniucker.now.sh/links/)