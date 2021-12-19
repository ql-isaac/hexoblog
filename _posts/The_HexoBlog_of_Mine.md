---
title: 我的博客
date: 2021-11-18 22:28:52
cover: https://image.ql-isaac.cn/Blogging-bro.png
categories:
 - NexT
 - Hexo
---

写博客，一种和自己相处的方式。

<!-- more -->

## Hexo

Hexo，一个静态博客框架，选择它的原因无非有二：一是它构建的是静态博客，这意味着零成本的部署，二是它的主题丰富，使用人最多。2020 年 1 月 24 日，正直除夕，伴随着我的博客的正式诞生，[我的第一篇博文](https://blog.ql-isaac.cn/2020/01/24/My_HexoBlog_with_NexT(1)/#more)也正式诞生了。

## 最受欢迎的 Hexo 主题——NexT

要说最受欢迎的 Hexo 主题，当属 NexT，其在 GitHub 的 star 数有 15.7k 之多。其实 NexT 目前一共有 3 个仓库，最开始是 [iissnan 的仓库](https://github.com/iissnan/hexo-theme-next)，也就是这个拥有 15.7k 收藏的仓库，之后该仓库不再维护，NexT 转为 [theme-next 组织](https://github.com/theme-next)维护，后来又换为 [next-theme 组织](https://github.com/next-theme)维护。

## 关于我博客的构建源码的故事

2020 年 1 月 29 日，我开始利用 Git 将我博客的构建源码上传到我的 GitHub Pages[^1] 仓库的 hexo 分支。当时出于对多端写博客的需求，在网上找到了[一篇教程](https://righere.github.io/2016/10/10/install-hexo/)，也是 NexT 主题，跟着成功上传了上去。

2020 年 9 月 24 日我将该分支又删除了，但本地克隆下来的 Hexo 分支还在，我不想失去这一曾经的记录，就把该分支上传到 [Gitee 仓库](https://gitee.com/ql-isaac/next.ql-isaac.cn)，要不然我早就忘记我第一次提交博客的构建源码是在什么时候:

![第一次提交](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My_HexoBlog_with_NexT(3)/第一次提交.png)

{% note info %}

我已经不记得我第一次接触 Hexo 具体是在什么时候，应该是在 2019 年的 12 月份，当时在本地玩崩了一次，这才促成我利用 Git 对源码进行版本控制并上传到 GitHub。

{% endnote %}

2020 年 9 月 26 日，我另开了[一个仓库](https://github.com/ql-isaac/HexoBlog-NexT)存放我博客的构建源码，同时，我发现了一个非常不错的主题——[Butterfly](https://github.com/jerryc127/hexo-theme-butterfly)，于是又新建了[一个仓库](https://github.com/ql-isaac/HexoBlog-Butterfly)存放这个主题博客的构建源码。

2021 年 2 月 21 日，我突然想到 Butterfly 主题的站点拿来做个人首页（www站点）也是再好不过的，那这样的话，Butterfly 主题站点（www站点）和 NexT 主题站点（blog站点）的博文最好能公用，也就是 _posts 能在两个站点的构建源码中同步更新，两边各编辑一遍是绝对不现实的，如果你是在 Windows 平台写博文，可以利用符号链接，如果是在 Linux 平台写，可以利用软链接，具体就不多说了。

## blog 站点升级

一直以来 NexT 主题站点（blog站点）都是使用的刚创建时候下载的 Hexo v4.2.0 和 NexT v7.7.0，是时候更新一波了。

[^1]: [Types of GitHub Pages sites](https://docs.github.com/cn/pages/getting-started-with-github-pages/about-github-pages/#Types-of-GitHub-Pages-sites)