---
title: 我的 HexoBlog 的诞生（三）
date: 2020-01-24 22:53:39
cover: https://image.ql-isaac.cn/Blogging-bro.png
tags:
  - Typora
  - Hexo v4.2.0
  - Windows 10 企业版 LTSC
categories:
  - 我的 HexoBlog 的诞生
---

本文记录和讲解我的 HexoBlog 的使用，会持续更新。

<!-- more -->

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>

## 使用 Typora 编辑 Markdown 文件，书写博客文章[^1]

通过执行`hexo new post <自定义 md 文件名>`，相应 Markdown 文件将在 \_posts 下生成，那么该如何编辑这种 Markdown 文件，书写自己的博客文章呢？

### Typora

Typora 是一个 Markdown 文件阅读器与编辑器，支持 MacOS、Windows、Linux 平台，可到 [Typora 官网](https://typora.io/)下载。

### Markdown

Markdown 是一种轻量级的标记语言，类似于 HTML，但 Markdown 的语法十分简单，常用的标记符号也不超过十个。

### 标题

使用`#`可表示 1-6 级标题。一级标题对应一个 #，二级标题对应两个 # ，以此类推，如下图（注意 # 后面有一个空格）：

![标题](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/标题.gif>)

### 脚注

不多说了，看图吧：

![脚注](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/脚注.gif>)

### 列表

经常用的是有序列表和无序列表。使用`<序号>. `（`.`后面有一个空格）可表示有序列表，若`<序号>. `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图：

![有序列表](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/有序列表.gif>)

使用`- `（`-`后面有空格）可表示无序列表，若`- `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图：

![无序列表](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/无序列表.gif>)

还有一个任务列表，使用`- [ ] `（`[ ]`后面有空格）可表示任务列表，若`- [ ] `之后接了实际内容，则回车自动生成下一项，如没有实际内容，回车回到正文，如下图：

![任务列表](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/任务列表.gif>)

{% note info %}

以上三种列表之间可以相互嵌套，只需在敲子列表前敲四个空格即可。

{% endnote %}

### 代码

如果是段落上的一个代码段，用一对单个反引号把它包起来即可，如下图：

![代码段](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/代码段.gif>)

如果是代码块，先敲三个反引号再回车，就能生成一个空代码块，粘贴进代码就可以了，右下方可以指定语言，会有相应的高亮显示，如下图：

![代码块](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/代码块.gif>)

{% note info %}

其实以上表示代码块的语法是 Typora 对 Markdown 语法的简化，可使用`Ctrl`+`/`切换到源代码模式，可看到是一对三个反引号包起来即表示代码块。

{% endnote %}

### 链接

先用一对中括号包裹链接文本，再用一对小括号包裹地址，如下图：

![链接](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/链接.gif>)

### 插入图片

先敲一个`!`，再用一对中括号包裹图片描述，最后敲一对小括号就可以选择图片插入，如下图：

![插入图片](<https://cdn.jsdelivr.net/npm/post-gifs-1/My_HexoBlog_with_NexT(3)/插入图片.gif>)

### 在文章内插入视频

在[存储 HexoBlog 的文件夹]下进入终端，输入如下命令安装 hexo-tag-dplayer。

```bash
cnpm install --save hexo-tag-dplayer
```

[^1]: [菜鸟教程](https://www.runoob.com/markdown/md-tutorial.html)
