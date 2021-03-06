> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [segmentfault.com](https://segmentfault.com/a/1190000017044563)

引言
--

页面滚动条造成宽度减小的场景很常见了，由于`div`块级元素的流动性，其宽度默认为 100% 的`body`宽度，但是当容器的高度超过视口宽度时候，页面就会出现滚动条，这个滚动条的宽度就会挤压`body`的可用宽度，也就是会挤压我们的容器的宽度，造成页面晃动的现象，很不友好，下面就来探讨下如何解决这个滚动条的问题。

滚动条的宽度是多少？
----------

既然要解决滚动条造成的问题那么首先需要了解滚动条，即`scrollbar`的信息主要就是他的宽度，我们把页面的`overflow`置为`scroll`，那么滚动条就会默认占据了空间，下面代码就可以很容易得到其宽度了：

CSS: 先把 body 的间距置为 0

```
* {
  margin: 0;
  padding: 0;
}
html {
  overflow-y: scroll;
}



```

JS: 用视口的`innerWidth`减去`body`就是滚动条的宽度

```
console.log('chrome下滚动条的宽度', window.innerWidth - document.body.clientWidth)

```

可以得出 chrome 浏览器下，宽度为 17px，我在`jsfiddle`中写的话打印出来是 16px，我没有在所有浏览器都去验证，但是各浏览器的值可能略有不同，但都是一个固定的值。以 chrome 来说，就是在触发页面滚动条时候，会挤压掉 17px 的空间，那我们就可以从不同角度考虑去解决了。

如何解决？
-----

### 一、最原始的 scroll 方法

首先来讲下最原始的方法，其思想是既然在触发滚动条时候会挤压空间，那么直接在没有滚动条的时候也触发不就可以了么，也就是我们上面算宽度时候的设置：

```
html {
  overflow-y: scroll;
}

```

这样不论什么时候都有滚动宽度占据空间，不存在挤压的问题了... 但是这样做有点蠢，毕竟在不需要滚动条的时候也有那么个丑丑的条子放在右边。但是他的优点在于方便而且没有兼容性的问题，其实很多大网站有时候也就这样用了。。。

### 二、新属性 overlay 方法

chrome 下`overflow`有个新的属性值`overlay`，这个属性简直就是为了这个问题而生，他和`auto`有点像，但是区别就是在触发滚动条时候并不挤压空间，说得直白点就像是移动端的悬浮滚动条，唯一的区别就是不会像手机上那样自动出现自动消失了，滚动条会遮盖住容器 17px 的空间。眼见为实用下面代码看一下就知道。  
高度还未触发滚动条时候：

```
* {
  margin: 0;
  padding: 0;
}
html {
  overflow-y: overlay;
}
.container {
  height: 200px;
  padding: 17px;
  background-color: #00b83f;
  text-align: right;
}


<div class="container">
  <h1>我是容器内容</h1>
</div>

```

效果图如下：  
![](https://segmentfault.com/img/bVbjGbB?w=1657&h=295)

然后修改容器高度，触发滚动条：

```
.container {
  height: 2000px;
  padding: 17px;
  background-color: #00b83f;
  text-align: right;
}

```

效果图如下：  
![](https://segmentfault.com/img/bVbjGbP?w=1656&h=367)

可以看到虽然出现了滚动条但是并未挤压容器的宽度，而是遮住了 17px 的空间，其实本质上就相当于实现了移动端的滚动条表现。  
但是非常遗憾，这个属性值目前只有 chrome 支持，要是 ff/ie 都支持，后面也就不用写了，但是据说以后都会加上去支持的，可以说是非常好用了，后面的方法也只是用其他方法实现这个效果而已。

### 三、利用 vw 和 calc 实现

因为 100vw 是`window`的宽度，其实就是`window.innerWidth`, 而容器的宽度 100% 就是除了滚动条的可用宽度，因此在没有滚动条时候`calc(100% - 100vw)`就是 0，触发滚动条时候其值为负的滚动条宽度，我们将其赋值给容器的`margin-right`，即可巧妙补偿这个宽度的挤压，在滚动条存在的情况下容器宽度仍然占据整个视口的宽度。

```
* {
  margin: 0;
  padding: 0;
}
html {
  overflow-y: auto;
  overflow-x: hidden;
}
.container {
  height: 2000px;
  margin-right: calc(100% - 100vw);
  padding: 17px;
  background-color: #00b83f;
  text-align: right;
}

```

效果如同方法二，很完美，并且兼容性还不错，起码高版本的 ie 和 ff 都没问题了。

### 四、张鑫旭大佬那里抄来的 absolute 方法

[链接在此](https://www.zhangxinxu.com/wordpress/2015/01/css-page-scrollbar-toggle-center-no-jumping/)，这个利用了绝对定位，保证了 body 的宽度一直保持完整空间。

```
html {
  overflow-y: scroll; //这是为了兼容ie8，不支持:root, vw
}

:root {
  overflow-y: auto;
  overflow-x: hidden;
}

:root body {
  position: absolute;
}

body {
  width: 100vw;
  overflow: hidden;
}

```

在一个普通的容器滚动条挤压怎么办？
-----------------

上面是针对浏览器视口的滚动条方案，但是假如在一个普通`div`容器中也有如此的需求改怎么办呢？因此此时并没有像 100vw 这样的值直接获取容器的宽度，只能使用 js 的方法来检测计算然后再用`margin-right`做补偿，原理都是一样的，但是我强烈不推荐也不喜欢用 js 来计算布局... 因此在这种情况下勉强委屈下用上面的第一种方法了，如果是 chrome 下用第二种方法。

```
.wrap {
    overflow-y: scroll;
    overflow-y: overlay;
}

```

当然你坚决不能忍的话也可以用 js 去算吧... 本质也是一样的，这里给个链接作为[参考](https://stackoverflow.com/questions/18548465/prevent-scroll-bar-from-adding-up-to-the-width-of-page-on-chrome)。

总结
--

方法主要就是上面的几种，大家根据需求自由选用即可，最重要的是在使用某些新属性的时候多加思考，很多问题的本质并没什么区别，只是用新的工具去做而已。

参考
--

都在文中了