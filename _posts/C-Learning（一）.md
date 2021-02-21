---
title: 	C从入门到精通（一）
date: 2020-02-13 19:56:24
cover: https://image.ql-isaac.cn/C%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%EF%BC%88%E4%B8%80%EF%BC%89.jpg
tags:
 - Ubuntu 18.04 LTS
 - VMware® Workstation 15 Pro(15.5.0 build-14665864)
categories: 
 - C从入门到精通
---

　　任何比C语言更低级的语言，都不足以完整地抽象一个计算机系统，任何比C语言高级的语言，都可以用C语言实现。C语言不像是被发明的，它更像是被发现的，它无可替代、精妙绝伦。

<!-- more -->

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>

## C语言的简单历史

　　C语言是从B语言发展而来，B语言是从BCPL发展而来，BCPL是从FORTRAN发展而来。C语言于1972年11月问世，1973年3月，第三版的Unix上出现了C语言的编译器，1973年11月，第四版的Unix发布了，这个版本是完全用C语言重新写的，1978年美国电话电报公司（AT&T）贝尔实验室正式发布C语言，1983年美国国家标准局（American National Standards Institute，简称 ANSI）开始制定C语言标准，于1989年12月完成，并在1990年春天发布，称之为ANSI C，有时也被称为C89或C90。

## 搭建C语言学习环境

### 安装VMware pro 15

　　下载[学习版](https://www.52pojie.cn/thread-1026907-1-1.html)，安装步骤不多说了，只是有一点建议，也是我装软件的原则：能不装C盘就别装C盘。

### 下载Ubuntu 18.04LTS系统映像

### 安装Ubuntu 18.04LTS

1. VMware pro 15安装完成后，启动，点击创建新的虚拟机；

   ![创建新的虚拟机](https://image.ql-isaac.cn/%E5%88%9B%E5%BB%BA%E6%96%B0%E7%9A%84%E8%99%9A%E6%8B%9F%E6%9C%BA.png)

2. 选择典型，下一步；

   ![典型](https://image.ql-isaac.cn/%E5%85%B8%E5%9E%8B.png)

3. 选择稍后安装操作系统，下一步；

   ![选择稍后安装操作系统](https://image.ql-isaac.cn/%E9%80%89%E6%8B%A9%E7%A8%8D%E5%90%8E%E5%AE%89%E8%A3%85%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.png)

4. 客户机操作系统选择Linux，版本选择Ubuntu 64位，下一步；

   ![选择客户机操作系统](https://image.ql-isaac.cn/%E9%80%89%E6%8B%A9%E5%AE%A2%E6%88%B7%E6%9C%BA%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.png)

5. 虚拟机名称和位置自定义，下一步；

   ![虚拟机名称和位置](https://image.ql-isaac.cn/%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%90%8D%E7%A7%B0%E5%92%8C%E4%BD%8D%E7%BD%AE.png)

6. 磁盘容量自定义。我这里就设为60GB，下一步，完成；

   ![指定磁盘容量](https://image.ql-isaac.cn/%E6%8C%87%E5%AE%9A%E7%A3%81%E7%9B%98%E5%AE%B9%E9%87%8F.png)

7. 点击编辑此虚拟机，将处理器数量设为4（一般为自己实体机处理器数量的一半）；

   ![处理器数量](https://image.ql-isaac.cn/%E5%A4%84%E7%90%86%E5%99%A8%E6%95%B0%E9%87%8F.png)

8. 点击CD/DVD (SATA)，选择使用ISO映像文件，浏览，选择Ubuntu 18.04 LTS系统的ISO映像文件，确定，点击开启此虚拟机，等待；

   ![选择系统镜像](https://image.ql-isaac.cn/%E9%80%89%E6%8B%A9%E7%B3%BB%E7%BB%9F%E9%95%9C%E5%83%8F.png)

9. 选择中文(简体)，再选择安装Ubuntu；

   ![中文简体](https://image.ql-isaac.cn/%E9%80%89%E6%8B%A9%E7%B3%BB%E7%BB%9F%E9%95%9C%E5%83%8F.png)

10. 继续；

   ![继续](https://image.ql-isaac.cn/%E7%BB%A7%E7%BB%AD.png)

11. 勾选最后一个，继续；

   ![勾选](https://image.ql-isaac.cn/勾选.png)

12. 现在安装；

   ![现在安装](https://image.ql-isaac.cn/现在安装.png)

13. 继续；

   ![再次确认](https://image.ql-isaac.cn/再次确认.png)

14. 在地图上点击，选择shanghai，继续；

   ![shanghai](https://image.ql-isaac.cn/shanghai.png)

15. 自定义信息，继续；

   ![您是谁](https://image.ql-isaac.cn/您是谁.png)

16. 等待；

   ![等待](https://image.ql-isaac.cn/等待.png)

17. 现在重启；

   ![现在重启](https://image.ql-isaac.cn/现在重启.png)

18. 登录刚创建的用户。

   ![登录](https://image.ql-isaac.cn/登录.png)

### 安装VMware Tools

　　可以安装上VMware Tools让我们拥有最佳的Ubuntu 18.04 LTS的操作体验，如在实体机上一般。首先点击左上方的虚拟机，再点击安装VMware Tools，这时会在桌面出现一个DVD，接下来具体安装过程如下：

   ![安装VMware_Tools](https://image.ql-isaac.cn/安装VMware_Tools.gif)

### 设置阿里镜像

1. 打开软件更新器；

   ![软件更新器](https://image.ql-isaac.cn/软件更新器.png)

2. 一般会有更新提示，先不更新，点击设置；

   ![设置](https://image.ql-isaac.cn/设置.png)

3. 点击Ubuntu软件，设置下载源；

   ![Ubuntu软件](https://image.ql-isaac.cn/Ubuntu软件.png)

4. 点击其他站点，选择阿里云镜像站点，需要输入用户密码认证；

   ![aliyun](https://image.ql-isaac.cn/aliyun.png)

5. 重新载入可用软件包列表；

   ![重新载入](https://image.ql-isaac.cn/重新载入.png)

6. 现在和以后就可以高速安装更新或软件包了，点击立即安装；

   ![更新](https://image.ql-isaac.cn/更新.png)

### 美化自己的Ubuntu 18.04 LTS

1. 右键点击桌面，在终端打开，输入以下命令回车，输入用户密码安装gnome-tweak-tool软件包；

   ```bash
   sudo apt install gnome-tweak-tool
   ```

2. 火狐浏览器访问[GNOME Shell Extensions](https://extensions.gnome.org)，点击安装该浏览器扩展；

   ![安装浏览器扩展](https://image.ql-isaac.cn/安装浏览器扩展.png)

3. 刷新一下浏览器，这时会有错误信息，右键点击桌面，在终端打开，输入以下命令回车，输入用户密码安装chrome-gnome-shell软件包，再刷新一下浏览器，错误消失了；

   ```bash
   sudo apt install chrome-gnome-shell
   ```

   ![错误](https://image.ql-isaac.cn/错误.png)

4. 分别点击两个GNOME Shell扩展User Themes和Dash to Dock，将它们都开启（即安装）；

   ![两个扩展](https://image.ql-isaac.cn/两个扩展.png)

5. 在安装完Dash to Dock时，你会发现侧边栏消失了，相信这是大多数人想要的效果；

   ![侧边栏消失了](https://image.ql-isaac.cn/侧边栏消失了.png)

6. 打开优化；

   ![优化](https://image.ql-isaac.cn/优化.png)

7. 打开Dash to Dock的设置；

   ![DashtoDock设置](https://image.ql-isaac.cn/DashtoDock设置.png)

8. 打开智能隐藏的设置

   ![智能隐藏的设置](https://image.ql-isaac.cn/智能隐藏的设置.png)

9. 勾选在全屏状态下启用，不勾选推压以显示......，调整显示超时时间为0.2秒，关闭窗口，此时，再打开火狐浏览器，当把鼠标移动到左侧，侧边栏自动显示，移走鼠标，侧边栏自动隐藏，相信这同样是大多数人想要的效果；

   ![设置和调整](https://image.ql-isaac.cn/设置和调整.png)

   ![智能隐藏](https://image.ql-isaac.cn/智能隐藏.gif)

10. 打开火狐浏览器，进入[该网址](https://www.gnome-look.org/p/1275087/)下载McMojave主题，等待，确定；

   ![下载主题](https://image.ql-isaac.cn/下载主题.png)

11. 提取到下载中，点击显示文件；

   ![提取](https://image.ql-isaac.cn/提取.png)

12. 右键，在终端打开；

   ![右键](https://image.ql-isaac.cn/右键.png)

13. 输入以下命令回车，输入用户密码，移动Mojave-light目录；

   ```bash
   sudo mv Mojave-light/ /usr/share/themes/
   ```

14. 打开优化，选择Mojave-light主题，就能看到效果了；

   ![更换主题](https://image.ql-isaac.cn/更换主题.gif)

15. [进入该网址](https://www.gnome-look.org/p/1305429/)，下载McMojave-circle图标，等待，确定；

   ![下载图标](https://image.ql-isaac.cn/下载图标.png)

16. 同上，提取到下载中，点击显示文件，右键，在终端打开，输入以下命令回车，输入用户密码，移动McMojave-circle目录；

   ```bash
   sudo mv McMojave-circle/ /usr/share/icons/
   ```

17. 打开优化，选择McMojave-circle图标，就能看到效果了；

   ![更换图标](https://image.ql-isaac.cn/更换图标.gif)

18. 有一个地方忘记了，打开优化，选择shell为Mojave-light；

   ![更换shell](https://image.ql-isaac.cn/更换shell.gif)

19. 可以在Dash to Dock设置中设置侧边栏的位置在底部；

   ![设置在底部](https://image.ql-isaac.cn/设置在底部.png)

20. 最后，在优化->窗口中，设置标题栏按钮在左边，右键桌面更换个壁纸，至此，美化算是告一段落了。

<video id="video1" preload controls loop style="height: 100%;width: 100%;object-fit: cover;"></video>
<script>
  if (Hls.isSupported()) {
    var video1 = document.getElementById('video1');
    var hls = new Hls();
    hls.loadSource('https://cdn.jsdelivr.net/gh/ql-isaac/CDN2/美化/美化.m3u8');
    hls.attachMedia(video1);
    hls.on(Hls.Events.MANIFEST_PARSED,function() {
      video.play();
  });
  }
</script>

### 安装build-essential软件包和Vim文本编辑器

　　右键点击桌面，在终端打开，输入以下命令回车，输入用户密码安装build-essential软件包。

```bash
sudo apt-get install build-essential
```

　　再输入以下命令回车，输入用户密码安装Vim文本编辑器。

```bash
sudo apt-get install vim
```

## 注释

　　如何注释应该是我们学习任何一门编程语言最先需要知道的，C语言中有两种注释方式：

- 以`/*`开始`*/`结束的块注释（block comment）；
- 以`//`开始换行符结束的单行注释（line comment）；

## C语言学习起步

　　右键点击桌面，新建一个学习文件夹C Learning，点开，再新建文件夹（一），再点开，再新建文件夹20200404 ，再点开，右键，在终端打开。

![20200404](https://image.ql-isaac.cn/20200404.png)

### 新建C源文件、用Vim编辑并保存

　　输入以下命令新建hello_world.c源文件并用Vim打开：

```bash
vim hello_world.c
```

![hello_world.c](https://image.ql-isaac.cn/hello_world.c.png)

　　按下i键进入插入模式，国际惯例，编写第一个程序：打印”Hello,World!”：

```c
#include <stdio.h>
int main(){
    printf("Hello,World!\n"); //print是打印的意思，f是format的简写，printf()函数的功能就是格式化输出
    return 0;
}
```

　　按下ESC键进入一般模式，再按`SHIFT+;`（即:键）进入命令模式，输入wq命令（write和quit），这样源文件就保存了。

![保存](https://image.ql-isaac.cn/保存.gif)

### 编译

　　之后就是编译（小技巧：打hello_world.c时，可以只打h再按TAB键，系统能自动匹配）：

```bash
gcc hello_world.c
```

　　输入以上命令后没有任何提示，别慌，这是正常的，在Linux中，没有消息就是好消息。可以输入以下命令(`ls -alF *`的别名）列出当前目录下有哪些文件和目录，./指的是当前目录，../指的是上一级目录，hello_world.c是刚刚保存的C源文件，那这个“a.out*”是什么呢？没错，就是刚刚编译出来的可执行文件（ 星号表示该文件为可执行文件）。

```bash
ll
```

![a.out](https://image.ql-isaac.cn/a.out.png)

### 运行

　　有了可执行文件，就可以运行了，输入以下命令执行就能打印出“Hello,World!”了。

```bash
./a.out
```

![打印结果](https://image.ql-isaac.cn/打印结果.png)

### 小结

　　以上就是C学习的起步内容，下面就开始正式的学习，会总是需要用到上面提到的新建并编辑保存、编译和运行的相关命令，还有一个小技巧，可以使用键盘的方向键上和下在历史命令中切换。

## 做点计算

　　范例：做点计算（新建compute.c）

```c
#include <stdio.h>

int main(){
    printf("12+34=%d\n",12+34); //%d为占位符，表示数据打印出来的格式应该是十进制整数的格式
    return 0;
}
```

　　打印结果：

```
12+34=46
```

　　除了做加法，当然还能做其他运算：

| 运算   | 运算符 |
| ------ | ------ |
| 加     | +      |
| 减     | -      |
| 乘     | *      |
| 除     | /      |
| 取余数 | %      |
| 括号   | ()     |

## 变量

### 变量类型

　　C语言是一种强类型的语言，所有的变量都必须有类型。

### 变量定义

　　变量定义的一般形式：

```
<类型名称> <变量名称>;
```

　　范例：定义变量price，存放价格的int型数据，定义变量payment，存放支付金额的int型数据

```c
int price;
int payment;
```

　　或

```c
int price,payment; //可以在一行中定义多个同类型的变量，有逗号分隔
```

### 标识符

　　标识符只能由字母、数字和下划线组成，数字不能出现在第一个字符的位置，标识符分为关键字，预定义标识符和用户自定义标识符，变量名称就属于用户自定义标识符。

### 赋值运算符

　　赋值也是一种运算，运算符为`=`，表示将右边的值复制一份赋给左边的变量，那么，这和数学中的等于号是一样的吗？当然不是，数学中的等于号表示的是相等的关系，C语言也有表示相等关系的运算符，即`==`。

　　范例：使用赋值运算符初始化变量

```
int price=56;
int payment=100;
```

　　或

```
int price;
int payment;
price=56;
payment=100;
```

　　或

```
int price=56,payment=100; 
```

### 用scanf()函数初始化变量

　　范例：定义price和payment并用scanf()函数初始化它们

```c
int price,payment;
printf("请输入该商品价格（元）：");
scanf("%d",&price); //scan是扫描的意思，f同样是format的简写，scanf()函数的功能就是格式化扫描,扫描什么？扫描字符呗，以回车为结束符（不计入输入中）将输入的字符以十进制整数的格式解析，&price的意思就是将解析出来的值复制一份赋给price
printf("请输入支付的金额（元）：");
scanf("%d",&payment); //同上
```

### 变量的使用

　　范例：找零（新建change.c)

```c
#include <stdio.h>

int main(){
    int price;
    int payment;
    printf("请输入该商品价格（元）：");
    scanf("%d",&price); //键盘输入的方式初始化price
    printf("请输入支付的金额（元）：");
    scanf("%d",&payment); //键盘输入的方式初始化payment
    int change=payment-price;
    printf("找零（元）：%d\n",change);
    return 0;
}
```

　　运行结果：

![change.c](https://image.ql-isaac.cn/change.c.gif)

### 没有初始化变量的后果

　　范例：没有初始化payment（修改change.c)

```c
#include <stdio.h>

int main(){
    int price;
    int payment;
    printf("请输入该商品价格（元）：");
    scanf("%d",&price); //键盘输入的方式初始化price
    int change=payment-price;
    printf("找零（元）：%d\n",change);
    return 0;
}
```

　　运行结果：

![没有初始化变量](https://image.ql-isaac.cn/没有初始化变量.gif)

　　什么！找零2亿多？？！！原来，变量在没有初始化，也就是刚一定义时，其实就是有值的，可是这个值只有计算机知道，在发生意想不到的问题之前，我们应该时刻注意变量在定义后一定要初始化。

## 常量

### 定义常量

　　变量定义的一般形式：

```c
const <类型名称> <常量名称>; //const是一个修饰符，是constant（常数）的简写，规定常量名称中的字母都为大写，这是命名规范
```

### 常量和变量的相同点和不同点

　　相同点：常量和变量都需要初始化。

　　不同点：常量在初始化后不能再被修改而变量可以。

### 常量的使用

　　在找零程序中，该商品，比如说一本书，它的价格就是56元，没必要总是输入56，于是我们可以这么写：

　　范例：使用常量（修改change.c)

```c
#include <stdio.h>

int main(){
    const int PRICE=56;
    int payment;
    printf("请输入支付的金额（元）：");
    scanf("%d",&payment); //键盘输入的方式初始化payment
    int change=payment-PRICE;
    printf("找零（元）：%d\n",change);
    return 0;
}
```

　　如果我们尝试去修改PRICE会如何？来试一下：

　　范例：尝试修改PRICE（修改change.c)

```c
#include <stdio.h>

int main(){
    const int PRICE=56;
    int payment;
    printf("请输入该商品价格（元）：");
    scanf("%d",&PRICE); //尝试修改PRICE
    printf("请输入支付的金额（元）：");
    scanf("%d",&payment); //键盘输入的方式初始化payment
    int change=payment-PRICE;
    printf("找零（元）：%d\n",change);
    return 0;
}
```

　　运行结果：

![尝试修改PRICE](https://image.ql-isaac.cn/尝试修改PRICE.gif)

## 浮点型

　　美国人习惯用几英尺几英寸的方式描述自己的身高，如果遇到一个美国人告诉你他的身高为5英尺7英寸，他的身高应该是一米几呢？由于1英尺 = 12英寸 = 0.3048米，所以5英尺7英寸应该为(5+7/12)*0.3048米，即1.7018米。来写个程序：

　　范例：长度换算（新建length_conversion.c)

```c
#include <stdio.h>

int main(){
    printf("请分别输入身高的英尺和英寸，如5,7表示5英尺7英寸:");
    int foot; //英尺
    int inch; //英寸
    scanf("%d,%d",&foot,&inch);
    printf("身高是%f米\n",((foot+inch/12)*0.3048));
    return 0;
}
```

　　运行结果：

![长度换算](https://image.ql-isaac.cn/长度换算.gif)

　　英尺似乎没发挥作用？这是怎么回事？原来，是由于C语言中相同数据类型的变量的计算结果仍然是该类型，inch是int类型，12是整形常量，默认是int类型，那么对于这个值永远都是在0到11范围的inch来说，其与12的除法运算永远都是int类型，永远都会直接舍弃掉小数点后面的数据，永远都为0，所以才会有以上的运行结果。

　　那么，以上程序该如何改进呢？这里，又紧接着引入一个知识点：在C语言中不同数据类型的变量的运算，是先将所有变量统一转化为一种表示范围最大的数据类型。

　　范例：长度换算（改）（修改length_conversion.c)

```c
#include <stdio.h>

int main(){
    printf("请分别输入身高的英尺和英寸，如5,7表示5英尺7英寸:");
    int foot; //英尺
    int inch; //英寸
    scanf("%d,%d",&foot,&inch);
    printf("身高是%f米\n",((foot+inch/12.0)*0.3048)); //12是整形常量，默认是int类型，12.0是浮点型常量，默认是double类型
    return 0;
}
```

　　运行结果：

![长度换算（改）](https://image.ql-isaac.cn/长度换算（改）.gif)

## 表达式

　　一个表达式是一系列运算符和算子的组合，用来计算出一个值。运算符（operator）是指进行运算的动作，比如加法运算符”+“，减法运算符”-“，算子（operand）是指参与运算的值，这个值可能是常数、变量和方法返回值等。

## 参考视频

https://www.bilibili.com/video/av15267247

https://www.bilibili.com/video/BV17s411N78s