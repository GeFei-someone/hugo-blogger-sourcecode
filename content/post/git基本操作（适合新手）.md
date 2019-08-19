---
title: "Git基本操作（适合新手）"
date: 2019-08-19T13:59:30+08:00
categories:
- git
- github
tags:
- git
- github
keywords:
- tech
#thumbnailImage: //example.com/image.jpg
---

<!--more-->
本人也是刚刚开始学习 大家可以一起交流，大佬可以在教一下 

目录
<br>

1. git配置
2. git本地仓库
3. SSH提交方式，git提交远程仓库

## 一、git配置
```` js
git config --global user.name 你的英文名
git config --global user.email 你的邮箱
git config --global push.default simple //simple必须保证本地分支和它的远程upstream分支同名，否则会拒绝push操作。
git config --global core.quotepath false //解决中文乱码问题
git config --global core.editor "code --wait" //默认文本编辑器 vscode打开
git config --global core.autocrlf input // 在提交时把CRLF转换成LF,签出时不转换
````
````!
注意：上面的英文名和邮箱跟 GitHub 没有关系，可以一样也可以不一样
````
```! 
 可能写的有问题，可自行百度6行配置的翻译
```

```` js
git config --gloval --list 查看配置
````
---
## 二、git本地仓库

新建目录 git-demo 
<br>
```` js
git init // 初始化
````

![](/images/blok1/1.png)
````!
注意：git init 只是创建 .git目录（隐藏的） 他的功能类似于快照
````
<br>

创建一个html文件，用来做操作
<br>
<br>
开始操作
<br>
```` js
git add index.html // 标记index.html
````

![](/images/blok1/2.png)

```` js
git status -sb // 查看需要提交的文件
````

![](/images/blok1/3.png)

A 代表` git add `了 
<br>
<font color=red size=2>还有别的状态,后面给介绍</font>

```` js
 git commit -v //提交并且打开默认编辑器，如果git6行配置你配置了，就会打开vscode 如果没有会打开vim编辑器
````
静静等待你的电脑端打开vsCode

![](/images/blok1/4.png)
打开成功会是这样的：


![](/images/blok1/5.png)
会让你看到代码里那块修改了，那块删除了 可以多写一点提交理由（在第一行写）
<br>
<br>
````!
写完保存->关闭
````


![](/images/blok1/6.png)


 回滚版本
 <br>

```` js
 git log // 查看版本
````

![](/images/blok1/7.png)

` git logo `查看一下提交过的版本信息，注意` commit `版本号

```` js
git reset --hard 5ea4ce // 回滚到第一个版本
````

![](/images/blok1/8.png)
![](/images/blok1/9.png)
成功


在查看一下版本（` git log `）

![](/images/blok1/10.png)
已经回到最初的版本了。

````!
注意：回滚完了就找不到之前的版本了
````

<br>
这里说一个高级操作 <font color=red size=2>git reflog</font> 查看全部版本历史
<font color=#8F8F8F size=2>（手动斜眼笑）</font>

![](/images/blok1/11.png)

想回滚到那个版本都可以了
<br>
````!
注意：运行 reset 命令前，一定要确保重要代码已经提交（commit）了,如果只是` git add `了但是没有` git commit ` 在回滚版本会丢失文件。版本号可以是6位也可以是4位只要保证是唯一的就可以
````

分支
<br>
```` js
 git branch a // 创建a分支
````

![](/images/blok1/12.png)
<font color=red size=2>会基于本地仓库里最新一次 commit，创建一个新的分支 a </font>
```` js
 git checkout a // 切换到a分支
````

![](/images/blok1/13.png)
文档改一下内容


![](/images/blok1/14.png)
` git add ` -> ` git commit ` 一下 


![](/images/blok1/15.png)

```` js 
 git branch // 查看分支 带 * 号是当前分支
````

![](/images/blok1/16.png)

```` js 
 git branch -d x // 删除分支，x新创建的分支
````

![](/images/blok1/17.png)

如果没有合并代码，` git branch -d x ` 会报错，如果必须删这个分支，可以使用 ` git branch -D x`

 合并分支
 <br>
```` js
 git merge a // 合并分支
````
````!
注： 最好切换到master分支，保留主分支（master）
````

![](/images/blok1/18.png)

 解决冲突
 <br>

合并分支和` git pull `时遇到的冲突,会报<font color=red size=1>CONFLICT</font>错误
![](/images/blok1/19.png)
可以使用 `git status -sb`查看冲突文件
切换到a分支 修改了 h1标签里的内容导致了冲突 因为master和a分支都写了这个地方，在vscode里就会出现冲突提示

![](/images/blok1/20.png)
UU ：2个分支都修改了此文件
<br>
vsocde会提示冲突
![](/images/blok1/21.png)
解决冲突的方式：
<br>

* 可以选择上面，也可以选择下面，甚至都可以选择
* 删除不需要的代码，（==== >>>> <<<<）
* 最次` git status -sb` 修改下一个文件
* `git add` 对应的文件
* 没有冲突了，在commit一下

我选择了保留双方更改
![](/images/blok1/22.png)

## 三、SSH提交方式，git提交远程仓库
github创建一个仓库

![](/images/blok1/23.png)

![](/images/blok1/24.png)

> 接下来生成SSH

```` js
 ssh-keygen -t rsa -b 4096 -C 邮箱
````
成功：
![](/images/blok1/25.png)
执行中 连续按3次回车就可以了,成功就会出现小气泡
<br>
失败
![](/images/blok1/26.png)
出现<font color=red size=2> Overwrite(y/n)</font> 表示失败 请去默认保存地址去删除SSH
或者备份

![](/images/blok1/27.png)

* id_res 私钥
* id_rsa.pub 公钥

自己保留私钥，gitHub设置公钥

````!
注意：私钥不要给别人看，也不要发给别人
````

 设置gitHub的公钥
 <br>

![](/images/blok1/28.png)



![](/images/blok1/29.png)
进入默认ssh存放目录 打开 id_rsa.pub 文件 复制进 key里 然后点 Add SSH key就可以了
![](/images/blok1/30.png)
添加时需要验证一次密码
验证SSH
<br>
```` js
ssh -T git@github.com // 如果问你(yes/no) 输入yes回车
````
![](/images/blok1/31.png)
````!
注：SSH和HTTPS的下载 SSH是不需要输入密码的，HTTPS是需要每次需要密码的
````
<br>
<br>
好了SSH的配置就结束了，现在开始提交gitHub

提交gitHub
 <br>
```` js
 git remote add origin git@github.com:GeFei-someone/gitdemo-2.git // 连接远程仓库 
````
![](/images/blok1/32.png)

```` js
git pull origin master // 更新  提交前最好先更新一下 如果代码没有别的同事修改，就可以直接提交
````
```` js
 git push -u origin master //提交 -u：记住这次操作 下次只需要 git push 就可以了
````

![](/images/blok1/33.png)

![](/images/blok1/34.png)
提交成功！！！
如果你是一个空目录 需要从github上克隆代码需要使用:

<font color=red size= 2>__一定要切换到SSH上复制__</font>
![](/images/blok1/35.png)

```` js
git clone origin git@github.com:GeFei-someone/gitdemo-2.git // 克隆项目
git clone origin git@github.com:GeFei-someone/gitdemo-2.git yyy // 克隆项目并且重命名为 yyy
git clone git@github.com:feiwen1119/git-demo-1.git . // 考虑项目不重新创建目录，使用当前目录容纳代码
````
````!
注：当前目录最好是空目录
````
![](/images/blok1/36.png)
成功！！！
![](/images/blok1/37.png)


## 结束语
因为没有结束语所以不写了