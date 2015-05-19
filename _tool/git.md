---
  layout: tool
  title: git
---

# git

## git描述

一个git项目一旦被克隆就包含了所有信息。如各个分支、各个改动等。如果服务器新建了分支，只需git pull即可访问分支


## ssh环境配置

ssh协议需要软件实现，windows的cmd是没有ssh软件的，需要git bash支持

使用ssh key，只需要在本地生成公钥，再把公钥上传到github里，就可以直接克隆github的项目了，无需输入密码

### 配置ssh key步骤

打开gitbush，首先在用户文件夹里建立一个.ssh的文件夹：

`cd ~`

`mkdir .ssh`


1.生成私钥公钥 ssh-keygen   回车到底

2.把.ssh文件夹的公钥id_rsa.pub上传到github，github的ssh key页面提供上传功能

3.保证使用ssh形式clone的github项目，直接push就可以成功，无需输入密码

如果项目是https协议或者没有ssh key，则每次都需要输入用户名和密码。


## git checkout

用于分支切换，如，`git checkout master`，`git checkout develop`

## git add

添加文件到git里，add后commit的时候才会提交此文件。如果要add本目录下所有子文件： `git add .`

## git commit

提交文件

-a 代表提交本项目所有add后的文件

-m 代表注释

## git pull

拉取最新的文件到本地

## git push origin develop

提交develop分支到服务器

## git diff 文件名

显示某个文件被修改了那些地方
