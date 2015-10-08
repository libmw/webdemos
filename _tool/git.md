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

### 如果一台电脑两个ssh账号，则需要生成两个ssh

1.切换到.ssh目录，执行 ssh-keygen -t rsa -C "your-email-address" 执行后输入一个名称如id_rsa_qq

2.把生成的id_rsa_qq.pub里的东西粘贴到git上

3.先执行 eval "$(ssh-agent)"，再执行 ssh-add ~/.ssh/id_rsa_qq 把生成的key加到ssh里

4.再修改config文件 ：

Host github
  HostName github.com
  IdentityFile ~/.ssh/id_rsa

Host github_qq
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_qq

`修改后，clone的时候要把github.com改为github_qq`

5.最后在项目下修改提交者的用户名和用户邮箱： git config user.name "lmj"  git config user.email "627574754@qq.com"

这样不方便的就是clone的时候需要修改下地址，二是需要从新指定提交者的邮箱，不然就会默认用global里的用户名和邮箱来提交了。

注意，如果指定了一个github上不存在的邮箱，在commit信息里会只显示用户名。

一旦使用了这个sshkey成功push了代码 sshkeys页面的key前的灰色圆点就会变为绿色。



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

## git remote -v

查看远程分支地址

## git diff 文件名

显示某个文件被修改了那些地方

## 开分支

### 创建分支

git branch mystudygit1.0

分支创建后，需要push到服务器服务器才能有新分支。

其他人需要pull后才能看到新分支

### 切换分支
git checkout mystudygit1.0

### 删除分支
git branch -d mystudygit1.0  //如果该分支没有合并到主分支会报错
或者
git branch -D mystudygit1.0   //强制删除
