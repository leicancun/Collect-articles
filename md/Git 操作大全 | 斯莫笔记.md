> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [notes.zhangxiaocai.cn](https://notes.zhangxiaocai.cn/posts/9f681b8c.html)

[](#Git-完全指南 "Git 完全指南")Git 完全指南
--------------------------------

[](#零、速查表 "零、速查表")零、速查表
-----------------------

### [](#1、底层命令速查 "1、底层命令速查")1、底层命令速查

<table><thead><tr><th>底层命令速查表：</th></tr></thead><tbody><tr><td><strong>git 对象：</strong>（blob 对象）</td></tr><tr><td><code>git hash-object -w file_url</code> 生成一个 key，val 存储到<code>.git/objects</code></td></tr><tr><td><strong>tree 对象：</strong></td></tr><tr><td><code>git update --add --cacheinfo 100644 hash file_name</code> ，表示向暂存区添加一条记录，让 git 对象对应上文件名，并存储到<code>.git/objects</code></td></tr><tr><td><code>git write-tree</code> ，生成树对象存储到<code>.git/objects</code></td></tr><tr><td><strong>commit 对象：</strong></td></tr><tr><td>`echo “first commit”</td></tr><tr><td><strong>查询操作</strong></td></tr><tr><td><code>git cat-file -p hash</code> ，显示 hash 值对应 git 对象的内容</td></tr><tr><td><code>git cat-file -t hash</code> ，显示 hash 值对应 git 对象的类型</td></tr><tr><td><code>git ls-files -s</code>，查看暂存区</td></tr></tbody></table>

### [](#2、Git命令速查 "2、Git命令速查")2、Git 命令速查

初始化

新增或修改操作：

bash

```
#初始化仓库 
git init
```

删除或重命名操作

bash

```
#查看文件状态
git  status 

#添加文件到暂存区
git  add ./ 

#提交到本地仓库
git  commit -m "msg"
```

查询操作

bash

```
#删除文件
git  rm  filename
#重命名文件
git  mv  filename1  filename2

#查看文件状态
git  status

#提交到本地仓库
git  commit -m "msg"
```

### [](#3、分支命令 "3、分支命令")3、分支命令

bash

```
#查看文件状态
git  status 

#查看未暂存的修改
git  diff

#查看位提交暂存
git  diff --cache

#查看提交历史记录
git  log  --oneline
```

[](#一、认识Git "一、认识Git")一、认识 Git
------------------------------

版本控制工具，用来记录文件内容变化的。

版本控制分类：

*   集中式版本控制系统，如`CVS`，`SVN`等都有一个单一集中管理的服务器，保存所有文件的修订版本，每个人都可以看到所有代码，管理员统一管理所有用户相关权限，项目管理方便，但是存在单点故障风险，如果服务器宕机，就无法提交代码协同工作，如果磁盘损坏，会丢失所有历史更新记录。
    
*   分布式版本控制系统，如`Git`，`BitKeeper` 等，客户端并不只是提取最新版版本的文件快照，而是会将代码仓库完整的镜像下来，所需空间相对大一点点。相当于每台电脑都是服务器。每次操作都是对代码仓库完整备份。分布式版本控制系统在管理项目时，存放的不是项目与版本之间的差异，它存的是索引，占用磁盘空间少，每个客户端都有历史记录。如果某个服务器宕机，不影响本地开发，不丢失历史记录。
    

GIT 优点：

​ 完全分布式

缺点：

​ 命令学习掌握

[](#二、Git-安装 "二、Git 安装")二、Git 安装
--------------------------------

### [](#1、安装验证 "1、安装验证")1、安装验证

下载：[https://git-scm.com/downloads](https://git-scm.com/downloads)

安装完成之后验证

Git 操作配置的命令：

一般配置有三大类：

*   **–system** ：系统中对所有用户都普遍适用的配置。使用`git config --system` 命令会修改`/etc/gitconfig`文件。
*   **–global** ：用户目录下的配置文件只适用于该用户。使用`git config --global` 读写的是`~/.gitconfig` 文件
*   不写参数，表示堆当前项目的 git 目录进行配置，使用`git config` 可以直接针对当前项目配置，即工作目录下的`.git/config`文件

优先级别以就近原则为准。

`.git/config` > `~/.gitconfig` > `/etc/gitconfig`

### [](#2、初始化配置 "2、初始化配置")2、初始化配置

安装完成后初始化配置用户名和邮件地址：

bash

```
# 查看完整的分支图
git log --oneline --decorate --graph --all

# 在当前提交对象上创建新的分支
git branch name

# 在指定提交对象（hash）上创建新的分支
git branch name commitHash

# 切换到name分支
git checkout name  

# 删除空的分支，删除已经合并的分支
git branch -d name

# 强制删分支
git branch -D name

# 存储
git stash 

# 查看存储
git stash list

# 应用存储并删除栈
git stash pop
```

查看已有配置：

[](#三、目录结构 "三、目录结构")三、目录结构
--------------------------

初始化工作区命令：

初始化之后，有一个`.git`隐藏文件，里面的目录结构大概如下：

```
git --version
```

<table><thead><tr><th>文件夹</th><th>作用</th></tr></thead><tbody><tr><td>hooks/</td><td>目录包含服务端或客户端的钩子脚本</td></tr><tr><td>info/</td><td>包含一个全局性排除文件</td></tr><tr><td>logs/</td><td>保存日志信息</td></tr><tr><td><mark>objects/</mark></td><td>目录存储所有数据内容，重要</td></tr><tr><td><mark>refs/</mark></td><td>目录存储指向数据提交对象的指针，分支，重要</td></tr><tr><td><mark>config</mark></td><td>文件包含项目特有的配置选项，重要</td></tr><tr><td>description</td><td>用来显示对仓库的描述信息</td></tr><tr><td>HEAD</td><td>文件指示目前被检出的分支，重要</td></tr><tr><td>index</td><td>文件保存暂存区信息，重要</td></tr></tbody></table>

[](#四、Git-原理 "四、Git 原理")四、Git 原理
--------------------------------

三个区域：

*   工作区：沙箱环境 git 不会管理 随便更改操作
*   暂存区：记录文件的操作
*   版本库：最终的代码实现提交到这里 .git 目录就是版本库

![](https://notes.zhangxiaocai.cn/images/git/git-01.jpg)

三个对象

*   Git 对象
*   树对象
*   提交树

### [](#4-1-Git-对象 "4.1 Git 对象")4.1 Git 对象

==**Git 对象** ==

Git 对象是 Git 的核心部分，是一个简单的键值对数据库。可以像该数据库插入任意类型的内容，它会返回一个键值，通过键值可以再次检索内容。

（1）Git 存储

向数据库写入内容并返回对应键值：

bash

```
git  config
```

**`-w`** ：指示 hash-object 命令存储数据对象，如果不指定该参数，则命令仅返回对应键值，不存储数据。

**`--stdin`**：standard input 的缩写，指示该命令从标准输入读取内容，如果不知道该参数，则需要在目录尾部给你待存储文件的路径。

如：

bash

```
git config --global user.name "xiaocai"
git config --global user.email "small-rose@qq.com"
```

（2）查看 Git 存储结构

bash

```
git  config --list
```

Git 的存储，一个文件对应一条内容，校验前两个字符，用于命名子目录，余下的 38 个字符用作文件名。

（3）根据键值拉取数据

bash

```
git init
```

**`-p`**：该参数可以指示该命令自动判断内容的类型，并显示格式友好的内容。

**`-t`**：该参数可以返回该内容的类型，一般是`blob`类型

（4）对一个文件进行简单的版本控制

创建一个新文件并将其内容存入数据库

bash

```
hooks/
ingfo/
objects/
refs/
config
description
HEAD
```

修改文件内容：

修改 1，将原来版本内容替换了

bash

```
echo "xiaocai“ | git hash-object -w --stdin
```

追加文件内容：

bash

```
# 返回对应文件的键值
echo "xiaocai" | git hash-object d:/objects 
a88713553b066c421f74fabac048560b3209c3a8

# 存储文件到/data/.git/objects传递
echo "xiaocai" | git hash-object -w  /data/.git/objects 
a88713553b066c421f74fabac048560b3209c3a8
```

每次存储只有一个文件的版本，不是整个项目版本，Git 对象没有保存文件名，直接保存到本地版本库。

Git 对象主要作用是用来存储数据内容，针对是单个文件的版本快照。

### [](#4-2-树对象 "4.2 树对象")4.2 树对象

== **树对象** ==

树对象（Tree Object）解决文件名保存问题，一般项目会将多个文件组织到一起，Git 就是一种类似 Unix 文件系统的方式存储内容，所有内容均以树对象和数据对象（Git 对象）的形式存储，其中树对象对应了 Unix 的目录项，数据对象（Git 对象）对应文件内容，一个树对象包含一条或多条记录，每条记录含有一个指向 Git 对象或子树对象的`SHA-1`指针，以及相应的模式、类型、文件名信息。一个树对象也可以包含另一个树对象。

> 简单的理解就是针对整个项目（多个文件的）版本快照

（1）查看树对象

bash

```
$ find .git/objects/ -type f
.git/objects/a8/8713553b066c421f74fabac048560b3209c3a8
```

master^{tree} 表示 master 分支上最新的提交锁指向的树对象。

（2）构建树对象

bash

```
# 返回对应文件的内容
$ git cat-file -p a88713553b066c421f74fabac048560b3209c3a8
xiaocai
# 返回对应文件内容的类型
$ git cat-file -t a88713553b066c421f74fabac048560b3209c3a8
blob
```

使用`update-index` 创建暂存区，并使用`write-tree` 生成树对象：

bash

```
# 创建新文件 xctest.txt
echo "version 1" > xctest.txt 
# 将文件存入数据库
git hash-object -w xctest.txt
83baae61804e65cc73a7201a7252750c76066a30 #返回值
# 查看文件内容
git cat-file -p 83baae61804e65cc73a7201a7252750c76066a30
vsersion 1
```

*   文件模式为 100644 表示这是一个普通文件
*   文件模式为 100755 表示这是一个可执行文件
*   文件模式为 120000 表示这是一个符号连接
*   `--add` 因为此前该文件并没有在暂存区中 首次要加 add
*   `--cacheinfo` 因为要添加的文件在 git 数据库中, 没有位于当前目录下，参数表示从数据库拿文件。

**注意：**

`update-index` 没有向本地版本库操作，只是在暂存区里生成了一条记录。

（3）查看暂存区命令

此时执行查看暂存区，里面只有一个文件

bash

```
# 修改原有内容
echo "version 2" > xctest.txt 
# 保存数据
git hash-object -w xctest.txt
1f7a7a472abf3dd9643fd615f6da379c4acb3e3a

# 查看文件内容
git cat-file -p 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a
vsersion 2
```

Git 对象（数据库）里：

bash

```
# 追加内容
echo "version 23" >> xctest.txt 
# 保存到Git数据
git hash-object -w xctest.txt
# 查看文件内容
$ git cat-file -p 0e80f6a3d33fed2e3c7d0b0e0f1eb9edaa5ff4e9
version 2
version 23
# 查看历史版本内容
git cat-file -p 83baae61804e65cc73a7201a7252750c76066a30
vsersion 1
```

（4）使用`write-tree` 生成树对象：

bash

```
git cat-file -p master^{tree}(或者是树对象的hash)
```

再次查看数据库中发现有两个对象：

bash

```
update-index
write-tree
read-tree
```

即：==**`write-tree` 生成树对象时，会将暂存区现有的内容生成一份快照（即项目快照、项目版本），并存储到 Git 数据库中，并且不会清空暂存区。**==

（5）如果后续再次向暂存区操作

bash

```
# 创建暂存区
git update-index --add --cacheinfo 100644\
    83baae61804e65cc73a7201a7252750c76066a30 xctest.txt
```

此时数据库应该有 3 个对象：

bash

```
git ls-files -s
```

（6）再次修改`xctest.txt`

bash

```
# 查看暂存区
git ls-files -s
100644 83baae61804e65cc73a7201a7252750c76066a30 0       xctest.txt
```

此时需要重新生成 hash，保存到数据库

bash

```
$ find .git/objects/ -type f
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30
```

再次查看数据库：

bash

```
# 生成树对象，会保存到数据库
git write-tree    
6e545fd2bd8f012c7c236e7818cabac6b36d9c2a
```

看看暂存区现有的：

bash

```
$ find .git/objects/ -type f
.git/objects/6e/545fd2bd8f012c7c236e7818cabac6b36d9c2a
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30
```

（7）重新加入暂存区

因为`xctest.txt`文件修改了，需要将第二个版本的 hash 重新加入暂存区

bash

```
# 创建新文件
echo "new v1" > new.txt

# 存入到数据库
$ git hash-object -w new.txt
eae614245cc5faa121ed130b4eba7f9afbcc7cd9
```

再次查看暂存区发现 `xctest.txt` 的 hash 重新计算了。

== **暂存区中，文件名字相同，只改变文件的内容，就会重新生成一个 hash**==

bash

```
# 此时数据库有三个对象了
find .git/objects/ -type f
.git/objects/6e/545fd2bd8f012c7c236e7818cabac6b36d9c2a  # 树对象，项目第一个版本
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30  # xctest.txt，第一个版本
.git/objects/ea/e614245cc5faa121ed130b4eba7f9afbcc7cd9  # new.txt，第一个版本
```

新建的文件 `new.txt` 也要加入到暂存区：

bash

```
echo "xiaocai v2" >> xctest.txt
```

此时暂存区情况：

bash

```
$ git hash-object -w xctest.txt
0b6ca5d6025d73d7d62d3c90555add1e8662ab91
```

== **暂存区中，文件名字不相同，就会新增一条新的记录** ==

此时暂存区内容和工作去内容一致，再次执行

bash

```
find .git/objects/ -type f
.git/objects/0b/6ca5d6025d73d7d62d3c90555add1e8662ab91  # xctest.txt的第2个版本(git对象)
.git/objects/6e/545fd2bd8f012c7c236e7818cabac6b36d9c2a  # 项目第1个版本（树对象）
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30  # xctest.txt第1个版本(git对象)
.git/objects/ea/e614245cc5faa121ed130b4eba7f9afbcc7cd9  # new.txt第1个版本(git对象)
```

生成一个新的树对象，即生成了项目第二个版本快照：

bash

```
$ git ls-files -s
100644 83baae61804e65cc73a7201a7252750c76066a30 0       xctest.txt
```

**== 树对象 ==**

此时此刻，执行到这里，数据库里已经有了 2 个项目版本，项目第 1 个版本指向`xctest.txt`第 1 个版本，项目第 2 个版本指向`new.txt`的第 1 个版本和`xctest.txt`的第 2 个版本。

将第一个树对象加入到第二个树对象，使其成为新的树对象

bash

```
# 加入暂存区
git update-index --add --cacheinfo 100644 0b6ca5d6025d73d7d62d3c90555add1e8662ab91 xctest.txt
```

查看暂存区：

bash

```
# 再次查询暂存区
git ls-files -s
100644 0b6ca5d6025d73d7d62d3c90555add1e8662ab91 0       xctest.txt
```

再次生成新的树对象：

bash

```
git update-index --add --cacheinfo 100644 eae614245cc5faa121ed130b4eba7f9afbcc7cd9 new.txt
```

查看类型：

bash

```
$ git ls-files -s
100644 eae614245cc5faa121ed130b4eba7f9afbcc7cd9 0       new.txt
100644 0b6ca5d6025d73d7d62d3c90555add1e8662ab91 0       xctest.txt
```

此时的数据库里：

bash

```
git write-tree
f1fa781509c015b1a1f4c7757cb7e1848d032f6d
```

整个结构为：

第 1 个版本：

txt

```
find .git/objects/ -type f
.git/objects/0b/6ca5d6025d73d7d62d3c90555add1e8662ab91  # xctest.txt的第2个版本(git对象)
.git/objects/6e/545fd2bd8f012c7c236e7818cabac6b36d9c2a  # 项目第1个版本（树对象）
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30  # xctest.txt第1个版本(git对象)
.git/objects/ea/e614245cc5faa121ed130b4eba7f9afbcc7cd9  # new.txt第1个版本(git对象)
.git/objects/f1/fa781509c015b1a1f4c7757cb7e1848d032f6d  # 项目第2个版本（树对象）
```

第 2 个版本：

txt

```
# 将一个树对象读入到暂存区
git read-tree --prefix=bak 6e545fd2bd8f012c7c236e7818cabac6b36d9c2a
```

那么可以推测，第 3 个版本：

txt

```
$ git ls-files -s
100644 83baae61804e65cc73a7201a7252750c76066a30 0       bak/xctest.txt
100644 eae614245cc5faa121ed130b4eba7f9afbcc7cd9 0       new.txt
100644 0b6ca5d6025d73d7d62d3c90555add1e8662ab91 0       xctest.txt
```

问题：无法区分版本做了什么，没有注释。

### [](#4-3-提交对象 "4.3 提交对象")4.3 提交对象

可以通过 commit-tree 命令创建一个提交对象，为此需要指定一个树对象的`SHA-1`值，以及该提交的父提交对象，第一次将暂存区做快照就没有父对象。

**创建提交对象**

bash

```
git write-tree
8ff5b56ab67cbb0336873021cf833b76eafa4067
```

**查看提交对象**

bash

```
git cat-file -p 8ff5b56ab67cbb0336873021cf833b76eafa4067
040000 tree 6e545fd2bd8f012c7c236e7818cabac6b36d9c2a    bak
100644 blob eae614245cc5faa121ed130b4eba7f9afbcc7cd9    new.txt
100644 blob 0b6ca5d6025d73d7d62d3c90555add1e8662ab91    xctest.txt
```

示例：提交刚才的第一个项目版本

bash

```
$ find .git/objects/ -type f
.git/objects/0b/6ca5d6025d73d7d62d3c90555add1e8662ab91  # xctest.txt的第2个版本(git对象)
.git/objects/6e/545fd2bd8f012c7c236e7818cabac6b36d9c2a  # 项目第1个版本（树对象）
.git/objects/83/baae61804e65cc73a7201a7252750c76066a30  # xctest.txt第1个版本(git对象)
.git/objects/ea/e614245cc5faa121ed130b4eba7f9afbcc7cd9  # new.txt第1个版本(git对象)
.git/objects/8f/f5b56ab67cbb0336873021cf833b76eafa4067  # 包含项目第1个版本和第2个版本的树对象
.git/objects/f1/fa781509c015b1a1f4c7757cb7e1848d032f6d  # 项目第2个版本（树对象）
```

查看这个 hash 的信息：

bash

```
tree1 -----> xctest.txt v1
```

再提交项目的第二个版本

bash

```
+------> tree1 -----> xctest.txt v1
           |
tree2 -----+------> xctest.txt v2
           |
           +------> new.txt v1
```

此时的`-p` 表示指定当前提交对象的父对象 hash。

再次查看当前对象：

bash

```
+------> tree1 -----> xctest.txt v1
                         |
      +-----> tree2 -----+------> xctest.txt v2
      |                  |
      |                  +------> new.txt v1
tree3 +                    
      |
      +------ xctest.txt v3
```

里面还包含了树对象，和父级提交对象，提交信息，注释。

![](https://notes.zhangxiaocai.cn/images/git//git-demo-01.png)

Git 的版本控制中，真正代表项目版本的是提交对象，而项目版本快照的真正本质是树对象。提交对象是对树对象的一层封装，并且提交对象是链式的，可以将版本进行串起来，Git 的每次版本提交都不是增量，而是快照。

如果要进行跳跃版本切换，可以直接切换对应提交对象的 hash。

**== 一次完整的项目提交 包括至少一个提交对象 一个树对象 0 或多个 git 对象 ==**

[](#五、Git-基础命令 "五、Git 基础命令")五、Git 基础命令
--------------------------------------

### [](#1、git-init "1、git init")1、git init

**== 初始化工作空间 ==**

初始化工作目录命令格式：

生成 `.git` 目录，所有 git 需要的数据和资源都存在在这个目录。

### [](#2、git-add "2、git add")2、git add

**== 跟踪已修改文件到暂存区：==**

跟踪一个已修改文件到暂存区的命令格式：

git add 命令将修改的文件生成 git 对象，加入暂存区。

过程：将将修改的文件生成成 git 对象，放入版本库，再将 Git 对象加入到暂存区，只是没有生成树对象。在这个过程中，生成 Git 对象是增量式的。

相当于执行了 N 次（N 个文件）：

```
# 返回提交对象的hash
echo "first commit" | git commit-tree <hash>
```

### [](#3、git-status "3、git status")3、git status

**== 跟踪文件状态：==**

status ：

*   `untracked`：未跟踪，红色
    
*   `tracked` ：已跟踪。
    
    *   `unmodified`：未修改，已提交，一般不列出显示。
*   `modified`：已修改，红色
    
    *   `staged` ： 已暂存，绿色

**== 跟踪新文件：==**

`git add` 命令执行之后使用 `git status`查看，出现`changes to be committed` 表示已经暂存。

**== 暂存已修改文件：==**

已经暂存的文件进行再次修改，使用 `git status`查看，此时会出现

`changes to be committed` 表示该文件之前暂存区有一份，表示已暂存；同时也会出现

`changes not staged for commit` 表示改文件又有了新的修改。此时已修改文件的状态为`modified`；修改之后的 git 对象还没有生成。如果`git add` 重新暂存，在暂存区则会进行覆盖操作，并重新生成 git 对象的 hash。

### [](#4、git-diff "4、git diff")4、git diff

**== 查看已暂存和未暂存的更新：==**

`git status` 仅仅列出修改过的文件。

*   判断当前做的哪些更新还没有做暂存：

*   判断哪些更新已经暂存准备好了下次提交

bash

```
git cat-file -p <hash>
```

示例：查看哪些暂存还没提交的数据，这是之前操作的数据。

bash

```
echo "first commit" | git commit-tree 6e545fd2bd8f012c7c236e7818cabac6b36d9c2a
6d8d40d59a48e33fd334ebabffe3e8cb89308f21
```

### [](#5、git-commit "5、git commit")5、git commit

**== 提交文件：==**

没有参数会进入一个注释文件可以写大段注释。

bash

```
#查看类型：
git cat-file -t 6d8d40d59a48e33fd334ebabffe3e8cb89308f21
commit

# 查看信息
$ git cat-file -p 6d8d40d59a48e33fd334ebabffe3e8cb89308f21
tree 6e545fd2bd8f012c7c236e7818cabac6b36d9c2a
author small-rose <small-rose@qq.com> 1605513658 +0800
committer small-rose <small-rose@qq.com> 1605513658 +0800

first commit
```

`-m` 一般写短小文字较少的注释。注释建议，带上关键信息，如完成进度，fix bug

2 条命令都是提交项目版本到本地库，生成树对象和提交对象。

相当于执行：

bash

```
# 再次提交
echo "second commit" | git commit-tree f1fa781509c015b1a1f4c7757cb7e1848d032f6d -p 6d8d40d59a48e33fd334ebabffe3e8cb89308f21
# 返回了当前提交对象hash
ca6961bbf978608e602b060d6c4a7a79cb0041c5
```

**== 跳过使用暂存区域：==**

bash

```
git cat-file -p ca6961bbf978608e602b060d6c4a7a79cb0041c5
tree f1fa781509c015b1a1f4c7757cb7e1848d032f6d
parent 6d8d40d59a48e33fd334ebabffe3e8cb89308f21
author small-rose <small-rose@qq.com> 1605514000 +0800
committer small-rose <small-rose@qq.com> 1605514000 +0800

second commit
```

通过`-a` 参数，git 可以自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过`git add`步骤。

注意：== 使用 -a 的前提是文件状态要已经被跟踪。==

### [](#6、git-rm "6、git  rm")6、git rm

**== 移除文件：==**

从 Git 中移除文件，就必须要从已跟踪文件清单中注册删除，其实就是从暂存区注册删除，然后提交。可以使用以下命令完成：

该命令将把文件从暂存区注册删除，并且同时从工作目录删除对应的文件，这样文件就不会出现在未跟踪文件清单中。

需要注意的是，删除之后进行`git add` 和 `git commit`操作，对应的 Git 对象永远不会删除，暂存区删除之后，版本库里进行的是新增操作，新增的是一个没有内容的 git 对象和一个树对象。如果要找回，可以找到对应的提交对象 hash，回退即可。

如果我们先手工删除了文件，可以执行`git rm` 即可，相当于执行了`git add ./` 和 `git commit` 。也可以手工执行

bash

```
git init
```

==`git rm` 其实就是删除工作目录中对应的文件，再将修改添加到暂存区。==

### [](#5、git-mv "5、git  mv")5、git mv

**== 文件改名：==**

git 文件修改文件名称命令

bash

```
git add ./
```

使用，新建一个文件然后提交：

bash

```
git hash-object -w 
git update-index
```

`git rm` 在旧的版本中类似相当于执行了三条命令：

bash

```
git status [指定的文件]
```

我的 git 版本比较新，新的版本 status 显示的是 renamed，暂时没注意过程，后续清楚了再补上。**==`TODO`==**

查看状态，此时是 renamed 状态，属于修改操作，

bash

```
git diff
```

==**`git mv file1 file2`** 其实就是将工作目录中的文件进行重命名，再将修改添加到暂存区。==

### [](#8、git-log "8、git log")8、git log

**== 查看历史记录：==**

在提交很多更新之后，想回顾查看提交历史，或者回退历史版本时，使用该命令。

没有参数会按提交时间列出所有更新，最近在上面，倒序排列。

示例：

bash

```
git diff --cached

# 1.6 以上
git diff --staged
```

按下箭头翻页， 按 `q` 退出。如果要回退，利用提交对象的 hash 即可。

不方便看还可以进行格式化显示：

bash

```
git diff --cached
diff --git a/bak/xctest.txt b/bak/xctest.txt
new file mode 100644
index 0000000..83baae6
--- /dev/null
+++ b/bak/xctest.txt
@@ -0,0 +1 @@
+version 1
diff --git a/new.txt b/new.txt
new file mode 100644
index 0000000..eae6142
--- /dev/null
+++ b/new.txt
@@ -0,0 +1 @@
+new v1
diff --git a/xctest.txt b/xctest.txt
new file mode 100644
index 0000000..0b6ca5d
--- /dev/null
+++ b/xctest.txt
@@ -0,0 +1,2 @@
+version 1
+xiaocai v2
```

效果：

bash

```
git commit
```

[](#六、Git-分支 "六、Git 分支")六、Git 分支
--------------------------------

Git 分支模型高效轻量。Git 亮点技能。

分支就是一个提交对象前面的指针，每次提交完成，指针就在提交对象的前面指向最新提交。

### [](#1、创建分支 "1、创建分支")1、创建分支

基础命令

没有参数时，显示分支列表。

后面带参数时，表示创建分支命令：

执行之后，查看日志：

bash

```
git commit -m " messgae info"
```

新建新的分支并切换到该分支上（一步到位式）

bash

```
git write-tree
git commit-tree
```

执行结果：

bash

```
git commit -a -m "xiaocai test"
```

再查看分支图：

bash

```
git rm
```

可以看到`HEAD` 已经指向了`dev_test`，并且创建新的`dev_test`分支是基于`master`分支创建的，表示创建并切换分支成功。

### [](#2、切换分支 "2、切换分支")2、切换分支

切换之后，可以看到路径变化：`~/Desktop/test (dev)`

执行之后，查看日志：

bash

```
git add ./
git commit`
```

在新的`dev` 分支进行操作开发

bash

```
# 重命名操作
git mv oldfile.suffix1  newfile.suffix2
```

执行之后，查看日志：

bash

```
# 新建xiaocai.txt
echo "xiaocai de wen jian" > xiaocai.txt

#git add
git commit -a -m "new a file test"

# 再执行重命名操作
git mv xiaocai.txt  xc.txt
```

此时 HEAD 指针跟着`dev` 分支前进了。

****注意****：**== 分支切换会改变工作目录中的文件，在切换分支时，一定要注意你工作目录里的文件会被改变。如果是切换到一个比较旧的分支，工作目录会恢复到该分支最后一次提交时的样子。如果 Git 不能完整这个切换工作，它将禁止切换分支。==**

最佳实践注意事项：

（1）每次切换分支前，当前分支一定是干净的（所有文件都是已提交状态）。所以在切换分支前使用`git status` 命令验证状态。

（2）问题发生于在切换分支时，如果当前分支上有未暂存的修改（一般是第一次）或者有未提交的暂存（一般是第一次），分支可以切换成功，但是会对其他分支造成污染。

### [](#3、删除分支 "3、删除分支")3、删除分支

删除之前一定要先切换分支

切换成功后，显示 master 分支

bash

```
mv xiaocai.txt  xc.txt
git rm  xiaocai.txt
git add  xiaocai.txt
```

删除分支命令：

### [](#4、其他分支相关 "4、其他分支相关")4、其他分支相关

查看每个分支最后一次提交：

新建一个分支并且使分支指向对应的提交对象：【时光机，版本穿梭】

bash

```
git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        renamed:    xiaocai.txt -> xc.txt
```

示例：

bash

```
git log
```

现在创建一个分支想回第一次提交的时候看看代码怎么写的：

bash

```
$ git log
commit c32a601099e6ca73b910829856bc4b1ba88c014e (HEAD -> master)
Author: small-rose <small-rose@qq.com>
Date:   Mon Nov 16 19:57:12 2020 +0800

    rename xiaocai.txt to xc.txt

commit d57678e00b1dea5ce92817f5ca495c2dc852496c
Author: small-rose <small-rose@qq.com>
Date:   Mon Nov 16 19:54:07 2020 +0800

    new a file test

commit 4e84326e84545905f106975a4ce32eb520b4bc98
Author: small-rose <small-rose@qq.com>
Date:   Mon Nov 16 19:46:44 2020 +0800

    first commit
```

此时新的 first 分支语句出现了，可以切换过去看看：

bash

```
git log --pretty=oneline
git log --oneline
```

查看哪些分支已经合并到当前分支：

在这个列表中分支名字前面没有`*`号的分支通常可以使用`git branch -d` 删除掉。

查看所有包含未合并工作的分支：

bash

```
$ git log --pretty=oneline
c32a601099e6ca73b910829856bc4b1ba88c014e (HEAD -> master) rename xiaocai.txt to xc.txt
d57678e00b1dea5ce92817f5ca495c2dc852496c new a file test
4e84326e84545905f106975a4ce32eb520b4bc98 first commit


$ git log --oneline
c32a601 (HEAD -> master) rename xiaocai.txt to xc.txt
d57678e new a file test
4e84326 first commit
```

尝试使用`git branch -d` 删除在这个列表中的分支时会失败。

如果真的确定要删除分支，可以使用`git branch -D` 进行强制删除。

**== 分支的本质是一个提交对象，HEAD 是一个指针，它默认指向 master，切换分支时，其实就是让 HEAD 指向不同的分支。每次有新的提交时，HEAD 都会带着当前指向的分支一起往前移动。==**

### [](#5、撤销与重置 "5、撤销与重置")5、撤销与重置

**== 撤销命令 ==**

该命令将暂存区的文件体积，如果上次提交以来你还未做任何修改，在杀你提交后马上执行此命令，那么快照会保持不变，而你锁修改的只是提交信息。

如果提交后发现忘记了暂存某些需要的修改，可以像下面这样操作：

bash

```
git branch
```

最终只会有一个提交，第二次提交将代替第一次提交的结果。

**== 重置命令 ==**

### [](#6、配置别名 "6、配置别名")6、配置别名

**== 配置别名 ==**

Git 没有自动推断命令功能，有些命令比较长，不想每次输入完整的命令，可以通过`git config`文件来轻松为每个命令设置一个别名。

```
git branch  dev
```

如果需要执行`git commit` 只需要输入 `git cm` 即可。

对于复杂命令，比如查看完整的分支图的命令：

bash

```
git log --oneline
c32a601 (HEAD -> master, dev) rename xiaocai.txt to xc.txt
d57678e new a file test
4e84326 first commit
```

执行结果：

bash

```
git checkout -b  dev_test
```

将该命令配置别名时需要带上双引号：

```
$ git checkout -b  dev_test
Switched to a new branch 'dev_test'
```