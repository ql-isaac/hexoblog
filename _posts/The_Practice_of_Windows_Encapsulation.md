---
title: Windows 封装实践
date: 2021-08-29 15:40:25
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/The_Practice_of_Windows_Encapsulation.png
tags:
 - 优启通 v3.5
 - Easy Sysprep v5.19.802.282 Release1
 - Windows 10 专业版
 - VMware® Workstation 15 Pro(15.5.0 build-14665864)
categories:
 - Windows 封装
---

## 准备工作

1. 使用优启通制作 PE。选择生成 ISO 的制作方式；

    ![生成 ISO](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/生成ISO.png)

2. 准备一个 U 盘，将 Easy Sysprep5、Windows 10 (business edition) ISO镜像和封装的软件放进去；
3. 安装 VMware pro 15。下载[学习版](https://www.52pojie.cn/thread-1026907-1-1.html)，安装步骤不多说了。

## 创建系统封装环境

1. 创建新的虚拟机；

    ![创建新的虚拟机](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/创建新的虚拟机.png)

2. 选择典型；

    ![典型](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/典型.png)

3. 选择安装程序光盘映像文件(iso)，选择准备工作中制作好的 ISO；

    ![安装程序光盘映像文件](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/安装程序光盘映像文件.png)

4. 选择客户机操作系统，按图选择即可；

    ![选择客户机操作系统](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/选择客户机操作系统.png)

5. 命名虚拟机，注意默认虚拟机文件的存放位置是用户文件夹下，建议改到非 C 盘；

    ![命名虚拟机](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/命名虚拟机.png)

6. 指定磁盘容量，考虑到会封装许多软件，容量调大些，100G；

    ![指定磁盘容量](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/指定磁盘容量.png)

7. 完成。

    ![完成](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/完成.png)

## 安装原版 Windows 10 专业版

　　开启此虚拟机，意外发生了：

![意外发生了](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/意外发生了.png)

　　百度到了办法，先关一下机，点击编辑虚拟机设置，点击选项中高级，固件类型选择 BIOS，确定，再开启虚拟机：

![固件类型](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/固件类型.png)

　　选择第二个进入 PE：

![第二个](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/第二个.png)

　　挂载 U 盘，选择准备好的 U 盘，我这里显示的是已经挂载好了：

![挂载 U 盘](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/挂载U盘.png)

　　双击桌面 DG 硬盘分区，选择第一个，即我们上面分配的 100G 的虚拟硬盘，点击快速分区，设置成一个分区就行：

![快速分区](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/快速分区.png)

　　再双击桌面 EIX 系统安装，左侧已经自动识别到我们 U 盘上的镜像，选择 Windows 10 专业版，右侧则是刚刚创建的那个分区，单击选择上，点击一键恢复：

![EIX 系统安装](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/EIX系统安装.png)

　　这里将“恢复完成后自动运行万能驱动”勾掉，确认。等待重启：

![勾掉](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/勾掉.png)

## 系统调整

　　重启之后就到了这个熟悉的流程（OOBE）：

![OOBE](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/OOBE.png)

　　不要着急下一步，这里要按`Ctrl`+`Shift`+`F3`进入审核模式，刚进入是这样的：

![审核模式](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/审核模式.png)

　　注意不要点确定，点了就又退回到 OOBE了，这里点取消：

![取消](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/取消.png)

1. 桌面图标设置。我习惯将“计算机”和“控制面板”显示出来；

    ![桌面图标设置](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/桌面图标设置.png)

2. 颜色偏爱设置。默认 Windows 模式改为浅色，透明效果打开，选择从我的背景自动选取一种主题色；

    ![颜色](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/颜色.png)

3. 显示搜索图标。感觉搜索框太占地方了；

    ![显示搜索图标](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/显示搜索图标.png)

4. 装上 Telnet 客户端。这样可以在 CMD 中使用`telnet`检测目标主机 TCP 端口是否开启；

    ![Telnet 客户端](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/Telnet客户端.png)

5. 显示文件扩展名，这个必须啊；

    ![文件扩展名](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/文件扩展名.png)

6. 系统激活，这个就不多说了；
7. 最后使用 Dism++ 对系统进行优化；

    ![Dism++](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/Dism++.png)

    ![任务栏时钟精确到秒](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/任务栏时钟精确到秒.png)

    ![桌面壁纸质量调整](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/桌面壁纸质量调整.png)

    ![打开资源管理器时显示此电脑](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/打开资源管理器时显示此电脑.png)

    ![最小化时显示完整路径](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/最小化时显示完整路径.png)

## 个人必装软件和设置

1. 顺便将 Dism++ 封装进系统，这个软件还有许多地方可以探索；
2. 安装 Node.js，下一步即可；
3. 安装 Git 和 配置 Git，相关的内容在 [Git for Windows 标签页](https://blog.ql-isaac.cn/tags/Git-for-Windows/) 中；
4. 安装 Notepad3，下一步即可；
5. 安装 Bandizip for Windows，默认即可；
6. Microsoft Edge 登录自己的微软账号；
7. 安装 NeatReader，登录自己的账号；
8. 安装 Typora，按推荐来即可；
9. 将 Universal Viewer Pro 放入 C 盘，为便携版；
10. 安装 Visual Studio Code，建议勾上如图的选项；

    ![VScode](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/VScode.png)

11. 安装火绒，极速安装即可；
12. 将 Beyond Compare 放入 C 盘，为便携版，再运行一下 CMD 以添加右键菜单；

    ![添加右键菜单](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/添加右键菜单.png)

13. 安装 TIM，不登录；
14. 安装 WeGame，这里注意安装路径在不在 C 盘，也是不登陆；
15. 安装 Steam，下一步下一步，登录时需要验证码，填验证码时下面填一个好记的名称；

    ![好记的名称](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/好记的名称.png)

16. 安装战网，完成之后登录并设置为开机不自启动再退出；

## ES5 封装

　　运行 U 盘中的 Easy Sysprep5，点击设置，图中标记自定义即可，其他建议默认，点击封装、确定，等待上方提示完毕，重启进入 PE 执行第二阶段：

![自定义](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/自定义.png)

　　重点来了！点击重启之后请不停按`F2`，直到进入 BIOS：

![进入 BIOS](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/进入BIOS.png)

　　重点没玩。左右键移动到“Boot”，然后让“CD-ROM Drive”往上移动两格，`F10`保存退出：

![调整启动顺序](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/调整启动顺序.png)

　　还没完，`F10`保存退出后按两次回车，到这里也是选择第二个：

![第二个](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/第二个.png)

　　再次运行 Easy Sysprep5，点击设置，优化栏里全不勾选，不需要：

![全不勾选](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/全不勾选.png)

　　部署栏里，我按下图设置，供参考：

![部署栏](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/部署栏.png)

　　系统栏里，我按下图设置，供参考：

![系统栏](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/系统栏.png)

　　用户栏里，我按下图设置，供参考：

![用户栏](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/用户栏.png)

　　其他栏中，有如图的注意，最后点击封装，确定，等待备份镜像完毕：

![其他栏](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/其他栏.png)

　　镜像备份完毕后重启，不用进行任何操作，等待：

![部署](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/部署.png)

![封装完毕](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/The_Practice_of_Windows_Encapsulation/封装完毕.png)
