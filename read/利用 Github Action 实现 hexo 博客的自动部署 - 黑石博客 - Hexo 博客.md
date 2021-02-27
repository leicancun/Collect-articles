> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.heson10.com](https://www.heson10.com/posts/61031.html)

[](#Hexo-博客的Github-Action自动化部署是什么？ "Hexo 博客的Github Action自动化部署是什么？")Hexo 博客的 Github Action 自动化部署是什么？
----------------------------------------------------------------------------------------------------

简单说，就是把 hexo 博客的源代码上传到 github 代码仓库，github 在代码发生变动的时候，自动通过安装一系列 nodejs 环境和相关依赖，生成 html 页面到 github pages 仓库。

再简单点说，就是把本地生成博客的工作，全部交给 github 执行。

[](#这样做好处是什么？ "这样做好处是什么？")这样做好处是什么？
-----------------------------------

*   省去生成 html 的时间
*   ☆随时随地都能修改或增加博文（重点，可以看到我的导航栏页面里面有一个`撰写`栏目，如下图）

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201120201912173.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201120201912173.png "黑石博客撰写栏目")

*   备份了你的源代码

[](#前言 "前言")前言
--------------

网上这种教程一大堆，有的装了插件不一样（gulp 等等），有的部署方法（ssh、令牌）不一样，以至于自动化部署的文件写法也不一样。

我这里尽量写一个适合小白和大多数 hexo 博客的一个自动化部署的教程。

**总体步骤**：

*   使用 Github 令牌部署 hexo 博客
*   Github 新建一个私有仓库，并上传 hexo 博客源码
*   配置 Github Action 实现自动化部署

[](#使用Github令牌部署hexo博客 "使用Github令牌部署hexo博客")使用 Github 令牌部署 hexo 博客
------------------------------------------------------------------

使用 Github 令牌部署的好处就是不用重复部署 ssh 密钥环境，换了电脑、电脑重装也不用重新配置。

### [](#github令牌获取 "github令牌获取")github 令牌获取

*   登陆 GitHub，右上角设置
    
    [![](https://pic.heson10.com/img/image-20200727123742808.png)](https://pic.heson10.com/img/image-20200727123742808.png "image-20200727123742808")
    
    [![](https://pic.heson10.com/img/image-20200727123819255.png)](https://pic.heson10.com/img/image-20200727123819255.png "image-20200727123819255")
    
    [![](https://pic.heson10.com/img/image-20200727123858727.png)](https://pic.heson10.com/img/image-20200727123858727.png "image-20200727123858727")
    
*   输入密码后创建一个全权限的 token，名称随意
    
    [![](https://pic.heson10.com/img/image-20200727124017855.png)](https://pic.heson10.com/img/image-20200727124017855.png "image-20200727124017855")
    

### [](#更改根目录配置deploy的仓库地址 "更改根目录配置deploy的仓库地址")更改根目录配置 deploy 的仓库地址

记录好此 token，后面放在配置文件里面 GitHub 的推送代码就是：

[![](https://pic.heson10.com/img/image-20200727124518685.png)](https://pic.heson10.com/img/image-20200727124518685.png "image-20200727124518685")

比如我的 github pages 仓库 https 地址是：

```
https://github.com/heson10/heson10.github.io.git
```

那么我在根目录配置文件中的`deploy`设置令牌部署地址则为：

```
https://令牌@github.com/heson10/heson10.github.io.git
```

[](#Github新建一个私有仓库，并上传hexo博客源码 "Github新建一个私有仓库，并上传hexo博客源码")Github 新建一个私有仓库，并上传 hexo 博客源码
-----------------------------------------------------------------------------------------

### [](#新建一个仓库，如图 "新建一个仓库，如图")新建一个仓库，如图

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122000503211.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122000503211.png "新建一个私有仓库")

### [](#上传hexo博客源码 "上传hexo博客源码")上传 hexo 博客源码

在博客源码中删除`.git`文件夹 (隐藏文件夹)，删除主题目录`.git`文件夹

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122001214227.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122001214227.png "删除git文件夹")

根目录输入以下命令

```
git initgit add .git commit -m "first commit"git branch -M maingit remote add origin https://github.com/用户名/新建的私有仓库名.git（私有仓库的地址）git push -u origin main
```

提交过程中会要求输入用户名和密码，输入即可。

提交完毕后，仓库代码如图：

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122001847923.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122001847923.png "私有仓库上传后")

[](#配置Github-Action实现自动化部署 "配置Github Action实现自动化部署")配置 Github Action 实现自动化部署
----------------------------------------------------------------------------

### [](#新建workflow "新建workflow")新建 workflow

点击博客源码仓库的`Action`

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122002117053.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122002117053.png "image-20201122002117053")

### [](#配置action "配置action")配置 action

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122002425835.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122002425835.png "image-20201122002425835")

代码如下（记得修改自己的地址）：

```
name: Deploy # 部署 on: # 触发条件  push:    branches:      - main # 推送到 main 分支（这里的分支名很重要，不要弄错了）   release:    types:      - published # 推送新版本号   workflow_dispatch: # 手动触发 jobs:  build:    runs-on: ubuntu-latest     steps:    - name: Checkout # Checkout 仓库      uses: actions/checkout@v2      with:        ref: main     - name: Setup Node # 安装 Node.js      uses: actions/setup-node@v1      with:        node-version: "12.x"     - name: Install Hexo # 安装 Hexo      run: |        npm install hexo-cli -g     - name: Cache Modules # 缓存 Node 插件      uses: actions/cache@v1      id: cache-modules      with:        path: node_modules        key: ${{runner.OS}}-${{hashFiles('**/package-lock.json')}}     - name: Install Dependencies # 如果没有缓存或 插件有更新，则安装插件      if: steps.cache-modules.outputs.cache-hit != 'true'      run: | # **如果仓库里没有 package-lock.json，上传一下，npm ci 必须要有 package-lock.json**        npm ci    - name: Generate # 生成      run: |        hexo clean        hexo generate     - name: Deploy # 部署      run: |        git config --global user.name "GitHub用户名"        git config --global user.email "GitHub邮箱"        git clone https://github.com/heson525/heson525.github.io.git（换成自己的GitHub pages地址） .deploy_git        export TZ='Asia/Shanghai'        hexo deploy
```

### [](#查看状态 "查看状态")查看状态

点击 action 即可看到部署状态

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122003418494.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122003418494.png "image-20201122003418494")

[![](https://picup.heson10.com/img/upyun/2020/11/image-20201122003452614.png)](https://picup.heson10.com/img/upyun/2020/11/image-20201122003452614.png "image-20201122003452614")

这样就代表自动部署成功了。

[](#如何使用 "如何使用")如何使用
--------------------

平时我在自己的电脑里写了文章后，使用这三条命令，直接推送修改的文件到博客源码仓库，后面就会自动部署

```
git add .git commit -m "增加博文"git push
```

也可直接在源码仓库的`source/_post`文件夹里面直接添加`markdown`文件，进行写博文

[](#结束语 "结束语")结束语
-----------------

基本步骤就是这样，**总体步骤**：

*   使用 Github 令牌部署 hexo 博客
*   Github 新建一个私有仓库，并上传 hexo 博客源码
*   配置 Github Action 实现自动化部署

有问题请留言。如有错误，欢迎指正。