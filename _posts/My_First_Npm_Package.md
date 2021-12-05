---
title: 我的第一个 npm 包？
date: 2021-09-15 19:00:00
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_First_Npm_Package/npm.jpg
tags:
 - jsdelivr
categories:
 - 我的 HexoBlog 的诞生
---

npm，即 Node Package Manager，是随同 NodeJS 一起安装的包管理工具，本质是一个软件注册表。

<!-- more -->

不可告人的缘由，如下图，听说 jsdelivr 对 npm 上的文件限度会大一些，于是决定将我博文的 Gifs 发布到 npm 上，这就成为了我的第一个 npm 包，哈哈。

![20MB](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_First_Npm_Package/20MB.png)

首先是注册自己的 npm 账号，然后认证一下邮箱。

![注册](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_First_Npm_Package/注册.png)

![Continue](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_First_Npm_Package/Continue.png)

克隆自己的 Gifs 仓库到本地，右键，点击 Git Bash Here，执行以下命令添加 npm 用户，需要输入自己刚刚注册好的 npm 用户名、密码和绑定的邮箱。

```bash
npm adduser
```

接着执行如下命令进行初始化，依次填写信息，如下图，回车确认。

```bash
npm init
```

![初始化](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_First_Npm_Package/初始化.png)

最后进行发布，执行如下命令，“稍稍”等待一会，Gifs 就被发布到 npm 上去了。

```bash
npm publish
```

