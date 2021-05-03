> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.wqh4u.cn](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/)

> 从不浪费时间的人，没有工夫抱怨时间不够。
> 
> 又在踩了无数次坑后，将我的小看板娘配置好了，在这里我会详细的介绍如何配置 Live 2D 看板娘 与我踩过的那些坑。  
> 那么，现在开始配置属于你自己的 Live 2D 看板娘 吧！（多图警告！）

[](#普通版本 "普通版本")普通版本
--------------------

之前在我的 [这篇博客](https://www.wqh4u.cn/2019/07/31/Hexo%E5%8D%9A%E5%AE%A2%E7%9A%84%E5%AE%89%E8%A3%85%E4%B8%8E%E5%9F%BA%E6%9C%AC%E9%85%8D%E7%BD%AE/#live2d) 中有提到使用 [这个项目](https://github.com/EYHN/hexo-helper-live2d) 来制作个性化的看板娘，其中一个样式如下：

![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/shizuku.gif)

可爱的 SHIZUKU

切换至 `Hexo` 根目录下，在终端中输入以下代码：

```
$ npm install -save hexo-helper-live2d
```

编辑 站点配置文件：（具体配置见 [官方文档](https://github.com/EYHN/hexo-helper-live2d)）

```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  model:
    use: live2d-widget-model-wanko
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```

你可以在 [这里](https://github.com/xiazeyu/live2d-widget-models) 找到非常多的 MODEL：

我尝试配置了一些 MODELS 并且做了截图，各位大佬们不用一个个的去试了：

| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/chitose.jpg)

* * *

ChiToSe

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/Epsilon2.1.png)

* * *

Epsilon2.1

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/Gantzert_Felixander.png)

* * *

Gantzert_Felixander

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/haru.png)

* * *

HaRu

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/haruto.png)

* * *

HaRuTo

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/hibiki.png)

* * *

HiBiKi

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/hijiki.png)

* * *

HiJiKi

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/izumi.jpg)

* * *

IZuMi

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/koharu.png)

* * *

KoHaRu

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/miku.png)

* * *

MiKu

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/nico.png)

* * *

NiCo

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/nietzche.png)

* * *

Nietzche

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/ni-j.png)

* * *

NI-J

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/nipsilon.png)

* * *

Nipsilon

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/nito.png)

* * *

Nito

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/shizuku.png)

* * *

ShiZuKu

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/tororo.png)

* * *

ToRoRo

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/tsumiki.png)

* * *

TsuMiKi

 |
| ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/Unitychan.png)

* * *

Unitychan

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/wanko.png)

* * *

wanko

 | ![](https://www.wqh4u.cn/2019/09/04/%E8%AE%BE%E7%BD%AE%E4%BD%A0%E5%96%9C%E6%AC%A2%E7%9A%84live2d%E7%9C%8B%E6%9D%BF%E5%A8%98/z16.png)

* * *

Z16

 |

~（是不是还是感觉 ShiZuKu 还是最好看呢 2333…）~

[](#进阶版本 "进阶版本")进阶版本
--------------------

> 什么？你想要一个 能说话、能互动、能玩游戏、能换装的看板娘？~呵~~

感谢 [张书樵大神](https://zhangshuqiao.org/) 的 [Live2D 项目](https://github.com/stevenjoezhang/live2d-widget)，让你可以实现你的愿望。

首先，`clone` 项目到你的本地（或你的 `Hexo` 根目录下）：

```
git clone https://github.com/stevenjoezhang/live2d-widget
```

> 如果你是在你的 `Hexo` 下配置的，请将项目文件解压至 `你的Hexo根目录/source/live2d-widget/` 下（没有 `live2d-widget` 请手动创建）

如果你想自定义你的看板娘 初始加载模型 或者 互动话语 的话，首先修改 live2d-widget 目录下的 autoload.js 文件，将：

```
const live2d_path = "https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget/";
```

改为：

```
const live2d_path = "/live2d-widget/";
```

随后，在 `你的Hexo根目录/themes/next/layout/_layout.swing` 中，`</body>` 之前，增加以下内容：

```
<script src="/live2d-widget/autoload.js"></script>
```

在 `</head>` 之前，增加以下内容：

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/font-awesome/css/font-awesome.min.css">
```

在你的 主题配置文件 中，新增以下内容：

```
live2d:
  enable: true
```

> 如果你已经使用了 `普通版本` 的 `Live 2D`，请将其他无关属性注释掉！

如果你想自定义看板娘大小、位置或者其他样式，请修改 waifu.css

如果你想自定义看板娘言语互动，请修改 waifu-tips.js 和 waifu-tips.json

[](#高级版本中我所踩的那些坑 "高级版本中我所踩的那些坑")高级版本中我所踩的那些坑
--------------------------------------------

### [](#jQuery加载失败 "jQuery加载失败")jQuery 加载失败

时刻注意着你的 `Console`，如果出现了找不到符号 `$`，因为首先加载的 autoload.js，里面第一个干的事情就是通过 `Ajax` 去请求 live2d.min.js 与 waifu-tips.js，所以要保证你已经导入了 `jQuery` 库，如果没有的话请在 `你的Hexo根目录/themes/next/layout/_layout.swing` 中，`</head>` 标签前，手动导入 `jQuery`。

### [](#loadlive2d方法未定义 "loadlive2d方法未定义")loadlive2d 方法未定义

在你的 autoload.js 文件中，将加载 live2d.min.js 那一段的 `URL` 请求改为：

```
url: "https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget/live2d.min.js",
```

### [](#CROS跨域请求失败 "CROS跨域请求失败")CROS 跨域请求失败

因为 ~人尽皆知~ 的原因，在 waifu-tips.js 中第 `162` 行向目标发起了一个 `getJSON` 请求你的目标文件 waifu-tips.json，这里会出现问题，需要你去设置跨域请求头。

我是用的 `Nginx` 来部署博客的，所以就用 `Nginx` 举例：

在你的 `Nginx` 网站配置文件中，在你的服务里面，添加如下代码：

```
add_header 'Access-Control-Allow-Origin' '*';
add_header 'Access-Control-Allow-Credentials' 'true';
add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS';
```

然后重启你的 `Nginx` 服务即可解决。

### [](#奇奇怪怪的问题 "奇奇怪怪的问题")奇奇怪怪的问题

使用 `hexo g` 后，在你的 `/public/` 文件夹中会生成一个 `/live2d-widget/` 文件，其中 waifu-tips.js 会有一些莫名其妙的问题，你需要将你的 `Hexo/source/live2d-widget/waifu-tips.js` 复制粘贴覆盖掉 `public` 目录下那个有问题的文件中的内容。同理，waifu-tips.json 也会有一些奇奇怪怪的问题，也需要你手动的去覆盖一次。

P.S. 觉得麻烦的可以写一个 `bash` 脚本，代码大致如下：

```
#!/bin/bash
hexo clean
hexo g
rm ./public/live2d-widget/waifu-tips.js
rm ./public/live2d-widget/waifu-tips.json
cp ./source/live2d-widget/waifu-tips.js ./public/live2d-widget/
cp ./source/live2d-widget/waifu-tips.json ./public/live2d-widget/
echo OK
```

然后就可以一键生成辽~