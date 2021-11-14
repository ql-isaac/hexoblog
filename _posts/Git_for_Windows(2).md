---
title: Git for Windows(2)
date: 2021-08-22 16:14:00
cover: https://image.ql-isaac.cn/Git_for_Windows.jpg
categories:
- Git for Windows
---

来记录一下 Git for Windows 的使用。

<!-- more -->

不可告人的缘由，我需要另外创建一个 GitHub 小号（[isaac-ql](https://github.com/isaac-ql)），创建完账号后，就应该是去绑定个人电脑的 SSH key，我想当然的以为可以复用建博客时生成的 SSH key，结果 GitHub 给我了这个提示：

![Key is already in use](https://image.ql-isaac.cn/Git_for_Windows/Key_is_already_in_use.png)

好吧，看来是不能复用。百度一番后，解决办法如下：

1. 右键，点击 Git Bash Here，执行以下命令，生成另外一对公钥与私钥，不能与之前的重名：

```bash
ssh-keygen -t rsa -f ~/.ssh/<自定义 SSH key 文件名>
```

2. 将公钥添加到自己的小号里，不多说了；
3. 进入 .ssh 文件夹（在用户文件夹下），新建 config 文件（注意这是 config 是完整文件名），编辑：

```diff
+Host github.com
+    HostName github.com
+    PreferredAuthentications publickey
+    IdentityFile ~/.ssh/id_rsa     
+Host <自定义别名>
+    HostName github.com
+    PreferredAuthentications publickey
+    IdentityFile ~/.ssh/<自定义 SSH key 文件名>
```

3. 以后在以 SSH 方式克隆 GitHub 小号时，将原来的地址@后面的域名改为以上的自定义别名即可。

- - - 

如下图，`git clone`很慢怎么办？

![克隆很慢](https://image.ql-isaac.cn/Git_for_Windows/克隆很慢.png)

请那啥之后设置代理（我使用的代理软件是 Clash）：

1. 要那啥，此处省略一百个字；
2. 右键，点击 Git Bash Here，依次执行以下命令：

```bash
git config --global http.https://github.com.proxy socks5://127.0.0.1:<socks代理端口号>
```

```bash
git config --global https.https://github.com.proxy socks5://127.0.0.1:<socks代理端口号>
```

3. 打开 Clash 的全局代理；
4. 起飞，还没开始截图就克隆完毕了。

![起飞](https://image.ql-isaac.cn/Git_for_Windows/起飞.png)