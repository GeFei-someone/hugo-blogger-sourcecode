---
title: "HTML入门笔记1"
date: 2019-08-26T14:38:32+08:00
categories:
- html
- html5
tags:
- html
- html5
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---
html新手基础，做个笔记
<!--more-->

目录

1. html谁发明的
2. html5是什么
3. html起手式
4. 常用的章节标签
5. 全局属性
6. 常用的内容标签

## 一、html谁发明的

html是[Tim Berners-Lee](https://baike.baidu.com/item/%E8%92%82%E5%A7%86%C2%B7%E4%BC%AF%E7%BA%B3%E6%96%AF%C2%B7%E6%9D%8E/8868412?fromtitle=Tim%20Berners-Lee&fromid=1836386&fr=aladdin)
万维网发明者，1990左右实现了HTTP代理与服务器的第一次通讯。

## 二、HTML5是什么
HTML5 有两个含义

最新版本的html语言，含旧标签和32个新标签

HTML5和他的朋友（包含css3等）

HTML5技术集合

* 新标签、新属性
* 新的通信技术：webSockets、webRTC等
* 离线存储：LocationStorage、断网检测
* 多媒体技术： 视频、音频
* 图像技术：Canvas SVG、webGL
* web增强技术：HistoryAPI、全屏
* 设备相关技术：摄像头、触摸屏
* 新的样式技术：css3新的flex、grid布局方式

## 三、html起手式

![](/images/blok4/1.png)

借用一下老师的图

在vscode里 Shift + 1 -> tab 就可以了

## 四、常用的章节标签

* 标题 h1 ~ h6
* 章节 section
* 文章 acticle
* 段落 p
* 头部 header
* 脚部 footer
* 主要内容 main
* 旁支内容 aside
* 划分 div

转义字符

` &cope; `  // 版权符号

## 五、全局属性

* class
* contenteditable 
* hidden 
* id
* style	
* tabindex 
* title

contenteditable：可编辑属性

hidden： 隐藏属性，是可以用css改回显示 （display: block）

id: id是不报错的，如果是全局唯一的可以使用，如果自己都不确定会不会有第二个，最好能用class就用class

tabindex：设置键盘Tab键的顺序，0最后选中 1第一个选中，正数访问，可以是无顺序的，-1 不选中

title 鼠标经过显示title

> 小技巧：

让style显示出来，并且能编辑

    1、把style写在body里
    2、style {display: block}
    3、<style contenteditable></style>

<font color=red size=3>注：编辑现有的css才能生效，新添加的css不起作用</font>

## 六、常用的内容标签

* ol+li
* ul+li
* dl+dt+dd
* pre
* hr
* br
* a
* em
* strong
* code
* quote
* blockquote

ol+li: 有序列表

ul+li:  无序列表

dl+dt+dd: 描述列表

pre 如果想保留空格或者换行就可以使用pre标签,一般用于写js代码

hr 分割线

br 换行

a 超链接

em 斜体

strong 加粗

code 等宽的标签，一般配合pre写js代码

quote 引用，默认没有什么效果，内元素

blockquote 引用，默认没有什么效果，块元素

<font  color=red size=3>注：html有个特点：如果有多个空格会被缩成一个，如果有回车也会被缩成一个空格，这个时候就需要使用pre</font>

pre使用：

```` js
 <pre>
    <code>
        iiii
        wwww
    </code>
 </pre>
````
