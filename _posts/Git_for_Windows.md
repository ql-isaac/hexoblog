---
title: Git for Windows
date: 2021-01-03 15:27:43
cover: https://image.ql-isaac.cn/Git.gif
tags:
 - Windows 10 企业版 LTSC
categories:
 - Git 和 GitHub 从入门到实践
---

　　来记录一下 Git for Windows 的使用。

<!-- more -->

## 2021-1-3

　　每次打开 VS Code 时右下角总提示这个，还是更新一下吧，直接点击更新 GIT。

![更新GIT](https://image.ql-isaac.cn/Git_for_Windows/更新GIT.png)

　　原来是跳转到 Git 官网。

![Git官网](https://image.ql-isaac.cn/Git_for_Windows/Git官网.png)

　　这里会跳转到 IE 浏览器，呵呵，赶紧到 Windows 的所有设置-应用-默认应用中把 Web 浏览器设置成 Microsoft Edge 再打开 Git 官网。

![Microsoft Edge](https://image.ql-isaac.cn/Git_for_Windows/Microsoft-Edge.png)

　　常规操作：下载，双击安装。

![下载安装](https://image.ql-isaac.cn/Git_for_Windows/下载安装.png)

　　Only show new option，嗯，很人性化！好评！

![Only show new option](https://image.ql-isaac.cn/Git_for_Windows/Only-show-new-option.png)

　　勾选第二个，以后用`git init`初始化的默认分支名就为 main 了。

{% note info %}

由于某些原因，2020 年 10 月 1 日，GitHub 将启用 main 作为默认分支名，master 将成为历史！

{% endnote %}

![main](https://image.ql-isaac.cn/Git_for_Windows/main.png)

　　这个，直接 Next，默认即可。

![默认](https://image.ql-isaac.cn/Git_for_Windows/默认.png)

　　credential helper，凭据帮助器？这是个什么玩意儿？star 一下这个[cross-platform version of the Git Credential Manager](https://github.com/microsoft/Git-Credential-Manager-Core)先，有时间看看（虽然看不懂）。

![credential helper](https://image.ql-isaac.cn/Git_for_Windows/credential-helper.png)

　　实验性的选项：允许在 Git Bash 窗口中运行原生控制台程序，如 Node 或 Python，而不使用 winpty，但它仍然有已知的 bug。不勾选。

![实验性的选项](https://image.ql-isaac.cn/Git_for_Windows/实验性的选项.png)

　　安装中。

![安装中](https://image.ql-isaac.cn/Git_for_Windows/安装中.png)

　　完成。

![完成](https://image.ql-isaac.cn/Git_for_Windows/完成.png)

　　Release Notes。

![Release Notes](https://image.ql-isaac.cn/Git_for_Windows/Release-Notes.png)
