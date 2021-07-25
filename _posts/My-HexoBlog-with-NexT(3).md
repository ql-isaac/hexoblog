---
title: 我的 HexoBlog 的诞生（三）
date: 2020-01-24 22:53:39
cover: https://image.ql-isaac.cn/Blogging-bro.png
tags:
 - Windows 10 企业版 LTSC
 - Hexo v4.2.0
 - Markdown
 - Typora
categories:
 - 我的 HexoBlog 的诞生
---

　　本文记录和讲解我的 HexoBlog 的使用，会持续更新。

<!-- more -->

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>

## 使用 Typora 编辑 Markdown 文件，书写博客文章

　　通过执行`hexo new post <自定义 md 文件名>`，相应 Markdown 文件将在 _posts 下生成，那么该如何编辑这种 Markdown 文件，书写自己的博客文章呢？

### Markdown

　　Markdown 是一种轻量级的标记语言，类似于 HTML，但 Markdown 的语法十分简单，常用的标记符号也不超过十个。

### Typora

　　Typora 是一个 Markdown 文件阅读器与编辑器，支持 MacOS、Windows、Linux 平台，可到[ Typora 官网](https://typora.io/)下载。

### 标题

　　使用`#`可表示 1-6 级标题。一级标题对应一个 #，二级标题对应两个 # ，以此类推，如下图（注意 # 后面有一个空格）。

![标题](https://cdn.jsdelivr.net/npm/post-gifs-1/My-HexoBlog-with-NexT(3)/标题.gif)

### 列表

　　经常用的是有序列表和无序列表。使用`<序号>. `（`.`后面有一个空格）可表示有序列表，若`<序号>. `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图。

![有序列表](https://cdn.jsdelivr.net/npm/post-gifs-1/My-HexoBlog-with-NexT(3)/有序列表.gif)

　　使用`- `（`-`后面有空格）可表示无序列表，若`- `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图。

![无序列表](https://cdn.jsdelivr.net/npm/post-gifs-1/My-HexoBlog-with-NexT(3)/无序列表.gif)

　　还有一个任务列表，使用`- [ ] `（`[ ]`后面有空格）可表示任务列表，若`- [ ] `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图。

![任务列表](https://cdn.jsdelivr.net/npm/post-gifs-1/My-HexoBlog-with-NexT(3)/任务列表.gif)

## 分割线



## 如何在文章中插入图片、视频和音乐？

### 开启每篇文章的资源文件夹

　　打开 Hexo 的配置文件，关键字 post_asset_folder 查找，将 post_asset_folder 的值改为 true。每次新生成 layout（layout 默认有 post、page 和 draft 三种 ）时都会在对应生成的 Markdown 文件同级目录下生成一个对应的资源文件夹，可将图片、音乐或视频存入该文件夹，这样，想插入图片、音乐或视频时直接填写图片、音乐或视频的完整文件名即可。

### 在文章内插入视频

　　在[存储 HexoBlog 的文件夹]下进入终端，输入如下命令安装  hexo-tag-dplayer。

```bash
cnpm install --save hexo-tag-dplayer
```

## 访问体验优化



