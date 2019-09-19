---
title: "Js基本语法"
date: 2019-09-19T17:04:57+08:00
categories:
- javascript
tags:
- javascript
keywords:
- javascript
#thumbnailImage: //example.com/image.jpg
---
介绍js的基本语法

<!--more-->

目录

1. 表达式与语句
2. 标识符
3. 空格
4. 注释
5. 区块
6. if语句
7. switch语句
8. 三元表达式
9. && || （短路逻辑）
10. while循环
11. for循环
12. break和continue
13. label

## 表达式与语句

> 表达式

1+2 表达式的值为3

add(1,2) 表达式的值为函数返回值，（只有函数有返回值)

console.log表达式的值为函数本身（函数表达式）

console.log(3) 表达式的值什么？

````
 console.log(3)  // undefined log方法代码里只写了一个return  return会自动补充undefined
````
> 语句

var a = 1 

> 区别

表达式一般有值，语句可能有也可能没有

语句一般是用来改变环境（声名，赋值）

## 标识符

变量名就是标识符

````
var _ = 1

var $ = 2

var ______ = 6

var 123 = 'hi'

````

> 规则

第一个字符，可以是Unicode字母或 $ 或 _ 或 中文（第一位不能是数字）

第二位开始的字符，除了上面说的，还可以使用数字


## 注释

只有2种

````
 // 

 /*
    
 */
````

> 建议

只在踩坑的地方写注释

为什么代码写这么奇怪，遇到了什么bug

在这些地方写注释，不要把代码翻译成中文

## 空格

大部分空格是没有实际意义的

var a = 1 和 var a=1 没有区别的

加回车大部分也是不影响的

只有一个地方不能加回车，那就是return

````
 function fn() {
     return   //这个属于在这里已经结束了 直接返回了 不会返回 3，而且还会补充undefined

     3
 }
````

## 区块

把代码包起来

````
 {
     let a = 1;
     let b = 2;
 }
````

常常与if / for / while 合用

## if语句

> 语法

if(表达式) {语句1} else {语句2}

{}在语句只有一句的时候可以省略，不建议这么做

推荐写法

````
if(表达式) {

}else if(表达式) {

}else {

}

````
> 变态写法

````
let a = 1;

if(a === 3) 
    console.log(1)
    console.log(2)  // 只会输出2  因为 a不等于3 所以不执行console.log(1),console.log(2)属于后语句了，已经不在if判断里面了，
````

## switch 语句

语法

````
switch(表达式) {
    case "banana": 
        // ...
    break;
    case "apple": 
        // ...
    break;
    default: 
    // ...
}
````
大部分时候，省略break你就完了,会进死循环

少部分时候，可以利用break，做多判断语句

必须写break,不会会走到另一个判断中

## 问号冒号表达式（三元表达式）

语法
    
    表达式1 ? 表达式2：表达式3

如果表达式1 为真就执行表达式2，为假就执行表达式3

## && || （短路逻辑）

###### &&
````
let a = false;
a && console.log(123)

````

> 第一个表达式为假执行返回a的值，语句中碰到第一个假整段语句都是假，

````
let b = true;
b && console.log(123)
````
> 第一个表达式为真，继续执行后面的语句

````
let a = true
let b = true
a && b && console.log(123)
````
> a / b 都为真，执行最后的语句

###### ||

````
let a = false || 6;

console.log(a); //返回的结果为 6
````
> 左边为false，那么就返回右边的值，（不管右边的值是真还是假）。

````
let a = true || 6;

console.log(a); //返回的结果为 true
````

> 左边为true直接取左边的值，由此看出 || 是取第一个不为false的值

## while循环

> 语法
while（表达式）{语句}

判断表达式的真假

当表达式为真，执行语句，执行完再次判断表达式的真假

当表达式为假，执行后面语句

>写法

````
let i = 0;
while(i < 10) {

console.log(i)

i = i++

}
````
少写一个都会变成死循环,所以升级成了for循环

## for循环

>语法

for循环是while循环的方便写法

````
for(let i = 0; i < 10; i++) {
    console.log(i)
}
````
先执行语句1

然后判断语法2

如果为真，行循环体，然后执行语句3

如果为假，直接退出循环，执行后面的语句

## break和continue

break： 退出当前循环的所有循环

continue： 退出当前循环的本次循环

## label （面试可能会问）

````
{
foo: 1
}
````
foo是一个label  他的语句就是一个1

> 推荐入门文章

http://wangdoc.com/javascript/basic/grammar.html

> 推荐书籍（1-2年的前端进阶）

https://book.douban.com/subject/26351021/

