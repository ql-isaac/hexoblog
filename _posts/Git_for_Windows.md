---
title: Git for Windows
date: 2021-01-03 15:27:43
updated: 2021-08-22 16:14:00
cover: https://image.ql-isaac.cn/Git.gif
tags:
 - Windows 10
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

## 2021-8-23

　　不可告人的缘由，我需要另外创建一个 GitHub 小号（[isaac-ql](https://github.com/isaac-ql)），创建完账号后，就应该是去绑定个人电脑的 SSH key，我想当然的以为可以复用建博客时生成的 SSH key，结果 GitHub 给我了这个提示：

![Key is already in use](https://image.ql-isaac.cn/Git_for_Windows/Key_is_already_in_use.png)

　　好吧，看来是不能复用。百度一番后，解决办法如下：

1. 右键，点击 Git Bash Here，执行以下命令：

    ```bash
    ssh-keygen -t rsa -f ~/.ssh/<自定义 SSH key 文件名>
    ```

2. 进入 .ssh 文件夹（在用户文件夹下），新建 config 文件（注意这是 config 是完整文件名），编辑：

    ```diff
    +Host github.com
    +    HostName github.com
    +    PreferredAuthentications publickey
    +    IdentityFile ~/.ssh/id_rsa     
    +Host <自定义别名>
    +    HostName github.com
    +    PreferredAuthentications publickey
    +    IdentityFile ~/.ssh/<自定义 SSH key 文件名>
    ```

3. 以后在以 SSH 方式克隆 GitHub 小号时，将原来的地址@后面的域名改为以上的自定义别名即可。

　　如下图，`git clone`很慢怎么办？

![克隆很慢](https://image.ql-isaac.cn/Git_for_Windows/克隆很慢.png)

　　请那啥之后设置代理（我使用的代理软件是 Clash）：

1. 要那啥，此处省略一百个字；
2. 右键，点击 Git Bash Here，依次执行以下命令：

    ```bash
    git config --global http.https://github.com.proxy socks5://127.0.0.1:<socks代理端口号>
    ```

    ```bash
    git config --global https.https://github.com.proxy socks5://127.0.0.1:<socks代理端口号>
    ```

3. 打开 Clash 的全局代理；
4. 起飞，还没开始截图就克隆完毕了。

![起飞](https://image.ql-isaac.cn/Git_for_Windows/起飞.png)

