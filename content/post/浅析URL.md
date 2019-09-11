---
title: "浅析URL"
date: 2019-09-04T17:28:30+08:00
categories:
- HTTP
- url
tags:
- url
- HTTP
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---

<!--more-->

> 前言

最近学习了HTTP，这里简单的写一下URL的一些事情

## URL

````
https://baidu.com/s?wd=hello#5
````

https： 协议

baidu.com：域名 / IP

/s：路径

?wd=hello：参数

#5: 锚点

## 域名

域名：对应着IP的别称

知识点：

* 一个域名可以对应不同IP地址
* 这个就叫负载均衡，防止一台机器扛不住
* 一个IP可以对应不同的域名
* 这个就叫共享主机

域名的关系：

1. com 是顶级域名
2. baidu.com 是二级域名（俗称一级域名）
3. www.baidu.com 是三级域名（俗称二级域名）

他们是父子关系，有可能你输入的baidu.com和www.baidu.com不是一家公司，类似于我这个网站。
这个网站的域名是github.io分配给我的,所以和github是一家公司吗？不是

## IP

IP分为内网IP和外网IP

内网IP想访问外网就得需要路由器去做转接

外网：需要从电信/移动去购买带宽，然后电信/移动会分配给你外网地址，保存在路由器里。

内网：内网的设备可以互相访问，但是不能访问外网

全名:internet Protocal,IP约定了两个事情

* 如何定位一台设备
* 如何封装数据报文，以及跟其他设备交流

这里有一些特殊的IP地址：

1. 127.0.0.1 自己
2. localhost 通过<font color=red>hosts</font> 指定到127.0.0.1
3. 0.0.0.0 不表示任何设备

设置localhost

![](https://i.loli.net/2019/09/04/ZoOKlPLuC97GWYy.png)

找到该文件，如何以管理员身份打开一个编辑器，把文件拖入编辑器里，一定要要管理员身份运行

![](https://i.loli.net/2019/09/04/QjV1Ce4rocMRfYx.png)

带 # 号的都可以删，删不删无所谓  在最后面添加

````
 127.0.0.1 demo  //  最后的demo可以随便换
````

修改完以后 随便找个项目，运行http-server，（安装http-server自行百度）

![](https://i.loli.net/2019/09/04/MJ6NRtcfeIr5Tah.png)


![](https://i.loli.net/2019/09/04/TkEvgpGCct2JSlr.png)

修改成功了。 可以使用自己设置的，也可以使用localhost，推荐最好使用localhost  因为业界都知道localhost是干嘛的

## 路径

路径指向 不同页面使用

例如这个：

````
https://developer.mozilla.org/zh-CN/docs/Web/HTML
````

把后面的` HTML ` 换成` CSS `，就可以进入CSS页面。

## 参数

参数指向 同一个域名，不同内容

例如这个：

````
https://www.baidu.com/s?wd=hello
````
把后面的` hello ` 换成自己想查的，就可以重新页面内容

## 锚点

锚点指向 同一个内容不同位置（就是锚链接）

```` 
https://developer.mozilla.org/zh-CN/docs/Web/CSS#参数
````

<font color=red>注意：锚点会在请求后台的时候，浏览器会排除掉锚点，和微信公众号的一样。中文会变成乱码，在浏览器里是没有事的，锚点实际上是不支持中文的</font>

## DNS

全名：Domain Name Server，将域名和IP对应起来

当你输入baidu.com

过程：

浏览器会向电信/联通提供的DNS服务器询问baidu.com的对应的IP地址

电信/联通会回答一个IP

然后浏览器会向对应的IP的80/443端口发送请求

请求内容是查看baidu.com的首页

询问IP：

````
nslookup baidu.com  //询问百度的IP地址
````

## 端口

一共有65535个端口，这里举3个常使用的：

要提供HTTP服务最好使用 80 端口

要提供HTTPS服务最好使用 443 端口

要提供FTP服务最好使用 21 端口

规则：

0到1023号端口是留给系统使用的，你只有拥有了管理员权限后，才可以使用这1024个端口

其他端口给普通用户使用

