---
title: 教程：Termux配置oh-my-zsh
date: 2021-10-24 12:33:22
tags: [termux,oh-my-zsh]
categories: Termux
cover: https://i.niupic.com/images/2021/10/24/9Exv.png
---


## 前言
**注意：本笔记有可能不适合其他系统**你受够termux的bash了吗，来试试oh-my-zsh，我对oh-my-zsh的理解是zsh的升级版，还可以装插件。

## 准备工作

- Termux最新版

## 安装oh-my-zsh以及配置主题

此命令源于[国光的termux教程](https://www.sqlsec.com/2018/05/termux.html)，这个命令不需要使用科学上网。
执行以下命令需要安装curl
```bash
sh -c "$(curl -fsSL https://html.sqlsec.com/termux-install.sh)"
```
然后它会请求储存权限，允许就好了。允许后会让你选择字体和主题配色，自己一个个试吧。然后重启Termux
如果出错或者其他问题，请在科学上网环境下面执行以下代码解决
```bash
sh -c "$(curl -fsSL https://github.com/Cabbagec/termux-ohmyzsh/raw/master/install.sh)"
```

## 安装插件

oh-my-zsh里面最吸引人的就是各式各样的插件，这里推荐一个自动补全代码的插件，使用方向右键即可补全。

```bash
# 拷贝到 plugins 目录下
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
以上命令源于国光的termux教程
然后在`~/.zshrc`里面配置
```
plugins=(其他的插件 zsh-autosuggestions)
```
![](https://i.niupic.com/images/2021/10/24/9ExG.png)
![](https://i.niupic.com/images/2021/10/24/9ExH.png)

## 更换主题

编辑`~/.zshrc`，第一行就是设置主题的，可以看到默认是`agnoster`，其实这个也不错的，如果不喜欢，你可以百度一下优秀的oh-my-zsh主题
## 可选美化

### 1更改光标
以下命令以及图片源于酷安@Kuan_Root

```bash
echo -e '\e[2 q' # Change to block 图一
echo -e '\e[6 q' # Change to bar 图二
echo -e '\e[4 q' # Change to underline 图三
```
![图1](https://i.niupic.com/images/2021/10/24/9Exw.jpg)
![图2](https://i.niupic.com/images/2021/10/24/9Exy.jpg)
![图3](https://i.niupic.com/images/2021/10/24/9Exx.jpg)
如果要一直保持，请把你喜欢的光标设置代码放进~/.zshrc
### 2 隐藏用户名

当你使用`agnoster`主题的时候，光标前面可能会出现用户名，这个用户名基本没有，所以你可以把它隐藏
![图源于酷安@Imagawa](https://i.niupic.com/images/2021/10/24/9Exz.jpg)

以下代码源于酷安@Kuan_Root，把它们放在你的~/.zshrc
```
prompt_context() {
if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
fi
}
```
效果如下
![效果](https://i.niupic.com/images/2021/10/24/9ExB.png)


