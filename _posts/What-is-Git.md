---
title: 什么是 Git？
date: 2020-01-24 22:53:47
cover: https://image.ql-isaac.cn/Git.gif
tags:
 - Git v2.25.0.windows.1
 - Git v2.17.1
 - Windows 10 企业版 LTSC
 - Ubuntu 18.04 LTS
categories: 
 - Git 和 GitHub 从入门到实践
---

　　Git 是一个目前世界上最流行的开源分布式版本控制系统。

<!-- more -->

## Git 的诞生

　　Git 是[林纳斯·托瓦兹](https://www.baidu.com/s?wd=林纳斯·托瓦兹&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)为了帮助管理[Linux](https://baike.baidu.com/item/Linux/27050)内核开发而开发的。在2002年以前，世界各地的志愿者还是以一种传统的方式将源代码文件发给林纳斯·托瓦兹，然后由他本人通过手工方式合并代码。当时虽然有 CSV、SVN 这些免费的版本控制系统，但是速度慢、需要联网，也有一些商用的版本控制系统，虽然比 CSV、SVN 好用，但是不开源，和 Linux 的开源精神不符。2002 年，Linux 系统已经发展了十年，代码库之大让林纳斯·托瓦兹很难继续通过手工方式管理，最终林纳斯·托瓦兹选择了一个商业的版本控制系统 BitKeeper，BitKeeper 的东家 BitMover 公司出于人道主义精神，授权 Linux 社区免费使用这个版本控制系统，这看起来是一个很好的局面。Linux 社区牛人聚集，2005年，开发 Samba 的 Andrew 试图破解 BitKeeper 的协议的行为被 BitMover 公司发现，Linux 社区的 BitKeeper 免费使用权被收回，于是，[林纳斯·托瓦兹](https://www.baidu.com/s?wd=林纳斯·托瓦兹&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)花了两周时间自己用 C 写了一个分布式版本控制系统，Git诞生！之后，Git 迅速成为最流行的分布式版本控制系统，随即，2008 年，GitHub 网站上线，它为开源项目免费提供 Git 存储，无数开源项目开始迁移至 GitHub，包括jQuery、PHP、Ruby 等等。

## 安装和配置 Git

　　我在《我的 HexoBlog 的诞生（一）》中已经完成了 Git 的安装和配置，不过那只是在 Windows上，而且也没详细讲，这里就详细讲解一下如何在 Windows 和 Linux 上安装和配置 Git 吧。

### Windows 10 上安装和配置 Git

1. 点击安装程序；

   ![安装程序](https://image.ql-isaac.cn/%E5%AE%89%E8%A3%85%E7%A8%8B%E5%BA%8F.png)

2. GNU 许可证：不看，Next；

   ![许可协议](https://image.ql-isaac.cn/%E8%AE%B8%E5%8F%AF%E5%8D%8F%E8%AE%AE.png)

3. 设置安装路径：建议将 C 改为 D，安装在 D 盘，这里就不改了，Next；

   ![设置安装路径](https://image.ql-isaac.cn/%E8%AE%BE%E7%BD%AE%E5%AE%89%E8%A3%85%E8%B7%AF%E5%BE%84.png)

4. 安装组件：第一个选项是说是否创建桌面快捷方式，可以不勾选，下面六个都勾选了，为默认，不更改，倒数第一个是说是否检查更新，可以不勾选，倒数第二个是说是否在所有控制台窗口中使用 TrueType 字体，勾选，Next；

   ![安装组件](https://image.ql-isaac.cn/%E5%AE%89%E8%A3%85%E7%BB%84%E4%BB%B6.png)

5. 开始菜单设置：直接 Next；

   ![开始菜单设置](https://image.ql-isaac.cn/%E5%BC%80%E5%A7%8B%E8%8F%9C%E5%8D%95%E8%AE%BE%E7%BD%AE.png)

6. 设置 Git 的默认文本编辑器：就选择 Vim，Next；

   ![设置Git的默认文本编辑器](https://image.ql-isaac.cn/%E8%AE%BE%E7%BD%AEGit%E7%9A%84%E9%BB%98%E8%AE%A4%E6%96%87%E6%9C%AC%E7%BC%96%E8%BE%91%E5%99%A8.png)

7. 调整 PATH 环境：就选择默认推荐的，Next。该推荐项是说仅向 PATH 添加一些最小的 Git 包装器，以避免使用可选的 Unix 工具造成环境混乱，能够通过 Git Bash、命令提示符、Windows PowerShell 以及在 PATH 中寻找 Git 的任何第三方软件使用 Git。

   ![调整Path环境](https://image.ql-isaac.cn/%E8%B0%83%E6%95%B4Path%E7%8E%AF%E5%A2%83.png)

8. 选择 HTTPS 后端传输：第一个选项是说使用 OpenSSL 库，服务器证书将使用 ca-bundle.crt 文件进行验证，这是我们常用的选项。第二个选项是说使用本地 Windows 安全通道库，服务器证书将使用 Windows 证书存储验证，此选项还允许使用公司的内部根 CA 证书，例如通过 Active Directory Domain Services。这里，就默认第一个选项，Next；

   ![选择HTTPS后端传输](https://image.ql-isaac.cn/%E9%80%89%E6%8B%A9HTTPS%E5%90%8E%E7%AB%AF%E4%BC%A0%E8%BE%93.png)

9. 配置行尾符号转换：第一个选项是说签出 Windows 风格，提交 Unix 风格的行尾，即签出文本文件时，Git 会将 LF 转换为 CRLF，提交文本文件时，CRLF 将转换为 LF，对于跨平台项目，这是 Windows 上的推荐设置（“core.autocrlf”设置为“true”）。第二个选项是说按原样签出，提交 Unix 样式的行尾，签出文本文件时，Git 不会执行任何转换，提交文本文件时，CRLF 将转换为 LF，对于跨平台项目，这是 Unix 上的建议设置（“core.autocrlf”设置为“input”）。第三个选项是说按原样签出，按原样提交，当签出或提交文本文件时，Git 不会执行任何转换，不建议跨平台项目选择此选项（“core.autocrlf”设置为“false”）。这里，就默认第一个选项，Next；

   ![配置行尾符号转换](https://image.ql-isaac.cn/%E9%85%8D%E7%BD%AE%E8%A1%8C%E5%B0%BE%E7%AC%A6%E5%8F%B7%E8%BD%AC%E6%8D%A2.png)

10. 配置终端模拟器以与 Git Bash 一起使用：第一个选项是说使用 MinTTY（MSYS2 的默认终端）。Git Bash 将使用 MinTTY 作为终端模拟器，该模拟器具有可调整大小的窗口，非矩形选择和 Unicode 字体，Windows 控制台程序（例如交互式 Python）必须通过“ winpty”启动才能在 MinTTY 中运行。第二个选项是说使用 Windows 的默认控制台窗口。Git 将使用 Windows 的默认控制台窗口（“cmd.exe”），该窗口可以与 Win32 控制台程序（如交互式 Python 或 node.js）一起使用，但默认的回滚非常有限，需要配置为使用 unicode 字体以正确显示非 ASCII 字符，并且在 Windows 10 之前，其窗口不能自由调整大小，并且只允许矩形文本选择。这里，就默认第一个选项，Next；

   ![配置终端模拟器以与Git_Bash一起使用](https://image.ql-isaac.cn/%E9%85%8D%E7%BD%AE%E7%BB%88%E7%AB%AF%E6%A8%A1%E6%8B%9F%E5%99%A8%E4%BB%A5%E4%B8%8EGit_Bash%E4%B8%80%E8%B5%B7%E4%BD%BF%E7%94%A8.png)

11. 配置额外的选项：第一个选项是说启用文件系统缓存。文件系统数据将被批量读取并缓存在内存中用于某些操作（“core.fscache”设置为“true”）， 这可以显着地提升性能。第二个选项是说启用 Git 凭证管理器。Windows 的 Git 凭证管理器为 Windows 提供安全的 Git 凭证存储，最显著的是对 Visual Studio Team Services 和 GitHub 的多因素身份验证支持（需要 .NET Framework v4.5.1 或更高版本）。第三个选项是说启用符号链接，启用符号链接需要 SeCreateSymbolicLink 权限，现有存储库不受此设置的影响。这里，就默认第一个和第二个选项，Install；

   ![配置额外的选项](https://image.ql-isaac.cn/%E9%85%8D%E7%BD%AE%E9%A2%9D%E5%A4%96%E7%9A%84%E9%80%89%E9%A1%B9.png)

12. 安装完成：Next；

   ![安装完成](https://image.ql-isaac.cn/%E5%AE%89%E8%A3%85%E5%AE%8C%E6%88%90.png)

13. Release Notes；

   ![ReleaseNotes](https://image.ql-isaac.cn/ReleaseNotes.png)

14. 至此 Git 就算安装完毕了，之后需要去 [Github](https://github.com/) 注册一个自己的账号，注意需要绑定自己的邮箱，建议是谷歌邮箱；

![注册](https://image.ql-isaac.cn/%E6%B3%A8%E5%86%8C.png)

15. 在桌面右键，点击 Git Bash Here；

   ![桌面右键](https://image.ql-isaac.cn/%E6%A1%8C%E9%9D%A2%E5%8F%B3%E9%94%AE.png)

16. 全局用户信息配置：分别输入以下两个命令回车执行，无提示表示命令执行成功，可以用`git config --list`来查看配置好的信息；

   ```bash
   $ git config --global user.name "<自己的 Github 用户名>"
   ```

   ```bash
   $ git config --global user.email "<自己的 Github 邮箱>"
   ```

17. 生成 SSH 秘钥：输入以下命令回车执行，然后连敲三次回车键，此时打开 .ssh 文件夹，其位于自己的 Windows 用户文件夹下，如下图，用文本编辑器打开 id_rsa.pub，Ctrl+A，复制里面全部的内容；

   ```bash
   $ ssh-keygen -t rsa
   ```

   ![SSH](https://image.ql-isaac.cn/SSH.png)

18. Github 的 SSH 公钥配置：登录自己的 Github 账号，点击右上角的头像，点击 Setting，点击左侧的 SSH and GPG keys，点击右侧的 New SSH key，填写 Tile，粘贴刚复制的内容为 Key，最后点击 Add SSH key；

19. 测试一下，输入以下命令回车执行，输入 yes，再回车，有如下提示，表示本机和自己的 GitHub 绑定成功。

   ```bash
   $ ssh -T git@github.com
   ```

   ```
   Hi <自己的 Github 用户名>! You've successfully authenticated, but GitHub does not provide shell access.
   ```

### Ubuntu 18.04 LTS 上安装和配置 Git

1. 相比在 Windows 上，在 Linux 上安装和配置 Git 的步骤就比较少了。在终端输入以下命令回车执行，确保系统和 apt 包列表完全更新；

   ```bash
   $ sudo apt-get update -y
   ```
![更新](https://image.ql-isaac.cn/%E6%9B%B4%E6%96%B0.png)
2. 在终端输入以下命令回车，安装 Git，可输入以下命令查看 Git 版本；

   ```bash
   $ sudo apt install git
   ```

   ```bash
   $ git --version
   ```

   ![安装Git](https://image.ql-isaac.cn/%E5%AE%89%E8%A3%85Git.gif)

3. 全局用户信息配置：分别输入以下两个命令回车执行，无提示表示命令执行成功，可以用`git config --list`来查看配置好的信息；

   ```bash
   $ git config --global user.name "<自己的 Github 用户名>"
   ```

   ```bash
   $ git config --global user.email "<自己的 Github 邮箱>"
   ```

4. 生成 SSH 秘钥：输入以下命令回车执行，然后连敲三次回车键；

   ```bash
   $ ssh-keygen -t rsa
   ```

5. 输入以下命令回车，输入用户密码安装 Vim 文本编辑器；

   ```bash
   $ sudo apt-get install vim
   ```

6. 执行以下命令，用 Vim 打开公钥文件，复制其中的内容（不要复制多了，也不要复制少了）；

   ```bash
   $ vim /home/<自己的用户名>/.ssh/id_rsa.pub
   ```

7. 登录自己的 Github 账号，点击右上角的头像，点击 Setting，点击左侧的 SSH and GPG keys，点击右侧的 New SSH key，填写Tile，粘贴刚复制的内容为 Key，最后点击 Add SSH key；

8. 测试一下，输入以下命令回车执行，有如下提示，表示本机和自己的 GitHub 绑定成功。
   ```bash
   $ ssh -T git@github.com
   ```

   ```
   Hi <自己的GitHub用户名>! You've successfully authenticated, but GitHub does not provide shell access.
   ```

## Git 的工作流程

1. 克隆 Git 资源作为工作副本；

2. 在工作副本中编辑、添加或修改文件；

3. 如果其他人提交了修改，你可以选择更新工作副本；

4. 在提交前查看修改；

5. 提交修改；

6. 在修改完成后，如果发现错误，可以撤回提交并再次修改并提交。

![Git 的工作流程](https://cdn.jsdelivr.net/gh/ql-isaac/post-images-1/What-is-Git/Git%20的工作流程.png)

## Git 工作区、暂存区和版本库

- 工作区：工作目录的实际情况。
- 暂存区：即工作副本（修改）。
- 版本库：即历史提交。