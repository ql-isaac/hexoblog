---
title: 建立个人云服务（一）
date: 2021-09-08 11:03:53
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/建立个人云服务.png
tags:
  - code-server v3.11.1
  - Ubuntu 18.04 LTS
categories:
  - TencentCloud Lighthouse
---

静态网站的弊端就是不能随时随地的更新，这是我一直以来的痛。

<!-- more -->

## Codespaces

Codespaces 是 GitHub 推出的在线编辑器，简单点说，就是可以实现将你本地的以 VsCode 为核心的开发环境迁移到云端，这样你只需要使用浏览器就可以随时随地进行开发，还可以多人协作。

目前这一云服务还不能免费使用，但是有一部分功能可以免费使用，那就是升级版的代码浏览编辑功能，请看下图。

![代码浏览编辑](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/代码浏览编辑.png)

以我的仓库为例，在仓库页面，按下 `.`之后，天啊，这不就是 Web 版 VsCode 吗？

![HexoBlog](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/HexoBlog.png)

再结合 GitHub Actions，这不就实现了在线写博客了吗？

可是我突然又发现了另外一个痛点，这写完博客不能 `hexo s`预览怎么办？也不能升级主题什么的，到头来还是要在本地环境写博客预览发布。

## code-server[^2]

我抓住网页端 VsCode 这一关键词，果然搜到了这个开源项目 [code-server](https://github.com/cdr/code-server)，那么，我之前买的腾讯云无忧实例就有用武之地了。

SSH 方式登录实例，我的实例是 Ubuntu 18.04 的，执行如下命令，其中 $VERSION 替换为版本号。

```bash
curl -fOL https://github.com/cdr/code-server/releases/download/v$VERSION/code-server_$VERSION_amd64.deb
```

发现根本下不动，正常正常。其实以上命令就是下载那个 deb 包，于是直接在仓库 Releases 页面下载然后上传到实例中，下载速度还不赖。

上传完成后，就是安装了，安装命令如下。

```bash
sudo dpkg -i code-server_$VERSION_amd64.deb
```

最后启用并启动服务，其中 $USER 替换为你自己的用户名，这个各位自定义即可。

```bash
sudo systemctl enable --now code-server@$USER
```

现在，就可以访问本地 8080 端口了，此时如果你以为也可以通过实例的公网 IP 加端口访问到 code-server 就大错特错了。我一开始也是这么以为，在实例控制台放行了端口还是不行，原来目前只是本地运行，要想暴露在公网，需要使用 HTTPS，code-server 的官方文档提供给了几种解决办法，我使用的是 Caddy，它类似于 Nginx，但相比之下它最大的一个特点是能帮你自动申请域名的数字证书。

首先是到自己的域名服务商那里添加一个 A 记录，主机记录就填 dev，记录值填实例的公网 IP，接着就是安装 Caddy，依次执行以下命令。

```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/cfg/gpg/gpg.155B6D79CA56EA34.key' | sudo apt-key add -
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/cfg/setup/config.deb.txt?distro=debian&version=any-version' | sudo tee -a /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
```

接着执行如下命令编辑 Caddyfile。

```bash
sudo vim /etc/caddy/Caddyfile
```

删除原来的内容，进行如下配置。

```
dev.ql-isaac.cn {
    reverse_proxy 127.0.0.1:8080
}
```

最后重启 Caddy 服务：

```bash
sudo systemctl reload caddy
```

这时，就可以通过域名公网访问了：

![公网访问](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/公网访问.png)

以上的密码可以打开 config.yaml 查看：

```bash
cat ~/.config/code-server/config.yaml
```

或者自己设定密码，$USER 替换为你自己的用户名：

```bash
vim ~/.config/code-server/config.yaml
sudo systemctl restart code-server@$USER
```

手机端也可以用：

![手机端](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/手机端.jpg)

[^1]: [code-server 安装](https://github.com/cdr/code-server/blob/main/docs/install.md#debian-ubuntu)
[^2]: [code-server 指导](https://github.com/cdr/code-server/blob/main/docs/guide.md#using-lets-encrypt-with-caddy)
