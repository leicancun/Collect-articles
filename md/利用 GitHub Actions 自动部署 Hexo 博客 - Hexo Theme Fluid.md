\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[hexo.fluid-dev.com\](https://hexo.fluid-dev.com/posts/actions-deploy/)

[](#前言 "前言")前言[](#前言)
---------------------

本文主要讲如何应用于 Hexo 部署中，如果还不太熟悉 GitHub Actions 可以看[这篇文章](https://zkqiang.cn/posts/e8ed6836/)，简单地说 Actions 就是在设定的时机触发创建一个虚拟云环境，然后执行一连串动作，从而实现自动部署的功能。

[](#创建工作流 "创建工作流")创建工作流[](#创建工作流)
---------------------------------

首先要保证你的 Hexo 博客项目是全部提交到 GitHub 仓库中，然后在博客目录下创建 `.github/workflows/xxx.yml` 文件，文件名任意。

文件内容如下，根据自己的需求增删 step：

```
name: Deploy                      # Actions 显示的名字，随意设置

on: \[push\]                        # 监听到 push 事件后触发

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - name: Checkout              # 拉取当前执行 Actions 仓库的指定分支
      uses: actions/checkout@v2
      with:
        ref: master

    - name: Update Submodule      # 如果仓库有 submodule，在这里更新，没有则删掉此步骤
      run: |
        git submodule init
        git submodule update --remote

    - name: Setup Node            # 安装 Node 环境
      uses: actions/setup-node@v1
      with:
        node-version: "10.x"

    - name: Hexo Generate         # 安装 Hexo 依赖并且生成静态文件
      run: |
        rm -f .yarnclean
        yarn --frozen-lockfile --ignore-engines --ignore-optional --non-interactive --silent --ignore-scripts --production=false
        rm -rf ./public
        yarn run hexo clean
        yarn run hexo generate

    - name: Hexo Deploy           # 部署步骤，这里以 hexo deploy 为例
      env:
        SSH\_PRIVATE: ${{ secrets.SSH\_PRIVATE }}
        GIT\_NAME: yourname
        GIT\_EMAIL: your@email.com
      run: |
        mkdir -p ~/.ssh/
        echo "$SSH\_PRIVATE" | tr -d '\\r' > ~/.ssh/id\_rsa
        chmod 600 ~/.ssh/id\_rsa
        ssh-keyscan github.com >> ~/.ssh/known\_hosts
        git config --global user.name "$GIT\_NAME"
        git config --global user.email "$GIT\_EMAIL"
        yarn run hexo deploy
```

只要配置了 hexo deploy 的都可以通过上面这种方式部署，注意如果是在其他 Pages 部署（比如 Coding Pages 或者 码云 Pages），`ssh-keyscan` 需要进行增改：

```
\# github、gitee 和 coding 三种 Pages 的示例，根据需求替换上例中语句，需要注意的是 coding 是使用二级域名。
ssh-keyscan github.com >> ~/.ssh/known\_hosts
ssh-keyscan gitee.com >> ~/.ssh/known\_hosts
ssh-keyscan e.coding.net >> ~/.ssh/known\_hosts
```

然后 `${{ secrets.SSH_PRIVATE }}` 这种调用方式，需要提前在下图中设置常量：

[![](https://rmt.dogedoge.com/fetch/fluid/storage/actions-deploy/1.png?w=1280&fmt=webp)](https://rmt.dogedoge.com/fetch/fluid/storage/actions-deploy/1.png?w=1280&fmt=webp)

这样做可以避免敏感数据放在 yml 文件中被泄漏，即使你是私有仓库也建议这样做，因为设置的常量是无法被二次查看的，就算你账号被盗也不用担心。

[](#常用步骤配置 "常用步骤配置")常用步骤配置[](#常用步骤配置)
-------------------------------------

以上是以部署 hexo deploy 为例，下面再提供几种其他常见的部署配置，注意修改你自己的变量参数。

### [](#阿里云-OSS "阿里云 OSS")阿里云 OSS[](#阿里云-OSS)

```
\- name: Deploy to OSS
  env:
    OSS\_AccessKeyID: ${{ secrets.ACCESS\_KEY\_ID }}
    OSS\_AccessKeySecret: ${{ secrets.ACCESS\_KEY\_SECRET }}
    OSS\_EndPoint: oss-ap-southeast-1.aliyuncs.com
    OSS\_Bucket: fluid-dev
  run: |
    wget -q http://gosspublic.alicdn.com/ossutil/1.6.10/ossutil64
    chmod +x ./ossutil64
    ./ossutil64 config -e $OSS\_EndPoint -i $OSS\_AccessKeyID -k $OSS\_AccessKeySecret -L CH
    ./ossutil64 rm -r -f oss://$OSS\_Bucket/
    ./ossutil64 cp -r -f ./public oss://$OSS\_Bucket/
```

### [](#腾讯云-COS "腾讯云 COS")腾讯云 COS[](#腾讯云-COS)

```
\- name: Deploy to COS
  uses: zkqiang/tencent-cos-action@v0.1.0
  with:
    args: delete -r -f / && upload -r ./public/ /
    secret\_id: ${{ secrets.SECRET\_ID }}
    secret\_key: ${{ secrets.SECRET\_KEY }}
    bucket: ${{ secrets.BUCKET }}
    region: ap-shanghai
```

### [](#腾讯云开发 "腾讯云开发")腾讯云开发[](#腾讯云开发)

```
\- name: Deploy to Tencent CloudBase
  uses: TencentCloudBase/cloudbase-action@v1.1.1
  with:
    secretId: ${{ secrets.SECRET\_ID }}
    secretKey: ${{ secrets.SECRET\_KEY }}
    envId: ${{ secrets.ENV\_ID }}
    staticSrcPath: ./public
```

### [](#服务器 "服务器")服务器[](#服务器)

如果是直接部署在服务器上，需要通过 FTP/SFTP 协议来完成上传操作，因此确保你的服务器开启了 FTP 服务。

```
\- name: Deploy to Server
  uses: SamKirkland/FTP-Deploy-Action@3.1.1
  with:
    ftp-server: ${{ secrets.FTP\_SERVER }}      # eg: ftp://ftp.xxx.com:22/mypath
    ftp-username: ${{ secrets.FTP\_USERNAME }}
    ftp-password: ${{ secrets.FTP\_PASSWORD }}
    local-dir: ./public
```