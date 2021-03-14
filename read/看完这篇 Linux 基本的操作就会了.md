> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzI4Njg5MDA5NA==&mid=2247484231&idx=1&sn=4cf217a4d692a7aba804e5d96186b15b&chksm=ebd74246dca0cb5024de2f1d9f9e2ecb631e49752713c25bbe44f44856e919df5a973049c189&scene=21#wechat_redirect)

前言
==

> 只有光头才能变强

这个学期开了 Linux 的课程了，授课的老师也是比较负责任的一位。总的来说也算是比较系统地学习了一下 Linux 了~~~

本文章主要是**总结 Linux 的基础操作以及一些简单的概念**~ 如果不熟悉的同学可下个 Linux 来玩玩 (或者去买一个服务器玩玩【学生版的不是很贵】)，对于开发者来说，能使用 Linux 做一些基本的操作是必要的！

那么接下来就开始吧，当然了**我的 Linux 仅仅是入门水平**，如果有错的地方还需请大家多多包涵，并不吝在评论区指出错误~

一、为什么我们要学习 Linux
================

相信**大部分人**的 PC 端都是用 Windows 系统的，那我们为什么要学习 Linux 这个操作系统呢？？？Windows 图形化界面做得这么好，日常基本使用的话，学习成本几乎为零。

而 Linux 不一样，**可能**刚接触 Linux 的人会认为：Linux 好麻烦哦，不好玩，都是字符界面。不直观、这个破系统是用来干嘛的~~

日常用的话 Windows 是比较顺手的，但是我们要知道的是：我们开发出来的程序**一般都是放在 Linux 下运行**的。

那可能就会有人提出疑问了：Windows 同样是操作系统，**为啥要放在 Linux 下，而不放在 Windows 下呢**？？相信 Windows 也是可以运行我们写出来的程序的。

我总结了 Linux 的**几个优点**：

1.  免费
    
2.  很多软件原生是在 Linux 下运行的，庞大的社区支持，**生态环境好**。
    
3.  **开源**，可被定制，开放，**多用户的网络操作系统**。
    
4.  **相对安全稳定**
    

参考资料：

*   https://www.zhihu.com/question/19738282
    

所以开发者**选择了 Linux** 来跑我们自己写出来的程序。

二、Linux 的基础知识
=============

**Linux 系统的组成**：

1.  **linux 内核**（linus 团队管理）
    
2.  **shell**：用户与内核交互的接口
    
3.  **文件系统**：ext3、ext4 等。windows 有 fat32  、ntfs
    
4.  **第三方应用软件**
    

2.1Shell 的基本知识
--------------

除了 Shell、其他的都应该挺好懂的，那么 **Shell 是什么东西呢**？？？

> Shell 是系统的用户界面，提供了**用户与内核进行交互操作的一种接口** (命令解释器)

Shell 可以执行：

*   **内部命令**
    
*   **应用程序**
    
*   **shell 脚本**
    

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQu0QFuF4S4tdKfgk2vDuJt2oXDtQ0k12Ket7YjXQ9Baxc3XEBiaVvRgw/640?wx_fmt=png)

使用`type`命令可以**区分**内部命令和外部命令

于是乎，我们利用 Shell 就可以干下面这些事了：

*   **命令行解释 (这是用得最多的！)**
    
*   命令的多种执行顺序
    
*   通配符（ wild-card characters ）
    
*   命令补全、别名机制、命令历史
    
*   I/O 重定向（ Input/output redirection ）
    
*   管道（ pipes ）
    
*   命令替换（ 或 $( ) ）
    
*   Shell 编程语言（ Shell Script ）
    

Shell 的主要版本有以下这么多：

*   我们**常用 (默认)** 的就是 **bash**(bourne again shell)
    

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQubdicpMWT6FxfElyycy3AAJndlRLxVZ5HkgIyDIjtBPfVXmhFD1jurA/640?wx_fmt=png)

使用`ps`命令观察正在执行的 shell

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQJdjBicFPDMEWZY2fmMiakC2PlYRxwovk9cWZ6MGNYmwjZDicCLlZr7epA/640?wx_fmt=png)

2.2Linux 基本目录结构
---------------

在 Windows 下，会有**基本的目录结构**的：

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQU8XaUUHVr9DohlibzuDvnEelIWBNUqw5gQaZwsibag4JRt7nFFeQxOxg/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQQ94S2K4CRicNWXicDL2ibicSKZy8icjbnjKPyprTGXmMQic9yfMbVlwWqvOA/640?wx_fmt=png)

Linux 下也不例外了，也是有基本的目录结构的：

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQwr93h5NQZLwW35Pt3psVFQahs5eaiatBv3ZL7HXDYIUyBCmnGBC92hw/640?wx_fmt=png)这里写图片描述

Linux 文件系统是一个**目录树的结构**，文件系统结构从一个根目录开始，根目录下可以有任意多个文件和子目录，子目录中又可以有任意多个文件和子目录

*   **bin   存放二进制可执行文件 (ls,cat,mkdir 等)**
    
*   boot  存放用于系统引导时使用的各种文件
    
*   dev   用于存放设备文件
    
*   **etc    存放系统配置文件**
    
*   home  存放所有用户文件的根目录
    
*   lib    存放跟文件系统中的程序运行所需要的共享库及内核模块
    
*   mnt   系统管理员安装临时文件系统的安装点
    
*   **opt    额外安装的可选应用程序包所放置的位置**
    
*   proc   虚拟文件系统，存放当前内存的映射
    
*   **root   超级用户目录**
    
*   sbin   存放二进制可执行文件，只有 root 才能访问
    
*   tmp   用于存放各种临时文件
    
*   usr    用于存放系统应用程序，比较重要的目录 / usr/local 本地管理员软件安装目录
    
*   var    用于存放运行时需要改变数据的文件
    

2.3 命令基本格式
----------

`cmd  [options]  [arguments]`，options 称为选项，arguments 称为参数

选项和参数都作为 Shell 命令执行时的输入，它们**之间用空格分隔开**。

*   Linux 是**区分大小**写的
    

**一般来说**，后面跟的选项如果**单字符**选项前使用**一个**`减号-`。**单词选项**前使用两个`减号--`

*   这是一般的情况，有些命令还是不归属这种规律的 (相对较少)~~~
    
*   例子：`ls -a`和`ls -all`，`a` 单个字符使用一个`-`，一个单词`all` 使用两个`--`
    

在 Linux 中，**可执行的文件**也进行了分类：

*   **内置命令**：出于效率的考虑，将一些常用命令的解释程序**构造在 Shell 内部**。
    
*   **外置命令**：存放在 / bin、/sbin 目录下的命令
    
*   **实用程序**：存放在 / usr/bin、/usr/sbin、/usr/share、/usr/local/bin 等目录下的实用程序
    
*   **用户程序**：用户程序经过编译生成可执行文件后，可作为 Shell 命令运行
    
*   **Shell 脚本**：由 Shell 语言编写的批处理文件，可作为 Shell 命令运行
    

2.4 通配符
-------

学过一些正则表达式的或者有点基础的同学对通配符应该就不陌生的了，在 Linux 也有通配符 (在搜索的时候挺有用的)

*   *：匹配任何字符和任何数目的字符
    
*   ?：匹配单一数目的任何字符
    
*   []：匹配 [] 之内的任意一个字符
    
*   [!]：匹配除了 [! ] 之外的任意一个字符，! 表示非的意思
    

2.5 文件的类型
---------

在 Linux 下文件的类型有这么多：

*   **普通文件**`-`
    
*   **目录**`d`
    
*   **符号链接** `l`
    

*   硬链接： 与普通文件没什么不同，inode 都指向同一个文件在硬盘中的区块
    
*   软链接： 保存了其代表的文件的绝对路径，是另外一种文件，在硬盘上有独立的区块，访问时替换自身路径 (简单地理解为 Windows 中常见的快捷方式)。
    

*   字符设备文件 `c`
    
*   块设备文件`b`
    
*   套接字`s`
    
*   命名管道`p`
    

我们常见的就是普通文件，目录和符号链接。其他的了解一下即可~

符号链接参考资料：

*   https://www.jianshu.com/p/dde6a01c4094
    

2.5.1 用户主目录
-----------

可能在网上查阅资料的时候会出现**用户主目录**这么一个名词，那他是什么呢？？？

前面已经说了，我们的 Linux 是**多用户的网络系统**！所以，我们可以在 Linux 下创建多个用户，**每个用户都会有自己专属的空间**。

*   所以，在创建用户时，系统管理员**会给每个用户建立一个主目录**，通常在`/home/`目录下
    
*   比如：用户 osmond 的主目录为：`/home/osmond`
    

用户**对自己主目录的文件拥有所有权**，可以在自己的主目录下进行相关操作。

三、常用的命令
=======

上面说了一堆的基础概念，这是给我们敲命令之前打了一点基础，在敲命令的同时也会遇到一些比较重要的知识点的。那就到时候再说说了~~~

3.1 常用的文件、目录操作命令
----------------

这是我们**使用得最多**的命令了，**Linux 最基础的命令**！

*   可用  `pwd`命令查看用户的当前目录
    
*   可用 `cd` 命令来切换目录
    
*   `.`表示当前目录
    
*   `..` 表示当前目录的上一级目录（父目录）
    
*   `-`表示用 cd 命令切换目录**前**所在的目录
    
*   `~` 表示**用户主目录**的绝对路径名
    

**绝对路径：**

*   以斜线（/）开头 ，描述到文件位置的**完整说明** ，任何时候你想指定文件名的时候都可以使用
    

**相对路径 ：**

*   不以斜线（/）开头 ，指定**相对于你的当前工作目录而言的位置** ，可以被用作指定文件名的简捷方式
    

tips: **输入命令的时候要常用 tab 键来补全**

*   `ls`：显示文件或目录信息
    
*   `mkdir`：当前目录下创建一个空目录
    
*   `rmdir`：要求目录为空
    
*   `touch`：生成一个空文件或更改文件的时间
    
*   `cp`：复制文件或目录
    
*   `mv`：移动文件或目录、文件或目录改名
    
*   `rm`：删除文件或目录
    
*   `ln`：建立链接文件
    
*   `find`：查找文件
    
*   `file/stat`：查看文件类型或文件属性信息
    
*   `cat：`查看文本文件内容
    
*   `more：`可以分页看
    
*   `less：`不仅可以分页，还可以方便地搜索，回翻等操作
    
*   `tail -10`： 查看文件的尾部的 10 行
    
*   `head -20`：查看文件的头部 20 行
    
*   `echo`：把内容重定向到指定的文件中 ，有则打开，无则创建
    
*   `管道命令 |` ：将前面的结果给后面的命令，例如：`ls -la | wc`，将 ls 的结果加油 wc 命令来统计字数
    
*   `重定向 > 是覆盖模式，>> 是追加模式`，例如：`echo "Java3y,zhen de hen xihuan ni" > qingshu.txt`把左边的输出放到右边的文件里去
    

学了这些命令我们能干嘛？**其实就是在 Windows 下复制文件、粘贴文件、创建文件、查看文件这几种**~~~

### 3.1.1 常用的文件、目录操作练习题

巩固一下基础，**来做做题目：**

*   （1）Linux 的 shell 程序默认是`bash   程序`；
    
*   （2）Linux 命令格式包含三个部分，分别是：  `命令` 、  `选项`  、  `参数` ；
    
*   （3）Linux 命令选项前为单个减号（-），后面一般为  `单字符` ，选项前为双减号（--），后面一般为 `单词`  ；
    
*   （4）Linux 命令中使用的通配符有 `？ * []`  ；
    
*   （5）命令 ls  /usr/bin/w*  的效果是  `列出指定目录下的所有以w开头的文件或目录`   ；
    
*   （6）命令 ls  /usr/bin/w??  的效果是  `列出指定目录下的以w开头名称长度为3的所有文件或目录`   ；
    
*   （7）命令 ls  /usr/bin/[xyz]*  的效果是  `列出指定目录下的文件名以x或y或z开头的所有文件或目录`  ；
    
*   （8）命令 ls  /usr/bin/[!a-h]*  的效果是  `列出指定目录下的文件名不以a到h区间字母开头的所有文件或目录`    ；
    
*   （9）目录操作时，“.” 表示   `当前目录` ；
    
*   （10）目录操作时，“..” 表示  `上一级目录`  ；
    
*   （11）目录操作时，“-” 表示   `上一次工作目录`  ；
    
*   （12）目录操作时，“~” 表示  `用户主目录` ；
    
*   （13）命令 ln 可以建立文件链接，这种链接分为：  `硬链接`  和 `软链接` ；
    
*   （14）命令 touch 可以改变文件的三种时间，分别是： `access time` 、  `modify time`  、 `change time` ；
    

> 进入 / tmp 目录，建立一个文件，goldXX（XX 为学号的末两位），查看文件的时间

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQQxBHria4xibCgJbyw7gDhj3JibksNEoupJsbT61swc2x7gPpTBT2mZT0g/640?wx_fmt=png)

> 在账户的主目录中，建立一个 dog 目录，进入 dog 目录后，建立一个 catXX（XX 为学号的末两位）目录, 进入 catXX 目录，显示当前目录；然后返回上一级目录，删除 catXX 目录；

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQgoD9wTJqkIpreqAynkyDm7gspKY7iaibxCicFY6vYEPPqbkxXgvf82qlA/640?wx_fmt=png)

> 复制 / etc/passwd 文件到账户主目录，修改账户主目录下 passwd 为 passwdXX（XX 为学号的末两位）

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQdHfnrGRBy797bicwcHQJo49icbFXNCyey1G5nFNMZaA2vv4qzlwj69jA/640?wx_fmt=png)

> 查找文件名叫做 zcat 的文件；复制该文件到 / tmp 目录；用长格式列出该文件；然后删除 / tmp 目录下的所有文件，并检查文件是否已被删除

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQ7IAOeW8vywRmbmsE4biczurWq8RicyYWZlVTiavakkH8DVnwPmabpFqLA/640?wx_fmt=png)

> 复制 / etc/hosts 文件到账户主目录下；在账户主目录中建立一个硬链接文件（文件名为 hostsYYY（YYY 为学生姓名拼音缩写）），链接到主目录下的 hosts 文件；分别查看 hosts 和 hostsYYY 的文件的 inode 信息

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQMmXtibv7zXkZ4GRY4H58rgeOwClGFZye3kjPTWSeV9rTqub5dANJibRQ/640?wx_fmt=png)

> 复制 / usr/bin/vdir 文件到账户主目录下；在账户主目录中建立一个软链接文件（文件名为 newdir），链接到主目录下的 vdir 文件；分别查看 vdir 和 newdir 的文件的 inode 信息

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQ2tnlibjTLwDQiajQMXiciam0zwuFynoIv5jm3ZbtNCcUgjvx9QoxD1SPJA/640?wx_fmt=png)

> 用长格式列出目录 / usr/bin 目录下的所有文件，输出重新定向到文件 outXX（XX 为学生学号末两位），检查结果；用长格式列出目录 / etc 目录下的所有文件，输出结果补充到文件 outXX 末尾

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQR7AeMJibnkSkO3AdLXP6olmG76KibuPU3kUaZpqfMukibO2fDUvW35Ykw/640?wx_fmt=png)

> 用长格式列出 / usr/bin 目录下的所有文件，通过管道与 more 命令连接，实现对文件列表的浏览

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQepfNpUMGSIzqIbWmxCFY7g5y6agZwTEGhQibL9FaDoXQVtwHkRD9d4g/640?wx_fmt=png)

> `>和>>`有何区别？

答：`>`是**覆盖**方式重定向到新的文件；`>>`是以**补充**方式，添加到原文件的末尾。

> 通过管道和 more 命令，浏览文件列表方便在哪里？

答：对于文件列表超出一个屏幕显示的情况，这种方式可以**分屏浏览，比较方便**。

3.2 文件打包和压缩命令
-------------

在 Windows 操作系统下，我们会使用 WinRAR 或者快压等等的压缩软件来进行压缩或者解压。

在 Linux 下**当然也存在压缩或解压的操作咯**，下面我们就来学习一下在 Linux 下是怎么压缩和解压的！

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQCsAXZI577CoUlTjKw0kicc3IGps8JM0Z8VqvnaDZeWnIYPs8HK28mgQ/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQsB4vvmGM65YHLdCaTN1QOdYSZ8UXCnQhoVAzQUxRpbrOKkI0Gaz0lA/640?wx_fmt=png)

压缩的方式也是有好几种，我们**常用**的有下面这三种：

*   gzip
    
*   bzip2
    
*   tar
    

常用的压缩的命令就有：

*   `gzip filename`
    
*   `bzip2 filename`
    
*   `tar -czvf filename`
    

常用的解压命令有：

*   `gzip -d filename.gz`
    
*   `bzip2 -d filename.bz2`
    
*   `tar -xzvf filename.tar.gz`
    

3.3 正则表达式 + grep
----------------

上面我们已经学过了`cat、more、less、tail`这些查看文本文件的命令了，但是我想**快速查看这个文本文件下的某些关键字是否存在**，那怎么办？？？

在 Windows 下就比较简单的，几乎所有的文本编辑器 (记事本) 都支持`CTRL+F`，往里面输入关键字就可查找出来：

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQta4deaWIgWpN2bgE3RPHbMicqlvxdZxwn0lO5MdLcFhEL3BZwqEdmhg/640?wx_fmt=png)

那在 Linux 下，没有图形界面，没有`CTRL+F`的情况下，**如果不懂一些命令的话，那还真是难找对应的字符出来**。下面我就来说说如何快速**查找一个文本文件下的某些字符**。

### 3.3.1 正则表达式

首先我们就来说说正则表达式，如果接触过的同学就知道：这玩意并不好记。一旦不用就很容易就忘记了，所以只能在用的时候查查了~~~ 所以下面我就直接给出一些规则了，不多说啦。

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQbt0hpicfOssd1GayCGkJ6jh1MuWVTQiaKicReiaUx9OI5Zpna8BLdO6n0w/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQnUlynCplBWO8AjpIvya6lmImKwrKZkKSx6sbTRKMTfn3RNXkDJicJxg/640?wx_fmt=png)

### 3.3.2grep 命令

grep(global search regular expression) 是一个**强大的文本搜索工具**。grep 使用正则表达式搜索文本，并把匹配的行打印出来。

格式：`grep [options] PATTERN [FILE...]`

*   PATTERN 是查找条件：**可以是普通字符串、可以是正则表达式**，通常用单引号将 RE 括起来。
    
*   FILE 是要查找的文件，可以是用空格间隔的多个文件，也可是使用 Shell 的通配符在多个文件中查找 PATTERN，省略时表示在标准输入中查找。
    
*   grep 命令不会对输入文件进行任何修改或影响，可以使用输出重定向将结果存为文件
    

例子：

*   在文件 myfile 中查找包含字符串 mystr 的行
    

*   `grep -n mystr myfile`
    

*   显示 myfile 中第一个字符为字母的所有行
    

*   `grep  '^[a-zA-Z]'  myfile`
    

*   在文件 myfile 中查找首字符不是 # 的行（**即过滤掉注释行**）
    

*   `grep -v '^#' myfile`
    

*   列出 / etc 目录（包括子目录）下所有文件内容中包含字符串 “root” 的文件名
    

*   `grep -lr root /etc/*`
    

> 用 grep 查找 / etc/passwd 文件中以 a 开头的行，要求显示行号；查找 / etc/passwd 文件中以 login 结束的行；

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQhiav0IELOzfiaLlUxt2ceSWOkCnfYLqmmCKuVWdH7DKpk3LIHyJtVztg/640?wx_fmt=png)

3.4 几种提高工作效率的方法
---------------

*   **自动补全命令**
    

*   TAB 键
    

*   **历史命令**
    

*   上下箭头键
    

*   **别名 alias**
    

这里感觉要说说的就只有别名 alias 了，我们下面看看例子就懂了！

> 显示 shell 当前已经定义的别名；执行其中的两个定义别名的命令；定义一个别名 grep，要求其采用彩色方式显示结果

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQecrCJicsqric3cuOiawnd7p9w7U4UWtdWfvZSjJ5S1zrPibjQpdcYBjfrA/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQsB6Slmn0iaNU89wTS7iayuVeTMI1iaTxk64j9Qu8rceGiaLicx5hOyEDoog/640?wx_fmt=png)

3.5Shell 变量 和 Shell 环境
----------------------

在 Windows 下有用户的环境变量，系统的环境变量。在 Linux 一样也是有的。

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQhrPicwcicBfYUudDdYCmdatOLDloWzXAEtf0tialJS6HgVccJ8UchC0dw/640?wx_fmt=png)

Shell 变量大致可以**分为三类**：

*   **内部变量**：由系统提供，用户只能使用不能修改。
    

*   ?
    
*   GROUPS
    

*   **环境变量**：这些变量决定了用户工作的环境，它们不需要用户去定义，可以直接在 shell 中使用，其中某些变量用户可以修改。
    
*   **用户变量**：由用户建立和修改，在 shell 脚本编写中会经常用到。
    

*   `varName=Value`
    
*   `export  varName=Value`
    
*   变量赋值（定义变量）
    
*   引用变量`$varName`
    

Shell 变量的**作用域**：

*   **局部变量**的作用范围仅仅**限制在其命令行所在的 Shell 或 Shell 脚本文件中**；
    
*   **全局变量**的作用范围则包括**本 Shell 进程及其所有子进程**。
    
*   局部变量与全局变量**互换**：可以使用 `export` 内置命令将局部变量设置为全局变量。 可以使用 `export` 内置命令将全局变量设置为局部变量。
    

**export 命令**：

*   **显示**当前 Shell 可见的全局变量
    

*   `export [-p]`
    

*   **定义变量值的同时声明为全局变量**。
    

*   `export <变量名1=值1>  [<变量名2=值2> ...]`
    

*   声明已经赋值的某个（些）**局部变量为全局变量**。
    

*   `export <变量名1> [<变量名2> ...]`
    

*   声明已经赋值的某个（些）**全局变量为局部变量**。
    

*   `export -n <变量名1> [<变量名2> ...]`
    

Shell 环境变量：

*   环境变量定义 Shell 的**运行环境**，保证 Shell 命令的正确执行。
    
*   Shell 用环境变量来确定查找路径、注册目录、终端类型、终端名称、用户名等。
    
*   所有环境变量**都是全局变量**（即可以传递给 Shell 的子进程），并可以由用户重新设置。
    

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQcZtjPUibpibkR7SW4iaGSTQfK97pDTzK46wkmEKOj26gk4uQJIduzKCaw/640?wx_fmt=png)

**Shell 变量：查询、显示和取消**：

*   显示当前已经定义的所有变量
    

*   所有**环境变量**：`env`
    
*   所有**变量和函数**（包括环境变量） ：`set`
    

*   显示某（些）个变量的值
    

*   `echo  $NAME1  [$NAME2 ……]`
    

*   取消变量的声明或赋值
    

*   `unset  <NAME>`
    

### 3.5.1Shell 变量 和 Shell 环境练习题

> 定义 Shell 变量 stuXX（XX 为学生学号末两位），初值为学生姓名全拼，用 echo 命令显示 stuXX 变量的值；用 unset 命令取消 stuXX 变量，检查结果；用 env 命令观察当前有哪些已经定义好的 shell 环境变量

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQ7ET1boibFMicZEKPrWVjJqDmicSDXXIsKIhjs73zxKZ7ERWlnDqwCouTQ/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQo7CbOoJgOmLm0bYa2zWVNlqnWsMm8ecq6Xagd5Hm9zINdqib6yo5qvA/640?wx_fmt=png)

> Shell 环境变量的值是否可以修改？为什么？

答：环境变量的值一般情况下，可以修改。但一定要**慎重修改**，因为一旦修改错误，对 shell 正常运行造成严重影响，甚至导致 shell 无法运行。

四、VI 编辑器
========

相信没有用过 Linux 的同学在看一些段子的时候都会看到过两个编辑器：

*   vim
    
*   emacs
    

下面我们学习如何简单使用 vi。vi 是 “Visual interface” 的简称，它可以执行输出、删除、查找、替换、块操作等众多文本操作，而且**用户可以根据自己的需要对其进行定制，这是其他编辑程序所没有的**。

*   vi 可以看做成我们 Windows 下的记事本
    
*   vim 即 Vi IMproved，vi 克隆版本之一
    

使用 Vi 来编辑文件：

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQ5G227QFrcuBbxNuhc9aICpAf6wb7ibDMfIWyBljD6dKicmlH2t0K3iaZw/640?wx_fmt=png)

Vi 有三种模式：

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQhU68ia6DMA1dF0o9ZXhMO9h6pvpD8kLM7aH3KE4CVibVBq2cyJiaicdXNw/640?wx_fmt=png)

4.1 普通模式
--------

*   `G`用于直接跳转到文件尾
    
*   `ZZ`用于存盘退出 Vi
    
*   `ZQ`用于不存盘退出 Vi
    
*   `/和？`用于查找字符串
    
*   `n`继续查找下一个
    
*   `yy`复制一行
    
*   `p`粘帖在下一行，P 粘贴在前一行
    
*   `dd`删除一行文本
    
*   `x`删除光标所在的字符
    
*   `u`取消上一次编辑操作（undo）
    

4.2 插入模式
--------

在 Normal 模式下输入插入命令 `i、 a 、 o`进入 insert 模式。用户输入的任何字符都被 vim **当做文件内容保存起来**，并将其显示在屏幕上。

*   在文本输入过程中，若想回到 Normal 模式下，按 Esc 键即可。
    

4.3 命令行模式
---------

Normal 模式下，用户按冒号 `:`即可进入 Command 模式，此时 vim 会在显示窗口的最后一行 (屏幕的最后一行) 显示一个 “:” 作为 Command 模式的提示符，等待输入命令。

*   `:w`   保存当前编辑文件，但并不退出
    
*   `:w` newfile  存为另外一个名为 “newfile” 的文件
    
*   `:wq` 用于存盘退出 Vi
    
*   `:q!`    用于不存盘退出 Vi
    
*   `:q`用于直接退出 Vi （未做修改）
    

**设置 Vi 环境:**

*   :set autoindent  缩进, 常用于程序的编写
    
*   :set noautoindent 取消缩进
    
*   :set number 在编辑文件时显示行号
    
*   :set nonumber 不显示行号
    
*   :set tabstop=value 设置显示制表符的空格字符个数
    
*   :set 显示设置的所有选项
    
*   :set all 显示所有可以设置的选项
    

4.4Vi 练习题
---------

> 在用户主目录下，执行 vi 程序，编辑文件 install.log；移动光标到第 10 行，第五个字符；按大写字母 G，达到文件末尾；不存盘退出；

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQ2VKaIwsbo4yCp2LSbBxlAFL2nfFzhxNr4jfcUmZbX8Bcic884N1y3Vw/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQVTPjeUfJkGMRgoW18oLJJZRa1fqII0aMFHcaUYfEv5uFhSKkvAJJPA/640?wx_fmt=png)

> 在用户主目录下，执行 vi 程序，编辑文件 install.log；用 / 命令查找字符串 sudo，复制包含字符串 sudo 的行

![](http://mmsns.qpic.cn/mmsns/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQFktq9Mb02QGNE84fCqYhqQ/0)

> 在用户主目录下，执行 vi 程序，编辑文件 install.log；进入命令模式，设置显示行号；用？命令查找字符串 openssh，用命令 n 查找下一个

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQUGYwL5zjRrUiceOicdYQibuJBjN1rfz8qMAY3SK3ug7D57iaNU0teWDsug/640?wx_fmt=png)![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQIc7m7867TB03fuINrS1ericMto4icwsicGnic0Io4mR6qsGQdwRUod25jQ/640?wx_fmt=png)

四、总结
====

本文主要讲解了 Linux 的最基础的知识，可以简单地操作 Linux 了。命令可以说是学不完的，只能是记住 Linux 是有这个功能，到时候去网上查查也很方便。

主要是多练、多玩就可以记住一些常用的 Linux 命令了~~~~

下面我就花点时间画个 Linux 命令的脑图 (当然了，**命令仅限于是本文章的知识点**，等写到用户、网络等知识点的时候再继续补充上去！)

![](https://mmbiz.qpic.cn/mmbiz_png/2BGWl1qPxib1iamZ06xAxlaAPVaOlycqaQR4AtgqT7M8556nG1zHf6Msqnd7UrD3bPRia8ickq7n9KlzDwTgaKQ1Cg/640?wx_fmt=png)

> 如果文章有错的地方欢迎指正，大家互相交流。习惯在微信看技术文章，想要获取更多的 Java 资源的同学，可以**关注微信公众号: Java3y**。为了大家方便，刚新建了一下 **qq 群：742919422**，大家也可以去交流交流。谢谢支持了！希望能多介绍给其他有需要的朋友

**文章的目录导航**：

*   https://zhongfucheng.bitcron.com/post/shou-ji/wen-zhang-dao-hang