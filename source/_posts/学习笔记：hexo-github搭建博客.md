---
title: 学习笔记：hexo+github搭建博客(termux)
date: 2021-10-24 08:02:19
categories: ['web','Termux']
tags: ['github','termux','hexo']
cover: https://i.niupic.com/images/2021/10/24/9Exd.png
---

## 前言
**这篇博文它不是教程，他是一篇笔记**如果你需要详细教程，请离开此地，懒人可以照着做，注意，本笔记**不适合Windows**
本文章讲解如何在termux中安装hexo，其他系统可能不适用
# 安装博客
## 1. 安装nodejs
```bash
pkg install nodejs
```
## 1.1 准备博客文件夹
```bash
mkdir xxxxx
```
## 1.2 安装Hexo
```bash
npm install -g hexo-cli
```
## 1.3 配置博客

```bash
hexo init
```

```bash
hexo g
```

## 1.4 测试链接

输入以下命令后进入[本机4000端口](127.0.0.1:4000),你就可以看到最初的博客页面
```bash
hexo s
```
可以改端口，命令如下
```bash
hexo s -p xxxx
```


