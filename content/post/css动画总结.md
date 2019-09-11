---
title: "Css动画总结"
date: 2019-09-10T17:09:19+08:00
categories:
- css
- 浏览器
tags:
- css
- 浏览器
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---
最近在学习css动画和浏览器的渲染机制，有兴趣的小伙伴可以一起
<!--more-->

## 动画的原理

> 定义

由许多静止的画面（帧），以一定的速度（如每秒30张）连续播放时，肉眼因视觉残像产生错觉，而误认为是活动的画面

> 概念

帧：每个静止的画面叫做帧

播放速度：每秒24帧（影视）或者每秒30帧（游戏）

## 浏览器渲染原理

步骤：

* 根据HTML构建HTML树（DOM）
* 根据CSS构建CSS树（CSSOM）
* 将两棵树合并成一颗渲染树（render tree）
* Layout布局（文档流、盒模型、计算大小和位置）
* Paint绘制（把边框颜色、文字颜色、阴影等画出来）
* Compose合成（根据层叠关系展示画面）

![](https://i.loli.net/2019/09/10/YSEZioKhAzIGqbT.png)

查看例子之前 先开启浏览器性能检测

<font color=red>在开发者工具，任何一个tab页  按Esc、点console左边的三个点，选择Rendering，点Paint flashing，页面的绿色就是重新渲染的</font>

更新DOM有三种方式，看下图

![](https://i.loli.net/2019/09/10/eQo81IMX5r6z9PB.png)

> 例1：


````
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    #demo{
        width: 100px;
        height: 100px;
        border: 1px solid red;
        transition: all 1s linear;
    }

    #demo.end{
        transform: translateX(300px);
    }
    .other{
        width: 100px;
        height: 100px;
        border: 1px solid red;
    }
  </style>
</head>

<body>
  <div class="wrapper">
    <div id="demo"></div>
    <div class=other>1</div>
    <div class=other>2</div>
  </div>
</body>
    <script>
        setTimeout(()=>{
            demo.remove()
        },3000)
    </script>
</html>

````

![](https://i.loli.net/2019/09/10/SmzhEwGLCW2cI4s.png)

remove时，会走<font color=red>第一种</font>更新方式。

> 例2：

````
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    #demo{
        width: 100px;
        height: 100px;
        border: 1px solid red;
        transition: all 1s linear;
    }

    #demo.end{
        transform: translateX(300px);
    }
    .other{
        width: 100px;
        height: 100px;
        border: 1px solid red;
    }
  </style>
</head>

<body>
  <div class="wrapper">
    <div id="demo"></div>
    <div class=other>1</div>
    <div class=other>2</div>
  </div>
</body>
 <script>
    setTimeout(()=>{
        demo.style.background = 'red'
    },3000)

 </script>
</html>
````

![](https://i.loli.net/2019/09/10/javTgwykRsEMdfb.png)

改变样式时，因为没有重新布局的地方，所有走的是<font color=red>第二种</font>更新方式

> 例3

````
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
  <style>
    #demo{
        width: 100px;
        height: 100px;
        border: 1px solid red;
        transition: all 1s linear;
    }

    #demo.end{
        transform: translateX(300px);
    }
    .other{
        width: 100px;
        height: 100px;
        border: 1px solid red;
    }
  </style>
</head>

<body>
  <div class="wrapper">
    <div id="demo"></div>
    <div class=other>1</div>
    <div class=other>2</div>
  </div>
</body>

</html>
````
开始渲染

![](https://i.loli.net/2019/09/10/uAIoLGf7n4UiQNk.png)

结束渲染

![](https://i.loli.net/2019/09/10/7raIWHcz9lNvw1u.png)

可以看出 ` translateX ` 只会在渲染开始前和渲染结束,在过程中是不会在渲染的,所以这时候 就知道那个` 性能 `好了吧？

建议： 做动画最好用transform和animation配合使用，这样性能会很好

每一个属性都有渲染过程

需要的时候可在 ` https://csstriggers.com/ `这个里查看

## transform 属性

四个常用功能：

* 位移：translate

* 缩放：scale

* 旋转：rotate

* 倾斜：skew

### translate

语法：

translateX(30px)    X轴

![](https://i.loli.net/2019/09/11/josVGRFEZO8qBmX.gif)

translateY(30px)    Y轴

![](https://i.loli.net/2019/09/11/muvTwS5QpHNoJ9F.gif)

translate(30px,40px)  X轴,Y轴

![](https://i.loli.net/2019/09/11/1aqtHnXPU8cGusD.gif)

translateZ(30px) 且父容器必须有perspective属性，（可自行MDN查看）

![](https://i.loli.net/2019/09/11/RWXt9flEcrCYVnm.gif)

translate3d(x,y,z)

tranlate(-50%,-50%)可做绝对定位元素居中

可以是数字，也可以使用百分数，50%：往右偏自身宽度的50%

perspective(1000) 视点是1000px 中心点

具体可查看 MDN文档

````
// 居中
#div {
    //不支持IE
    width: 100px;
    height: 100px;
    border: 1px solid red;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
}
````

### scale

scale（1.5） 变大到原来的1.5倍


scaleX（1.5） 变宽的1.5倍

scakeY(1.5,0.5)  X变宽，Y变低

![](https://i.loli.net/2019/09/11/fBdvRnYwWoguJEs.gif)

不经常使用，容易出现模糊，看上方图，边框是出现模糊的情况

### rotate

rotate(45deg) 旋转45度

rotateX(45deg) 在X轴旋转45deg

rotateY(45deg) 在Y轴旋转45deg

rotateZ(45deg) 在Z轴旋转45deg

rotate3d(45deg)

![](https://i.loli.net/2019/09/11/bODZENhauBSeXrJ.gif)

### skew

skewX(15deg) 在X轴倾斜15deg

skewY(15deg) 在Y轴倾斜15deg

skew(15deg,15deg) 在X轴倾斜15deg,在Y轴倾斜15deg

![](https://i.loli.net/2019/09/11/MNLWbTzH9fYyIm4.gif)


推荐配合着 ` transition `属性一起使用，这样可以做成动画，` transiton `属性看下面

![](https://i.loli.net/2019/09/11/DGc9YpjXgk1Ifbv.gif)


## transtion

> 作用

补充中间帧（只要给他一开始什么样子，结束什么样子。自动补全中间帧）

> 语法

transition: 属性名 时长 过渡方式 延迟

    transition: left 1s linear

可以使用逗号分隔两个不同属性

    transition: left 1s,top 2ms

可以使用all代表所有属性

    transition: all 200ms

过渡方式有：linerar | ease | ease-in | ease-out | ease-in-out | cubic-bezier | step-start | step-end | steps

<font color=red>注意： 不是所有属性都可以过渡</font>

display: none => block 没法过渡,
一般改成visibilitiy: hidden => visible 

js监听过渡完成

````
div.addEventListener('transitionend',() => {
    console.log("完成")
})
````

## animation

> 语法

animation: 时长 | 过渡方式 | 延迟 | 次数 | 方式 | 填充模式 | 是否暂停 | 动画名

    时长：1s 或者1000ms

    过渡方式：跟transition取值一样

    次数：3或者2.4或者 infinite

    方向：reverse | alternate | altenate-reverse

    reverse 反过来

    alternate 交替 

    altenate-reverse 交替反过来

    填充模式：none | forwards | backwards | both   //forwards 结束不动

    是否暂停：paused | running

    paused 暂停

    running 继续

### keyframes 语法

搜索 ` keyframes MDN ` 讲的更清楚

百分数的写法

````
@keyframes xxx {  // 声名关键帧
    0% {
        transform: none;
    }
    66% {
        transform: translateX(200px);
    }
    100% {
        transform: translateX(200px) translateY(300px)
    }
}
````

form / to 写法

````
@keyframes xxx {
    form {  // 开始
        transform: translateX(0%);
    }
    to {   // 结束
        transform: translateX(100%);
    }
}
````
看例子了  ` http://js.jirengu.com/jilaxenero/edit?html,css,output ` 会动的心 

