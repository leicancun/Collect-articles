> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.heson10.com](https://www.heson10.com/next/posts/53612.html#more)

先上地址：[https://yf.heson10.com](https://yf.heson10.com/)

前方高能音乐来袭。。。。注意保护耳朵，可预先试听：

Your browser does not support the audio tag.

[](#为什么搭建？ "为什么搭建？")为什么搭建？
--------------------------

[![](https://picup.heson10.com/img/upyun/image-20200908220604976.png)](https://picup.heson10.com/img/upyun/image-20200908220604976.png "因为穷")

[因为穷](https://picup.heson10.com/img/upyun/image-20200908220604976.png "因为穷")

[](#效果图 "效果图")效果图
-----------------

### [](#前台效果图 "前台效果图")前台效果图

[![](https://cdn.jsdelivr.net/gh/heson10/pic@master/img/image-20200908215411128.png)](https://cdn.jsdelivr.net/gh/heson10/pic@master/img/image-20200908215411128.png "黑石要饭系统前台界面")

[黑石要饭系统前台界面](https://cdn.jsdelivr.net/gh/heson10/pic@master/img/image-20200908215411128.png "黑石要饭系统前台界面")

前三个没付款的家伙，你们有本事倒是付啊！😂

### [](#后台 "后台")后台

[![](https://picup.heson10.com/img/upyun/image-20200908215618777.png)](https://picup.heson10.com/img/upyun/image-20200908215618777.png "黑石要饭系统后台界面")

[黑石要饭系统后台界面](https://picup.heson10.com/img/upyun/image-20200908215618777.png "黑石要饭系统后台界面")

[](#搭建摘要 "搭建摘要")搭建摘要
--------------------

*   源码用的是烟雨要饭 源码下载地址：[http://cdn.yyhy.me/yaofan.zip](http://cdn.yyhy.me/yaofan.zip)
    
*   对接的是**码支付**，特点：支付宝 QQ 全免 微信免手续费只需交易额度 码支付地址→[点击我](https://codepay.fateqq.com/i/570001) 下面是其网站的宣传图：
    
    [![](https://picup.heson10.com/img/upyun/image-20200908220215882.png)](https://picup.heson10.com/img/upyun/image-20200908220215882.png "码支付功能介绍")
    
    [码支付功能介绍](https://picup.heson10.com/img/upyun/image-20200908220215882.png "码支付功能介绍")
    

*   支付宝开通了商家服务、qq 钱包上传了收款码、微信付费签约了并上传收款码
*   源码需要修改适配码支付，下面简单讲一下

[](#关于源码修改适配问题 "关于源码修改适配问题")关于源码修改适配问题
--------------------------------------

### [](#核心函数php文件：Pay-Class-php "核心函数php文件：Pay.Class.php")核心函数 php 文件：`Pay.Class.php`

主要修改了`submit()`函数，增加了对码支付支付工具`type`的判断，以及财主爸爸昵称`nick`的调用，以及增加码支付一些自用参数，函数代码如下:

```
public function submit($type, $out_trade_no, $notify_url, $return_url, $name, $money, $sitename, $nick)
{
    if ($type == 'alipay') {
        $typeid = 1;
    }
    if ($type == 'qqpay') {
        $typeid = 2;
    }
    if ($type == 'wxpay') {
        $typeid = 3;
    }


    $data = [
        'id' => $this->pid,
        'type' => $typeid,
        'out_trade_no' => $out_trade_no,
        'notify_url' => $notify_url,
        'return_url' => $return_url,
        'name' => $name,
        'price' => $money,
        'sitename' => $sitename,
        'act' => 0,
        'debug' => 0,
        'pay_type' => 1,
        'pay_id' => $nick,
        'param' => $out_trade_no


    ];
    $string = http_build_query($data);
    $sign = $this->getsign($data);
    return 'http://codepay.fateqq.com/create_order/?' . $string . '&token=换成自己的token';
}
```

其中`http://codepay.fateqq.com/create_order/?`是码支付 API 的地址，码支付的`token`写在`token=`的后面。

网站端`yf.heson10.com/Admin/`后台里，要填写码支付的 id：

[![](https://picup.heson10.com/img/upyun/image-20200911075559955.png)](https://picup.heson10.com/img/upyun/image-20200911075559955.png "码支付ID")

[码支付 ID](https://picup.heson10.com/img/upyun/image-20200911075559955.png "码支付ID")

### [](#Pay-Submit-index-php的修改 "Pay/Submit/index.php的修改")Pay/Submit/index.php 的修改

主要是前面和前面 submit() 函数相对应。注意这里的 https，如果服务器没开 ssl，就换成 http

```
submit($order['type'], $order['trade_no'], 'https://' . $_SERVER['HTTP_HOST'] . '/Pay/Notify/', 'https://' . $_SERVER['HTTP_HOST'] . '/Pay/Return/', config('sitename') . ' - 支付订单', $order['money'], config('sitename'), $order['nick']);
```

修改后附图：

[![](https://picup.heson10.com/img/upyun/image-20200911075700994.png)](https://picup.heson10.com/img/upyun/image-20200911075700994.png "要饭系统submit修改图")

[要饭系统 submit 修改图](https://picup.heson10.com/img/upyun/image-20200911075700994.png "要饭系统submit修改图")

### [](#Pay-Ruturn-index-php的修改 "Pay/Ruturn/index.php的修改")Pay/Ruturn/index.php 的修改

去掉验证数据，增加对订单号的验证，同时调用自定义参数`param`，用于定位当前订单号。

```
$data = $_REQUEST;
$pay = new Pay(config('pid'), config('key'),config('api'));
if ($data['pay_no']) {
    $order = Db('select * from yyhy_order where trade_no="' . $data['param'] . '"');
    if (!$order) exit('fail');
    $order = $order[0];
    if ($order['status'] != 1) {
        Db('update yyhy_order set `status`=1,`endtime`="' . date('Y-m-d H:i:s') . '" where trade_no="' . $data['param'] . '"');
    }
    alert('施舍成功，好人有好报！', '/');
} else {
    alert('支付验证失败,施舍失败了，又吃不到饭饭了！', '/');
}
```

修改后附图：

[![](https://picup.heson10.com/img/upyun/image-20200911075745019.png)](https://picup.heson10.com/img/upyun/image-20200911075745019.png "要饭系统ruturn页面设置")

[要饭系统 ruturn 页面设置](https://picup.heson10.com/img/upyun/image-20200911075745019.png "要饭系统ruturn页面设置")

### [](#Pay-Notify-index-php的修改 "Pay/Notify/index.php的修改")Pay/Notify/index.php 的修改

简单验证单号就行，还要具备补单功能：

```
include '../../Core/Common.php';

$data = $_REQUEST;
$pay = new Pay(config('pid'), config('key'),config('api'));
if ($data['pay_no']) {
    echo 'success';
    $order = Db('select * from yyhy_order where trade_no="' . $data['param'] . '"');
    if (!$order) exit('fail');
    $order = $order[0];
    if ($order['status'] != 1) {
        Db('update yyhy_order set `status`=1,`endtime`="' . date('Y-m-d H:i:s') . '" where trade_no="' . $data['param'] . '"');
    }
} else {
    echo 'fail';
}
```

[](#写在后面 "写在后面")写在后面
--------------------

~好吧，今天又水了一篇。😂😂~

~Q: 为什么写这么一篇水文？~

~A: 因为弄这个还是花了不少功夫，简单记录一下：~

*   ~一是做笔记让自己知道修改了哪些东西~
*   ~二是为需要的小伙伴提供思路。~

**9 月 11 日更新：**

已经不算是水文了，更新的文章加上了修改方法和配图，学会的扣 **111111111111111**，没学会的扣**眼珠子**！

**9 月 12 日更新：**

解决微信、qq 支付异步问题。

[](#后期打算更新 "后期打算更新")后期打算更新
--------------------------

*   前台界面二开
*   待定