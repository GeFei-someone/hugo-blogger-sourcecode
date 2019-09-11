---
title: "JavaScript的诞生"
date: 2019-09-11T11:26:56+08:00
categories:
- javascript
tags:
- javascript
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---
javaScript的历史、设计缺陷
<!--more-->

## 历史

它最初由Netscape的Brendan Eich设计。JavaScript是甲骨文公司的注册商标。Ecma国际以JavaScript为基础制定了ECMAScript标准。JavaScript也可以用于其他场合，如服务器端编程。完整的JavaScript实现包含三个部分：ECMAScript，文档对象模型，浏览器对象模型。

Netscape在最初将其脚本语言命名为LiveScript，后来Netscape在与Sun合作之后将其改名为JavaScript。JavaScript最初受Java启发而开始设计的，目的之一就是“看上去像Java”，因此语法上有类似之处，一些名称和命名规范也借自Java。但JavaScript的主要设计原则源自Self和Scheme。JavaScript与Java名称上的近似，是当时Netscape为了营销考虑与Sun微系统达成协议的结果。为了取得技术优势，微软推出了JScript来迎战JavaScript的脚本语言。为了互用性，Ecma国际（前身为欧洲计算机制造商协会）创建了ECMA-262标准（ECMAScript）。两者都属于ECMAScript的实现。尽管JavaScript作为给非程序人员的脚本语言，而非作为给程序人员的脚本语言来推广和宣传，但是JavaScript具有非常丰富的特性。

发展初期，JavaScript的标准并未确定，同期有Netscape的JavaScript，微软的JScript和CEnvi的ScriptEase三足鼎立。1997年，在ECMA（欧洲计算机制造商协会）的协调下，由Netscape、Sun、微软、Borland组成的工作组确定统一标准：ECMA-262。

## 诞生

1994年，网景公司（Netscape）发布了Navigator浏览器0.9版。这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。......网景公司急需一种网页脚本语言，使得浏览器可以与网页互动。

网页脚本语言到底是什么语言？网景公司当时有两个选择：一个是采用现有的语言，比如Perl、Python、Tcl、Scheme等等，允许它们直接嵌入网页；另一个是发明一种全新的语言。

这两个选择各有利弊。第一个选择，有利于充分利用现有代码和程序员资源，推广起来比较容易；第二个选择，有利于开发出完全适用的语言，实现起来比较容易。

到底采用哪一个选择，网景公司内部争执不下，管理层一时难以下定决心。

就在这时，发生了另外一件大事：1995年Sun公司将Oak语言改名为Java，正式向市场推出。

Sun公司大肆宣传，许诺这种语言可以"一次编写，到处运行"（Write Once, Run Anywhere），它看上去很可能成为未来的主宰。


网景公司动了心，决定与Sun公司结成联盟。它不仅允许Java程序以applet（小程序）的形式，直接在浏览器中运行；甚至还考虑直接将Java作为脚本语言嵌入网页，只是因为这样会使HTML网页过于复杂，后来才不得不放弃。

总之，当时的形势就是，网景公司的整个管理层，都是Java语言的信徒，Sun公司完全介入网页脚本语言的决策。因此，Javascript后来就是网景和Sun两家公司一起携手推向市场的，这种语言被命名为"Java+script"并不是偶然的。

## 发明者

Brendan Eich。1995年4月，网景公司录用了他   

![](http://www.ruanyifeng.com/blogimg/asset/201106/bg2011060503.jpg)

Brendan Eich的主要方向和兴趣是函数式编程，网景公司招聘他的目的，是研究将Scheme语言作为网页脚本语言的可能性。

仅仅一个月之后，1995年5月，网景公司做出决策，未来的网页脚本语言必须"看上去与Java足够相似"，但是比Java简单，使得非专业的网页作者也能很快上手。这个决策实际上将Perl、Python、Tcl、Scheme等非面向对象编程的语言都排除在外了。

Brendan Eich被指定为这种"简化版Java语言"的设计师。

但是，他对Java一点兴趣也没有。为了应付公司安排的任务，他只用10天时间就把Javascript设计出来了。

由于设计时间太短，语言的一些细节考虑得不够严谨，导致后来很长一段时间，Javascript写出来的程序混乱不堪。如果Brendan Eich预见到，未来这种语言会成为互联网第一大语言，全世界有几百万学习者，他会不会多花一点时间呢？

总的来说，他的设计思路是这样的：

````
　　（1）借鉴C语言的基本语法；

　　（2）借鉴Java语言的数据类型和内存管理；

　　（3）借鉴Scheme语言，将函数提升到"第一等公民"（first class）的地位；

　　（4）借鉴Self语言，使用基于原型（prototype）的继承机制。
````

所以，Javascript语言实际上是两种语言风格的混合产物----（简化的）函数式编程+（简化的）面向对象编程。这是由Brendan Eich（函数式编程）与网景公司（面向对象编程）共同决定的。

## 为什么Javascript有设计缺陷？

这里有三个客观原因，导致Javascript的设计不够完善。

1. 设计阶段过于仓促

Javascript的设计，其实只用了十天。而且，设计师是为了向公司交差

另一方面，这种语言的设计初衷，是为了解决一些简单的网页互动（比如，检查"用户名"是否填写），并没有考虑复杂应用的需要。设计者做梦也想不到，Javascript将来可以写出像Gmail这种极其庞大复杂的网页。

2. 没有先例

Javascript同时结合了函数式编程和面向对象编程的特点，这很可能是历史上的第一例。而且直到今天为止，Javascript仍然是世界上唯一使用Prototype继承模型的主要语言。这使得它没有设计先例可以参考。

3. 过早的标准化

Javascript的发展非常快，根本没有时间调整设计。

1995年5月，设计方案定稿；10月，解释器开发成功；12月，向市场推出，立刻被广泛接受，全世界的用户大量使用。Javascript缺乏一个从小到大、慢慢积累用户的过程，而是连续的爆炸式扩散增长。大量的既成网页和业余网页设计者的参与，使得调整语言规格困难重重。

更糟的是，Javascript的规格还没来及调整，就固化了。

1996年8月，微软公司强势介入，宣布推出自己的脚本语言Jscript；11月，为了压制微软，网景公司决定申请Javascript的国际标准；1997年6月，第一个国际标准ECMA-262正式颁布。

也就是说，Javascript推出一年半之后，国际标准就问世了。设计缺陷还没有充分暴露就成了标准。相比之下，C语言问世将近20年之后，国际标准才颁布。

## 10个设计缺陷

###### 1、不适合开发大型程序

Javascript没有名称空间（namespace），很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。

###### 2、非常小的标准库

Javascript提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。

###### 3、null和undefined

null属于对象（object）的一种，意思是该对象为空；undefined则是一种数据类型，表示未定义。

````
    typeof null; // object

　　typeof undefined; // undefined
````

两者非常容易混淆，但是含义完全不同。

````
    var foo;

　　alert(foo == null); // true

　　alert(foo == undefined); // true

　　alert(foo === null); // false

　　alert(foo === undefined); // true
````

在编程实践中，null几乎没用，根本不应该设计它。

###### 4、全局变量难以控制

Javascript的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。

````
　　a = 1;

　　(function(){

　　　　b=2;

　　　　alert(a);

　　})(); // 1

　　alert(b); //2
````

###### 5、自动插入行尾分号

Javascript的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。

比如，下面这个函数根本无法达到预期的结果，返回值不是一个对象，而是undefined。

````
　　function(){

　　　　return
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
````

原因是解释器自动在return语句后面加上了分号。

````
　function(){

　　　　return;
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
````

###### 6、加号运算符

+号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。

````
　　alert(1+10); // 11

　　alert("1"+"10"); // 110
````

如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。

````
　alert(1+"10"); // 110

　alert("10"+1); // 101
````

这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。

###### 7、NaN

NaN是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：

````
　　NaN === NaN; //false

　　NaN !== NaN; //true

　　alert( 1 + NaN ); // NaN
````
与其设计NaN，不如解释器直接报错，反而有利于简化程序。

###### 8、数组和对象的区分

由于Javascript的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。Douglas Crockford的代码是这样的：

````
　　if ( arr && 
　　　　typeof arr === 'object' &&
　　　　typeof arr.length === 'number' &&
　　　　!arr.propertyIsEnumerable('length')){

　　　　alert("arr is an array");

　　}
````

###### 9、== 和 ===

==用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。

````
　　"" == "0" // false

　　0 == "" // true

　　0 == "0" // true

　　false == "false" // false

　　false == "0" // true

　　false == undefined // false

　　false == null // false

　　null == undefined // true

　　" \t\r\n" == 0 // true
````

因此，推荐任何时候都使用"==="（精确判断）比较符。

###### 10、基本类型的包装对象

Javascript有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。

````
　　new Boolean(false);

　　new Number(1234);

　　new String("Hello World");
````

与基本数据类型对应的对象类型，作用很小，造成的混淆却很大。

````
　　alert( typeof 1234); // number

　　alert( typeof new Number(1234)); // object
````

原文地址：

10个设计缺陷：http://www.ruanyifeng.com/blog/2011/06/10_design_defects_in_javascript.html

Javascript诞生记： http://www.ruanyifeng.com/blog/2011/06/birth_of_javascript.html