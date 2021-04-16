\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[blog.yuanpei.me\](https://blog.yuanpei.me/posts/1417719502/)

最近给博客做了升级，从 3.x 升级到了 4.x，主要是在官网看到了关于静态页面生成效率提升的内容。众所周知，Hexo 在文章数目增加以后会越来越慢。博主大概是从 14 年年底开始使用 Hexo 这个静态博客的，截止到目前一共有 176 篇博客，其中的 “慢” 可想而知，中间甚至动过使用 Hugo 和 VuePress 的念头，所以，听说有性能方面的提升，还是决定第一时间来试试。整个升级过程挺顺利的，唯一遇到的问题是关于外部链接检测方面的，具体可以参考[这里](https://github.com/hexojs/hexo/issues/4107)。今天，博主主要想和大家分享下关于如何使用 [jsDelivr](http://www.jsdelivr.com/) 来为博客提供免费、高效的 CDN 服务，希望对大家有所帮助。

[jsDelivr](http://www.jsdelivr.com/) 是一个免费、快速和可信赖的 CDN 加速服务，官网上声称它每个月可以支撑 680 亿次的请求。博主是在去年年底的时候，偶然了解到这个服务的存在，这次趁着疫情肆虐的间隙，终于把这个服务集成到了博客中。更重要的是，这个服务在 Github 上是[开源](https://github.com/jsdelivr/jsdelivr)的。目前，它提供了针对 [npm](https://www.npmjs.com/)、[Github](https://github.com/) 和 [WordPress](https://cn.wordpress.org/) 的加速服务，只需要一行代码就可以获得加速效果，以常用的 jQuery 和 Bootstrap 为例：

```
https:


https:
```

这意味着我们只需要发布一个 npm 的包，就可以使用它提供的加速服务。CDN 加速的好处我这里就不再多说了，只要我们的项目中用到了第三方的静态资源，譬如 JavaScript/CSS 等等都应该考虑接入到 CDN 中。有人常常担心 CDN 挂掉或者是私有化部署无法接入外网环境。我想说，我们目光应该长远一点，现在早已不是早年那种单打独斗式的开发模式了，我们不可能把所有资源都放到本地来。随着云计算的概念越发地深入人心，越来越多的基础服务都运行在一台又一台虚拟化的 “云服务器” 上，这种情况下，搞这种集中化配置的做法，是完全违背分布式的发展趋势的。

如果说，针对 npm 包的 CDN 加速服务离我们还有点遥远，因为我们大多数情况下都是在使用别人写好的库。那么，接下来，针对 Github 的 CDN 加速服务应该会让我们无比兴奋吧，毕竟 Github Pages 的 “慢” 大家是可以感受得到的。不然，为什么大家要用 Coding Pages 做国内 / 国外的双线部署呢？首先，我们在浏览器里输入下面这个地址：[https://cdn.jsdelivr.net/gh/qinyuanpei/qinyuanpei.github.io@latest/](https://cdn.jsdelivr.net/gh/qinyuanpei/qinyuanpei.github.io@latest/)

![](https://i.loli.net/2020/02/05/HtmhUdsSRLW4Q9A.png)

jsDelivr 提供的 CDN 加速资源

此时，可以注意到，[jsDelivr](http://www.jsdelivr.com/) 可以把我们 Github 上的资源呈现出来，只要我们在 Github 上发布过相应的版本即可。这里的版本，可以理解为一次 Release，对应 Git 中 tag 的概念，虽然 Github 现在引入了包管理器的概念，试图统一像 npm、nuget、pip 等等这样的包管理器。它提供的 CDN 服务有一个基本的格式：

> [https://cdn.jsdelivr.net/gh/user/repo@version/file](https://cdn.jsdelivr.net/gh/user/repo@version/file)

如果大家感兴趣，可以把这里的 user 和 repo 改成自己的来体验一番。需要注意的是，这里的版本号同样可以换成 Commit ID 或者是分支的名称。我个人建议用 tag，因为它通常携带了版本号信息，语义上要更好一点。那么，顺着这个思路，我们只要把 Hexo 中的资源的相对路径改为 jsDelivr 的 CDN 加速路径就好啦！为了让切换更加自如，这里我们为 Hexo 写一个 Helper，它可以理解为 Hexo 中的辅助代码片段。我们在`<YouTheme>/scripts/`目录下新建一个`plugins.js`文件，这样 Hexo 会在渲染时自动加载这个脚本文件：

```
const source = (path, cache, ext) => {
    if (cache) {
        const minFile = \`${path}${ext === '.js' ? '.min' : ''}${ext}\`;
        const jsdelivrCDN = hexo.config.jsdelivr;
        return jsdelivrCDN.enable ? \`//${jsdelivrCDN.baseUrl}/gh/${jsdelivrCDN.gh\_user}/${jsdelivrCDN.gh\_repo}@latest/${minFile}\` : \`${minFile}?v=${version}\`
    } else {
        return path + ext
    }
}
hexo.extend.helper.register('theme\_js', (path, cache) => source(path, cache, '.js'))
hexo.extend.helper.register('theme\_css', (path, cache) => source(path, cache, '.css'))
```

接下来，修改布局文件，项目中的 JavaScript 和 CSS 文件，均通过`theme_js()`和`thems_css()`两个函数引入：

```
//加载JavaScript
<script src="<%- url\_for(theme\_js('assets/scripts/search', cache)) %>" async></script>
//加载CSS
<link rel="stylesheet" href="<%- url\_for(theme\_css('/assets/styles/style', cache)) %>">
```

既然是否使用 CDN 加速是可配置的，我们要在\_config.yml 文件中添加相应的配置项：

```
jsdelivr:
  enable: true
  gh\_user: qinyuanpei
  gh\_repo: qinyuanpei.github.io
  baseUrl: cdn.jsdelivr.net
```

除此以外，我们还需要在部署博客的时候，生成一个名为 latest 的 tag。虽然官网上说，在引用 CDN 的时候版本号可以省略，不过经过博主反复尝试，不带版本号并不会指向正确的版本，有些资源文件会报 404，因为这部分资源文件回滚以后发现还是没有。所以，最后博主只好把这个版本号给固定下来了，这样又引入一个新问题，即：每次部署的时候都要先删除远程的 latest。所以，这块儿的 [Travis CI 脚本](https://raw.githubusercontent.com/qinyuanpei/qinyuanpei.github.io/blog/.travis.yml)看起来会有点讨厌，如果大家有更好的方案，欢迎大家在博客中留言：

```
git tag latest
git push --force --quiet "https://${CI\_TOKEN}@${GH\_REF}" master:master --tags
```

好了，现在重新生成、部署，来看看效果吧：

![](https://i.loli.net/2020/02/05/FZJi9esXWQzxLYf.png)

Coding Pages 速度

![](https://i.loli.net/2020/02/05/E3WYBRQk4DJCZr5.png)

Github Pages 速度

感觉效果还不错，Github Pages 比平时要快很多，博主顺便就给 Coding Pages 启用了 CDN 加速。话说，看到这张图的时候总是感慨，如果肺炎疫情地图能像这两张图一样就好啦！面对这场无声的战役，有很多人一直在一线抗击病魔，还有很多人默默无闻地在支援武汉。或许，宅在家里的你我，什么都做不了，可即便如此，还是让我们一起来祈祷疫情快点结束吧，因为春天都要来了呢…… 好了，这就是这篇博客的全部内容啦，谢谢大家！

在此之前，博主提到版本号的问题，即每一次在 CDN 上生成的版本，怎样体现到 Hexo 中引用的资源上面。当时采用了一个取巧的方法，Hexo 中固定版本号为 latest，然后每次都推送这个 tag。这样引发一个问题，每次都先去远程删除这个 tag，显然这不是我期望的解决方案。最终，我采用的方案是，通过 Travis CI 编译部署的时候，首先导出变量`$TRAVIS_BUILD_NUMBER`到一个文本文件中，然后 Hexo 在生成静态页面的时侯，从这个文本文件中读取该变量的值作为版本号，这样每次编译部署的时候，我们总能获得一个新的 tag，而这个 tag 和 Hexo 中引用的资源版本一致，这样就彻底解决了这个遗留问题。修改后的`plugins.js`文件内容如下：

```
var fs = require('fs');
var version = 'latest'
fs.readFile('./BUILD\_NUMBER.txt', function (error, data) {
    if (error) {
      console.log('load BUILD\_NUMBER.txt fails, ' + error)
    } else {
        version = data.toString().trim();
    }
});

const source = (path, cache, ext) => {
    if (cache) {
        const minFile = \`${path}${ext === '.js' ? '.min' : ''}${ext}\`;
        const jsdelivrCDN = hexo.config.jsdelivr;
        return jsdelivrCDN.enable ? \`//${jsdelivrCDN.baseUrl}/gh/${jsdelivrCDN.gh\_user}/${jsdelivrCDN.gh\_repo}@${version}/${minFile}\` : \`${minFile}?v=${version}\`
    } else {
        return path + ext
    }
}
hexo.extend.helper.register('theme\_js', (path, cache) => source(path, cache, '.js'))
hexo.extend.helper.register('theme\_css', (path, cache) => source(path, cache, '.css'))
```

修改后的`.travis.yml`文件可以在[这里](https://raw.githubusercontent.com/qinyuanpei/qinyuanpei.github.io/blog/.travis.yml)获取。