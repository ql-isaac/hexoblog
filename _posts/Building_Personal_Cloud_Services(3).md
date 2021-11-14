---
title: 建立个人云服务（三）
date: 2021-10-13 12:53:21
updated: 2021-11-13 12:53:21
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/建立个人云服务.png
tags:
 - frp v0.37.1
 - Raspberry Pi OS with desktop
 - TencentCloud Lighthouse
categories:
 - 内网穿透
---

上回说到，我辛辛苦苦白忙活了一趟后发现配置太低服务根本跑不起来，奈何高配置的又太贵，于是决定买个树莓派玩玩，搞个自建服务器，但前提是需要内网穿透。

<!-- more -->

## 内网穿透

字面理解，想必大家已经猜到内网穿透是干嘛的了。自己有一台服务器，如何才能向互联网提供服务呢，对于一般个人来说，唯一的方法就是内网穿透，而相应的方案稍微查一查也能发现有许多，我选择的是开源软件——[frp](https://github.com/fatedier/frp)搭配腾讯云无忧实例的方案。

简单说下原理，frp 分为服务端（frps）和客户端（frpc）两部分，frps 部署在腾讯云无忧实例中，frpc 部署在自建服务器中，启动本地服务后，frp 可以把本地服务的端口映射为无忧实例的端口，这样，客户端和无忧实例的端口通信就相当于与本地服务的端口通信。

## 安装 frps

首先是去 frp 仓库下载最新的安装包。如下图，这里有许多的版本，我们 SSH 连接无忧实例执行`uname -i`可查看其硬件平台，是 x86_64，则应该下载 amd64 版本的。

![下载frp](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/下载frp.png)

下载完毕后上传到无忧实例家目录下。

解压缩到家目录：

```bash
tar -zxvf ~/frp_0.37.1_linux_amd64.tar.gz -C ~
```

编辑 frps 配置文件：

```bash
vim ~/frp_0.37.1_linux_amd64/frps.ini
```

默认 frps 绑定的端口是 7000，我们需要再设定一下 Token 认证[^1]，要不然我们的内网穿透服务对任何人都是可用的。为此，追加下面的内容。

```diff
[common]
bind_port = 7000
+authentication_method = token
+token = <一串字符>
```

启动 frps：

```
cd ~/frp_0.37.1_linux_amd64
./frps -c ./frps.ini
```

以这种方式启动的话，你会发现你干不了其他事，按`ctrl+c`的话程序也会退出。我们可以使用`nohup`让其在后台运行，同时错误日志会重定向到 frps.log 中，方便查看：

```bash
nohup ./frps -c ./frps.ini > frps.log 2>&1 &
```

{% note warning %}

后台运行后，如果你是通过 SSH 连接的无忧实例，不要直接叉掉窗口，这样 frps 仍会停止运行，这里需要执行`exit`注销掉当前会话，再叉掉窗口才行。

{% endnote %}

是的，现在 frps 的确是在后台运行了，可是万一无忧实例重启了怎么办，还要执行一下上面的命令。Linux 系统工具——Systemd 是最终的解决之道，刚好在目录 frp_0.37.1_linux_amd64 下有一个 systemd 目录，作者已经给我们提供了现成的配置文件，只需修改一二。

编辑 frps.service：

```bash
cd systemd
vim frps.service
```

```diff
[Unit]
Description=Frp Server Service
After=network.target

[Service]
Type=simple
-User=nobody
+User=ubuntu
Restart=on-failure
RestartSec=5s
-ExecStart=/usr/bin/frps -c /etc/frp/frps.ini
+ExecStart=/home/ubuntu/frp_0.37.1_linux_amd64/frps -c /home/ubuntu/frp_0.37.1_linux_amd64/frps.ini
LimitNOFILE=1048576

[Install]
WantedBy=multi-user.target
```

复制 frps.service 到指定路径下：

```bash
sudo cp ~/frp_0.37.1_linux_amd64/systemd/frps.service /usr/lib/systemd/system
```

启用并启动服务：

```bash
sudo systemctl enable --now frps
```

## 安装 frpc

SSH 连接树莓派4B，执行`uname -i`，是 armv71，应该下载 arm 版本的，如下图。

![arm](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/arm.png)

上传到树莓派、解压，编辑 frpc 配置文件：

```bash
vim ~/Document/frp_0.37.1_linux_arm/frpc.ini
```

```diff
[common]
-server_addr = 127.0.0.1
+server_addr = 119.91.70.149
server_port = 7000
+authentication_method = token
+token = <一串字符>

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 6000
```

{% note info %}

[common] 部分对应 frps 的 [common] 部分，注意 token 要保持一致。[ssh] 部分表示的就是本地 SSH 的 22 端口与无忧实例的 6000 端口的映射关系。关于 frp 的更多使用，可见[官方中文文档](https://gofrp.org/)

{% endnote %}

也是需要后台随操作系统启动运行，同理，编辑 frpc.service：

```bash
vim ~/Document/frp_0.37.1_linux_arm/systemd/frpc.service
```

```diff
[Unit]
Description=Frp Client Service
After=network.target

[Service]
Type=simple
-User=nobody
+User=pi
Restart=on-failure
RestartSec=5s
-ExecStart=/usr/bin/frpc -c /etc/frp/frpc.ini
-ExecReload=/usr/bin/frpc reload -c /etc/frp/frpc.ini
+ExecStart=/home/pi/Document/frp_0.37.1_linux_arm/frpc -c /home/pi/Document/frp_0.37.1_linux_arm/frpc.ini
+ExecReload=/home/pi/Document/frp_0.37.1_linux_arm/frpc reload -c /home/pi/Document/frp_0.37.1_linux_arm/frpc.ini
LimitNOFILE=1048576

[Install]
WantedBy=multi-user.target
```

复制 frpc.service 到指定路径下：

```bash
sudo cp ~/Document/frp_0.37.1_linux_arm/systemd/frpc.service /usr/lib/systemd/system
```

启用并启动服务：

```bash
sudo systemctl enable --now frpc
```

## 验证

[^1]: [Authenticating the Client](https://github.com/fatedier/frp#authenticating-the-client)

