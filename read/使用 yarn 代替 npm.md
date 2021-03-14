> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [juejin.cn](https://juejin.cn/post/6844903507212894216) npm 命令 yarn 命令 描述 npm init yarn init 初始化一个新项目 npm install yarn install 根据 pageage.json 来安装项目 npm install --global [package] yarn global add [package] 全局安装一个 package npm install [--save]/[--save-dev] yarn add /[-dev] 添加项目依赖 / 开发依赖 npm run yarn run 运行 package.json 中的 script

基本命令就这几个，有一些 npm 有缩写，自行查阅。（以下并无卵用，因为准备放弃使用 npm）  
比如：

1.  `npm install`都可以写成`npm i`
2.  `npm --global` 可以简写成 `npm -g`
3.  `npm install XXX --save` 可以简写成`npm i XXX -S` --------> 安装项目依赖
4.  `npm install XXX --save-dev`可以简写成`npm i XXX -D` ------> 安装开发依赖

yarn 的简写比较少，很可能是我不知道。就是把`yarn install`简写为`yarn`，依照 yarn.lock 或 package.json 里面的依赖顺序来安装模块。

yarn.lock
---------

官网说的已经很清楚了，可以去 [yarn.lock](https://yarn.bootcss.com/docs/yarn-lock.html) 看看。

所有 yarn.lock 文件都应该被提交到版本控制系统，这样可以帮助 yarn 在所有机器上安装完全相同的依赖树。npm5.0 以上的版本也加入的这个功能，叫`package-lock.json`。

锁定版本的好处就是依赖版本相同，可以避免好多在这台电脑上能运行，但是到了另外一台可能都 run 不起来这种尴尬的事情。

结论
--

使用 yarn 比 npm 快，cnpm 容易丢失依赖，所以懒得比。锁定版本很好用，所有人用同一个版本的依赖美滋滋。

其实使用 yarn 最好的地方就是官网，建议一定要去看。好像没说这怎么安装`npm i yarn -g`或者按照官网的方法装吧。