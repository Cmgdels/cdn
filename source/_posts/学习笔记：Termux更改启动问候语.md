---
title: 学习笔记：Termux更改启动问候语以及换源
date: 2021-10-25 14:06:58
tags: termux
categories: Termux
---
## 前言

这个问候语对于Termux初学者是有一丁点帮助的~~没有帮助的~~，等你已经熟悉了Termux后，你就完全不需要它了，于是我们可以把它修改一下。

## 修改启动问候语

```bash
vim $PREFIX/etc/motd
```

然后删掉所有内容，自己往里面写，全选并删除快捷键：`ggvGd`（vim快捷键，在只读模式下使用）

这里有一个比较好的

```
 _____
|_   _|__ _ __ _ __ ___  _   ___  __
  | |/ _ \ '__| '_ ` _ \| | | \ \/ /
  | |  __/ |  | | | | | | |_| |>  <
  |_|\___|_|  |_| |_| |_|\__,_/_/\_\
```

from：[国光的termux教程](https://www.sqlsec.com/2018/05/termux.html#)

然后保存，重启Termux就OK了。

### 换源

如果不换源（**意思就是更改线上程序仓库**）我们的Termux会很慢，因为程序仓库在国外，我们可以把这个程序仓库换成清华大学的仓库，（怎么换其他仓库自己百度）输入以下命令即可。

```bash

sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list

sed -i 's@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@' $PREFIX/etc/apt/sources.list.d/game.list

sed -i 's@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@' $PREFIX/etc/apt/sources.list.d/science.list

pkg update
```
对，就是这么多，不要一段一段的执行，直接复制粘贴回车

> 有选择一律选择yes，即输入y，出问题重新执行

然后重新Termux，输入`pkg update`，是不是变快了很多？

### 安装基本工具

Termux为了节约空间，没有安装一些其他东西，像[Arch Linux](https://baike.baidu.com/item/arch/1614148?fromtitle=archlinux&fromid=10857530&fr=aladdin)一样，所以我们需要自己安装。

```bash
pkg update
pkg install vim curl wget git tree -y
```

大功告成。


