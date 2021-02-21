---
title: Java从入门到实践（一）
date: 2020-02-06 16:03:27
cover: https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning（一）/Java.jpg
tags:
 - Windows 10 专业版
 - JDK 9.0.4
categories:
 - Java从入门到实践
---

　　Java——面向对象编程语言的领军者！

<!-- more -->

## 参考视频教程

https://www.bilibili.com/video/av55246614

## 搭建Java学习环境

### 安装VMware pro 15

　　下载[学习版](https://www.52pojie.cn/thread-1026907-1-1.html)，安装步骤不多说了，只是有一点建议，也是我装软件的原则：能不装C盘就别装C盘。

### 安装Windows 10

　　我在网上找到一个[精简版的Windows 10系统](https://www.cnblogs.com/gxhunter/p/10290748.html)，有介绍和下载方式，这回就用这个精简版的镜像。由于是安装Windows系统，具体如何安装这里就不再多说了。

### 安装JDK 9.0.4

　　[下载JDK 9.0.4](https://pan.baidu.com/s/1R0Y6nDqlYxKvelV3dAtekQ)，提取码：ua1e，下好后安装，安装路径可以自定义，公共JRE可装可不装，如下图，我这次装一装。

![安装](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning（一）/安装.png)

### 配置系统环境变量

　　右键此电脑->属性->高级系统设置->高级->环境变量，点击下方的新建，变量名填写JAVA_HOME，变量值就是安装JDK 9.0.4时设置的路径，确定。

　　如下图，在系统变量栏中找到Path变量，点击编辑，点击新建，键入%JAVA_HOME%\bin，确定。运行CMD，键入java，发现系统识别了java命令。

![Path](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Java-Learning（一）/Path.png)

## String（字符串）

## 类集框架



