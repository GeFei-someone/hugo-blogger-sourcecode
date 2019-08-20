---
title: "Hugo生成博客网站"
date: 2019-08-19T22:03:20+08:00
categories:
- git
- Hugo
- gitHub
tags:
- git
- Hugo
- github
keywords:
- tech
---

hugo从0到1生成博客教程
<!--more-->
> 前言

最近学习了hugo生成博客，把我遇到的一些坑、和遇到点小问题记录一下，如果你是刚刚了解到hugo，那么看我这个网站怎么样？这就是hugo生成的。

> 开始操作

目录

1. 下载安装hugo
2. 按照hugo官网设置基本操作
3. 更换主题
4. 部署github，生成免费博客网站


## 一、下载安装hugo

Mac安装方式

* brew install hugo
* hugo version  查看hugo版本

Window安装方式

* 去[Hugo releases 页面](https://github.com/gohugoio/hugo/releases)下载hugo_xxx_Windows-64bit.zip

![](/images/blok2/1.png)

* 解压，找个目录解压出hugo.exe

![](/images/blok2/2.png)

* 将路径写进系统变量里(path)
  
![](/images/blok2/3.png)

* 启动控制台 输入 hugo version

![](/images/blok2/4.png)

## 二、按照hugo官网设置基本操作

进入[Hugo 官网](https://gohugo.io/),点击 <font color=red >Qick Start </font>开始
从Step2开始抄代码

> Step2:

![](/images/blok2/5.png)

生成博客的目录

![](/images/blok2/9.png)

config.toml配置文件介绍

![](/images/blok2/10.png)

> Step3:

![](/images/blok2/6.jpg)

> Step4:

![](/images/blok2/7.png)

生成的博客位置

![](/images/blok2/8.png)

博客内容

![](/images/blok2/11.png)

> Step5:

![](/images/blok2/13.png)

<font color=red >注：开了server 就不要关了，关了就访问不了，需要重新开启</font>

开起后是这样的

![](/images/blok2/14.png)

改一下配置文件(config.toml)

![](/images/blok2/15.png)

保存后浏览器会自动刷新

![](/images/blok2/16.png)

> 插入图片

在根目录` static `目录里放图片

![](/images/blok2/36.png)

## 三、更换主题

进这个网站里

![](/images/blok2/17.png)

我选择这个主题

![](/images/blok2/18.png)

点这个

![](/images/blok2/19.png)

后面的themes/jane 是克隆在themes下jane文件夹

![](/images/blok2/20.png)

注意：在vscode里重新开一个终端，不要关闭之前的

![](/images/blok2/21.png)

开始换主题了。。。

![](/images/blok2/22.png)

主题换成功了，但是这里有一点问题 注意

![](/images/blok2/23.png)

需要运行这两句，因为content -> props 而主题里的content->post需要替换一下,config.toml也一样 默认的配置文件已经支持不了主题的了，需要复制出来

```` javascript
 cp -r themes/jane/exampleSite/content ./
````

```` javascript
 cp themes/jane/exampleSite/config.toml ./
````
<font color=red size=3>使用这两句命令可以，也可以自己手动替换</font>

![](/images/blok2/26.png)

这样就可以了，配置文件里需要改几个地方 

![](/images/blok2/27.png)

<font color=red size=3>注：每个主题的配置文件都是不一样的，可以看他的主题文档</font>

换完以后运行 ` hugo `，会生成public目录 

![](/images/blok2/24.png)


## 四、部署github，生成免费博客网站

根目录创建 .gitignore 文件。 public是不提交的，public目录是需要单独提交的，public才是最后的网站

![](/images/blok2/28.png)


进入public，如果还不会git提交远程仓库可以看我另一个文章，[戳我](/2019/08/git基本操作适合新手/)

![](/images/blok2/29.png)

创建远程仓库 ` gefei.github.io `

![](/images/blok2/30.png)

提交成功后 在github点这个

![](/images/blok2/31.png)

找到gitHub Pages 把Source选择成master branch，如果没有就不用管了，直接点上面的地址

![](/images/blok2/33.png)

放上去后是没有样式的  需要改一下config.toml里的BaseUrl参数

![](/images/blok2/34.png)

然后重新hugo

<font class=red >注意：记住一定要在博客根目录hugo，不然会在你当前目录创建public目录<font>

![](/images/blok2/35.png)

<font size=5 >打完收工</font>

> 结尾

hugo是需要git的，如果你还不会git可以看我另一篇文章，希望对你有帮助。如果是上传博客源代码注意主题是不会上传的。有问题可以联系我，微信：836456907

hugo的写文章语言是 Markdown 语法