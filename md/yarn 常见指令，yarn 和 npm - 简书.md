\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[www.jianshu.com\](https://www.jianshu.com/p/06f7d1097408)

> 本文章不着重介绍 yarn，而是罗列项目常用的指令，方便在项目快速使用，更多原理另行百度可查

#### 创建一个新项目

```
yarn init
```

接着提示一下

```
name (your-project):
version (1.0.0):
description:
entry point (index.js):
git repository:
author:
license (MIT):
```

生成 package.json 文件

```
{
  "name": "my-new-project",
  "version": "1.0.0",
  "description": "My New Project description.",
  "main": "index.js",
  "repository": {
    "url": "https://example.com/your-username/my-new-project",
    "type": "git"
  },
  "author": "Your Name <you@example.com>",
  "license": "MIT"
}
```

#### 添加、更新、删除依赖

```
yarn / yarn install 一键安装jpackage.json所有包
yarn add \[package\] — 添加包，会自动安装最新版本，注意会覆盖指定版本号！！！
yarn add \[package\]@\[version\] — 带版本号安装
yarn remove \[package\] 移除某个包
yarn upgrade \[package\] 更新一个包
yarn add vue 安装一个包
yarn add vue@2.5.0  安装一个包
yarn upgrade vue 更新一个包
yarn upgrade vue@3.0.0 指定更新某个版本的包
yarn remove vue 

yarn add vue 安装到dependencies
yarn add vue --save-dev 安装到devDependencies
```

#### npm 和 yarn 比较

<table><thead><tr><th>npm</th><th>yarn</th><th>用法</th></tr></thead><tbody><tr><td>npm install</td><td>yarn install</td><td>一键安装 package.json 的所有包</td></tr><tr><td>npm install [package] --save / -S</td><td>yarn add [package]</td><td>安装到 dependencies</td></tr><tr><td>npm install [package] --save-dev/ -D</td><td>yarn add [package] --save-dev</td><td>安装到 devDependencies</td></tr><tr><td>npm i [package]@[版本号]</td><td>yarn add [package]@[版本号]</td><td>指定版本号下载更新</td></tr><tr><td>npm install [package] --global</td><td>yarn global add [package]</td><td>全局安装某个包</td></tr><tr><td>npm update --global</td><td>yarn updade upgrade</td><td>更新所有包</td></tr><tr><td>npm uninstall [package]</td><td>yarn remove [package]</td><td>删除某个包</td></tr></tbody></table>

![](http://upload-images.jianshu.io/upload_images/3029162-b71cccb4632a07ad.png) aonaotu-download.png