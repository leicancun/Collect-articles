\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[sitoi.cn\](https://sitoi.cn/posts/15908.html#%E5%88%9B%E5%BB%BA-GitHub-Action)

遇到任何问题，优先在本页面搜索，看看是否已经有该配置教程；  
不懂得可以百度或者 Google；  
还有弄不明白的可以在本站点留言，或添加站长 Wechat、QQ 等

文档目录

[环境准备](https://sitoi.cn/posts/6666.html)  
[搭建基础](https://sitoi.cn/posts/27801.html)  
[主题配置](https://sitoi.cn/posts/63466.html)  
[主题优化 - 添加 PWA](https://sitoi.cn/posts/49115.html)  
[自动部署](https://sitoi.cn/posts/15908.html)

[](#前言 "前言")前言
--------------

本文教程教你实现，如何将你的 Hexo 博客自动部署到多个平台

*   GitHub
*   GitLab
*   Coding
*   Gitee

优点：

*   编写文章，推送到 `GitHub` 即可实现自动部署
*   利用 `GitHub` 的私有仓库将博客源码直接保存在 `GitHub` 上

[](#准备 "准备")准备
--------------

1.  `Hexo` 博客源码的仓库，在 `GitHub` 上。
2.  `ssh` 密钥，参考文章：[Windows 下利用 Git 生成 SSH KEY 并配置到 GitHub](https://sitoi.cn/posts/43508.html)

[](#步骤 "步骤")步骤
--------------

1.  为需要部署的平台添加密钥
2.  修改 `_config.yml` 中的 `deploy` 配置
3.  在 GitHub 上设置 `Secrets`
4.  创建 GitHub Action

[](#为需要部署的平台添加密钥 "为需要部署的平台添加密钥")为需要部署的平台添加密钥
--------------------------------------------

按照之前的教程，只要你之前成功将 Hexo 的博客部署到 GitHub 上，那你电脑在 `~/.ssh` 目录下一定有以下三个文件：

*   `id_rsa`：私钥
*   `id_rsa.pub`：公钥
*   `known_hosts`：记录对所有用户都可信赖的远程主机的公钥

将 `id_rsa.pub`（公钥）添加到不同平台中即可，参考文章：[Windows 下利用 Git 生成 SSH KEY 并配置到 GitHub](https://sitoi.cn/posts/43508.html#%E6%9F%A5%E7%9C%8B-SSH-KEY)

下面是不同平台添加的地址：

*   [GitHub](https://github.com/settings/ssh/new)
*   [GitLab](https://gitlab.com/profile/keys)
*   [Coding](https://e.coding.net/)
*   [Gitee](https://gitee.com/profile/sshkeys)

[](#修改-config-yml-中的-deploy-配置 "修改 _config.yml 中的 deploy 配置")修改 `_config.yml` 中的 `deploy` 配置
--------------------------------------------------------------------------------------------

请使用 `ssh` (即以 `git@` 开头的 `clone` 链接) 的连接方式，根据直接的实际地址填写。

yaml

```
deploy:
  - type: git
    repo:
      github: git@github.com:Sitoi/Sitoi.github.io.git
      coding: git@e.coding.net:Sitoi/Sitoi.git
      gitee: git@gitee.com:sitoi/sitoi.git
      gitlab: git@gitlab.com:Sitoi/sitoi.gitlab.io.git
    branch: master
```

[](#在-GitHub-上设置-Secrets "在 GitHub 上设置 Secrets")在 GitHub 上设置 `Secrets`
----------------------------------------------------------------------

1.  进入到你在 `GitHub` 上面的源码仓库
    
2.  点击右上角的 `Settings`
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/repos_settings.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/repos_settings.png)
    
    Settings
    
3.  点击左侧的 `Secrets`
    
4.  点击右上角的 `New secret`
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/secrets.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/secrets.png)
    
    New secret
    
5.  在 `Name` 中输入 `HEXO_DEPLOY_PRI`，在 `Value` 中填入 `id_rsa`（私钥）的全部内容
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/add_secret.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/add_secret.png)
    
    Add secret
    

[](#创建-GitHub-Action "创建 GitHub Action")创建 GitHub Action
--------------------------------------------------------

1.  点击项目上方的 `Action` 按钮
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/action.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/action.png)
    
    Action
    
2.  点击 `set up a workflow yourself` 创建 `Workflow`
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/workflow.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/workflow.png)
    
    Workflow
    
3.  修改 `main.yaml` 的内容
    
    [![](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/create_workflow.png)](https://cdn.jsdelivr.net/gh/Sitoi/cdn/img/hexo/create_workflow.png)
    
    Create Workflow
    
    > 根据实际情况修改成你自己的内容
    
    *   Git 推送使用的用户名：git config –global user.name ‘sitoi’：
        
    *   Git 推送使用的邮箱：git config –global user.email ‘133397418@qq.com’
        
    *   Hexo 的版本：npm i [hexo@4.1.1](mailto:hexo@4.1.1) -g
        
        yaml
        
        ```
        name: Hexo CI
        
        on:
          push:
            branches:
              - butterfly
        
        jobs:
          butterfly-build:
        
            runs-on: ubuntu-latest
        
            strategy:
              matrix:
                node-version: \[10.x\]
        
            steps:
              - uses: actions/checkout@v1
              - name: Use Node.js 10.x
                uses: actions/setup-node@v1
                with:
                  node-version: '10.x'
              - name: env prepare
                env:
                  HEXO\_DEPLOY\_PRI: ${{ secrets.HEXO\_DEPLOY\_PRI }}
                run: |
                  mkdir -p ~/.ssh/
                  echo "$HEXO\_DEPLOY\_PRI" > ~/.ssh/id\_rsa
                  chmod 600 ~/.ssh/id\_rsa
                  ssh-keyscan github.com >> ~/.ssh/known\_hosts
                  ssh-keyscan gitlab.com >> ~/.ssh/known\_hosts
                  ssh-keyscan e.coding.net >> ~/.ssh/known\_hosts
                  ssh-keyscan gitee.com >> ~/.ssh/known\_hosts
                  git config --global user.name 'sitoi'
                  git config --global user.email '133397418@qq.com'
                  npm i
                  npm i hexo@4.1.1 -g
              - name: gen
                run: |
                  hexo clean
                  hexo generate
                  hexo deploy
        ```
        
4.  将你的源码推送到 `GitHub` 上，你的博客一会就会自动更新了。