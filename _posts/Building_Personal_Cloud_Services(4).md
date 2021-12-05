---
title: 建立个人云服务（四）
date: 2021-11-11 17:00:00
updated: 2021-11-11 22:00:00
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/建立个人云服务.png
tags:
 - frp v0.37.1
 - code-server v3.12.0
 - Ubuntu 18.04.4 LTS
categories:
 - TencentCloud Lighthouse
---

腾讯云的这个 1h2g 无忧实例，一个月 15 元还是贵了点，计划 22 年 1 月 25 日到期之后就不续费了，还是新用户最划算。

<!-- more -->

## 双十一活动

腾讯云在双十一推出智惠云集活动，下图这个轻量应用服务器实在是太香了，可是我已经不符合要求了，于是邀请来一位符合条件的小伙伴来买，我们两共用，买的时候镜像还是选择 Ubuntu 18.04。

![智惠云集活动](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/What_is_GitHub/智惠云集活动.jpg)

## 迁移 code-server

直接下载安装最新版本的安装包，再安装Caddy。具体安装方式和[之前](https://blog.ql-isaac.cn/2021/09/08/Building_Personal_Cloud_Services(1)/#code-server)完全一样。

code-server 所有的用户数据都在某一目录下[^1]。我们 SSH 连接无忧实例，将该目录打包压缩得到 code-server.tar.gz：

```bash
cd ~/.local/share/
tar -zcf code-server.tar.gz code-server
```

SSH 连接新买的轻量实例，保险起见，将本机的 code-server 用户数据目录也打包压缩一下后删除：

```bash
cd ~/.local/share/
tar -zcf code-server.tar.gz.bak code-server
rm -rf code-server
```

SFTP 上传以上 code-server.tar.gz（也是目录 share 下面），解压缩：

```bash
tar -zxf code-server.tar.gz
```

无需重启服务，直接登录 code-server，就会发现之前无忧实例中的设置和配置都迁移过来了（如果你已经登录，直接刷新应该也是没问题的）。

## 迁移 frps

参考[当时的安装方式](https://blog.ql-isaac.cn/2021/10/13/Building_Personal_Cloud_Services(3)/#%E5%AE%89%E8%A3%85-frps)，迁移方式其实很简单：直接将目录 frp_0.37.1_linux_amd64 转移过来，复制里面的 frps.service 到指定路径下，启用并启动服务。

经过测试，发现 frps.service 启动不起来，查看下日志发现权限不足：

```bash
journalctl -u frps.service
```

```text
Nov 11 22:03:28 VM-16-11-ubuntu systemd[1]: Started Frp Server Service.
Nov 11 22:03:28 VM-16-11-ubuntu systemd[28411]: frps.service: Failed to execute command: Permission denied
Nov 11 22:03:28 VM-16-11-ubuntu systemd[28411]: frps.service: Failed at step EXEC spawning /home/ubuntu/frp_0.37.1_linux_amd64/frps: Permission denied
Nov 11 22:03:28 VM-16-11-ubuntu systemd[1]: frps.service: Main process exited, code=exited, status=203/EXEC
Nov 11 22:03:28 VM-16-11-ubuntu systemd[1]: frps.service: Failed with result 'exit-code'.
Nov 11 22:03:33 VM-16-11-ubuntu systemd[1]: frps.service: Service hold-off time over, scheduling restart.
Nov 11 22:03:33 VM-16-11-ubuntu systemd[1]: frps.service: Scheduled restart job, restart counter is at 1.
Nov 11 22:03:33 VM-16-11-ubuntu systemd[1]: Stopped Frp Server Service.
```

问题出在转移 frp_0.37.1_linux_amd64 这里，我是直接将无忧实例的以上目录下载下来，再上传到轻量实例中的，这种方式使上传之后的目录权限变为 775，文件权限变为 666，即所有的文件都是没有执行权限的。我们给命令 frps 赋予恰当的权限后重启 frps.service 就没问题了：

```bash
chmod 755 frps
sudo systemctl restart frps.service
```

[^1]: [Upgrade](https://github.com/cdr/code-server/blob/main/docs/upgrade.md)