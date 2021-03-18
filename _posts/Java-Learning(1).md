---
title: Java 从入门到实践（一）
date: 2020-02-06 16:03:27
cover: https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning(1)/Java.jpg
tags:
 - JDK 9.0.4
 - Windows 10 专业版
 - VMware® Workstation 15 Pro(15.5.0 build-14665864)
categories:
 - Java 从入门到实践
---

　　Java——面向对象编程语言的领军者！

<!-- more -->

## 搭建 Java 学习环境

### 安装 VMware pro 15

　　下载[学习版](https://www.52pojie.cn/thread-1026907-1-1.html)，安装步骤不多说了，只是有一点建议，也是我装软件的原则：能不装 C 盘就别装 C 盘。

### 安装 Windows 10

　　我在网上找到一个[精简版的 Windows 10 系统](https://www.cnblogs.com/gxhunter/p/10290748.html)，有介绍和下载方式，这回就用这个精简版的镜像。由于是安装 Windows 系统，具体如何安装这里就不再多说了。

### 安装 JDK 9.0.4

　　[下载 JDK 9.0.4](https://pan.baidu.com/s/1R0Y6nDqlYxKvelV3dAtekQ)，提取码：ua1e，下好后安装，安装路径可以自定义，公共 JRE 可装可不装，如下图，我这次装一装。

![安装](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning(1)/安装.png)

### 配置系统环境变量

　　右键此电脑->属性->高级系统设置->高级->环境变量，点击下方的新建，变量名填写 JAVA_HOME，变量值就是安装 JDK 9.0.4 时设置的路径，确定。

　　如下图，在系统变量栏中找到 Path 变量，点击编辑，点击新建，键入 %JAVA_HOME%\bin，确定。运行 CMD，键入 java，发现系统识别了 java 命令。

![Path](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning(1)/Path.png)

## String（字符串）

## 类集框架

## 参考

[黑马Java零基础入门到就业_Java基础(IDEA版本)](https://www.bilibili.com/video/BV1Lf4y1U7Cz?p=9)