---
title: git基础
categories: java基础
cover_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1548248701909&di=4f5a2f1fbb411b973ea12fcc3e0cf4a0&imgtype=0&src=http%3A%2F%2Fimg.mukewang.com%2F5837a38f00015b6905960404.png
feature_img:  http://www.pptbz.com/pptpic/UploadFiles_6909/201408/2014080414534056.jpg
description: git的基本配置和git的基本使用和git的版本管控 
keywords: 设计模式

---
<meta name="referrer" content="no-referre"/>

### 安装github
<!--more-->
点击下面的链接可以到达git下载，根据你的安装系统进行安装

https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git
<!-- more -->

### 最小配置（配置user信息）
配置user.name 和user.email 信息

	git config --global user.name 'your_name'
	git config --global user.email 'your_email@domain.com'

**配置user信息原因：**每次的变更都是带着个人信息，git会自动的把变更者的信息取出来，然后发送邮件给变更人

其中 --global 的配置是可以更改的

	git config --local   //local只对每个仓库有效
    git config --global   //global对当前用户的所以仓库有效
	git config --system   //system对系统所以登陆的用户有效

仓库：在使用git的时候，git会管理文件系统，比如，你在C盘的git文件中创建了一个git的仓库，这个仓库就相当于一个独立的项目管理的区域；

可以使用 **--list**来查看某个配置的所有的信息,例如
	
	git config --list --global 

### 创建Git仓库
两个场景：

1.把已有的项目代码纳入到Git管理
	
	cd 项目代码所在文件夹
	git init

2.新建的项目直接用Git管理（还没用项目代码）
	
	cd 某个文件夹	
	git init your_project_name  #会在当前路径下创建和项目名称同名的文件夹
	cd your_project_name

### 往仓库添加文件

**版本历史**<--(git commit -m '添加的原因')--**暂存区**<--（git add files（git add -u :提交所有的文件））-- **工作目录**

### 重命名文件名
如果使用mv修改文件名，会导致git会重新添加一个文件名，并且原来的的文件也存在

		mv readme  readme.md  //加入文件名叫readme 想要改为readme.md

那么我们就要删除原来的文件

	 	git rm readme   //删除readme
		git add readme.md   //再添加文件

现在我们重新清除到暂存区里面的东西，使用另外一种方式来重命名：

	git reset --hard  //清除暂存区里面所有的东西
	gir mv readme  readme.md  //加入文件名叫readme 想要改为readme.md

### git log查看版本演变历史

- git log --all 查看所有分支的历史
- git log --all --graph 查看图形化的 log 地址
- git log --oneline 查看单行的简洁历史。
- git log --oneline -n4 查看最近的四条简洁历史。
- git log --oneline --all -n4 --graph 查看所有分支最近 4 条单行的图形化历史。
- git help --web log 跳转到git log 的帮助文档网页

### 通过图形界面查看版本历史
	
	gitk

![](https://i.imgur.com/J6tCQ1T.png)


### 探秘.git目录
config:存放配置信息(我们在配置user信息的时候，配置过config)

HAD:你正在工作在那个分支(编辑head可以进行切换分支)

refs：存放各个分支，或者是tags的信息 

- tags:存放tag,又名里程碑（项目开发到一定的程序，你就可以标识v1.0，到下一个阶段可以是v2.0）
- heads:分支，独立的开发空间
	- master  属于commit对象
	- temp		属于commit对象
- objects：存放对象 

git car-file：显示版本库对象的内容、类型及大小信息

git car-file -t 哈希值：查看该哈希值对象的类型

git car-file -p 哈希值：查看该哈希值对象的内容

git car-file -s 哈希值：查看该哈希值对象的大小	

### 分离头指针
分离头指针的含义：表示我们正工作在一个没有分支的状态下
缺点：容易没有在某个分支下进行，git会认为操作的数据，属于垃圾数据，就会导致数据丢失。
分离头指针的使用：当我们想操作一些变更，但是这个变更你只是尝试下，如果你决定觉得这个变更不好，那么你就可以切换到其他的分支，之前的变更也不会存储







