---
title: "安装node.js"
date: 2019-08-26T10:03:54+08:00
categories:
- node
tags:
- node
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---
一个前端 连npm和yarn都不知道，没用过 那出去面试会很伤人的，所以大家学起来把。
<!--more-->

目录

1. 下载/安装node
2. 使用淘宝代替原npm
3. 安装yarn

## 一、下载/安装node

[进入node官网](https://nodejs.org/en/)

默认node提交使用node 10版本，这里推荐使用node 8版本的，10可能会有bug

点进 Other Downloads

![](https://i.loli.net/2019/08/26/HwU1vGmapsufekR.png)

最下面找到Previous Releases

![](https://i.loli.net/2019/08/26/1zL8qgCDabxJISF.png)

点进 Node.js 8.x

![](https://i.loli.net/2019/08/26/1zL8qgCDabxJISF.png)

根据你的系统找到版本，我的是64位 （86是32位），zip是需要解压，msi是安装包无需解压

![](https://i.loli.net/2019/08/26/HevqzpXnOIrWdu7.png)

运行安装包，点击运行

![](https://i.loli.net/2019/08/26/WLTHhloazriw59Z.png)

点击下一步

![](https://i.loli.net/2019/08/26/RKD9CHEelOnBPJf.png)

勾选、下一步

![](https://i.loli.net/2019/08/26/a4MKXvg5j1LDQZG.png)

选择安装目录，注意 nodejs不允许安装目录有空格 改一下

![](https://i.loli.net/2019/08/26/9YLwmGTKsPfAx3v.png)

大小写无所谓，只要没有空格就可以了

![](https://i.loli.net/2019/08/26/RCjd9HE6us8bVLf.png)

改完安装路径、下一步

![](https://i.loli.net/2019/08/26/5UGXvhaLPJOlZjW.png)

这里推荐全选上，尤其是 Add to Path

Path 就是系统变量里的

下一步，等待安装完成

![](https://i.loli.net/2019/08/26/kCdUg7ATRV8u2Fs.png)

点击Finish

系统变量里已经有了 node的路径

![](https://i.loli.net/2019/08/26/j7dCrDsHcpuyzvt.png)

<font color=red size=3>如果发现安装完了node不能使用，就检查一下path的路径，安装玩了 注销电脑或者重启终端</font>

> 修改默认安装地址

然后终端 运行

```` js
 npm config set prefix "D:\Program Files\nodejs\node_global"  // 注意改路径,改成你的
 npm config set cache"D:\Program Files\nodejs\node_cache"  // 注意改路径,改成你的
````
运行后 node目录会多2个文件夹

![](/images/blok3/1.png)

添加一个系统变量

![](/images/blok3/2.png)


安装完node 就会带

* node命令
* npm命令
* npx命令

查看是否安装成功

```` javascript
  node --version  // 简写 node -v
````
![](https://i.loli.net/2019/08/26/LYE78qSusCRtlIb.png)

公司电脑，懒的重新换版本。。。

```` javascript
 npm --version // 简写 npm -v
````

![](https://i.loli.net/2019/08/26/QIevCuyT3qRtLlz.png)

```` javascript
 npx --version // 简写 npx -v
````

![](https://i.loli.net/2019/08/26/ew2itzsOjD6vrcy.png)

## 二、使用淘宝替代原npm

原npm的服务器是国外的，会很慢。所以需要替换成淘宝的

使用淘宝源（不要用cnpm）

```` javascript
 npm i -g nrm // i (install) -g (全局) 
````

![](https://i.loli.net/2019/08/26/xILmMwTN3HgQ4R8.png)

安装完成检查有没有安装成功

```` js
 nrm --version
````

![](https://i.loli.net/2019/08/26/iA7TOKgpmrRzHwL.png)

查看可以使用那些服务

```` js
 nrm ls
````

![](https://i.loli.net/2019/08/26/pBAgJudhUSQMeiV.png)

选择淘宝的服务

```` js
 nrm use taobao 
````

![](https://i.loli.net/2019/08/26/x3OHlmuW8w4Pqds.png)

安装http-server

```` js
 npm i -g http-server // 你会发现安装的很快
````

![](/images/blok3/3.png) 

注意看下面的路径，配置的默认安装路径的地方

## 三、安装yarn

安装：

[进入官网](https://www.yarnpkg.com/zh-Hans/)

![](https://i.loli.net/2019/08/26/ve2Duj58rFH6y7h.png)

默认已经都选择好了，直接下载就可以了

![](https://i.loli.net/2019/08/26/onsROUkjIgerZFl.png)

![](https://i.loli.net/2019/08/26/KNGTC52DqoPAmte.png)

下一步、记得改路径

![](https://i.loli.net/2019/08/26/Euca4xhzCFTtKwp.png)

然后 install 等待安装就好了

在系统变量Path里就加进去了 yarn

![](https://i.loli.net/2019/08/26/huV8dvP9SMTl6aY.png)

重启终端或者注销电脑

```` javascript
  yarn --version
````

![](https://i.loli.net/2019/08/26/iVJwYlcOEbzuXIN.png)

修改一下yarn也使用淘宝源
```` js
 yarn config list // 查看一下 yarn 的配置列表
````

![](https://i.loli.net/2019/08/26/XzbyFeQ4CmET9tx.png)

```` js
 yarn config get registry // 查看yarn的源
````
![](https://i.loli.net/2019/08/26/I2O8YnfeJwShPq1.png)

安装淘宝源 

```` js
  yarn config set registry https://registry.npm.taobao.org -g 
  yarn config set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass -g
````