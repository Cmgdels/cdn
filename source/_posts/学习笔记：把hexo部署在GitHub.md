---
title: 学习笔记：把hexo部署在GitHub
date: 2021-10-24 08:20:53
tags: [github,hexo,ssh,termux]
categories: web
cover: https://i.niupic.com/images/2021/10/24/9Exj.png
---
## 前言

**这篇博文它不是教程，他是一篇笔记**如果你需要详细教程，请离开此地，懒人可以照着做，注意，本笔记**不适合Windows**
这次我们把搭建好的博客部署到GitHub，日后你可以进行美化，**下文的素质三连指`hexo cl & hexo g -d`**
# 链接GitHub
## 1.1 安装openssh

首先你需要有GitHub账户，没有请你注册（建议使用国外邮箱），不会的你可以走了

termux木有安装openssh，所以让我们手动安装

```bash
pkg install openssh
```
## 1.2 链接GitHub
然后做一些准备工作，绑定GitHub账户信息

```bash
git config --global user.name "你的用户名"

git config --global user.email "你的邮箱@example.com"

ssh-keygen -t rsa -C "你的邮箱@example.com"
```
执行到最后一串代码时，会让你输入密钥密码，想输入就输入，不想回车，然后`vim ~/.ssh/id_rsa.pub`，复制所有内容，准备输入进GitHub。
进入 [github ssh](https://github.com/settings/keys) 点击New SSH Key把之前复制的内容粘贴到这里就可以了。
# 部署博客
## 1.1建立GitHub仓库

![](https://i.niupic.com/images/2021/10/24/9Exj.png)

## 1.2 上传文件以及访问
配置`_config.yml`
```
deploy:
  type: git
  repo: #你的仓库地址              
        #如:https://github.com/milovemengmeng/milovemengmeng.github.io.git 复制ssh链接。进入仓库主页，code-ssh
  branch: master
```
安装部署插件
bash```
npm install hexo-deployer-git --save
```
在你博客根目录素质三连一下就好了，然后打开`GitHub用户名.github.io`即可看到你的博客页面


