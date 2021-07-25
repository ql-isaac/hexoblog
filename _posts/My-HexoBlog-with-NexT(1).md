---
title: 我的 HexoBlog 的诞生（一）
date: 2020-01-24 22:53:24
cover: https://image.ql-isaac.cn/Working-rafiki.png
tags:
 - Windows 10 企业版 LTSC
 - Node.js v12.14.0
 - Hexo v4.2.0
 - Git v2.25.0.windows.1
 - GitHub
categories: 
 - 我的 HexoBlog 的诞生
---

　　本文记录和讲解一下我的 HexoBlog 是如何一步一步被部署至 Github Pages 上的，可供大家参考。部署完成后可参考我的下一篇文章《我的 HexoBlog 的诞生（二）》对自己的 HexoBlog 进行个性化设置和配置，不过在此之前，需阅读[ Hexo 官方文档](https://hexo.io/zh-cn/docs/)，对 Hexo 有基本的完整的认识。

<!-- more -->

### 注册自己的 Github 账户，创建 Github Pages

1. 进入[ Github 首页](http://github.com/)，点击 Sign up 注册，填写 Username 等，验证邮箱，注册成功；
2. 点击右上角的加号，点击 New repository，填写 Repository name，这里的仓库名建议按照”<自己的 Github 用户名>.github.io“的格式来填，填写 Description，点击 Creat repository，创建 Github Pages 成功；

### 安装 Node.js，安装 Git 和 Git 的配置

3. 进入[ Node.js 官方网站](https://nodejs.org/zh-cn/)，点击下载 LTX（Long Term Support）版，我下载的是[ v12.14.0 版本的 msi 安装程序](https://nodejs.org/download/release/v12.14.0/)，安装步骤非常简单，一直 next；

4. 进入[ Git 官方网站下载页面](https://git-scm.com/downloads)，选择 Windows 版本的 Git 下载，我下载的是[ v2.25.0 版本的 exe 安装程序(提取码：u7fp)](https://pan.baidu.com/s/1YJxkbnkwx-9x4Hr5Sz4jMQ)，[安装和配置步骤](https://blog.ql-isaac.cn/2020/01/24/What-is-Git/#more)记录在另一篇文章中；

### 安装 Hexo

5. 在合适的路径下新建一个文件夹，文件夹名自定义，例如 HexoBlog，作为<存储 HexoBlog 的文件夹>；

6. 打开<存储 HexoBlog 的文件夹>，在空白处点鼠标的右键，选择 Git Bash Here 进入终端；

7. 安装 cnpm 提高下载速度，以后下载插件都可用 cnpm（即将下载某一个插件的命令中的 npm 改为 cnpm）。在终端输入如下命令，回车，等待 cnpm 下载完成；

    ```bash
    npm install -g cnpm --registry=http://registry.npm.taobao.org
    ```

8. 在终端输入如下命令，回车，等待 hexo-cli 下载完成，完成后，可输入`hexo -v`查看相关版本信息；

    ```bash
    cnpm install -g hexo-cli
    ```

9. 在终端输入`hexo init`，等待，可在<存储 HexoBlog 的文件夹>中看到生成了如下图所示的文件。

![初始文件](https://image.ql-isaac.cn/My-HexoBlog-with-NexT%281%29/%E5%88%9D%E5%A7%8B%E6%96%87%E4%BB%B6.png)

### 本地部署我的 HexoBlog

10. 在终端输入`hexo s`，之后打开浏览器，输入 localhost:4000，可看到本地部署的我的 HexoBlog，表明没什么问题；

### 部署至 Github Pages

11. 安装 Hexo 的 Git 插件。终端输入如下命令，回车，等待下载完成。

    ```bash
    cnpm install --save hexo-deployer-git
    ```

12. 编辑 Hexo 的配置文件：

    ```diff
    # 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 97 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 97 行，请以实际情况为准）
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:  
    -  type: ''
    ```
    
    ```diff
    # 本行为<存储 HexoBlog 的文件夹>\_config.yml 的第 97 行（随着 Hexo 的不断更新，本行对应在你的 _config.yml 中不一定是第 97 行，请以实际情况为准）
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:  
    +  type: git  
    +  repo: 
    +   github: git@github.com:<自己的 Github 用户名>/<自己的 Github 用户名>.github.io.git,master        
    ```

13. 在终端输入`hexo g -d`，回车，进行博客的最终操作——生成静态文件后立即部署到 Github Pages 中；

14. [大功告成](https://ql-isaac.github.io)（将 ql-isaac 替换成自己的 Github 用户名）。

### 参考

[手把手教你从 0 开始搭建自己的个人博客|无坑版视频教程|hexo（bilibili）](https://www.bilibili.com/video/av44544186)

[caiyantao（个人博客）](https://caiyantao.gitee.io/)