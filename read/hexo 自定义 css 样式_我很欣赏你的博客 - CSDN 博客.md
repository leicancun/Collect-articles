> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_43827114/article/details/104373665)

### 文章目录

*   *   [自定义 CSS 部分](#CSS_19)
    *   [彩色标签](#_446)
    *   [心形转动分类](#_491)
    *   [底栏修改](#_653)
    *   [配置文件解释](#_778)
    *   *   [站点配置文件](#_784)
        *   [主题配置文件](#_924)

个人博客

[https://www.renke666.top](https://www.renke666.top)

尽管在配置文件中做了修改美化了博客，但原有样式还是比较简陋，修改的话就需要自定义 CSS 样式。这也算是美化博客的一大步进展吧，踩了很多坑。

这篇算是博客的美化部分暂时完结之作，花了很多的精力去美化，整体从十二月初断断续续的忙，寒假初期忙了会也算是忙了有两个月吧。果然写博客不是关键，捣鼓才是关键，中间还是学到挺多也挺值得的。然而慢慢捣鼓发现还有很多很多新鲜神奇的东西，目前也没有太多时间，暂且放一边。以后就专心写点东西放上来了，在电脑上写有时东西一多一乱就不好找，这下也算有个地方可以聚合一下。

首先需要 HTML+CSS+JS 基础，在修改样式时参考了很多博客好的样式，也学到了很多，中间踩了很多坑，基础很关键。回顾前面的美化过程其实走了很多弯路，最好是在有基础的情况下，然后把配置文件详细搞清楚，再大概了解`\themes\next\layout`部分的`.swig`文件的具体格式和用法就能完成的很快，且可以较轻松的自定义各布局。

新版本的 hexo 自定义 CSS 需要在`\themes\next\source\css\main.styl`中`// Custom Layer`之后也就是最后增加自己自定义的 CSS

写 HTML 和 CSS 用`IntelliJ IDEA`很好，还可以写 java，学生免费。

> swig 介绍 https://www.jianshu.com/p/c5d333e6353c

自定义 CSS 部分
----------

> 参考 https://www.cnblogs.com/LyShark/p/11834144.html，感谢这篇使我入门

```
/*
***
  全局部分美化
**
*/
body {
//  background:url(https://source.unsplash.com/random/1600x900);
//    background:url(/images/background4.jpg);
//    background:url(https://blog.maplesugar.space/uploads/body-bg-3.jpg);
    background-repeat: no-repeat;
    background-attachment:fixed;
    background-position:50% 50%;
    background-color: white;
    //background:#FFFFFF;                    // 添加背景颜色
}

// 菜单栏
.header-inner {
  // box-shadow: 1px 1px 8px 2px rgba(179,22,132,0.15);
  // border: solid #a166ab 2px;// 菜单栏
  border-radius: 15px;    // 圆角边框
  box-shadow: 0 1px 2px 0px rgba(0,0,0,0.1),
    0 2px 4px 0px rgba(0,0,0,0.1);
  margin-top: 10px;    // 露出全部
  width: 270px !important;    // 自定义头像栏的宽度
  background: rgba(255,255,255,0.9);    // 增加透明度                                                                                                                                         // 增加透明度
}
.header-inner:hover{
  // box-shadow:1px 1px 8px 4px rgba(185,43,232,0.4);
  transition-property: all;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  box-shadow:0 2px 4px 0px rgba(0,0,0,0.1),
    0 4px 8px 0px rgba(0,0,0,0.1),
    0 8px 16px 0px rgba(0,0,0,0.1),
    0 16px 32px 0px rgba(0,0,0,0.1) !important;
}

// 头像栏
.sidebar-inner {
  // border: solid wheat 2px
  // box-shadow: 0 0 20px antiquewhite;
  border-radius: 15px;
  position: absolute;
  overflow: hidden;
  width: 270px;    // 自定义侧边栏的宽度
  box-shadow: 0 1px 2px 0px rgba(0,0,0,0.1),
    0 2px 4px 0px rgba(0,0,0,0.1);
  background: rgba(255,255,255,0.9);                                                                                                                                         // 增加透明度
}
.sidebar-inner:hover{
  // box-shadow: 1px 1px 8px 5px rgba(232,167,78,0.5);
  color: antiquewhite
  transition-property: all;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  box-shadow:0 2px 4px 0px rgba(0,0,0,0.1),
    0 4px 8px 0px rgba(0,0,0,0.1),
    0 8px 16px 0px rgba(0,0,0,0.1),
    0 16px 32px 0px rgba(0,0,0,0.1) !important;
}

// 主文章页面
.post-block {                                                                                                                                                                                  // 主文章页面
  border-radius: 15px !important;
  box-shadow: 0 1px 2px 0px rgba(0,0,0,0.1), 0 2px 4px 0px rgba(0,0,0,0.1)     // 覆盖
  margin-top: 10px;    // 露出全部
  margin-bottom: 20px;
  // border: solid rgba(180,255,0,0.6) 2px;
  padding: 30px 20px 20px 30px;    // 上右下左
  background: rgba(255,255,255,0.9);    // 增加透明度
}
.post-block:hover{
  transition-property: all;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  box-shadow:0 2px 4px 0px rgba(0,0,0,0.1),
    0 4px 8px 0px rgba(0,0,0,0.1),
    0 8px 16px 0px rgba(0,0,0,0.1),
    0 16px 32px 0px rgba(0,0,0,0.1) !important;

}
.post-block.home:hover{
  transform: scale(1.02);
}

// 后面的文章
#posts > article + article .post-block {                                                                                                                                           // 后面的文章
  border-radius: 15px;
  box-shadow: 1px 2px 8px 4px rgba(0,0,0,0.15);
  background: rgba(255,255,255,0.9);                                                                                                                                         // 增加透明度
}


// 页面分页
.pagination {                                                                                                                                                                                   // 页面分页
  border-radius: 15px;                                                                                                                                        // 扁平化,两边非对称
  box-shadow: 1px 2px 8px 4px rgba(0,0,0,0.15);
  background: rgba(255,255,255,0.9);                                                                                                                                         // 增加透明度
}
.pagination:hover{
  transition-property: all;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  box-shadow:0 2px 4px 0px rgba(0,0,0,0.1),
    0 4px 8px 0px rgba(0,0,0,0.1),
    0 8px 16px 0px rgba(0,0,0,0.1),
    0 16px 32px 0px rgba(0,0,0,0.1) !important;
}

// valine评论页
.comments{
  border-radius: 15px;
  box-shadow: 0 1px 2px 0px rgba(0,0,0,0.1),
    0 2px 4px 0px rgba(0,0,0,0.1);
  background: rgba(255,255,255,0.9);
}
.comments:hover {
  transition-property: all;
  transition-duration: 0.3s;
  transition-timing-function: ease;
  transition-delay: 0s;
  box-shadow:0 2px 4px 0px rgba(0,0,0,0.1),
    0 4px 8px 0px rgba(0,0,0,0.1),
    0 8px 16px 0px rgba(0,0,0,0.1),
    0 16px 32px 0px rgba(0,0,0,0.1) !important;
}

// 悬浮在头部菜单栏时显示白色
.menu-item-active a, .menu .menu-item a:hover, .menu .menu-item span.exturl:hover {
  background: #f9f9f99e;                                                                                                                                                             // 首页菜单选中后,变成淡白色.
}

// 设置内容区的宽度
.content-wrap {
  width: calc(100% - 300px);
}
@media (max-width: 767px) {
  .content-wrap {
    padding: $content-mobile-padding;
    width: 100%;
  }
}


// 返回顶部标志设为圆形
.back-to-top.back-to-top-on {
  bottom: 30px;
  border-radius: 10px;
}


// 侧边栏个人信息
.site-author-image{
  max-width: 150px;
  width: 135px;
}

// 侧边栏图标间距
.links-of-author-item a, .links-of-author-item span.exturl{
  padding: 0 10px;
}


/*
**
  文章内容美化
***
 */
// 文章字体设为高级的灰色
.post-body {
  color: #333;
}

// Code部分美化
code {
  padding: 2px 4px;
  word-wrap: break-word;
  color: #ff7600;
  background: #fbf7f8;
  border-radius: 3px;
  font-size: 15px;
  font-weight: 500;
}

// 下划线美化
hr {
  background-color: #86dca3;
}

// 去掉图片的边框,显得更加自然
.posts-expand .post-body img {
  border: 1px #6f42c1;
}


// 鼠标选择的段落变成黄色
::selection {
  background-color: #59ff83;
  color: #555;
}

// 对页面文章的美化
.posts-expand .home .post-title {
  font-size: 1.2em;
  text-align: left;
  border-left: #7fb8ee 8px solid;
  padding-left: 12px;
}
.post-title {
  font-weight: 900!important;
}
.posts-expand .home .post-meta{
  text-align: left;
  margin: 8px 0 15px!important;
}
.post-button{
  text-align: right;
  margin-top: 0;
}

// 文章底部标签样式
.posts-expand .post-tags a {
  -webkit-box-shadow: 0 1px 3px rgba(0, 0, 0, .12), 0 1px 2px rgba(0, 0, 0, .24);
  -moz-box-shadow: 0 1px 3px rgba(0, 0, 0, .12), 0 1px 2px rgba(0, 0, 0, .24);
  box-shadow: 0 1px 3px rgba(0, 0, 0, .12), 0 1px 2px rgba(0, 0, 0, .24);
  font-family: 'Comic Sans MS', sans-serif;
  transition: .2s ease-out;
  padding: 3px 10px;
  margin: 5px;
  background: #f5f5f5;
  border-bottom: none;
  border-radius: 15px;

  +mobile() {
    padding: 1px 3px;
    font-size: 8px;
  }

  &:hover {
    background: #34495e;
    color: #fff;
    -webkit-box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    -moz-box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }
}


// 阅读全文按钮美化
.btn {
  padding: 3px 15px;
  color: #34495e!important;
  box-shadow: 0 0 0 1px #34495e;
  border: 1px;
  border-radius: 15px;
  position: relative!important;
  text-decoration: none!important;
  transition: color .3s ease-in-out;
  display: inline-block;
  line-height: 2;
}
.btn:hover{
  color: #fff!important
  border-color: #222;
  background: #34495e;
}

// 修改代码块mac-panel上方颜色
.highlight-container{
  background: #7fb8ee
}

// 光标放到文章列表上面的时候,会变成彩色
.posts-expand .post-title-link::before {
  background-image: linear-gradient(90deg,#a166ab 0,#ef4e7b 25%,#f37055 50%,#ef4e7b 75%,#a166ab 100%);
}


// 文章分类页面中,标签的颜色属性.
.category-list a{
  color:#6f42c1;
}

// 调整段落间距
p {
  margin: 0 0 10px 0;
}


// 顶部进度条隐藏
.headband {
  height: 0px;
  background: #fc6423;
}



/*
***
  滚动条美化
**
*/
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}
::-webkit-scrollbar-button {
  width: 0;
  height: 0;
}
::-webkit-scrollbar-button:start:increment,::-webkit-scrollbar-button:end:decrement {
  display: none;
}
::-webkit-scrollbar-corner {
  display: block;
}
::-webkit-scrollbar-thumb {
  // border-radius: 8px;
  background-color: rgba(0,0,0,.2);
}
::-webkit-scrollbar-thumb:hover {
  // border-radius: 8px;
  background-color: rgba(127,184,238,.5);
}
::-webkit-scrollbar-track,::-webkit-scrollbar-thumb {
  border-right: 1px solid transparent;
  border-left: 1px solid transparent;
}
//::-webkit-scrollbar-track:hover {    // 按住滚动条时悬浮的样式
//  background-color: rgba(0,0,0,.15);
//}
::-webkit-scrollbar-button:start {
  width: 10px;
  height: 10px;
  /*background: url(../images/scrollbar_arrow.png) no-repeat 0 0;*/  /*可以添加滚动条样式*/
}



/*
***
  归档部分美化
**
*/

// 改变归档竖线彩带效果
.posts-collapse::before {
  background: linear-gradient(180deg,#f79533 0,#f37055 15%,#ef4e7b 30%,#a166ab 44%,#5073b8 58%,#1098ad 72%,#07b39b 86%,#6dba82 100%);
  opacity: 0.3
}

.page-archive .posts-collapse .archive-move-on{
  background-color: #fc6423;
}

// 改变归档彩球颜色
.posts-collapse .collection-title::before{
  background-color: #fc6423;
}
.posts-collapse .collection-year::before{
  background-color: blueviolet
}
.posts-collapse .post-header::before {
  background-color: gray;
  opacity: 0;
}

// 改变归档日期颜色以及发布内容部分
.posts-collapse .post-meta {
  color: #5073b8;
  font-weight: 900;
}
.posts-collapse .post-title {
  margin-left: 5px;
}

// 设置归档方框美化
.posts-collapse .post-header {
  position: relative;
  box-shadow: 0 1px 3px #6f42c100, 0 0px 6px #6f42c1;
  padding: 2px 10px;
  margin: 8px;
  border-bottom: none;
  border-radius: 10px;
  width: 85%;
}
.posts-collapse .post-header:hover{
  transition-duration: 0.2s;
  transition-timing-function: ease-in-out;
  transition-delay: 0s;
  transition-property: inherit;
  box-shadow: 0 1px 3px #6f42c100, 0 0px 17px 2px #6f42c1;
  transform: scale(1.02) !important;
}
.posts-collapse .post-title a, .posts-collapse .post-title span.exturl{
  font-size: small;
}



// 主标题栏位背景颜色美化
.site-meta {
  background-image: linear-gradient(200deg, #e4a0a3, #3F51B5) !important;
  background: #fff;
  //background-image: linear-gradient(90deg, #4263c1 0, #ef4ec5 25%, #b255f3 50%, #4eb2ef 75%, #8466ab 100%);
}

// 标签页设置前面的符号
.tag-cloud-tags a:before{
  content: "🔖";
}
```

彩色标签
----

> 参考[此篇博客](https://zhengyujie.github.io/2019/08/20/hexo%E5%BD%A9%E8%89%B2%E6%A0%87%E7%AD%BE/)随机颜色

关键在于需要自定义一个随机颜色并且知道各个元素具体的标签名字，并且知道`.swig`该文件含义

1.  修改`\themes\next\layout\page.swig`文件，修改主题配置文件中标签起始和终止颜色为白色，再添加自定义的彩色标签
    
    ```
    <div class="tag-cloud">        
        <!--目前共计xxx个标签-->  
        <!--  <div class="tag-cloud-title">
        {{ _p('counter.tag_cloud', site.tags.length) }}
        </div>  -->
    
        <!--标签样式-->
        <div class="tag-cloud-tags">
        {{ tagcloud({min_font: 15, max_font: 25, amount: theme.tagcloud.amount, color: true, start_color: theme.tagcloud.start, end_color: theme.tagcloud.end}) }}    
        </div>  
    </div>
    
    <!--自定义彩色标签-->
    {% include 'tag-color.swig' %}
    ```
    
2.  在同级目录下创建`\themes\next\layout\tag-color.swig`文件，用到了 js DOM 知识
    
    ```
    <script type="text/javascript">
        var alltags = document.getElementById('tags');
        var tags = alltags.getElementsByTagName('a');
    
        for (var i = tags.length - 1; i >= 0; i--) {
            var r = Math.floor(Math.random()*75+130);
            var g = Math.floor(Math.random()*75+100);
            var b = Math.floor(Math.random()*75+80);
            tags[i].style.background = "rgb("+r+","+g+","+b+")";
        }
    </script>
    ```
    

心形转动分类
------

> 参考[此篇博客](https://www.liaofuzhan.com/posts/4158923031.html)

1.  修改`\themes\next\layout\page.swig`文件
    
    ```
    {% elif page.type === 'categories' %}
    <div class="category-all-page">
        <div class="category-all-title">
        {{ _p('counter.categories', site.categories.length) }}
        </div>
        <!--分类详情-->
        <div class="category-all">
        {{ list_categories() }}
        </div>
    </div>
    
    <!--自定义心形分类-->
    {% include 'category-love.swig' %}
    ```
    
2.  在同级目录下创建`\themes\next\layout\category-love.swig`文件，用到了 js DOM 知识
    
    ```
    <style>
      .love {
          width: 500px;
          height: 650px;
          position: relative;
          margin: 60px auto;
      }
    
      .love a {
          position: absolute;
          left: 0;
          //color: goldenrod;
          //color: #e804048f;
          font-size: 20px;
          font-family: sans-serif;
          text-shadow: 0 0 1em white;
          animation:
              x-move 10s ease-in-out infinite alternate,
              y-move 20s linear infinite;
          animation-delay: calc(45s / var(--particles) * var(--n) * -1);
          user-select: auto; // none
      }
    
      .love a:first-child {
          color: orangered;
          font-size: 3em;
          text-shadow:
              0 0 0.1em black,
              0 0 1em white;
          z-index: 1;
      }
    
      @keyframes x-move {
          to {
              left: 450px;
          }
      }
    
      @keyframes y-move {
          0% { transform: translateY(180px); }
          10% { transform: translateY(45px); }
          15% { transform: translateY(5px); }
          18% { transform: translateY(0); }
          20% { transform: translateY(5px); }
          22% { transform: translateY(35px); }
          24% { transform: translateY(65px); }
          25% { transform: translateY(110px); }
          26% { transform: translateY(65px); }
          28% { transform: translateY(35px); }
          30% { transform: translateY(5px); }
          32% { transform: translateY(0); }
          35% { transform: translateY(5px); }
          40% { transform: translateY(45px); }
          50% { transform: translateY(180px); }
          71% { transform: translateY(430px); }
          72.5% { transform: translateY(440px); }
          75% { transform: translateY(450px); }
          77.5% { transform: translateY(440px); }
          79% { transform: translateY(430px); }
          100% { transform: translateY(180px); }
      }
    
      /* 移动端样式 */
      @media (max-width: 767px) {
        .love{
            width: 360px;
            height: 450px;
            margin: 30px auto;
        }
        @keyframes x-move {
            to {
                left: 285px;
            }
        }
      }
    </style>
    
    
    <div class="love"></div>
    
    
    <script type="text/javascript">
         var categoryall = document.getElementsByClassName('category-all');    
         var categories = categoryall[0].getElementsByTagName('a');
         var numbers = categoryall[0].getElementsByTagName('span');
         //  隐藏categoryall类，不能直接修改布局文件，否则找不到上面的属性
         categoryall[0].setAttribute("hidden","hidden")
         
         var words = ['❤️'];
         for(var i = 0 ; i < categories.length ; i ++){
            words.push(categories[i]);    //  此处不是放入.innerHTML，因为要用到链接
            words.push('♠');
         }
         words.push('💕');
         
         var dom = {
             love: document.querySelector('.love')
         }
         dom.love.style.setProperty('--particles', words.length)
    
        // =>为匿名函数，forEach应用于数组  https://www.runoob.com/jsref/jsref-foreach.html
         var index = 0;
         words.forEach((word, i) => {
            //  创建一个元素
             let atag = document.createElement('a');
             atag.style.setProperty('--n', i + 1);
             atag.style.setProperty('text-decoration', 'none');
             atag.style.setProperty('border-bottom', 'none');
            
            //  设置随机颜色属性
             var r=Math.floor(Math.random()*75+130);
             var g=Math.floor(Math.random()*75+100);
             var b=Math.floor(Math.random()*75+80);
             atag.style.setProperty("color", "rgb("+r+","+g+","+b+")");
             
             //  设置文字和链接
             if(word.href == undefined){
                atag.setAttribute("href", "#");
                atag.innerText = word;
             }
            //  为每个分类后添加数目
             else{
                atag.innerText = word.innerText + '(' + numbers[index].innerHTML + ')';   
                index+=1;
                atag.setAttribute("href", word.href);
             }
    
             dom.love.appendChild(atag);
         })
    </script>
    ```
    

底栏修改
----

修改`\themes\next\layout\_partials\footer.swig`文件，主要修改了总字长的格式（省去了原有的字），添加了网站运行时间。

```
<div class="copyright">
  {% set copyright_year = date(null, 'YYYY') %}
  © {% if theme.footer.since and theme.footer.since != copyright_year %}{{ theme.footer.since }} – {% endif %}
  <span itemprop="copyrightYear">{{ copyright_year }}</span>
  <span class="with-love">
    <i class="fa fa-{{ theme.footer.icon.name }}"></i>
  </span>
  <span class="author" itemprop="copyrightHolder">{{ theme.footer.copyright or author }}</span>

<!-- 底栏总字长 -->
  {%- if config.symbols_count_time.total_symbols %}
    <span class="post-meta-divider">|</span>
    <span class="post-meta-item-icon">
      <i class="fa fa-area-chart"></i>
    </span>
<!--    {%- if theme.symbols_count_time.item_text_total %}-->
<!--       <span class="post-meta-item-text">{{ __('symbols_count_time.count_total') + __('symbol.colon') }}</span>-->
<!--     {%- endif %}-->
    <span title="{{ __('symbols_count_time.count_total') }}">{{ symbolsCountTotal(site) }}</span>
  {%- endif %}

<!-- 底栏总阅读时间 -->
  {%- if config.symbols_count_time.total_time %}
    <span class="post-meta-divider">|</span>
    <span class="post-meta-item-icon">
      <i class="fa fa-coffee"></i>
    </span>
<!--    {%- if theme.symbols_count_time.item_text_total %}-->
<!--    <span class="post-meta-item-text">{{ __('symbols_count_time.time_total') }} ≈</span>-->
<!--    {%- endif %}-->
    <span title="{{ __('symbols_count_time.time_total') }}">{{ symbolsTimeTotal(site, theme.symbols_count_time.awl, theme.symbols_count_time.wpm) }}</span>
  {%- endif %}
</div>

{%- if theme.footer.powered.enable %}
  <div class="powered-by">
    {{- __('footer.powered', next_url('https://hexo.io', 'Hexo', {class: 'theme-link'})) }}
    {%- if theme.footer.powered.version %} v{{ hexo_version }}{%- endif %}
  </div>
{%- endif %}

{%- if theme.footer.powered.enable and theme.footer.theme.enable %}
  <span class="post-meta-divider">|</span>
{%- endif %}

{%- if theme.footer.theme.enable %}
  <div class="theme-info">
    {%- set next_site = 'https://theme-next.org' %}
    {%- if theme.scheme !== 'Gemini' %}
      {%- set next_site = 'https://' + theme.scheme | lower + '.theme-next.org' %}
    {%- endif %}
    {{- __('footer.theme') }} – {{ next_url(next_site, 'NexT.' + theme.scheme, {class: 'theme-link'}) }}
    {%- if theme.footer.theme.version %} v{{ next_version }}{%- endif %}
  </div>
{%- endif %}

{%- if theme.add_this_id %}
  <div class="addthis_inline_share_toolbox">
    <script src="//s7.addthis.com/js/300/addthis_widget.js#pubid={{ theme.add_this_id }}" async="async"></script>
  </div>
{%- endif %}

{{- next_inject('footer') }}


<!-- 网站运行时间的设置 -->
<span id="timeDate">载入天数...</span>
<span id="times">载入时分秒...</span>   Talk is cheap. Show me the code.
<script>
    var now = new Date();
    function createtime() {
        var grt= new Date("12/12/2019 12:00:00");    //此处修改你的建站时间或者网站上线时间
        now.setTime(now.getTime()+250);
        days = (now - grt ) / 1000 / 60 / 60 / 24; 
        dnum = Math.floor(days);
        hours = (now - grt ) / 1000 / 60 / 60 - (24 * dnum); 
        hnum = Math.floor(hours);
        if(String(hnum).length ==1 )
        {
            hnum = "0" + hnum;
        } 
        minutes = (now - grt ) / 1000 /60 - (24 * 60 * dnum) - (60 * hnum);
        mnum = Math.floor(minutes); if(String(mnum).length ==1 )
        {
            mnum = "0" + mnum;
        }
        seconds = (now - grt ) / 1000 - (24 * 60 * 60 * dnum) - (60 * 60 * hnum) - (60 * mnum);
        snum = Math.round(seconds); 
        if(String(snum).length ==1 )
        {
            snum = "0" + snum;
        }
        document.getElementById("timeDate").innerHTML = "本站已运行 "+dnum+" 天 ";
        document.getElementById("times").innerHTML = hnum + " 小时 " + mnum + " 分 " + snum + " 秒    ";
    }
    setInterval("createtime()",250);
</script>


<!--备案信息-->
{%- if theme.footer.beian.enable %}
  <div class="beian">
    {{- next_url('http://www.beian.miit.gov.cn', theme.footer.beian.icp) }}
    <span>   |  </span>
    {%- if theme.footer.beian.gongan_icon_url %}
      <img src="{{ theme.footer.beian.gongan_icon_url }}" style="display: inline-block;">
    {%- endif %}
    {%- if theme.footer.beian.gongan_id and theme.footer.beian.gongan_num %}
      {{- next_url('http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=' + theme.footer.beian.gongan_id, theme.footer.beian.gongan_num + ' ') }}
    {%- endif %}
  </div>
{%- endif %}
```

配置文件解释
------

初期什么都不知道，只单纯的跟着网上做，完全没有头绪的阶段。后面把配置文件捋清楚了一遍，再自定义了一些 css 样式，算是初步完成了整体搭建吧。

大部分的美化工作已经在配置文件中定义了，上面的自定义主要是针对整体布局和细节进行修改的，暂时改的还是比较满意的，**了解配置文件很重要，可以解决大部分问题**

### 站点配置文件

```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: Rkkkk    # 网站的标题，可能用在各种布局的页面中
subtitle: ''    # 网站子标题
description: 'Go go go!'    # 网站的描述性
keywords:    # 网站的关键字
author: 我很欣赏你    # 网站的作者
language: zh-CN    # 网站采用语言，要跟/theme/***/languages/**.yml下的文件名对应。
timezone: ''    # 网站的时区

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://qypu1r.coding-pages.com/    # 网站的url，如果不在域名根目录，应包含子目录，且root要设置为`/子目录/`
# https://renke999.github.io/
root: /    # 网站的根目录
permalink: :year/:month/:day/:title/    #文章永久链接的形成模版。每一篇文章都有唯一的url。
permalink_defaults:    #文章永久链接中，各部分的默认值。
pretty_urls:
  trailing_index: true # Set to false to remove trailing index.html from permalinks

# Directory
source_dir: source    # 网站中源文件（比如Markdown啊什么的所在的文件夹）
public_dir: public    # 生成的静态网站的目录
tag_dir: tags    # 标签页所在的文件夹。
archive_dir: archives    # 文档页所在的文件夹
category_dir: categories    # 类别也所在的文件夹
code_dir: downloads/code    # 代码也所在的文件夹
i18n_dir: :lang    # 国际语言所在的文件夹
skip_render:    # 忽略文档清单
 
# Writing
new_post_name: :title.md    # 默认新建文档名，`:title`为变量，指文档标题，也可用其他变量
default_layout: post    # 新建文档的默认布局
titlecase: false    # 是否要把标题中的首字符大写
external_link:    # 是否要在新开tab中打开外链
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: ''
filename_case: 0    # 文件名是否小写敏感
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag
default_category: uncategorized    # 对文档的默认分类
category_map:    # 对文档中的分类字段进行映射。建立分类文件夹时采用映射后的字符串
tag_map:    # 对文档中的标签字段进行映射。建立标签文件夹时采用映射后的字符串

# Metadata elements
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD    # 日期格式
time_format: HH:mm:ss    # 时间格式
## Use post's date for updated date unless set in front-matter
use_date_for_updated: false

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10    # 主页/分类/标签/存档等类型索引页包含文章数量
pagination_dir: page    # 分页所在文件夹

# Include / Exclude file(s)
## include:/exclude: options only apply to the 'source/' folder
include:
exclude:
ignore:

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:    # 定义部署
  type: git
  repo: 
      github: git@github.com:renke999/renke999.github.io.git
      coding: git@e.coding.net:renke666/renke666.git
  branch: master


live2d:
  enable: true
  pluginModelPath: assets/
  model:
    use: live2d-widget-model-hijiki  #模板目录，在node_modules里
  display:
    position: right
    width: 160
    height: 360
  mobile:
    show: false  #是否在手机进行显示
  react: 
    opacity: 0.7 # 透明度


# 文章末尾添加“本文结束”标记
passage_end_tag:
    enabled: true
    
        
backup:
  type: git
  theme: hexo-next
  message: Back up www.renke666.top
  repository:
    github: git@github.com:renke999/renke999.github.io.git,backup
```

### 主题配置文件

```
# ---------------------------------------------------------------
# Theme Core Configuration Settings
# See: https://theme-next.org/docs/theme-settings/
# ---------------------------------------------------------------

# If false, merge configs from `_data/next.yml` into default configuration (rewrite).
# If true, will fully override default configuration by options from `_data/next.yml` (override). Only for NexT settings.
# And if true, all config from default NexT `_config.yml` must be copied into `next.yml`. Use if you know what you are doing.
# Useful if you want to comment some options from NexT `_config.yml` by `next.yml` without editing default config.
override: false    # 设置为true，则完全重载默认配置，当你完全不想继承主题配置时很有用

# Console reminder if new version released.
reminder: false

# Allow to cache content generation. Introduced in NexT v6.0.0.
cache:
  enable: true

# Remove unnecessary files after hexo generate.
minify: false

# Define custom file paths.
# Create your custom files in site directory `source/_data` and uncomment needed files below.
custom_file_path:
  #head: source/_data/head.swig
  #header: source/_data/header.swig
  #sidebar: source/_data/sidebar.swig
  #postMeta: source/_data/post-meta.swig
  #postBodyEnd: source/_data/post-body-end.swig
  #footer: source/_data/footer.swig
  #bodyEnd: source/_data/body-end.swig
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl


# ---------------------------------------------------------------
# Site Information Settings
# See: https://theme-next.org/docs/getting-started/
# ---------------------------------------------------------------

favicon:    # 网站图标
  small: /images/jiji_cat_16px_1141982_easyicon.net.ico
  medium: /images/jiji_cat_32px_1141982_easyicon.net.ico
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml

footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
  since: 2019

  # Icon between year and copyright info.
  icon:
    # Icon name in Font Awesome. See: https://fontawesome.com/v4.7.0/icons/
    # `heart` is recommended with animation in red (#ff0000).
    name: heart    #作者图标（默认是author人像)
    # If you want to animate the icon, set it to true.
    animated: true
    # Change the color of icon, using Hex Code.
    color: "#FF0000"

  # If not defined, `author` from Hexo `_config.yml` will be used.
  copyright:

  powered: 
    # Hexo link (Powered by Hexo).
    enable: false
    # Version info of Hexo after Hexo link (vX.X.X).
    version: false

  theme:
    # Theme & scheme info link (Theme - NexT.scheme).
    enable: false
    # Version info of NexT after scheme info (vX.X.X).
    version: false

  # Beian ICP and gongan information for Chinese users. See: http://www.beian.miit.gov.cn, http://www.beian.gov.cn
  beian:
    enable: true
    icp: 苏ICP备20005221号-1
    # The digit in the num of gongan beian.
    gongan_id: 32111102000194
    # The full num of gongan beian.
    gongan_num: 苏公网安备 32111102000194号
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url: http://www.beian.gov.cn/portal/download?token=7ec73880-3394-48ef-933f-1710644bc2ec

# Creative Commons 4.0 International License.
# See: https://creativecommons.org/share-your-work/licensing-types-examples
# Available values of license: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
# You can set a language value if you prefer a translated version of CC license, e.g. deed.zh
# CC licenses are available in 39 languages, you can find the specific and correct abbreviation you need on https://creativecommons.org
creative_commons:
  license: by-nc-sa
  sidebar: false
  post: false
  language:


# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini


# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# When running the site in a subdirectory (e.g. yoursite.com/blog), remove the leading slash from link value (/archives -> archives).
# External url should start with http:// or https://
menu:
  home: / || home    # 主页链接及其图标
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat

# Enable / Disable menu icons / item badges.
menu_settings:
  icons: true
  badges: false


# ---------------------------------------------------------------
# Sidebar Settings
# See: https://theme-next.org/docs/theme-settings/sidebar
# ---------------------------------------------------------------

sidebar:
  # Sidebar Position.
  position: left
  #position: right

  # Manual define the sidebar width. If commented, will be default for:
  # Muse | Mist: 320
  # Pisces | Gemini: 240
  # width: 300

  # Sidebar Display (only for Muse | Mist), available values:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
  display: post

  # Sidebar padding in pixels.
  padding: 18
  # Sidebar offset from top menubar in pixels (only for Pisces | Gemini).
  offset: 12
  # Enable sidebar on narrow view (only for Muse | Mist).
  onmobile: false

# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
  url: /images/avatar.jpg
  # If true, the avatar will be dispalyed in circle.
  rounded: true
  # If true, the avatar will be rotated with the cursor.
  rotated: true

# Posts / Categories / Tags in sidebar.
site_state: true

# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimiter is the target permalink, value after `||` delimiter is the name of Font Awesome icon.
social:
  GitHub: https://github.com/renke999 || github
  E-Mail: mailto:446917139@qq.com || envelope
  QQ: tencent://Message/?Uin=446917139&websiteName=www.oicqzone.com&Menu=yes || qq
  Wechat: /images/wechat.png || weixin
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
  #RSS: /atom.xml || rss

social_icons:
  enable: true
  icons_only: true
  transition: true

# Blog rolls
links_settings:
  icon: link
  title: Links
  # Available values: block | inline
  layout: block

links:
  #Title: http://yoursite.com

# Table of Contents in the Sidebar
# Front-matter variable (unsupport wrap expand_all).
toc:
  enable: true     #是否自动生成目录
  # Automatically add list number to toc.
  number: false     #目录是否自动产生编号
  # If true, all words will placed on next lines if header width longer then sidebar width.
  wrap: false    # 标题目录是否自动换行
  # If true, all level of TOC in a post will be displayed, rather than the activated part of it.
  expand_all: false
  # Maximum heading depth of generated toc.
  max_depth: 6

# A button to open designated chat widget in sidebar.
# Firstly, you need enable the chat service you want to activate its sidebar button.
chat:
  enable: false
  #service: chatra
  #service: tidio
  icon: comment # Icon name in Font Awesome, set false to disable icon.
  text: Chat # Button text, change it as you wish.


# ---------------------------------------------------------------
# Post Settings    文章设置
# See: https://theme-next.org/docs/theme-settings/posts
# ---------------------------------------------------------------

# Automatically excerpt description in homepage as preamble text.
excerpt_description: false    # 自动摘要，可以<!--more-->精确控制

# Read more button
# If true, the read more button will be displayed in excerpt section.
read_more_btn: true

# Post meta display settings    摘要元数据
post_meta:
  item_text: true    # 是否显示"发表于"三个字
  created_at: true    # 文章创建日期
  updated_at:    # 文章修改日期
    enable: true
    another_day: true
  categories: true    # 文章所属分类

# Post wordcount display settings
# Dependencies: https://github.com/theme-next/hexo-symbols-count-time
symbols_count_time:    # 站点字数和阅读时长
  separated_meta: false
  item_text_post: true
  item_text_total: true
  awl: 3
  wpm: 300

# Use icon instead of the symbol # to indicate the tag at the bottom of the post
tag_icon: false    # 可以在此处修改，不用自己修改配置文件

# Reward (Donate)
# Front-matter variable (unsupport animation).
reward_settings:    # 打赏设置
  # If true, reward will be displayed in every article by default.
  enable: false
  animation: false
  #comment: Donate comment here.

reward:
  #wechatpay: /images/wechatpay.png
  #alipay: /images/alipay.png
  #bitcoin: /images/bitcoin.png

# Related popular posts
# Dependencies: https://github.com/tea3/hexo-related-popular-posts
related_posts:
  enable: false
  title: # Custom header, leave empty to use the default one
  display_in_home: false
  params:
    maxCount: 5
    #PPMixingRate: 0.0
    #isDate: false
    #isImage: false
    #isExcerpt: false

# Post edit
# Dependencies: https://github.com/hexojs/hexo-deployer-git
post_edit:
  enable: false
  url: https://github.com/user-name/repo-name/tree/branch-name/subdirectory-name # Link for view source
  #url: https://github.com/user-name/repo-name/edit/branch-name/subdirectory-name # Link for fork & edit

# Show previous post and next post in post footer if exists
# Available values: left | right | false
post_navigation: left


# ---------------------------------------------------------------
# Custom Page Settings
# See: https://theme-next.org/docs/theme-settings/custom-pages
# ---------------------------------------------------------------

# TagCloud settings for tags page.
tagcloud:
  # All values below are same as default, change them by yourself.
  min: 15 # Minimun font size in px
  max: 25 # Maxium font size in px
  start: "#ffffff" # Start color (hex, rgba, hsla or color keywords)    # #ccc
  end: "#ffffff" # End color (hex, rgba, hsla or color keywords)
  amount: 100 # Amount of tags, change it if you have more than 200 tags

# Google Calendar
# Share your recent schedule to others via calendar page.
calendar:
  calendar_id: <required> # Your Google account E-Mail
  api_key: <required>
  orderBy: startTime
  offsetMax: 24 # Time Range
  offsetMin: 4 # Time Range
  showDeleted: false
  singleEvents: true
  maxResults: 250


# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Set the text alignment in posts / pages.
text_align:
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
  desktop: justify
  mobile: justify

# Reduce padding / margin indents on devices with narrow width.
mobile_layout_economy: false

# Android Chrome header panel color ($brand-bg / $headband-bg => $black-deep).
android_chrome_color: "#222"

# Hide sticky headers and color the menu bar on Safari (iOS / macOS).
safari_rainbow: false

# Custom Logo (Do not support scheme Mist)
custom_logo: #/uploads/custom-logo.jpg

codeblock:
  # Code Highlight theme
  # Available values: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
  highlight_theme: normal
  # Add copy button on codeblock
  copy_button:
    enable: true
    # Show text copy result.
    show_result: true
    # Available values: default | flat | mac
    style: mac

back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
  scrollpercent: true

# Reading progress bar
reading_progress:
  enable: false
  # Available values: top | bottom
  position: top
  color: "#37c6c0"
  height: 3px

# Bookmark Support
bookmark:
  enable: false
  # Customize the color of the bookmark.
  color: "#222"
  # If auto, save the reading progress when closing the page or clicking the bookmark-icon.
  # If manual, only save it by clicking the bookmark-icon.
  save: auto

# `Follow me on GitHub` banner in the top-right corner.
github_banner:
  enable: false
  permalink: https://github.com/yourname
  title: Follow me on GitHub


# ---------------------------------------------------------------
# Font Settings
# See: https://theme-next.org/docs/theme-settings/#Fonts-Customization
# ---------------------------------------------------------------
# Find fonts on Google Fonts (https://www.google.com/fonts)
# All fonts set here will have the following styles:
#   light | light italic | normal | normal italic | bold | bold italic
# Be aware that setting too much fonts will cause site running slowly
# ---------------------------------------------------------------
# To avoid space between header and sidebar in scheme Pisces / Gemini, Web Safe fonts are recommended for `global` (and `title`):
# Arial | Tahoma | Helvetica | Times New Roman | Courier New | Verdana | Georgia | Palatino | Garamond | Comic Sans MS | Trebuchet MS
# ---------------------------------------------------------------

font:
  enable: true

  # Uri of fonts host, e.g. //fonts.googleapis.com (Default).
  host: https://fonts.loli.net 

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # Global font settings used for all elements inside <body>.
  global:    # 在<body>元素中设置全局字体
    external: true
    family: EB Garamond
    size:

  # Font settings for site title (.site-title).
  title:    # 标题（h1~h6字体，有global字体设置托底）
    external: true
    family:  Noto Serif SC
    size:

  # Font settings for headlines (<h1> to <h6>).
  headings:    # post文章字体，有global字体设置托底
    external: true
    family: Noto Serif SC
    size:

  # Font settings for posts (.post-body).
  posts:    # logo字体设置，有global字体设置托底
    external: true
    family: Noto Serif SC

  # Font settings for <code> and code blocks.
  codes:    # 代码块字体
    external: true
    family:


# ---------------------------------------------------------------
# SEO Settings
# ---------------------------------------------------------------

# Disable Baidu transformation on mobile devices.
disable_baidu_transformation: false

# Set a canonical link tag for your Hexo site.
# See: https://support.google.com/webmasters/answer/139066
# Remember to set up your URL in Hexo `_config.yml` (e.g. url: http://yoursite.com)
canonical: true

# Change headers hierarchy on site-subtitle (will be main site description) and on all post / page titles for better SEO-optimization.
seo: false

# If true, site-subtitle will be added to index page.
# Remember to set up your site-subtitle in Hexo `_config.yml` (e.g. subtitle: Subtitle)
index_with_subtitle: false

# Automatically add external URL with Base64 encrypt & decrypt.
exturl: false

# Google Webmaster tools verification.
# See: https://www.google.com/webmasters
google_site_verification:

# Bing Webmaster tools verification.
# See: https://www.bing.com/webmaster
bing_site_verification:

# Yandex Webmaster tools verification.
# See: https://webmaster.yandex.ru
yandex_site_verification:

# Baidu Webmaster tools verification.
# See: https://ziyuan.baidu.com/site
baidu_site_verification:

# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO.
baidu_push: false


# ---------------------------------------------------------------
# Third Party Plugins & Services Settings
# See: https://theme-next.org/docs/third-party-services/
# You may need to install dependencies or set CDN URLs in `vendors`
# There are two different CDN providers by default:
#   - jsDelivr (cdn.jsdelivr.net), works everywhere even in China
#   - CDNJS (cdnjs.cloudflare.com), provided by cloudflare
# ---------------------------------------------------------------

# Math Formulas Render Support
math:
  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front-matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support.
  mathjax:
    enable: true
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: false
    

  # hexo-renderer-markdown-it-plus (or hexo-renderer-markdown-it with markdown-it-katex plugin) required for full Katex support.
  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false

# Easily enable fast Ajax navigation on your website.
# Dependencies: https://github.com/theme-next/theme-next-pjax
pjax: false

# FancyBox is a tool that offers a nice and elegant way to add zooming functionality for images.
# For more information: https://fancyapps.com/fancybox
fancybox: false

# A JavaScript library for zooming images like Medium.
# Do not enable both `fancybox` and `mediumzoom`.
# For more information: https://github.com/francoischalifour/medium-zoom
mediumzoom: false

# Vanilla JavaScript plugin for lazyloading images.
# For more information: https://github.com/ApoorvSaxena/lozad.js
lazyload: false

# Pangu Support
# For more information: https://github.com/vinta/pangu.js
pangu: false

# Quicklink Support
# For more information: https://github.com/GoogleChromeLabs/quicklink
# Front-matter (unsupport home archive).
quicklink:
  enable: false

  # Home page and archive page can be controlled through home and archive options below.
  # This configuration item is independent of `enable`.
  home: false
  archive: false

  # Default (true) will initialize quicklink after the load event fires.
  delay: true
  # Custom a time in milliseconds by which the browser must execute prefetching.
  timeout: 3000
  # Default (true) will enable fetch() or falls back to XHR.
  priority: true

  # For more flexibility you can add some patterns (RegExp, Function, or Array) to ignores.
  # See: https://github.com/GoogleChromeLabs/quicklink#custom-ignore-patterns
  ignores:


# ---------------------------------------------------------------
# Comments Settings
# See: https://theme-next.org/docs/third-party-services/comments
# ---------------------------------------------------------------

# Multiple Comment System Support
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: changyan | disqus | disqusjs | gitalk | livere | valine
  active:
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any navs, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2

# Disqus
disqus:
  enable: false
  shortname:
  count: true
  #post_meta_order: 0

# DisqusJS
# Alternative Disqus - Render comment component using Disqus API.
# Demo: https://suka.js.org/DisqusJS/
# For more information: https://github.com/SukkaW/DisqusJS
disqusjs:
  enable: false
  # API Endpoint of Disqus API (https://disqus.com/api/).
  # Leave api empty if you are able to connect to Disqus API. Otherwise you need a reverse proxy for it.
  # For example:
  # api: https://disqus.skk.moe/disqus/
  api:
  apikey: # Register new application from https://disqus.com/api/applications/
  shortname: # See: https://disqus.com/admin/settings/general/

# Changyan
changyan:
  enable: false
  appid:
  appkey:
  #post_meta_order: 0

# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
  enable: true
  appid: OQqgSbJIYga73FaHFPLMJngp-gzGzoHsz
  appkey: UpH8H3RynfSOI0lMmpBlVEeJ
  notify: true # Mail notifier
  verify: false # Verification code
  placeholder: 留个评论吧☺ # Comment box placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
  language: # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
  recordIP: false # Whether to record the commenter IP
  serverURLs: # When the custom domain name is enabled, fill it in here (it will be detected automatically by default, no need to fill in)
  #post_meta_order: 0

# LiveRe comments system
# You can get your uid from https://livere.com/insight/myCode (General web site)
livere_uid: # <your_uid>

# Gitalk
# For more information: https://gitalk.github.io, https://github.com/gitalk/gitalk
gitalk:
  enable: false
  github_id: # GitHub repo owner
  repo: # Repository name to store issues
  client_id: # GitHub Application Client ID
  client_secret: # GitHub Application Client Secret
  admin_user: # GitHub repo owner and collaborators, only these guys can initialize gitHub issues
  distraction_free_mode: true # Facebook-like distraction free mode
  # Gitalk's display language depends on user's browser or system environment
  # If you want everyone visiting your site to see a uniform language, you can set a force language value
  # Available values: en | es-ES | fr | ru | zh-CN | zh-TW
  language:


# ---------------------------------------------------------------
# Post Widgets & Content Sharing Services
# See: https://theme-next.org/docs/third-party-services/post-widgets
# ---------------------------------------------------------------

# Star rating support to each article.
# To get your ID visit https://widgetpack.com
rating:
  enable: false
  id:     # <app_id>
  color:  fc6423

# AddThis Share. See: https://www.addthis.com
# Go to https://www.addthis.com/dashboard to customize your tools.
add_this_id:


# ---------------------------------------------------------------
# Statistics and Analytics
# See: https://theme-next.org/docs/third-party-services/statistics-and-analytics
# ---------------------------------------------------------------

# Google Analytics
google_analytics:
  tracking_id: # <app_id>
  # By default, NexT will load an external gtag.js script on your site.
  # If you only need the pageview feature, set the following option to true to get a better performance.
  only_pageview: false

# Baidu Analytics
baidu_analytics: # <app_id>

# Growingio Analytics
growingio_analytics: # <project_id>

# CNZZ count
cnzz_siteid:

# Show number of visitors of each article.
# You can visit https://leancloud.cn to get AppID and AppKey.
# AppID and AppKey are recommended to be the same as valine's for counter compatibility.
# Do not enable both `valine.visitor` and `leancloud_visitors`.
leancloud_visitors:
  enable: false
  app_id: # <app_id>
  app_key: # <app_key>
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true
  betterPerformance: false

# Another tool to show number of visitors to each article.
# Visit https://console.firebase.google.com/u/0/ to get apiKey and projectId.
# Visit https://firebase.google.com/docs/firestore/ to get more information about firestore.
firestore:
  enable: false
  collection: articles # Required, a string collection name to access firestore database
  apiKey: # Required
  projectId: # Required

# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye


# ---------------------------------------------------------------
# Search Services
# See: https://theme-next.org/docs/third-party-services/search-services
# ---------------------------------------------------------------

# Algolia Search
# For more information: https://www.algolia.com
algolia_search:
  enable: false
  hits:
    per_page: 10
  labels:
    input_placeholder: Search for Posts
    hits_empty: "We didn't find any results for the search: ${query}"
    hits_stats: "${hits} results found in ${time} ms"

# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false

# Swiftype Search API Key
swiftype_key:


# ---------------------------------------------------------------
# Chat Services
# See: https://theme-next.org/docs/third-party-services/chat-services
# ---------------------------------------------------------------

# Chatra Support
# See: https://chatra.io
# Dashboard: https://app.chatra.io/settings/general
chatra:
  enable: false
  async: true
  id: # Visit Dashboard to get your ChatraID
  #embed: # Unfinished experimental feature for developers. See: https://chatra.io/help/api/#injectto

# Tidio Support
# See: https://www.tidiochat.com
# Dashboard: https://www.tidiochat.com/panel/dashboard
tidio:
  enable: false
  key: # Public Key, get it from dashboard. See: https://www.tidiochat.com/panel/settings/developer


# ---------------------------------------------------------------
# Tags Settings
# See: https://theme-next.org/docs/tag-plugins/
# ---------------------------------------------------------------

# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0

# Tabs tag
tabs:
  transition:
    tabs: false
    labels: true

# PDF tag, requires two plugins: pdfObject and pdf.js
# pdfObject will try to load pdf files natively, if failed, pdf.js will be used.
# The following `cdn` setting is only for pdfObject, because cdn for pdf.js might be blocked by CORS policy.
# So, you must install the dependency of pdf.js if you want to use pdf tag and make it available to all browsers.
# See: https://github.com/theme-next/theme-next-pdf
pdf:
  enable: false
  # Default height
  height: 500px

# Mermaid tag
mermaid:
  enable: false
  # Available themes: default | dark | forest | neutral
  theme: forest


# ---------------------------------------------------------------
# Animation Settings
# ---------------------------------------------------------------

# Use velocity to animate everything.
# For more information: http://velocityjs.org
motion:
  enable: true
  async: false
  transition:
    # Transition variants:
    # fadeIn | flipXIn | flipYIn | flipBounceXIn | flipBounceYIn
    # swoopIn | whirlIn | shrinkIn | expandIn
    # bounceIn | bounceUpIn | bounceDownIn | bounceLeftIn | bounceRightIn
    # slideUpIn | slideDownIn | slideLeftIn | slideRightIn
    # slideUpBigIn | slideDownBigIn | slideLeftBigIn | slideRightBigIn
    # perspectiveUpIn | perspectiveDownIn | perspectiveLeftIn | perspectiveRightIn
    post_block: fadeIn
    post_header: slideDownIn
    post_body: slideDownIn
    coll_header: slideLeftIn
    # Only for Pisces | Gemini.
    sidebar: slideUpIn

# Progress bar in the top during page loading.
# Dependencies: https://github.com/theme-next/theme-next-pace
# For more information: https://github.com/HubSpot/pace
pace:
  enable: flase
  # Themes list:
  # big-counter | bounce | barber-shop | center-atom | center-circle | center-radar | center-simple
  # corner-indicator | fill-left | flat-top | flash | loading-bar | mac-osx | material | minimal
  theme: bounce

# JavaScript 3D library.
# Dependencies: https://github.com/theme-next/theme-next-three
three:
  enable: false
  three_waves: false
  canvas_lines: false
  canvas_sphere: false

# Canvas-nest
# Dependencies: https://github.com/theme-next/theme-next-canvas-nest
# For more information: https://github.com/hustcc/canvas-nest.js
canvas_nest:
  enable: false
  onmobile: true # Display on mobile or not
  #132,138,135   84,78,77
  color: "132,138,135" # RGB values, use `,` to separate
  opacity: 0. 7 # The opacity of line: 0~1
  zIndex: -1 # z-index property of the background
  count: 150 # The number of lines

# Canvas-ribbon
# Dependencies: https://github.com/theme-next/theme-next-canvas-ribbon
# For more information: https://github.com/zproo/canvas-ribbon
canvas_ribbon:
  enable: false
  size: 300 # The width of the ribbon
  alpha: 0.6 # The transparency of the ribbon
  zIndex: -1 # The display level of the ribbon


#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! See: https://theme-next.org/docs/advanced-settings
#! ---------------------------------------------------------------

# Script Vendors. Set a CDN address for the vendor you want to customize.
# Be aware that you would better use the same version as internal ones to avoid potential problems.
# Remember to use the https protocol of CDN files when you enable https on your site.
vendors:
  # Internal path prefix.
  _internal: lib

  # Internal version: 3.1.0
  # anime: //cdn.jsdelivr.net/npm/animejs@3.1.0/lib/anime.min.js
  anime:

  # Internal version: 4.7.0
  # fontawesome: //cdn.jsdelivr.net/npm/font-awesome@4/css/font-awesome.min.css
  # fontawesome: //cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css
  fontawesome:

  # MathJax
  # mathjax: //cdn.jsdelivr.net/npm/mathjax@2/MathJax.js?config=TeX-AMS-MML_HTMLorMML
  # mathjax: //cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML
  # mhchem: //cdn.jsdelivr.net/npm/mathjax-mhchem@3
  # mhchem: //cdnjs.cloudflare.com/ajax/libs/mathjax-mhchem/3.3.0
  mathjax: 
  mhchem: 

  # KaTeX
  # katex: //cdn.jsdelivr.net/npm/katex@0/dist/katex.min.css
  # katex: //cdnjs.cloudflare.com/ajax/libs/KaTeX/0.11.1/katex.min.css
  # copy_tex_js: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.js
  # copy_tex_css: //cdn.jsdelivr.net/npm/katex@0/dist/contrib/copy-tex.min.css
  katex:
  copy_tex_js:
  copy_tex_css:

  # Internal version: 0.2.8
  # pjax: //cdn.jsdelivr.net/gh/theme-next/theme-next-pjax@0/pjax.min.js
  pjax: //cdn.jsdelivr.net/gh/theme-next/theme-next-pjax@0/pjax.min.js

  # FancyBox
  # jquery: //cdn.jsdelivr.net/npm/jquery@3/dist/jquery.min.js
  # fancybox: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.js
  # fancybox_css: //cdn.jsdelivr.net/gh/fancyapps/fancybox@3/dist/jquery.fancybox.min.css
  jquery:
  fancybox:
  fancybox_css:

  # Medium-zoom
  # mediumzoom: //cdn.jsdelivr.net/npm/medium-zoom@1/dist/medium-zoom.min.js
  mediumzoom:

  # Lazyload
  # lazyload: //cdn.jsdelivr.net/npm/lozad@1/dist/lozad.min.js
  # lazyload: //cdnjs.cloudflare.com/ajax/libs/lozad.js/1.9.0/lozad.min.js
  lazyload:

  # Pangu
  # pangu: //cdn.jsdelivr.net/npm/pangu@4/dist/browser/pangu.min.js
  # pangu: //cdnjs.cloudflare.com/ajax/libs/pangu/4.0.7/pangu.min.js
  pangu:

  # Quicklink
  # quicklink: //cdn.jsdelivr.net/npm/quicklink@1/dist/quicklink.umd.js
  quicklink:

  # DisqusJS
  # disqusjs_js: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqus.js
  # disqusjs_css: //cdn.jsdelivr.net/npm/disqusjs@1/dist/disqusjs.css
  disqusjs_js:
  disqusjs_css:

  # Valine
  # valine: //cdn.jsdelivr.net/npm/valine@1/dist/Valine.min.js
  # valine: //cdnjs.cloudflare.com/ajax/libs/valine/1.3.10/Valine.min.js
  valine: 

  # Gitalk
  # gitalk_js: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js
  # gitalk_css: //cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css
  gitalk_js:
  gitalk_css:

  # Algolia Search
  # algolia_instant_js: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.min.js
  # algolia_instant_css: //cdn.jsdelivr.net/npm/instantsearch.js@2/dist/instantsearch.min.css
  algolia_instant_js:
  algolia_instant_css:

  # PDF
  # pdfobject: //cdn.jsdelivr.net/npm/pdfobject@2/pdfobject.min.js
  # pdfobject: //cdnjs.cloudflare.com/ajax/libs/pdfobject/2.1.1/pdfobject.min.js
  pdfobject:

  # Mermaid
  # mermaid: //cdn.jsdelivr.net/npm/mermaid@8/dist/mermaid.min.js
  # mermaid: //cdnjs.cloudflare.com/ajax/libs/mermaid/8.3.0/mermaid.min.js
  mermaid:

  # Internal version: 1.2.1
  # velocity: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.min.js
  # velocity: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.min.js
  # velocity_ui: //cdn.jsdelivr.net/npm/velocity-animate@1/velocity.ui.min.js
  # velocity_ui: //cdnjs.cloudflare.com/ajax/libs/velocity/1.2.1/velocity.ui.min.js
  velocity:
  velocity_ui:

  # Internal version: 1.0.2
  # pace: //cdn.jsdelivr.net/npm/pace-js@1/pace.min.js
  # pace: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/pace.min.js
  # pace_css: //cdn.jsdelivr.net/npm/pace-js@1/themes/blue/pace-theme-minimal.css
  # pace_css: //cdnjs.cloudflare.com/ajax/libs/pace/1.0.2/themes/blue/pace-theme-minimal.min.css
  pace: //cdn.jsdelivr.net/npm/pace-js@1/pace.min.js
  pace_css: //cdn.jsdelivr.net/npm/pace-js@1/themes/blue/pace-theme-minimal.css

  # Internal version: 1.0.0
  # three: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three.min.js
  # three_waves: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/three-waves.min.js
  # canvas_lines: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_lines.min.js
  # canvas_sphere: //cdn.jsdelivr.net/gh/theme-next/theme-next-three@1/canvas_sphere.min.js
  three:
  three_waves:
  canvas_lines:
  canvas_sphere:

  # Internal version: 1.0.0
  # canvas_nest: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest.min.js
  # canvas_nest_nomobile: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-nest@1/canvas-nest-nomobile.min.js
  canvas_nest:
  canvas_nest_nomobile:

  # Internal version: 1.0.0
  # canvas_ribbon: //cdn.jsdelivr.net/gh/theme-next/theme-next-canvas-ribbon@1/canvas-ribbon.js
  canvas_ribbon:

# Assets
css: css
js: js
images: images

# 设置文章结束标签
passage_end_tag:
  enabled: true
  
  
# hexo-neat
# 博文压缩
neat_enable: true
# 压缩html
neat_html:
 enable: true
 exclude:
# 压缩css
neat_css:
 enable: true
 exclude:
   - '*/*.min.css'
# 压缩js
neat_js:
 enable: true
 mangle: true
 output:
 compress:
 exclude:
   - '**/*.min.js'
   - '**/jquery.fancybox.pack.js'
   - '**/index.js'


post_asset_folder: true

# hexo-blog-encrypt
encrypt: 
  abstract: 这篇文章已进行加密，请输入密码。
  message: 请输入密码。
  tags:
  - {name: encryptAsDiary, password: passwordA}
  - {name: encryptAsTips, password: passwordB}
  template: <div id="hexo-blog-encrypt" data-wpm="{{hbeWrongPassMessage}}" data-whm="{{hbeWrongHashMessage}}"><div class="hbe-input-container"><input type="password" id="hbePass" placeholder="{{hbeMessage}}" /><label>{{hbeMessage}}</label><div class="bottom-line"></div></div><script id="hbeData" type="hbeData" data-hmacdigest="{{hbeHmacDigest}}">{{hbeEncryptedData}}</script></div>
  wrong_pass_message: 密码错误，请重新尝试
  wrong_hash_message: Oh, these decrypted content cannot be verified, but you can still have a look.

# hexo-generator-searchdb
search:
  path: search.xml
  field: post
  content: true
  format: html
```