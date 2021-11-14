---
title: 建立个人云服务（二）
date: 2021-10-03 19:48:18
updated: 2021-10-06 20:44:00
cover: https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/建立个人云服务.png
tags:
 - Atlassian
 - TencentCloud Lighthouse
categories:
 - 项目管理
---

工作的机会，接触到 [Atlassian 公司](https://www.atlassian.com/)旗下的多款软件产品，虽然不是开源的，虽然不是免费的，但是好用啊，无论是对个人还是企业来说。

<!-- more -->

## 下载 Jira Software

Jira Software 是 [Atlassian 公司](https://www.atlassian.com/) 出品的问题管理与协同工具，被广泛应用于缺陷跟踪、客户服务、需求收集、流程审批、任务跟踪、项目跟踪和敏捷管理等工作领域。

Jira Software 有两种部署方式：云平台和自建。云平台方式就是 Atlassian 官方提供全套云服务，你只需要注册账号通过浏览器使用即可，但是这种方式在国内体验并不好，出于个人自学的目的，我选择自建方式。

在[官方下载页面](https://www.atlassian.com/software/jira/download-archives)，选择下载最新的长期支持版。

![长期支持版](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/长期支持版.png)

这里选择 TAR.GZ 格式的，这种格式需要进行手动安装，下载完成后使用 SSH 上传到无忧实例家目录下的 Atlassian 下。

![tar.gz](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/tar.gz.png)

这里有安装手册，官方的文档写得非常好，只是需要一点英文基础。

![安装手册](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/安装手册.png)

## 下载 Confluence

Confluence 是 [Atlassian 公司](https://www.atlassian.com/) 出品的知识管理与协同软件，可以用于构建企业 wiki。

Confluence 同样有两种部署方式：云平台和自建，我们还是选择自建。

在[官方下载页面](https://www.atlassian.com/software/confluence/download-archives)，也是选择最新的长期支持版和 TAR.GZ 格式下载，然后上传到无忧实例家目录下的 Atlassian 下。

![confluence](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/confluence.png)

## 下载安装 Jdk8

前往[官方下载地址](https://www.oracle.com/java/technologies/downloads/#java8)，也是下载 TAR.GZ 格式的，如下图，这里需要登录才能下载，没有账号就注册一下。

![jdk8](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/jdk8.png)

下载完成后，使用 root 用户登录无忧实例，如果确认密码是正确的还是登不上，那可能是 SSH 没开启 root 远程登录，百度一下即可。登录上之后创建目录，如下。

```bash
mkdir /usr/lib/jdk
```

上传刚刚下好的 Jdk 到此目录下，再解压到此目录下。

```bash
tar -zxvf jdk-8u301-linux-x64.tar.gz -C /usr/lib/jdk
```

再换成 ubuntu 用户登录，这是平常使用的用户。编辑 .bashrc。

```bash
vim ~/.bashrc
```

在文件的末尾，空一格，追加下面内容：

```
#Set Oracle Jdk environment
export JAVA_HOME=/usr/lib/jdk/jdk1.8.0_301
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH
```

使环境变量马上生效:

```bash
source ~/.bashrc
```

执行如下命令，输出版本信息，表明 Jdk 安装成功。

![安装成功](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/安装成功.png)

## 下载安装配置 MySQL5.7[^3]

分别执行以下命令，下载 MySQL APT 并安装。

```bash
wget https://repo.mysql.com/mysql-apt-config_0.8.19-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.19-1_all.deb
```

选择第一个回车，之后可以选择版本，也是选择第一个 mysql-5.7，回车，回到了上一级，移动到最底下，即选择 Ok，回车：

![回车](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/回车.png)

使用以下命令更新 MySQL APT 存储库中的包信息。

```bash
sudo apt-get update
```

执行以下命令安装 MySQL，安装过程中会要求输入 root 数据库用户的密码。

```bash
sudo apt-get install mysql-server
```

安装完成后，服务是已经启动的，可执行以下命令查看。

```bash
systemctl status mysql
```

编辑 my.cnf：

```bash
sudo vim /etc/mysql/my.cnf
```

空一行，追加以下内容：

```
[mysqld]
character-set-server=utf8mb4
collation-server=utf8mb4_bin
default-storage-engine=INNODB
max_allowed_packet=256M
transaction-isolation=READ-COMMITTED
binlog_format=row
log-bin-trust-function-creators = 1
optimizer_switch = derived_merge=off
innodb_default_row_format=DYNAMIC
innodb_large_prefix=ON
innodb_file_format=Barracuda
innodb_log_file_size=2G
```

重启 MySQL：

```bash
sudo service mysql stop
sudo service mysql start
```

如下，以 root（不是操作系统的 root）登入 MySQL，密码就是上面设定的。

```bash
mysql -u root -p
```

这里可以看到 MySQL 的具体版本：

![具体版本](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/具体版本.png)

分别执行以下 SQL，创建数据库用户 jira 和 confluence，数据库 jiradb 和 confluencedb。

```sql
CREATE USER jira IDENTIFIED by '<jira的密码>';
CREATE USER confluence IDENTIFIED by '<confluence的密码>';
CREATE DATABASE jiradb CHARACTER SET utf8mb4 COLLATE utf8mb4_bin;
CREATE DATABASE confluence CHARACTER SET utf8mb4 COLLATE utf8mb4_bin;
```

分别执行以下 SQL，授予数据库用户 jira 和 confluence 相应权限。

```sql
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,REFERENCES,ALTER,INDEX on jiradb.* TO 'jira'@'%' IDENTIFIED BY '<自己设定的jira的密码>';
GRANT ALL PRIVILEGES ON confluencedb.* TO 'confluence'@'%' IDENTIFIED BY '<自己设定的confluence的密码>';
```

最后使权限生效。

```sql
flush privileges;
```

退出 MySQL：

```
exit
```

## 下载 MySQL JDBC Drive

了解到要想使用 confluence，官方推荐的 JDBC driver 是 5.1 版本的[^4]，于是前往 [MySQL 官方地址下载该版本的 JDBC driver](https://downloads.mysql.com/archives/c-j/)，如下图，注意选择 Platform Independent，即与平台无关。

![Platform-Independent](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/Platform-Independent.png)

下载完成后直接解压到当前文件夹，我们只需要里面的 jar 文件，如下图，先将其上传到无忧实例家目录下的 Atlassian 下。

![jar](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/jar.png)

Jira 也可以使用 5.1 版本的 JDBC driver[^5]，那就不用再下了。

## 安装 Jira Software[^6]

### 准备

1. 创建安装目录：

```bash
mkdir ~/Atlassian/jirasoftware
```
2. 解压压缩包到安装目录：

```bash
tar -xzf ~/Atlassian/atlassian-jira-software-8.13.11.tar.gz -C ~/Atlassian/jirasoftware
```
3. 复制下载好的 MySQL JDBC Drive 到相应目录：

```bash
cp ~/Atlassian/mysql-connector-java-5.1.49.jar ~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/lib
```

4. 创建 Jira Software 的家目录，这是应用产生的数据的存放之处：

```bash
mkdir ~/Atlassian/jirasoftware/jirasoftware-home
```

5. 创建了家目录，就要告诉 Jira Software 家目录在哪儿，同样是编辑 .bashrc，在文件的末尾空一格，追加下面内容：

```
export JIRA_HOME=~/Atlassian/jirasoftware/jirasoftware-home
```

### 使用 Candy 代理 Jira Software

注释掉无代理连接器：

```diff
#本行为~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/conf/server.xml的第17行（随着Jira Software的不断更新，本行对应在你的server.yml中不一定是第17行，请以实际情况为准）
<Server port="8005" shutdown="SHUTDOWN">
    <Listener className="org.apache.catalina.startup.VersionLoggerListener"/>
    <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on"/>
    <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener"/>
    <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener"/>
    <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener"/>

    <Service name="Catalina">
        <!--
         ==============================================================================================================
         DEFAULT - Direct connector with no proxy for unproxied access to Jira.

         If using a http/https proxy, comment out this connector.
         ==============================================================================================================
        -->

        <!-- Relaxing chars because of JRASERVER-67974 -->
-        <Connector port="8080" relaxedPathChars="[]|" relaxedQueryChars="[]|{}^\`"<>"
-                   maxThreads="150" minSpareThreads="25" connectionTimeout="20000" enableLookups="false"
-                   maxHttpHeaderSize="8192" protocol="HTTP/1.1" useBodyEncodingForURI="true" redirectPort="8443"
-                   acceptCount="100" disableUploadTimeout="true" bindOnInit="false"/>
```

```diff
#本行为~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/conf/server.xml的第17行（随着Jira Software的不断更新，本行对应在你的server.yml中不一定是第17行，请以实际情况为准）
<Server port="8005" shutdown="SHUTDOWN">
    <Listener className="org.apache.catalina.startup.VersionLoggerListener"/>
    <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on"/>
    <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener"/>
    <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener"/>
    <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener"/>

    <Service name="Catalina">
        <!--
         ==============================================================================================================
         DEFAULT - Direct connector with no proxy for unproxied access to Jira.

         If using a http/https proxy, comment out this connector.
         ==============================================================================================================
        -->

        <!-- Relaxing chars because of JRASERVER-67974 -->
+        <!--
+        <Connector port="8080" relaxedPathChars="[]|" relaxedQueryChars="[]|{}^\`"<>"
+                   maxThreads="150" minSpareThreads="25" connectionTimeout="20000" enableLookups="false"
+                   maxHttpHeaderSize="8192" protocol="HTTP/1.1" useBodyEncodingForURI="true" redirectPort="8443"
+                   acceptCount="100" disableUploadTimeout="true" bindOnInit="false"/>
+        -->
```

要使用 Candy 代理，需要将 HTTPS 代理连接器放开，同时设置端口为8081（8080 已经用于本系列第一篇中的 code-server 服务了），代理域名设为 proj.ql-isaac.cn：

```diff
#本行为~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/conf/server.xml的第62行（随着Jira Software的不断更新，本行对应在你的server.yml中不一定是第62：行，请以实际情况为准）
        <!--
         ==============================================================================================================
         HTTPS - Proxying Jira via Apache or Nginx over HTTPS

         If you're proxying traffic to Jira over HTTPS, uncomment the below connector and comment out the others.
         Ensure the proxyName and proxyPort are updated with the appropriate information if necessary as per the docs.

         See the following for more information:

            Apache - https://confluence.atlassian.com/x/PTT3MQ
            nginx  - https://confluence.atlassian.com/x/DAFmGQ
         ==============================================================================================================
        -->

-        <!--
-        <Connector port="8080" relaxedPathChars="[]|" relaxedQueryChars="[]|{}^\`"<>"
-                   maxThreads="150" minSpareThreads="25" connectionTimeout="20000" enableLookups="false"
-                   maxHttpHeaderSize="8192" protocol="HTTP/1.1" useBodyEncodingForURI="true" redirectPort="8443"
-                   acceptCount="100" disableUploadTimeout="true" bindOnInit="false" secure="true" scheme="https"
-                   proxyName="<subdomain>.<domain>.com" proxyPort="443"/>
-        -->
```

```diff
#本行为~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/conf/server.xml的第62行（随着Jira Software的不断更新，本行对应在你的server.yml中不一定是第62行，请以实际情况为准）
        <!--
         ==============================================================================================================
         HTTPS - Proxying Jira via Apache or Nginx over HTTPS

         If you're proxying traffic to Jira over HTTPS, uncomment the below connector and comment out the others.
         Ensure the proxyName and proxyPort are updated with the appropriate information if necessary as per the docs.

         See the following for more information:

            Apache - https://confluence.atlassian.com/x/PTT3MQ
            nginx  - https://confluence.atlassian.com/x/DAFmGQ
         ==============================================================================================================
        -->

+        <Connector port="8081" relaxedPathChars="[]|" relaxedQueryChars="[]|{}^\`"<>"
+                   maxThreads="150" minSpareThreads="25" connectionTimeout="20000" enableLookups="false"
+                   maxHttpHeaderSize="8192" protocol="HTTP/1.1" useBodyEncodingForURI="true" redirectPort="8443"
+                   acceptCount="100" disableUploadTimeout="true" bindOnInit="false" secure="true" scheme="https"
+                   proxyName="proj.ql-isaac.cn" proxyPort="443"/>
```

编辑 Caddyfile，空一行，追加以下内容，重启 Caddy 服务：

```
proj.ql-isaac.cn {
    reverse_proxy 127.0.0.1:8081
}
```

{% note info %}

编辑 Caddyfile 和重启 Caddy 服务请见[本系列第一篇](https://blog.ql-isaac.cn/2021/09/08/Building_Personal_Cloud_Services(1)/#code-server[1][2])

{% endnote %}

启动 Jira：

```bash
cd ~/Atlassian/jirasoftware/atlassian-jira-software-8.13.11-standalone/bin
./start-jira.sh
```

### 设置 Jira Software

现在，可以通过域名公网访问了，还需要完成最后几步，先将语言设置成中文，如下图。

![language](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/language.png)

选择第二个，下一步：

![第二个](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/第二个.png)

选择“其他数据库”，设置数据库，密码就是上面自己设定的，设置好后可以点击测试连接，如下图，提示成功后下一步。

![测试连接成功](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/测试连接成功.png)

心头一震，响应失败了：

![无法处理此请求](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/无法处理此请求.png)

马上看了一下资源使用情况，如下图，好家伙，看来这 1h2g 的配置完全不够啊。

![不堪重负](https://cdn.jsdelivr.net/gh/isaac-ql/post-images-1/Building_Personal_Cloud_Services/不堪重负.png)

等了许久，一直都显示的满负荷，去 TencentCloud Lighthouse 的监控页面看了一下，监控数据都接收不到，看来是死机了。

看了一下轻量无忧计划 2h4g 的费用，告辞，本次搭建失败。后面考虑自建服务器吧，玩玩树莓派？

[^1]: [A Quick Guide to Using the MySQL APT Repository](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/)

[^2]: [Database Setup For MySQL](https://confluence.atlassian.com/doc/database-setup-for-mysql-128747.html)

[^3]: [Connecting Jira applications to MySQL 5.7](https://confluence.atlassian.com/adminjiraserver0813/connecting-jira-applications-to-mysql-5-7-1027137456.html)

[^4]: [Database JDBC Drivers](https://confluence.atlassian.com/doc/database-jdbc-drivers-171742.html)

[^5]: [Supported platforms](https://confluence.atlassian.com/adminjiraserver0813/supported-platforms-1027137429.html)

[^6]: [Installing Jira applications on Linux from Archive File](https://confluence.atlassian.com/adminjiraserver0813/installing-jira-applications-on-linux-from-archive-file-1027137443.html)
