---
title: "HTML常用标签"
date: 2019-08-28T15:53:49+08:00
categories:
- html
tags:
- html
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---
html常用的一些标签
<!--more-->

目录

1. [a标签](#a)
2. [img标签](#img)
3. [form标签](#form)
4. [input标签](#input)
5. [table标签](#table)

## <div id='a'>一、a标签</div>

> 属性

* href
* target
* download
* rel=noopener

href取值
    
* 网站：

        https://baidu.com

        http://baidu.com

        //baidu.com  无协议网址，会自动适用http还是https

![](https://i.loli.net/2019/08/28/aTQsH7Y8qrj5CdZ.png)

* 路径

        /a/b/c // 绝对路径

        a/b/c // 相对路径

* 伪协议

        javascript: ;  //一般用于直接执行js代码，现在用于点击无动作的a标签 : ; 中间是js代码

        mailto: 邮箱

        tel: 手机号 // 在手机里会自动跳进打电话界面，填充你点击的手机号
* id

        href="#xxx"  //锚点链接

target取值

* _blank

    新窗口打开

* _top 

    最顶层打开,一般在iframe里使用,不管有多少个iframe 都会在最顶层打开

    ![](https://i.loli.net/2019/08/28/c8QV3tBSdDsfK9z.png)

    ![](https://i.loli.net/2019/08/28/OtyTNJmKuH2eFpE.png)

* _parent

    当前窗口的上一级窗口打开，一般在iframe里使用

    ![](https://i.loli.net/2019/08/28/8XIoldup4qS2E3G.png)

    ![](https://i.loli.net/2019/08/28/5G7PcK3D9Ej46LU.png)

    ![](https://i.loli.net/2019/08/28/UC9lngpmKIF8qTO.png)

* _self

    当前窗口打开

* xxx

    如果有一个叫xxx的窗口就在xxx打开，如果没有就创建xxx窗口，
    如何验证窗口是xxx   控制台输入  window.name,

    ![](https://i.loli.net/2019/08/28/ihHGmUbo7gQ3P2B.png)
    
    ![](https://i.loli.net/2019/08/28/NXhjvJP513lTQ8F.png)

* iframe的name

    实现在iframe里打开新页面

    ![](https://i.loli.net/2019/08/28/5Iuq8gj1QrCZdHe.png)

    ![](https://i.loli.net/2019/08/28/ZAdcW6vCtpx1TYB.png)

## <div id='img'>二、img标签</div>

> 作用

    发出get请求，展示一张图片

> 属性

* alt

    图片加载失败显示的提示

    ![](https://i.loli.net/2019/08/28/Sdx5JQ7nqMK4gN3.png)

* height

    高度  只写高度 宽度会自适应

* width

    宽度 只写宽度 高度会自适应

* src

    路径

> 事件

    onload: 图片加载成功触发

    onerror: 图片加载失败触发

> 响应式

```` js
max-width: 100%;
````

## <div id='form'>三、form标签</div>

> 作用

发get或post请求，然后刷新页面

> 属性

* action

    请求地址

* autocomplete

    是否自动填充  使用这个需要在input里写name属性

* method

    设置请求方式，get或post 大小写无所谓

* target

    和 a标签的一样

> 事件

    onsubmit：当用户点提交的时候，触发事件

<font color=red size=2>注：在表单里，如果button里不设置type默认会是submit属性</font>

## <div id='input'>四、input标签</div>

> 作用

让用户输入内容

> 属性

* type

```` js
    button
    checkbox
    redio
    email
    file  //多选上传属性 multiple
    hidden
    number
    password
    search
    submit
    tel
    text
    color
````

* name
* autofocus
* checked
* disabled
* maxlength
* minlength
* pattern
* value
* placeholder

> 事件

        onchange 用户输入改变时
        onfocus 获取焦点时
        onblur 失去焦点时
> 验证器

    required 必须填写 html5新增

> textarea标签

    resize: none 禁止拖动 css设置

> select 标签

    <select>
        <option value="1">1</option>  // value是真正的值，里面的是给用户看到的
    </select>

注意事项：

    一般不监听input的click事件

    form里面的input要有name属性

    form里放一个type=submit才能触发submit事件

## <div id='table'>五、table标签</div>

table标签里只能有3个标签

    thead  头部

    tbody 主体

    tfoot   脚步

tr :  行

th: 表头 

td: 数据 列

> 相关样式

```` css
table {
    border-collapse: collapse;  // 表格的边框是分开还是合并 collapse合并
    border-spacing: 0  // 相邻单元格边框之间的距离 
}
````

## 其他感想

之前写表单的时候一直都不写` from `，导致内容老是自己填充，最后使用` hidden `属性隐藏` input `骗浏览器，现在知道了 ` autocomplete ` 属性了，还是挺有用的，感谢 