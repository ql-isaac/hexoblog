---
title: Oracle数据库从入门到精通（一）
date: 2020-02-29 18:22:37
cover: https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/Oracle.jpg
tags:
 - Windows 10 专业版
 - Oracle Database 11g Release 2
categories:
 - Oracle数据库从入门到精通
---

　　参考视频教程：https://www.bilibili.com/video/BV1NJ411M7fE?p=80

<!-- more -->

## 下载Oracle Database 11g Release 2

　　访问官方[Oracle Database 11g Release 2下载地址](https://www.oracle.com/database/technologies/oracle-database-software-downloads.html)下载即可，注意有两个压缩包，下好后分别右键解压到当前目录，这样就得到了安装文件夹database。

## 安装和配置Oracle Database 11g Release 2

1. 打开database文件夹，双击setup.exe安装，刚开始有一个如下图的错误，解决办法是编辑database下的stage下的cvu下的cvu_prereq.xml，在<CERTIFIED_SYSTEMS></CERTIFIED_SYSTEMS>间的最后位置添加以下代码，保存并关闭，重新安装即可。

![错误](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/错误.png)

```xml
<OPERATING_SYSTEM RELEASE="6.2">
           <VERSION VALUE="3"/>
           <ARCHITECTURE VALUE="64-bit"/>
           <NAME VALUE="Windows 10"/>
           <ENV_VAR_LIST>
               <ENV_VAR NAME="PATH" MAX_LENGTH="1023" />
           </ENV_VAR_LIST>
</OPERATING_SYSTEM>
```

2. 不更新，下一步；

![不更新](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/不更新.png)

3. 直接下一步；

![创建](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/创建.png)

4. 选择服务器类，下一步；

![服务器类](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/服务器类.png)

5. 直接下一步；

![单实例](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/单实例.png)

6. 选择高级安装，下一步；

![高级安装](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/高级安装.png)

7. 默认即可，下一步；

![语言](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/语言.png)

8. 就选择企业版，下一步；

![企业版](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/企业版.png)

9. 默认即可，下一步；

![默认即可](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/默认即可.png)

10. 默认即可，下一步；

![下一步](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/下一步.png)

11. 自定义SID的名称，不改，就默认也行；

![自定义SID的名称](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/自定义SID的名称.png)

12. 使用Unicode字符集；

![Unicode](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/Unicode.png)

13. 勾选创建具有示例方案的数据库，下一步；

![创建具有示例方案的数据库](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/创建具有示例方案的数据库.png)

14. 默认即可，下一步；

![过](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/过.png)

15. 默认即可，下一步；

![再过](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/再过.png)

16. 不启动自动备份，下一步；

![不自动备份](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/不自动备份.png)

17. 个人学习用，为了方便，设置为对所有账户使用相同的口令（口令必须以字母开头），下一步；

![设置口令](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/设置口令.png)

18. 检查到错误，可以忽略，勾选全部忽略，下一步；

![检查到错误](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/检查到错误.png)

19. 点击完成，等待；

![等待](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/等待.png)

20. 点击口令管理；

![口令管理](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/口令管理.png)

21. 设置sys用户密码为change_on_install，设置system用户为manager，解锁SCOTT用户并设置密码为tiger，解锁SH用户并设置密码为sh，确定，是，确定；

![设置四个用户的密码](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/设置四个用户的密码.png)

22. 安装完成；

![完成](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/完成.png)

## SQL PLUS的使用

### 登录SCOTT用户

　　命令行CMD里输入sqlplus，输入scott，再输入密码tiger（不会回显），即可登录SCOTT用户。

![登录scott用户](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/登录scott用户.gif)

### 第一次查询

　　数据库最重要的组成对象是表，登录上SCOTT用户后，首先通过以下命令查询一下该用户有哪些表吧。

```sql
SELECT * FROM TAB;
```

![第一次查询](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/第一次查询.gif)

　　呃，查询结果显示得比较乱，有一个命令可以解决这个问题，如下，设置每行显示的数据长度，执行完这个命令后再查询一下SCOTT用户有哪些表看看。

```
SET LINESIZE 100
```

![显示问题](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/显示问题.gif)

　　呃，如果觉得TNAME列的数据所占的长度太长了，有一个命令可以解决这个问题，如下，设置TNAME列的数据所占的长度，执行完这个命令后再查询一下SCOTT用户有哪些表看看。

```
COL TNAME FOR A20
```

![太长了](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/太长了.gif)

　　终于，能很舒服地查看到SCOTT用户下有四个表：BONUS、DEPT、EMP和SALGRADE。那么，再查询一下DEPT表吧。

```sql
SELECT * FROM DEPT;
```

![再查询一下DEPT表](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/再查询一下DEPT表.gif)

### 切换用户

　　换个用户登录是怎样的命令？如下命令格式，其中`[]`表示可选内容，`|`表示多选一。

```
CONN[ECT] 用户名/密码 [AS SYSDBA|SYSUSER]
```

　　登录sys用户看看，由于sys是超级管理员用户，命令如下：

```
CONN SYS/change_on_install AS SYSDBA
```

![切换到sys用户](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/切换到sys用户.png)

　　登录system用户看看，由于sys是普通管理员用户，命令如下：

```
CONN SYSTEM/manager
```

![切换到system用户](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/切换到system用户.png)

　　system用户和sys用户都是管理员，应该是可以查询到SCOTT用户的DEPT表的，来试试。

```sql
SELECT * FROM DEPT;
```

![表或视图不存在](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/表或视图不存在.png)

　　来确认一下当前用户是否是管理员用户。

```
SHOW USER
```

![SHOWUSER](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/SHOWUSER.png)

　　这就奇怪了，难道不能查询到？原来，是需要在表前指定用户。

```sql
SELECT * FROM SCOTT.DEPT;
```

![加用户名](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/加用户名.png)

## SQL

　　关系型数据库的理论诞生之后，世界上出现了许多的关系型数据库管理系统，熟悉了A关系型数据库管理系统后几乎还得重新学B关系型数据库管理系统，这很大程度上是由于每个关系型数据库管理系统都实现了自己的一套语言，语言只是一种工具，弄那么多套语言毫无意义，于是，SQL（Structured Query Language，即结构化查询语言）作为一个标准和一个功能强大的关系型数据库语言诞生了。

　　SQL分为以下几类：

- DML（Data Manipulation Language，数据操作语言）：数据查询（SELECT)、数据更新（UPDATE、INSERT和DELETE）和事务管理等。
- DDL（Data Definition Language，数据定义语言）：数据对象定义等（用户和数据表等）。
- DCL（Data Control Language，数据控制语言）：授权等。

## SCOTT的数据表分析

　　在Oracle 11g以前SCOTT和其数据表等是会默认给用户提供的，如果在以上安装Oracle 11g的步骤13中未勾选创建具有示例方案的数据库，我们就需要手动执行一个脚本，该脚本在如下路径。

```
C:\app\ql\product\11.2.0\dbhome_1\RDBMS\ADMIN\scott.sql
```

### 部门信息表（DEPT)

　　先切换回SCOTT用户：

```
CONN SCOTT/tiger
```

　　查询DEPT：

```sql
SELECT * FROM DEPT;
```

　　查看数据表的结构的语法：

```
DESC 数据表;
```

　　查看DEPT的结构：

```
DESC DEPT;
```

![DEPT的结构](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/DEPT的结构.png)

　　DEPT的结构解释：

| 字段   | 含义     | 类型         | 类型作用     | 说明            |
| ------ | -------- | ------------ | ------------ | --------------- |
| DEPTNO | 部门编号 | NUMBER(2)    | 最多2位数字  |                 |
| DNAME  | 部门名称 | VARCHAR2(14) | 最多14位字符 | 3位字符保存中文 |
| LOC    | 部门位置 | VARCHAR2(13) | 最多13为字符 |                 |

### 雇员信息表（EMP）

　　查询EMP：

```sql
SELECT * FROM EMP;
```

　　同样有显示问题，设置一行的长度为150：

```
SET LINESIZE 150
```

　　再查询EMP：

![EMP](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/EMP.png)

　　查看EMP的结构：

```sql
DESC EMP;
```

　　EMP的结构解释：

| 字段     | 含义     | 类型         | 类型作用                     | 说明                             |
| -------- | -------- | ------------ | ---------------------------- | -------------------------------- |
| EMPNO    | 雇员编号 | NUMBER(4)    | 最多4位数字                  |                                  |
| ENAME    | 雇员姓名 | VARCHAR2(10) | 最多10位字符                 |                                  |
| JOB      | 雇员职位 | VARCHAR2(9)  | 最多9位字符                  |                                  |
| MGR      | 领导编号 | NUMBER(4)    | 最多4位数字                  | 领导本身也是雇员                 |
| HIREDATE | 雇佣日期 | DATE         |                              | 包含日期和时间                   |
| SAL      | 基本工资 | NUMBER(7,2)  | 小数位最多2位，整数位最多5位 |                                  |
| COMM     | 佣金     | NUMBER(7,2)  | 小数位最多2位，整数位最多5位 | 只有销售职位的雇员才会存在有佣金 |
| DEPTNO   | 部门编号 | NUMBER(2)    | 最多2位数字                  | 雇员所在的部门编号               |

### 工资等级表（SALGRADE）

　　查询SALGRADE：

```sql
SELECT * FROM SALGRADE;
```

　　查看SALGRADE的结构：

```sql
DESC SALGRADE;
```

![SALGRADE](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/SALGRADE.png)

　　SALGRADE的结构解释：

| 字段  | 含义             | 类型   | 类型作用 | 说明 |
| ----- | ---------------- | ------ | -------- | ---- |
| GRADE | 等级编号         | NUMBER |          |      |
| LOSAL | 此等级的最低工资 | NUMBER |          |      |
| HISAL | 此等级的最高工资 | NUMBER |          |      |

### 工资表（BONUS)

　　BONUS表没有数据，只有表结构。

![BONUS](https://cdn.jsdelivr.net/gh/ql-isaac/CDN1/Oracle-Database-Learning（一）/BONUS.png)

　　BONUS的结构解释：

| 字段  | 含义     | 类型         | 类型作用     | 说明 |
| ----- | -------- | ------------ | ------------ | ---- |
| ENAME | 雇员姓名 | VARCHAR2(10) | 最多10位字符 |      |
| JOB   | 职位     | VARCHAR2(9)  | 最多9位字符  |      |
| SAL   | 基本工资 | NUMBER       |              |      |
| COMM  | 佣金     | NUMBER       |              |      |

