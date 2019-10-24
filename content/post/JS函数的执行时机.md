---
title: "JS函数的执行时机"
date: 2019-10-23T10:39:20+08:00
categories:
  - javascript
tags:
  - javascript
keywords:
  - tech
#thumbnailImage: //example.com/image.jpg
---

<!--more-->

先来一个常见的面试题

```
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
// 6 个 6
```

为什么不是 0-5 呢？

答案是:在 i = 0 时，由于 js 是异步运行机制，导致当 setTimeout 计时的过程中,for 循环继续在执行，又因为 for 循环的执行时间远远小于计时时间，所以 for 的循环完成即 i = 6.当 i = 0 时，开启一个定时， i = 1 时又开启一个定时,i=2 时开启一个定时，所以开启了 6 个定时，当第一个定时时间到了之后 for 循环执行了 6 次，开启了 6 个定时，所以 i = 5,后面的定时器就会按照开启的间隔时间依次输出 5

解决办法：

一：let 方式

```
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
```

二：闭包方式

```
for(var i = 0;i < 6; i++) {
  ((i) => {
    setTimeout(() => {
      console.log(i)
    },i*1000)
  })(i)
}
```

由于定时函数在闭包内，每次都将 i 的值传入了闭包内，不会由于 for 循环的继续执行而被污染，外部的 for 循环的 i 值不会影响闭包内部的值

三：立即执行函数方式

```
for (var i = 0; i < 5; i++) {
  setTimeout((function () {
      console.log(i);
  })(),i*1000);
  console.log(i,"执行第" + i + "次for循环");
  }
```
