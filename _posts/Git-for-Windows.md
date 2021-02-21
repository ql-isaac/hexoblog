---
title: Git for Windows
date: 2021-01-03 15:27:43
cover: https://image.ql-isaac.cn/Git.gif
tags:
 - Windows 10 企业版 LTSC
categories:
 - Git和GitHub从入门到实践
---

　　来记录一下Git for Windows的使用。

<!-- more -->

## 2020-1-3

　　每次打开VS Code时右下角总提示这个，还是更新一下吧，直接点击更新GIT。

![更新GIT](https://image.ql-isaac.cn/Git-for-Windows/更新GIT.png)

　　原来是跳转到Git官网。

![Git官网](https://image.ql-isaac.cn/Git-for-Windows/Git官网.png)

{% note warning %}

这里会跳转到IE浏览器，呵呵，赶紧在所有设置-应用-默认应用中把Web浏览器设置成Microsoft Edge再打开Git官网。

{% endnote %}

![Microsoft Edge](https://image.ql-isaac.cn/Git-for-Windows/Microsoft-Edge.png)

　　常规操作：下载，双击安装。

![下载安装](https://image.ql-isaac.cn/Git-for-Windows/下载安装.png)

　　Only show new option，嗯，很人性化！好评！

![Only show new option](https://image.ql-isaac.cn/Git-for-Windows/Only-show-new-option.png)

　　勾选第二个，以后用`git init`初始化的默认分支名就为main了。

{% note info %}

由于某些原因，2020年10月1日，GitHub将启用main作为默认分支名，master将成为历史！

{% endnote %}

![main](https://image.ql-isaac.cn/Git-for-Windows/main.png)

　　这个，直接Next，默认即可。

![默认](https://image.ql-isaac.cn/Git-for-Windows/默认.png)

　　credential helper，凭据帮助器？这是个什么玩意儿？star一下这个[cross-platform version of the Git Credential Manager](https://github.com/microsoft/Git-Credential-Manager-Core)先，有时间看看（虽然看不懂）。

![credential helper](https://image.ql-isaac.cn/Git-for-Windows/credential-helper.png)

　　实验性的选项：允许在Git Bash窗口中运行原生控制台程序，如Node或Python，而不使用winpty，但它仍然有已知的bug。不勾选。

![实验性的选项](https://image.ql-isaac.cn/Git-for-Windows/实验性的选项.png)

　　安装中。

![安装中](https://image.ql-isaac.cn/Git-for-Windows/安装中.png)

　　完成。

![完成](https://image.ql-isaac.cn/Git-for-Windows/完成.png)

　　Release Notes。

![Release Notes](https://image.ql-isaac.cn/Git-for-Windows/Release-Notes.png)
