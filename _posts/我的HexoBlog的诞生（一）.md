---
title: 我的HexoBlog的诞生（一）
date: 2020-01-24 22:53:24
cover: https://image.ql-isaac.cn/Working-rafiki.png
tags:
 - Windows 10 企业版 LTSC
 - Node.js v12.14.0
 - Hexo v4.2.0
 - Git v2.25.0.windows.1
 - GitHub
categories: 
 - 我的HexoBlog的诞生
---

　　本文记录和讲解一下我的HexoBlog是如何一步一步被部署至Github Pages上的，可供大家参考。部署完成后可参考我的下一篇文章《我的HexoBlog的诞生（二）》对自己的HexoBlog进行个性化设置和配置，不过在此之前，需阅读[Hexo官方文档](https://hexo.io/zh-cn/docs/)，对Hexo有基本的完整的认识。

<!-- more -->

### 注册我的Github账户，建立Github Pages

1. 进入[Github首页](http://github.com/)，点击Sign up注册，填写Username等，验证邮箱，注册成功；
2. 点击右上角的加号，点击New repository，填写Repository name，这里的仓库名建议按照”<自己的Github用户名>.github.io“的格式来填，填写Description，点击Creat repository，创建Github Pages成功；

### 安装Node.js，安装Git和Git的配置

3. 进入[Node.js官方网站](https://nodejs.org/zh-cn/)，点击下载LTX（Long Term Support）版，我下载的是[v12.14.0版本的msi安装程序](https://nodejs.org/download/release/v12.14.0/)，安装步骤非常简单，一直next；

4. 进入[Git官方网站下载页面](https://git-scm.com/downloads)，选择Windows版本的Git下载，我下载的是[v2.25.0版本的exe安装程序(提取码：u7fp)](https://pan.baidu.com/s/1YJxkbnkwx-9x4Hr5Sz4jMQ)，[安装和配置步骤](https://blog.ql-isaac.cn/2020/01/24/%E4%BB%80%E4%B9%88%E6%98%AFGit%EF%BC%9F/#Windows-10%E4%B8%8A%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AEGit)记录在另一篇文章中；

### 安装Hexo

5. 在合适的路径下新建一个文件夹，文件夹名自定义，例如HexoBlog，作为<存储HexoBlog的文件夹>；

6. 打开<存储HexoBlog的文件夹>，在空白处点鼠标的右键，选择Git Bash Here进入终端；

7. 安装cnpm提高下载速度，以后下载插件都可用cnpm（即将下载某一个插件的命令中的npm改为cnpm）。在终端输入如下命令，回车，等待cnpm下载完成；

    ```bash
    npm install -g cnpm --registry=http://registry.npm.taobao.org
    ```

8. 在终端输入如下命令，回车，等待hexo-cli下载完成，可输入`hexo -v`查看相关版本信息；

    ```bash
    cnpm install -g hexo-cli
    ```

9. 在终端输入`hexo init`，等待，可在<存储HexoBlog的文件夹>中看到生成了如下图所示的文件。

![初始文件](https://image.ql-isaac.cn/初始文件.png)

### 本地部署我的HexoBlog

10. 在终端输入`hexo s`，之后打开浏览器，输入localhost:4000，可看到本地部署的我的HexoBlog，表明没什么问题；

### 部署至Github Pages

11. 安装Hexo的Git插件。终端输入如下命令，回车，等待下载完成。

    ```bash
    cnpm install --save hexo-deployer-git
    ```

12. 编辑Hexo的配置文件：

    ```diff
    # 本行为<存储HexoBlog的文件夹>\_config.yml的第97行（随着Hexo的不断更新，本行对应在你的_config.yml中不一定是第97行，请以实际情况为准）
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:  
    -  type: ''
    ```
    ```diff
    # 本行为<存储HexoBlog的文件夹>\_config.yml的第97行（随着Hexo的不断更新，本行对应在你的_config.yml中不一定是第97行，请以实际情况为准）
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:  
    +  type: git  
    +  repo: 
    +   github: git@github.com:<自己的Github用户名>/<自己的Github用户名>.github.io.git,master        
    ```

13. 在终端输入`hexo g -d`，回车，进行博客的最终操作——生成静态文件后立即部署到Github Pages上；

14. [大功告成](https://ql-isaac.github.io)（将ql-isaac替换成自己的Github用户名）。

### 参考

https://caiyantao.gitee.io/2019/04/13/Hexo-%E4%B8%80
https://caiyantao.gitee.io/2019/04/13/Hexo-一/
https://caiyantao.gitee.io/2019/04/13/Hexo%EF%BC%88%E4%BA%8C%EF%BC%89/#more
https://caiyantao.gitee.io/2019/04/13/Hexo（二）/#more
https://www.bilibili.com/video/av44544186?from=search&seid=9508828059673681599