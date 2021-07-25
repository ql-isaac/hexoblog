---
title: 我的 HexoBlog 的诞生（二）
date: 2020-01-24 22:53:32
updated: 2021-02-21 19:03:49
cover: https://image.ql-isaac.cn/Setup-bro.png
tags:
 - Windows 10 企业版 LTSC
 - Hexo v4.2.0
 - NexT v7.7.0
categories: 
 - 我的 HexoBlog 的诞生
---

　　本文记录和讲解一下我的 HexoBlog 是如何个性化设置和配置的，可供大家参考，我会持续更新，保持和[我的 HexoBlog ](https://ql-isaac.github.io)的同步。

<!-- more -->

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>

## 重要提示

　　个性化设置和配置了一处自己的 HexoBlog，可以通过本地部署的方式（即在<存储 HexoBlog 的文件夹>下进入终端，输入`hexo s`）查看相应效果，甚至可以直接修改一处，刷新一下查看效果，等都设置和配置完毕了再部署到 Github Pages 中，即在<存储 HexoBlog 的文件夹>下进入终端，执行`hexo clean && hexo g -d`。

## Hexo 的个性化设置和配置

### 配置博客站点基本信息

　　编辑 Hexo 的配置文件，个性化配置自己的站点信息即可：

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 4 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 4 行，请以实际情况为准）
# Site
-title: Hexo
-subtitle: ''
-description: ''
-keywords:
-author: John Doe
-language: en
-timezone: ''
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 4 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 4 行，请以实际情况为准）
# Site
+title: ql's HexoBlog
+subtitle: It's a beautiful day!
+description: 学习与生活
+keywords: 学习与生活
+author: ql-isaac
+language: zh-CN
+timezone: 
```

　　效果展示：

![配置博客站点基本信息](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/配置博客站点基本信息.png)

### 下载和设置 NexT 主题

　　原版的 landscape 主题并不好看，在网上搜索了一下，发现 NexT 主题是最受欢迎的。

　　在<存储 HexoBlog 的文件夹>下进入终端，输入如下命令，等待 NexT 下载到当前文件夹下 themes 下 next 下。

```bash
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

　　下载完成后，编辑 Hexo 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 92 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 92 行，请以实际情况为准）
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
-theme: landscape
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 92 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 92 行，请以实际情况为准）
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
+theme: next
```

## NexT 的个性化设置与配置

### 在页脚添加建站年份

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 49 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 49 行，请以实际情况为准
footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
-  #since: 2015
```

```diff
footer:
  # Specify the date when the site was setup. If not defined, current year will be used.
+  since: 2020
```

　　效果展示：

![页脚建站年份](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/页脚建站年份.png)

### 在页脚添加备案信息

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 78 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 78 行，请以实际情况为准
  # Beian ICP and gongan information for Chinese users. See: http://www.beian.miit.gov.cn, http://www.beian.gov.cn
  beian:
-    enable: false
-    icp:
    # The digit in the num of gongan beian.
    gongan_id:
    # The full num of gongan beian.
    gongan_num:
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url:
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 78 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 78 行，请以实际情况为准
  # Beian ICP and gongan information for Chinese users. See: http://www.beian.miit.gov.cn, http://www.beian.gov.cn
  beian:
+    enable: true
+    icp: 京 ICP 备 20031573 号 -1
    # The digit in the num of gongan beian.
    gongan_id:
    # The full num of gongan beian.
    gongan_num:
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url:
```

　　效果展示：

![页脚备案信息](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/页脚备案信息.png)

### 选择主题风格

　　编辑 NexT 的配置文件（我保持的默认，喜欢其他的风格的话把前面的 # 去掉即可，注意只能启用一种风格）：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 105 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 105 行，请以实际情况为准
# Schemes
scheme: Muse
#scheme: Mist
#scheme: Pisces
#scheme: Gemini
```

　　各种主题风格展示：

![Muse](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/Muse.png)

![Mist](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/Mist.png)

![Pisces](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/Pisces.png)

![Gemini](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/Gemini.png)

### 添加标签和分类菜单项

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 116 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 116 行，请以实际情况为准
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# When running the site in a subdirectory (e.g. yoursite.com/blog), remove the leading slash from link value (/archives -> archives).
# External url should start with http:// or https://
menu:
  home: / || home
  #about: /about/ || user
-  #tags: /tags/ || tags
-  #categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 116 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 116 行，请以实际情况为准
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# When running the site in a subdirectory (e.g. yoursite.com/blog), remove the leading slash from link value (/archives -> archives).
# External url should start with http:// or https://
menu:
  home: / || home
  #about: /about/ || user
+  tags: /tags/ || tags
+  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```

　　在<存储 HexoBlog 的文件夹>下进入终端，执行如下命令：

```bash
hexo new page tags
```

　　编辑生成的 index.md：

```diff
---
-title: tags
date: 2020-01-24 22:20:25
---
```

```diff
---
+title: 标签
date: 2020-01-24 22:20:25
+type: tags
---
```

　　在<存储 HexoBlog 的文件夹>下进入终端，执行如下命令：

```bash
hexo new page categories
```

　　编辑生成的 index.md：

```diff
---
-title: categories
date: 2020-01-24 22:21:09
---
```

```diff
---
+title: 分类
date: 2020-01-24 22:21:09
+type: categories
---
```

　　编辑文章模板文件（为<存储 HexoBlog 的文件夹>下 scaffolds 下 post.md）：

```diff
---
title: {{ title }}
date: {{ date }}
tags:
+categories:
---
```

　　以后想写文章（执行`hexo new post <自定义名>`，编辑相应生成的<自定义名>.md）时，只需自定义 tags 和 categories 的值（注意键值之间有空格），该文章就会在标签页面和分类页面被标记和分类起来。

### 加入豆瓣页面

　　在<存储 HexoBlog 的文件夹>下进入终端，输入如下命令安装 hexo-douban 插件。

```bash
cnpm install --save hexo-douban
```

　　编辑 Hexo 的配置文件，如下：

```diff
# 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 104 行
+douban:
+  user: <豆瓣 ID>
+  builtin: true
+  book:
+    title: <书籍页面的标题>
+    quote: <开头的引言>
+  movie:
+    title: <电影页面的标题>
+    quote: <开头的引言>
+  game:
+    title: <游戏页面的标题>
+    quote: <开头的引言>
+  timeout: 10000
```

　　添加图书、电影和游戏菜单项。编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的 116 行
# Usage: `Key: /link/ || icon`
# Key is the name of menu item. If the translation for this item is available, the translated text will be loaded, otherwise the Key name will be used. Key is case-senstive.
# Value before `||` delimiter is the target link, value after `||` delimiter is the name of Font Awesome icon.
# When running the site in a subdirectory (e.g. yoursite.com/blog), remove the leading slash from link value (/archives -> archives).
# External url should start with http:// or https://
menu:
  home: / || home
  #about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
+  books: /books || book
+  movies: /movies || video-camera
+  games: /games || gamepad
```

　　编辑 NexT 的中文语言文件（为<存储 HexoBlog 的文件夹>下 themes 下 next 下 languages 下 zh-CN.yml）：

```diff
---
title:
  archive: 归档
  category: 分类
  tag: 标签
  schedule: 日程表
menu:
  home: 首页
  archives: 归档
  categories: 分类
  tags: 标签
  about: 关于
  search: 搜索
  schedule: 日程表
  sitemap: 站点地图
  commonweal: 公益 404
+  books: 阅读
+  movies: 电影
+  games: 游戏
sidebar:
  overview: 站点概览
  toc: 文章目录
post:
  posted: 发表于
  edited: 更新于
  created: 创建时间
  modified: 修改时间
  edit: 编辑
  in: 分类于
  more: 更多
  read_more: 阅读全文
  untitled: 未命名
  sticky: 置顶
  views: 阅读次数
  related_posts: 相关文章
  copyright:
    author: 本文作者
    link: 本文链接
    license_title: 版权声明
    license_content: "本博客所有文章除特别声明外，均采用 %s 许可协议。转载请注明出处！"
footer:
  powered: "由 %s 强力驱动"
  theme: 主题
  total_views: 总访问量
  total_visitors: 总访客量
counter:
  tag_cloud:
    zero: 暂无标签
    one: 目前共计 1 个标签
    other: "目前共计 %d 个标签"
  categories:
    zero: 暂无分类
    one: 目前共计 1 个分类
    other: "目前共计 %d 个分类"
  archive_posts:
    zero: 暂无日志。
    one: 目前共计 1 篇日志。
    other: "目前共计 %d 篇日志。"
state:
  posts: 日志
  tags: 标签
  categories: 分类
search:
  placeholder: 搜索...
cheers:
  um: 嗯..
  ok: 还行
  nice: 不错
  good: 很好
  great: 非常好
  excellent: 太棒了
keep_on: 继续努力。
symbol:
  comma: "，"
  period: "。"
  colon: "："
reward:
  donate: 打赏
  wechatpay: 微信支付
  alipay: 支付宝
  bitcoin: 比特币
accessibility:
  nav_toggle: 切换导航栏
  prev_page: 上一页
  next_page: 下一页
symbols_count_time:
  count: 本文字数
  count_total: 站点总字数
  time: 阅读时长
  time_total: 站点阅读时长
  time_minutes: 分钟
  
```

### 侧边栏显示设置（只适合风格 Muse 或 Mist）

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 155 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 155 行，请以实际情况为准
  # Sidebar Display (only for Muse | Mist), available values:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
-  display: post
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 155 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 155 行，请以实际情况为准
  # Sidebar Display (only for Muse | Mist), available values:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically.
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  totally remove sidebar including sidebar toggle.
+  display: always
```

### 头像

　　选择一张图片，放在<存储 HexoBlog 的文件夹>下 themes 下 next 下 source 下 images 下，然后编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 169 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 169 行，请以实际情况为准
# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
-  url: #/images/avatar.gif
  # If true, the avatar will be dispalyed in circle.
-  rounded: false
  # If true, the avatar will be rotated with the cursor.
-  rotated: false
```
```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 169 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 169 行，请以实际情况为准
# Sidebar Avatar
avatar:
  # Replace the default image and set the url here.
+  url: /images/<自己放的图片完整名>
  # If true, the avatar will be dispalyed in circle.
+  rounded: true
  # If true, the avatar will be rotated with the cursor.
+  rotated: true
```

### 添加联系方式

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 181 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 181 行，请以实际情况为准
# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimiter is the target permalink, value after `||` delimiter is the name of Font Awesome icon.
social:
-  #GitHub: https://github.com/yourname || github
-  #E-Mail: mailto:yourname@gmail.com || envelope
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
  #RSS: /atom.xml || rss
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 181 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 181 行，请以实际情况为准
# Social Links
# Usage: `Key: permalink || icon`
# Key is the link label showing to end users.
# Value before `||` delimiter is the target permalink, value after `||` delimiter is the name of Font Awesome icon.
social:
+  blog: https://blog.ql-isaac.cn/ || sticky-note
+  www: https://ql-isaac.cn/ || quora
+  nav: https://nav.ql-isaac.cn/ || location-arrow
+  space: https://space.ql-isaac.cn/ || codepen
+  GitHub: https://github.com/ql-isaac || github
+  E-Mail: mailto:834471527@qq.com || envelope
  #Weibo: https://weibo.com/yourname || weibo
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype
  #RSS: /atom.xml || rss
```

### 添加友情链接

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 214 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 214 行，请以实际情况为准
links:
-  #Title: http://yoursite.com
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 214 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 214 行，请以实际情况为准
links:
+  <标题 1>: <地址 1>
+  <标题 2>: <地址 2>
+  <标题 3>: <地址 3>
```

　　演示视频：

<video id="video2" preload controls loop style="height: 100%;width: 100%;object-fit: cover;"></video>
<script>
  if (Hls.isSupported()) {
    var video2 = document.getElementById('video2');
    var hls = new Hls();
    hls.loadSource('https://cdn.jsdelivr.net/gh/isaac-ql/post-videos-1/添加友情链接/添加友情链接.m3u8');
    hls.attachMedia(video2);
    hls.on(Hls.Events.MANIFEST_PARSED,function() {
      video.play();
  });
  }
</script>

### Use icon instead of the symbol # to indicate the tag at the bottom of the post

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 272 行（随着 NexT 的不断更新，本行对应在你的_config.yml中不一定是第 272 行，请以实际情况为准
# Use icon instead of the symbol # to indicate the tag at the bottom of the post
-tag_icon: false
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 272 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 272 行，请以实际情况为准
# Use icon instead of the symbol # to indicate the tag at the bottom of the post
+tag_icon: true
```

　　效果展示：

![tag](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/tag.png)

### 设置文本对齐方式为左对齐

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 344 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 344 行，请以实际情况为准
# Set the text alignment in posts / pages.
text_align:
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
-  desktop: justify
-  mobile: justify
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 344 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 344 行，请以实际情况为准
# Set the text alignment in posts / pages.
text_align:
  # Available values: start | end | left | right | center | justify | justify-all | match-parent
+  desktop: left
+  mobile: left
```

### 代码块设置

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 362 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 362 行，请以实际情况为准
codeblock:
  # Code Highlight theme
  # Available values: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
-  highlight_theme: normal
  # Add copy button on codeblock
  copy_button:
-    enable: false
    # Show text copy result.
-    show_result: false
    # Available values: default | flat | mac
    style:
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 362 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 362 行，请以实际情况为准
codeblock:
  # Code Highlight theme
  # Available values: normal | night | night eighties | night blue | night bright | solarized | solarized dark | galactic
  # See: https://github.com/chriskempson/tomorrow-theme
+  highlight_theme: solarized
  # Add copy button on codeblock
  copy_button:
+    enable: true
    # Show text copy result.
+    show_result: true
    # Available values: default | flat | mac
    style:
```

### 回到顶部按钮设置

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 375 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 375 行，请以实际情况为准
back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
-  scrollpercent: false
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 375 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 375 行，请以实际情况为准
back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false
  # Scroll percent label in b2t button.
+  scrollpercent: true
```

### 在页面顶部显示浏览进度

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 382 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 382 行，请以实际情况为准
# Reading progress bar
reading_progress:
-  enable: false
  # Available values: top | bottom
  position: top
  color: "#37c6c0"
  height: 3px
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 382 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 382 行，请以实际情况为准
# Reading progress bar
reading_progress:
+  enable: true
  # Available values: top | bottom
  position: top
  color: "#37c6c0"
  height: 3px
```

### 在右上角添加渲染本站的源码仓库传送门

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 399 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 399 行，请以实际情况为准
# `Follow me on GitHub` banner in the top-right corner.
github_banner:
-  enable: false
-  permalink: https://github.com/yourname
  title: Follow me on GitHub
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 399 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 399 行，请以实际情况为准
# `Follow me on GitHub` banner in the top-right corner.
github_banner:
+  enable: true
+  permalink: https://github.com/ql-isaac/HexoBlog/tree/main/NexT
  title: Follow me on GitHub
```

### 字体

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 419 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 419 行，请以实际情况为准
font:
-  enable: false

  # Uri of fonts host, e.g. //fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # Global font settings used for all elements inside <body>.
  global:
    external: true
-    family: Lato
    size:

  # Font settings for site title (.site-title).
  title:
    external: true
    family:
    size:

  # Font settings for headlines (<h1> to <h6>).
  headings:
    external: true
    family:
    size:

  # Font settings for posts (.post-body).
  posts:
    external: true
-    family:

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 419 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 419 行，请以实际情况为准
font:
+  enable: true

  # Uri of fonts host, e.g. //fonts.googleapis.com (Default).
  host:

  # Font options:
  # `external: true` will load this font family from `host` above.
  # `family: Times New Roman`. Without any quotes.
  # `size: x.x`. Use `em` as unit. Default: 1 (16px)

  # Global font settings used for all elements inside <body>.
  global:
    external: true
+    family:
    size:

  # Font settings for site title (.site-title).
  title:
    external: true
    family:
    size:

  # Font settings for headlines (<h1> to <h6>).
  headings:
    external: true
    family:
    size:

  # Font settings for posts (.post-body).
  posts:
    external: true
+    family: Noto Serif SC

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family:
```

### 优雅地查看图片

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 533 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 533 行，请以实际情况为准
# FancyBox is a tool that offers a nice and elegant way to add zooming functionality for images.
# For more information: https://fancyapps.com/fancybox
-fancybox: false
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 533 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 533 行，请以实际情况为准
# FancyBox is a tool that offers a nice and elegant way to add zooming functionality for images.
# For more information: https://fancyapps.com/fancybox
+fancybox: true
```

### 开启图片懒加载

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 542 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 542 行，请以实际情况为准
# Vanilla JavaScript plugin for lazyloading images.
# For more information: https://github.com/ApoorvSaxena/lozad.js
-lazyload: false
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 542 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 542 行，请以实际情况为准
# Vanilla JavaScript plugin for lazyloading images.
# For more information: https://github.com/ApoorvSaxena/lozad.js
+lazyload: true
```

### 添加 Valine 评论系统

　　Valine 是基于 LeanCloud 的，首先需要[注册 LeanCloud 账号](https://leancloud.cn/dashboard/login.html)，注意需要验证邮箱，注册成功后进入控制台，需要先实名认证，认证成功后，点击创建应用，新应用名称就填 Valine，这个随便，选择开发版，点击创建，点击存储图标，点击创建 Class，Class 名称填 Comment，添加，再点击创建 Class，Class 名称填 Counter，添加，创建 Class 成功后如下图。

![](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/My-HexoBlog-with-NexT(2)/创建Class.png)

　　点击左边的设置，点击安全中心，服务开关里仅打开数据存储服务，Web 安全域名中填写自己的博客地址，保存，点击左侧应用 keys，获取到<自己的 App ID>和<自己的 App key>。

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 578 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 578 行，请以实际情况为准
# Multiple Comment System Support
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: changyan | disqus | disqusjs | gitalk | livere | valine
-  active:
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any navs, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 578 行（随着 NexT 的不断更新，本行对应在你的 _config.yml中不一定是第 578 行，请以实际情况为准
# Multiple Comment System Support
comments:
  # Available values: tabs | buttons
  style: tabs
  # Choose a comment system to be displayed by default.
  # Available values: changyan | disqus | disqusjs | gitalk | livere | valine
+  active: valine
  # Setting `true` means remembering the comment system selected by the visitor.
  storage: true
  # Lazyload all comment systems.
  lazyload: false
  # Modify texts or order for any navs, here are some examples.
  nav:
    #disqus:
    #  text: Load Disqus
    #  order: -1
    #gitalk:
    #  order: -2
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 625 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 625 行，请以实际情况为准
# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
-  enable: false
-  appid: # Your leancloud application appid
-  appkey: # Your leancloud application appkey
  notify: false # Mail notifier
  verify: false # Verification code
  placeholder: Just go go # Comment box placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
-  language: # Language, available values: en, zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
-  recordIP: false # Whether to record the commenter IP
  serverURLs: # When the custom domain name is enabled, fill it in here (it will be detected automatically by default, no need to fill in)
  #post_meta_order: 0
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 625 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 625 行，请以实际情况为准
# Valine
# For more information: https://valine.js.org, https://github.com/xCss/Valine
valine:
+  enable: true
+  appid: <自己的 App ID>
+  appkey: <自己的 App key>
  notify: false # Mail notifier
  verify: false # Verification code
  placeholder: Just go go # Comment box placeholder
  avatar: mm # Gravatar style
  guest_info: nick,mail,link # Custom comment header
  pageSize: 10 # Pagination size
+  language: zh-cn
  visitor: false # Article reading statistic
  comment_count: true # If false, comment count will only be displayed in post page, not in home page
+  recordIP: true # Whether to record the commenter IP
  serverURLs: # When the custom domain name is enabled, fill it in here (it will be detected automatically by default, no need to fill in)
  #post_meta_order: 0
```

###  开启 busuanzi 统计

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 725 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 725 行，请以实际情况为准
# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
-  enable: false
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 725 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 725 行，请以实际情况为准
# Show Views / Visitors of the website / page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi
busuanzi_count:
+  enable: true
  total_visitors: true
  total_visitors_icon: user
  total_views: true
  total_views_icon: eye
  post_views: true
  post_views_icon: eye
```

### 添加本地搜索功能

　　在<存储 HexoBlog 的文件夹>下进入终端，输入如下命令安装 hexo-generator-searchdb 模块。

```bash
cnpm install --save hexo-generator-searchdb
```

　　开启本地搜索功能。编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 753 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 753 行，请以实际情况为准
# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
-  enable: false
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 753 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 753 行，请以实际情况为准
# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
+  enable: true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false　
```

### 设置 Note tag

　　编辑 NexT 的配置文件：

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 798 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 798 行，请以实际情况为准
# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
-  style: simple
-  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```

```diff
# 本行为<存储 HexoBlog 的文件夹>\themes\next\_config.yml 的第 798 行（随着 NexT 的不断更新，本行对应在你的 _config.yml 中不一定是第 798 行，请以实际情况为准
# Note tag (bs-callout)
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
+  style: flat
+  icons: true
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```

## 参考

[NexT 主题文档](https://theme-next.js.org/)

[lixint](https://lixint.github.io/)

[dragonbaby308](http://www.dragonbaby308.com/)