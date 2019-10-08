---
title: "Js对象"
date: 2019-10-08T16:38:19+08:00
categories:
- category
- subcategory
tags:
- javascript
keywords:
- javascript
#thumbnailImage: //example.com/image.jpg
---
js对象基础
<!--more-->

### 定义

1. 无序的数据集合
2. 键值对的集合
   
### js对象声明

````
let obj = {'name': 'gefei','age': 23}
let obj = new Object({'name': 'gefei','age': 23})
console.log({'name': 'gefei','age': 23})
````

### 细节

* 键名是字符串，不是标识符，可以包含任何字符
* 引号可以省略，省略之后就只能写标识符
* 就算引号省略了，键名也是字符串，（没有数字下标，都是字符串）

### 一些奇怪的属性名

````
let obj = {
    1: "a",
    3.2: 'b',
    1e2: true,
    1e-2: true,
    .234: true,
    0xFF: true
};
// 1e2 会变成100,js会自动计算，想要1e2作为属性名 可以使用‘1e2’,就不会自动计算
````
#### 小技巧

如果想要变量作为属性名

````
let a = "xxx";
let obj = {
    [a]: 111
}
演示：
{
    xxx: 111
}
````

#### 对象的隐藏属性

js中每一个对象都有一个隐藏属性

这个隐藏属性存储着其共有<font color=red>属性组成的对象</font>

这个<font color=red>共有属性组成的对象</font>叫做原型

隐藏属性叫做`__proto__`

## Object的一些方法

#### 删属性

````
delete obj.name 或 delete obj['name']  //删除值和名
````

检测是否删除了对象的属性

````
'name' in obj   // obj里是否有name属性  true/false	
````

#### 读属性

````
Object.keys(obj) // 查看对象的所有键名
Object.values(obj) // 查看对象的所有值
Object.entries(obj) // 查看所有属性和值
obj.__proto__  //查看自身所有的隐藏属性
obj.hasOwnPrototype('toString') // 判断一个属性是否是自身属性
obj['key'] // 中括号语法
obj.key // 点语法

````

#### 修改属性或值

````
// 一
let obj = {name: 'gefei'}
obj.name = 'bjll'
obj['name'] = 'abc'

Object.assign(obj,{age: 18,gender: 'man'}) //es6 新出
````

注意： 无法通过自身修改或增加共有属性

````
let obj = {}, obj2 = {} // 共有属性 toString
obj.toString = 'xxx' //只会在改obj自身属性
console.log(obj.toString)
// obj2.toString还是在原型上
````

修改或者增加原型上的属性

````
// 一
obj.__proto__.toString = "xxx"; // 不推荐使用__proto__
// 二
obj.prototype.toString = "xxx";
// 三
let common= {'name': '葛飞','age': 23}
let obj = Object.create(common)
obj.name = 'abc'
//这样的写法会生成原型链， create只是修改原型，注意最好不要修改原型，会出问题,推荐使用第三种 es6新出

````

### in 和 hasOwnPrototype的区别

````
'toString' in obj // true 检测自身属性和原型是否拥有此属性 true/false
obj.hasOwnProperty("toString") // false 检测属性是否是自身的，不会检测到原型
````