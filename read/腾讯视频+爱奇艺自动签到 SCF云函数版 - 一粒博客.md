\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[1li.kim\](http://1li.kim/index.php/archives/295/)

![QQ截图20200331160210.png](http://1li.kim/usr/uploads/2020/03/2455677631.png "QQ截图20200331160210.png")  
自动签到省去你手动签到的麻烦，节省时间，避免忘记。有些视频网站签到可以增加成长值或者签到指定天数送vip。废话我就不说了 上干货！

4月7日更新爱奇艺查找cookie方法

写在前面
----

修改代码最好不要使用记事本，使用notepad++ 等 ，方便编辑避免格式和缩进出错

听说腾讯视频的cookie更新很快，然后有大佬找出了二次ck接口 可用自动更新,我也没测试ck存活多久，测试ok就写教程。

腾讯云函数有免费额度，拿来签到是足够的了，太多签到项目估计会超额，使用一天看看自己的额度 [免费额度规则](http://1li.kim/index.php/go/aHR0cHM6Ly9jbG91ZC50ZW5jZW50LmNvbS9kb2N1bWVudC9wcm9kdWN0LzU4My8xMjI4Mg==)

一、腾讯视频签到
--------

1.打开[v.qq.com](http://1li.kim/index.php/go/aHR0cDovL3YucXEuY29t) 登录后 按**f12** 再次刷新点击**network**点击搜索输入`auth`找到一条带有`auth_refresh`的数据

2.双击这条数据，右边会自动定位当前数据位置，右击选择`open in new tab`继续**f12**查看ck  
![QQ截图20200331150107.png](http://1li.kim/usr/uploads/2020/03/3762715306.png "QQ截图20200331150107.png")  
复制ck 不要多不要少

3.编辑代码 为了防止代码变形

代码下载链接:[](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cubGFuem91cy5jb20vaWF0enU3Zw==)[https://www.lanzous.com/iatzu7g](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cubGFuem91cy5jb20vaWF0enU3Zw==)

需要修改5处地方

第9行填入完整的ck

```
'Cookie': '腾讯视频cookie' 
```

第11行填入auth\_refresh的完整链接

```
 login = requests.get('auth_refresh的完整链接',headers=login_headers) 
```

第14行需要把ck`vqq_vusession`以后删掉（包括`vqq_vusession`）例图

```
 'Cookie': '腾讯视频cookie vqq_vusession='+cookie['vqq_vusession']+';' 
```

![QQ截图20200331151655.png](http://1li.kim/usr/uploads/2020/03/2981035173.png "QQ截图20200331151655.png")  
如果需要server酱通知修改20行和23行的`sever酱key`

**修改的时候注意`''`两个单引号中间修改，避免出错**

4.创建云函数

打开腾讯云函数-[](http://1li.kim/index.php/go/aHR0cHM6Ly9jb25zb2xlLmNsb3VkLnRlbmNlbnQuY29tL3NjZi9saXN0)[https://console.cloud.tencent.com/scf/list](http://1li.kim/index.php/go/aHR0cHM6Ly9jb25zb2xlLmNsb3VkLnRlbmNlbnQuY29tL3NjZi9saXN0)  
环境选择**python2.7**选择其他代码会无法运行  
创建方式选择**空白函数**  
删除原有代码 再把自己代码复制进`index.py` 保存并测试

![QQ截图20200331152401.png](http://1li.kim/usr/uploads/2020/03/136696541.png "QQ截图20200331152401.png")  
![QQ截图20200331152752.png](http://1li.kim/usr/uploads/2020/03/3094753925.png "QQ截图20200331152752.png")

提示测试成功或者server酱提示成功 或者app显示签到 都表示成功

二、爱奇艺签到
-------

1.打开[](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cuaXFpeWkuY29tLw==)[https://www.iqiyi.com/](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cuaXFpeWkuY29tLw==)并登录

2.f12翻到第一个[https://www.iqiyi.com/](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cuaXFpeWkuY29tLw==) 双击复制request headers 里面的cookie

某些时候找不到www.iqiyi.com 这条数据的时候，点击个人中心 f12 \`record\` 这条记录的cookie 也可以使用

![QQ截图20200331153236.png](http://1li.kim/usr/uploads/2020/03/1053848156.png "QQ截图20200331153236.png")  
3.修改代码

**代码下载链接** : [](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cubGFuem91cy5jb20vaWF1MWw2ZA==)[https://www.lanzous.com/iau1l6d](http://1li.kim/index.php/go/aHR0cHM6Ly93d3cubGFuem91cy5jb20vaWF1MWw2ZA==)

修改第9行`爱奇艺cookie`

**填入真实ck**

4.创建云函数 如腾讯视频签到那样创建一个云函数 测试成功即可

三、设置定时执行
--------

光创建还是不行，只有点击测试按钮才会执行一次给他设置触发条件即可

![QQ截图20200331154059.png](http://1li.kim/usr/uploads/2020/03/487131755.png "QQ截图20200331154059.png")  
![QQ截图20200331154229.png](http://1li.kim/usr/uploads/2020/03/3435478431.png "QQ截图20200331154229.png")

结束
--

爱奇艺签到代码来自 吾爱破解论坛@anyuhang  
腾讯视频签到代码来自 吾爱破解论坛@豆战剩佛

感谢大佬！

如果测试出错，跟着教程重新走一遍。感谢观看！

* * *

> 版权属于：一粒
> 
> 本文链接：[http://1li.kim/index.php/archives/295/](http://1li.kim/index.php/archives/295/)
> 
> 转载时须注明出处及本声明