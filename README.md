![Linux](https://img.iliy.net/i/2022/10/18/160726.png)

## 你会得到什么

我是一个 Linux 小白，通过这篇文章分享一点基本操作，以及一些杂七杂八的经验。希望能让一个未接触过 Linux 的人，用 2 小时的时间上手 Linux（不包括购买VPS、域名、喝咖啡的时间）

你会得到什么：

+ 学会对 Linux 的基本操作
+ 了解 apt、手动、脚本、docker 的服务安装方式
+ 搭建一个自己的文件列表（网盘）、一个图床、一个内网穿透服务
+ 你觉得 Linux 没那么陌生了，你可以很好的使用它

最重要的是，我希望你能从中得到乐趣  :)

由于假想读者是 “未接触过Linux的人”，我尽可能只提到常用的命令，描述方式 “更好理解” 而不是 “更精确”，除了这一点点东西，还有更丰富多彩的内容等待你探索

<br/>

## 一点儿历史

1965年，麻省理工学院、通用电气、贝尔实验室成立大型机的 Multics计划（“复杂”计划）

1969年，由于进度缓慢、资金短缺，贝尔实验室退出 Multics计划

贝尔实验室有几台 PDP-7 主机闲置，原计划参与者 Ken Thopson 的妻儿恰好回美国西部探亲，他就有了一个月时间，将游戏 ”星际旅行“（Space Travel）移植到 PDP-7 上玩，为了实现这个想法，他用汇编语言写出了一组内核程序、一些内核工具、一个文件系统，这个系统就是 UNIX 的原型 Unics（意为”简单“），这个文件系统有两个重要概念：

+ 所有的程序或系统设备都是文件
+ 不管程序本身还是附属文件，所写的程序只有一个目的，且要有效地完成目标

由于 Unics 非常好用，它在贝尔实验室内部广为流传。

1973年，Ken Thompson 与 Dennis Ritchie 合作，用当时的高级程序语言 B语言改写 Unics，但编译出的内核性能不佳，于是 Dennis Ritchie 将 B语言改写成 C语言，再用 C 语言重新改写 Unics，命名为 Unix。

此时 AT&T 对旗下贝尔实验室的 Unix 采取较开放的态度，Unix 得以和学术界合作，伯克利大学的 Bill Joy 将 Unix 修改成适合自己机器的版本，增加了许多工具软件和编译器，命名为 BSD（Berkeley Software Distribution），这个版本后来衍生出 FreeBSD。

随着 Unix 在学术界和大型企业的广泛应用，AT&T 意识到了 Unix 的商业价值，试图收回版权，措施包括禁止学生获取 Unix 的源代码，这引发了学术界的不满。

1984年，荷兰阿姆斯特丹自由大学计算机教授 Andrew S.Tanenbaum 出于教学需要，完全不参照 Unix源代码，动手写了 Minix系统，但 Minx 出于教育目的，Andrew教授不愿意修改它以满足更高需求。

1984年，Richard Mathew Stallman 发起 GUN，计划建立一个自由的 Unix操作系统，但无人响应。于是他转向写 Unix上运行的开源软件，这让GUN逐渐打开知名度。1985年，他与律师起草了**GPL**（通用公共许可证），并称呼它为 copyleft，GPL相关的几个理念：

+ 版权制度是促进社会进步的手段，版权本身不是自然权利
+ 自由软件是一种自由的权力，并非是价格。自由软件指具有自由度，用户可以自由的执行、复制、再发行、学习、修改与强化自由软件

1991年，芬兰赫尔辛基大学的 Linus Torvalds 不满自己 386计算机上的 Minix，于是动手用 GUN 工具写自己想要的操作系统内核 Linux。Linus 希望得到更多人的建议和反馈来发展这个操作系统，这一理念与 Minix 刚好背道而驰，但得到了极客社区的欢迎。Linus 参考可移植操作系统规范 POSIX 修改 Linux ，使它很容易兼容 Unix 软件，这两个原因让 **Linux内核**很快流行起来。

1993年，美国普渡大学学生 Ian Murdock 发布自己修改的 Linux发行版，以女友的名字 Debra 和自己的名字 Ian 合并起名为 **Debian**，逐渐完善的 Debian社群不带任何商业性质，不依附任何商业公司和机构，坚守自由理念和风格。

1994年，Marc Ewing 成立 Red Hat公司，提供自己创建的 Linux发行版，可免费获取源代码，但对搭建、维护、后续支持等<u>服务收费</u>。这是 GPL 商业行为的良好实践，其开源代码编译出的社区发行版是 **CentOS**，和商业发行版的主要区别是移除了 Red Hat 商标、移除闭源软件。由于 Red Hat 相关教学、商业实践的普及，中国早期 IT基本是从 CentOS 开始接触 Linux的。

2004年，Mark Shuttleworth 在英国成立 Canonical 公司，基于 Debian 和 GNOME桌面环境发布 **Ubuntu**，这一 Linux 发行版以桌面应用为主，强调易用性和国际化，更多地通过商业发展策略推动 Ubuntu发展。

2020年，Red Hat 宣布将停止维护 CentOS，将之转换到 CentOS Stream。红帽旗下有三个主要的 Linux 发行版，先行实验版 Fedora、主要发行版 ReaHat Linux（RHEL）、社区版 CentOS，新的 CentOS Stream 将随 RHEL 同步更新，以使开源社区的反馈可以改进 RHEL 。

<br/>

## 我要选择哪个系统

Linux 有三百多个不同的发行版，推荐从 Debian、Ubuntu、CentOS 之一开始接触，从上面的历史可以看到：

+ Debian  社区驱动
+ Ubuntu  基于 Debian，偏向桌面环境（硬件要求更高），商业化较好
+ CentOS  中文教程最多，但即将停止维护

对于<u>非深入使用的用户，这三个发行版没有显著区别</u>，不同发行版是用一台通用发动机（Linux内核）加入不同工具组装出的跑车、小轿车、越野车，它们在启动、跑起来、拐弯的操作上几乎没有差别。

我建议从 Debian 开始，以下内容均基于 Debian 11。

<br/>

## 购买一个 VPS

VPS（Virtual Private Server，虚拟专用服务器），是在互联网上的一个台专用服务器，世界上有很多 VPS 商家，你可以从 [hostloc](https://hostloc.com/forum-45-1.html)、[let](https://lowendtalk.com/)、[v2ex](https://v2ex.com/) 等论坛的推荐，或 Google 搜索结果里找一个你喜欢的。

我的建议是从1台大约 $2/月的机器开始，月付，选择国外服务商。$2/月大概可以买到 1核- 0.5~1G内存- 10~20G硬盘的VPS：

1. 购买 VPS，选择系统 Debian 11
2. 检查你的 VPS IP 在中国是否可访问：[vps234](https://www.vps234.com/ipchecker/)

你需要：

1. 外币信用卡 / 可用于支付的 Paypal
1. 可以访问谷歌服务的网络环境

如果你没有支付环境或网络环境，可以看看阿里云、腾讯云；如果你有谷歌账户，可以从 3个月 $300免费额度的  [Google Cloud](https://cloud.google.com/) 开始，国外学生可以尝试 $100免费额度的 [微软 Azure学生试用](https://azure.microsoft.com/en-us/free/students/) ，但它们会增加困难，大厂面向企业IT的复杂设置对新手并不友好。

<br/>

## 基础操作

### 1. 连接 VPS

购买机器后，你会得到 IP、用户名、ssh 登录密码，假设分别是`10.20.30.166`、`root`、`2OFSND929`，现在你要用 ssh客户端连接你的 VPS。

如果你本的地设备是 Windows 操作系统，建议先用 PowerShell（ 或 cmd）把以下内容尝试完，再去挑选你喜欢的终端工具，如果是其它系统，可以在网络上搜索自带的 ssh工具。

#### **1.1 启用 OpenSSH**

在 PowerShell 中检查系统是否已经启用了 OpenSSH，输入以下内容并回车：

```
ssh
```

（ 这是一个输入，通常会用 $ssh 表示输入 ssh，以区别输出内容，我在上面的表示方式并不好，但方便你复制、粘贴）

如果已经启用了 OpenSSH，PowerShell 会输出：

```
#=> usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface]
           [-b bind_address] [-c cipher_spec] [-D [bind_address:]port]
           [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11]
           [-i identity_file] [-J [user@]host[:port]] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] destination [command]
```

（你的 PowerShell  输出结果没有 #=>，这是我为了表示这是输出内容增加的，`#`表示后续内容是注释。如果命令有多行，表示逐行运行）

如果没有启用 OpenSSH，在 win10 中搜索`可选功能`→`添加功能`→ 找到 OpenSSH → 安装 → PowerShell  输入`ssh`检查

**在 cmd 中复制命令、粘贴命令的问题**

通常，在终端中选中等于复制，鼠标右键单击等于粘贴，在 Powershell 或 cmd 中并不一定如此，鼠标右键单击能够粘贴，但你可能要结合 Ctrl+C 复制

<br/>

#### **1.2 连接 VPS**

连接VPS（ 10.20.30.166 换成你的 ip）

```
ssh root@10.20.30.166 -p22
```

连接成功会显示：

```
#=>root@10.20.30.166's password: 
```

输入密码并回车，输入的密码不会显示，这是一个安全措施

连接成功会显示：

```
[root@主机名 ~]$	             # 可能是 root@主机名:~# 等形式
```

你登陆成功了！

<br/>

### **3. 简单的看看它**

你可以看看它是什么系统，`cat`命令可以在终端上输出某个文件的内容

```
cat /etc/issue
```

看看 Linux内核版本

```
uname -a
```

看看本机IP地址

```
ip addr
```

看看硬盘的大小、已经用了多少（这个命令输出结果可能要稍微等一下）

```
df -h
```

VPS商家给的登录用户名可能不是 root，你可以切换到它

```
sudo -i
```

修改 root 用户的密码（输入的密码不会显示）

```
passwd
```

<br/>

### **4. 在目录里逛一逛**

</br>

**pwd 命令**

`[root@主机名 ~]$`的`~`表示你的当前位置，`~`是家目录的简写，你可以用`pwd`（print working directory）显示绝对路径：

```
pwd
```

输出

```
#=>/root
```

原来我们在`/root`这个位置，即`~`等于`/root`

💡 小提示：我们现在是以 root 身份登录的，如果是 user1@主机名，`~`等于`/home/user1`，非 root用户的家目录在`/home`下面

</br>

**ls 命令**

我可以用`ls`命令看看目录下有哪些文件、权限、属于哪些用户，我们先看看当前目录：

```
ls -lh
```

输出

```
#=>total 0	#没有文件
```

看看根目录`/`呢？

```
ls -lh /
```

输出

```
#=>
lrwxrwxrwx   1 root root    7 Oct 20 17:58 bin -> usr/bin
drwxr-xr-x   4 root root 4.0K Sep 20 18:03 boot             
drwxr-xr-x  14 root root 2.8K Oct 19 08:42 dev
drwxr-xr-x  68 root root 4.0K Oct 19 10:47 etc              # 配置文件通常在 /etc
drwxr-xr-x   3 root root 4.0K Oct 19 08:55 home             # 非root用户的家目录在 /home
lrwxrwxrwx   1 root root    7 Oct 20 17:58 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Oct 20 17:58 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Oct 20 17:58 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Oct 20 17:58 libx32 -> usr/libx32
drwx------   2 root root  16K Oct 20 17:58 lost+found
drwxr-xr-x   2 root root 4.0K Oct 20 17:58 media
drwxr-xr-x   2 root root 4.0K Oct 20 17:58 mnt
drwxr-xr-x   2 root root 4.0K Oct 20 17:58 opt
dr-xr-xr-x 134 root root    0 Oct 19 08:42 proc
drwx------   3 root root 4.0K Oct 19 09:24 root            # root用户的家目录 /root
drwxr-xr-x  19 root root  580 Oct 19 10:24 run
lrwxrwxrwx   1 root root    8 Oct 20 17:58 sbin -> usr/sbin
drwxr-xr-x   2 root root 4.0K Oct 20 17:58 srv
dr-xr-xr-x  13 root root    0 Oct 19 08:42 sys
drwxrwxrwt  11 root root 4.0K Oct 19 10:42 tmp
drwxr-xr-x  14 root root 4.0K Oct 20 17:58 usr             # 用户文件夹 /usr
drwxr-xr-x  11 root root 4.0K Oct 20 17:58 var             # 会不断扩充的文件习惯放在 /var
#从左至右是：
文件类型和权限 硬链接数 用户 用户组 大小 修改时间 目录名或文件名
```

我们通常会接触`etc`、`var`这两个目录。

以`etc`目录为例，`drwxr-xr-x`表示文件类型和权限，首位的`d`表示这是一个目录（directory），如果是`-`表示这是一个文件，`l`表示这是一个链接；后续每3位一组表示权限，`r`可读、`w`可写、`x`可执行，`rwxr-xr-x`表示所属用户`rwx`（可读可写可执行），用户组`r-x`（可读，不可写，可执行），其他成员`r-x`（可读，不可写，可执行）

`68 root root 4.0K Oct 19 10:47 etc`表示有`68`个硬链接，用户是`root`，用户组是`root`，大小是`4.0K`，最后修改时间是本年`Oct 19 10:47`，目录名称是`etc`

</br>

**cd 命令**

我们已经知道了`/`下有很多目录（d），现在我们想从家目录`/root`（`~`）切换到`/`目录，用`cd 路径`（change directory）切换目录

绝对路径：由根目录`/`写起，`/目录/目录`的形式

相对路径：`.`表示当前位置，`..`表示相对于当前位置的上级位置（`./`当前目录 、`../`上级目录）

切换到根目录`/`看看：

```
cd /
```

可以看到，前面变成了`[root@主机名 /]$`，即你处于根目录`/`，这里也可以用`cd ..`从`/root`切换到上级位置`/`

可以`ls -lh`看看有哪些文件（等义于`ls -lh ./`不指定位置默认为当前位置）

现在我想到 var 目录去看看：

```
cd var
```

等义于`cd ./var`（不指定位置默认为当前位置）

现在回到上级目录

```
cd ..
```

我们已经学会了切换目录，你可以多试试，用`pwd`或`ls -lh`到处看看

我已经学会了在不同目录中切换，正如我在桌面系统里进入不同文件夹，我在桌面系统还会做些什么？新建文件或文件夹、复制、剪切、粘贴、重命名

<br/>

**mkdir**

在指定位置新建一个空白目录，比如我在 /etc 新建目录 alist

```
mkdir /etc/alist
```

省略路径是在当前目录下新建目录 alist 么？试试看，用 ls -lh 看看结果

新建层级目录，例如在根目录下新建目录 sync 并在 sync 下新建目录 qb

```
mkdir -p /sync/qb
```

如果写成`mkdir -p sync/qb`呢？

路径开头的`/`表示从根目录开始，不带`/`等义于当前位置，即上句等义于`mkdir -p ./sync/qb`，试试看

<br/>

**touch**

在当前目录新建一个空白文件`a`

```
touch a
```

如果是在指定目录，例如在 /sync 目录新建空白文件`filter.txt`

```
touch /sync/filter.txt
```

<br/>

**cp**

复制，复制并保留原文件属性（时间、创建者）和权限

```
cp -a <源文件或目录> <目的文件或目录>
```

例如将刚刚新建的 /sync/filter.txt 复制到 root 目录

```
cp -a /sync/filter.txt /root/
```

💡 上面命令中 /root/ 等义于 /root，但后面带`/`更清晰的表示 root 是一个目录，是要把前面的对象移动到这个目录 “里面”。

Linux 中有一个通配符`*`匹配所有文件，如果你要将 /sync 中所有文件复制到 /root

```
cp -a /sync/* /root/
```

<br/>

**mv**

`mv`的第二个参数如果是已存在的目录，执行移动操作（相当于剪切并粘贴到），第二个参数如果是文件，执行重命名操作：

```
mv <源文件或目录> <目的文件或目录>
```

例如把 /sync/qb 目录重命名为 /sync/qb1

```
mv /sync/qb/ /sync/qb1/
```

如果 /sync/qb1 目录存在，则会将 /sync/qb 目录移入 /sync/qb1；如果 /sync/qb1 目录不存在，则将 /sync/qb 目录重命名为 /sync/qb1

💡 都不带后面的 / ，或 qb、qb1/，结果是一样的，但对操作者来说更明确这是在对目录操作

💡 在 Linux中，所有的程序或系统设备都是文件，对文件或文件夹的操作是一样的

<br/>

**rm**

删除当前目录下的文件 a

```
rm a
```

删除当前目录下的目录 a ，需要加上`-r`（recursive 递归，同时将目录下的全部目录和文件删除）

```
rm -r a
```

如果被删除的目录下有`r--`权限（只读）的文件会逐一询问确认，因此删除目录时更常用强制删除

```
rm -rf a
```

删除指定目录下某个文件或文件夹，加上路径即可

你可以新建文件 a、目录 a，在目录中新建文件，然后逐一测试

<br/>

**find**

在指定目录下查找文件

```
find <路径> -name 文件或目录名
```

例如在 /var 目录找名为 logs 的对象

```
find /var -name logs
```

<br/>

现在你已经学会了进入不同文件夹，新建、剪切、复制、重命名、删除文件或文件夹，查找某个文件，你几乎掌握了在桌面系统上会的所有操作！**你已经如同掌握你用过的桌面系统同等程度的精熟 Linux 了！**

还差点什么？安装、卸载软件？

<br/>

## screen

我用 screen 来介绍软件源里有软件包的安装，不同 Linux发行版提供了各自的软件源，它类似一个不断更新的文件清单，列出了所有软件包管理器中有的软件（想象一下 app商店），debian 默认的软件包管理器是 apt 命令。

**apt 命令**

在安装前，我们习惯更新一下这个清单，用到两个命令：

```
apt update
```

然后

```
apt upgrade
```

更新可能特别慢，会提示按 Y 或 y 确认更新，区分大小写

💡 你可以`Ctrl+C`结束一个正在运行的进程，比如特别慢的更新，安装好 screen 再运行它，这正是 screen 的用途 —— 在你看不到的地方执行进程

💡不推荐的做法：关闭终端（已经登陆的当前窗口，也叫会话或前台）来强制退出，在你屏幕上显示进度的前台进程，会在关闭终端后终止，screen 后台窗口中运行的进程不会终止

安装软件的命令

```
apt install <软件包名>	
```

删除软件的命令（保留配置文件）

```
apt remove <软件包名>
```

移除软件并删除配置文件

```
apt purge <软件包名>
```

查找软件

```
apt search <软件包名>
```

</br>

**安装 screen**

screen 用于创建多个终端窗口，可以保持会话退出（命令继续运行），例如你在运行一个命令，需要它在关闭终端窗口后继续运行，我们来安装 screen（部分系统会提示已经安装了 screen）

```
apt install screen -y
```

后面加上`-y`默认自动同意安装过程中所有的 [y/n] （包括 Y）

</br>

**使用**

创建一个名称为`rclone`的会话并进入

```
screen -S rclone
```

退出并关闭会话

	exit

保持会话退出：快捷键`Ctrl+A+D`

列出在运行的会话，会输出 id. 名称

	screen -ls

进入其中某个会话（用id或名称）

	screen -r screen_id

提示 Attached 无法进入，强制连接，踢掉原来的

	screen -D -r screen_id

提示 Attached 无法进入，强制关闭会话

	screen -S session_name -X quit

我们已经学会了安装 apt软件包管理器里有的软件，并且你知道可以用`apt search`去找一个软件在不在里面

</br>

## alist 

如果一个软件不在软件源里呢？

我用 alist 来举例这类安装，这是一个文件列表程序，可以把本地、网盘的文件列在网页上，供在线播放、分享下载，支持本地文件、GoogleDrive、Onedrive、阿里云、百度网盘等，支持 WebDav

**1. 一键脚本**

像我这样的小白会经常用到一键脚本，即开发者提供一条 Ctrl + C、Ctrl + V、Enter 即可完成的命令，可能需要在安装过程中选择 y 或 n

```
curl -fsSL "https://alist.nn.ci/v3.sh" | bash -s install
```

这就完了，打开 http://10.20.30.166:5244  可以看到登录页面

其他内容详见 [alist官方文档](https://alist.nn.ci/zh/guide/install/script.html)，你可以执行官方提供的一键卸载，然后按照 2.手动安装来重新安装 alist，也可以试着去用已经安装好的 alist，只是看看后面的内容。

**2. 手动安装**

如历史部分所说，<u>所有的程序或系统设备都是文件</u>，手动安装可以理解为就是把文件放进Linux，修改好配置，然后运行

在`/etc`新建一个目录，我们在上面已经学会了`mkdir`

```
mkdir /etc/alist
```

 进入它，我们用什么命令？

```
cd /etc/alist
```

下载用`wget`

```
wget https://github.com/alist-org/alist/releases/download/v3.2.1/alist-linux-amd64.tar.gz
```

你可以用`ls -lh`看一下我们下载的文件（以 .tar.gz为后缀）

然后是压缩和解压的命令`tar`

```
tar -zxvf alist-linux-amd64.tar.gz
```

如果没有带路径，默认解压到当前所在目录，有兴趣可以去搜索一下 wget 到特定目录，和 tar 解压到特定目录的命令

授予程序执行权限

```
chmod +x alist
```

运行程序

```
./alist server
```

这就结束了，在 Linux中运行一个文件只需要打开它，./alist，它类似于在 windows里双击 alist.exe

然后我们获取默认的帐号信息

```
./alist admin
```

接下来你可以登录这个自建的服务，参照官方文档添加不同的网盘挂载

大部分 Debian 软件的安装、使用和此相似，可能会要你打开一些配置文件进行修改，如果有问题，通常是缺少某些文件、配置不对，或权限问题。在 Linux 中修改文件可以用到 nano、vi 等命令，但比较推荐 vim

<br/>

## vim

这是一个好用的文本编辑器，系统可能已经装好了 vim，如果没有怎么办？

```
apt install vim -y
```

（如果你上次执行`apt update`、`apt upgrade`在很久以前，记得先更新一下）

我们在当前目录新建一个空白文件aaa，记得怎么操作么？

```
touch aaa
```

我们现在可以用 vim 打开它

```
vim aaa
```

你可以看到一个新界面，类似：

```
~
~
~
~
~
"aaa" 0L, 0B                                             0,0-1         All 
```

下脚标识了文件名、行数、大小等信息，敲敲键盘看看？

可能有输入内容，左下角变成`-- INSERT --`，或者你可以点击`i`键进入 Insert 模式（插入模式），这个状态可以写新东西，用方向键在已经输入的内容上切换位置。

怎么保存呢？按键盘左上角的`ESC`键退出输入模式，然后输入`:`进入命令模式，输入`wq`确认保存文件，并退出 vim

常用的保存和退出的命令模式

+ `:w` 保存文件
+ `:wq` 保存文件，退出 vim
+ `:q` 不保存文件，退出 vim
+ `:q!` 不保存文件，强制退出 vim
+ `:wq!` 强制保存并退出 vim

在文本中查找内容，ESC 键退出插入模式后输入`/`进入查找模式，输入内容，Enter 进行查找，`N`键切换到下一个查找结果，`Shift+N`切换到上一个查找结果，如果查找到哪一行不清晰，可以按方向键看光标。

vim 还有很多设置，`:set nu`显示行号、正常模式，编辑时跳转到外部等等，常用的大概就是上面的内容。

<br/>

## Nginx

我们在前面已经安装了 alist，访问它的方式是打开 http://ip:5244，但我看别人家孩子的服务，是 https://iliy.net 这样的呀？

我们叫 <u>iliy.net</u>`根域名`，像 www.iliy.net、<u>blog.iliy.net</u> 是子域名，好看，好记，而且通过域名这一层抽象，我们可以随意更换对应的服务器、IP地址，只要再把域名指向更换后的服务器IP。

我推荐刚接触 Linux 就买一个域名，快速从依赖 IP:端口 转到享受域名。

<br/>

### 1. 购买一个域名

这个世界上的域名服务商可能和 VPS商家一样多，我推荐 [GoogleDomains](https://domains.google/) 和 [Namesilio](https://www.namesilo.com/)

+ GoogleDomains 可能是最便宜的，换区土耳其 6-9位数字.xyz 折约 ￥4/年，其他域名可能是其他商家的一半（不定时调价），<u>续费同价</u>，需信用卡
+ Namesilio 支持支付宝，6-9位数字.xyz 折约 ￥7/年（$0.99），需要注意是否续费同价（Renewal 价格）

其他商家我只用过 Namecheap，买了一个域名被它没收了，因为购买域名需要提交海外个人信息，我们通常是乱填的，或者 [fakena](https://fakena.me/fake-name/) 这类网站生成的信息，Namecheap 以此为由吃了我的钱和域名。Google 和 Namesilio 暂时未严格管理。

一个域名最多续费 9年，可以在不同域名服务商之间转移域名，但转出需要离购买/迁入至少 60天（不同服务商可能不同），且转入至少再续费1年。

以下以 Google Domains 为例：

<br/>

**1. 登录谷歌域名，改区到土耳其**

在 [Google Domains](https://domains.google.com/registrar/search) 左侧点击显示的当前地区，在弹出窗口改为 ”土耳其“，确认就改区了。这一改区不影响其他 Google服务的地区

**2. 挑一个域名加入购物车**

推荐 6-9位数字.xyz，这类域名在中文被叫做 "小姨子"。

我不建议一开始就去找 .com、.net 等后缀的域名，思考一个中意域名需要大量时间，且价格较贵，你可以从一个比较随意的 .xyz 开始，你也总会需要一个备用域名用来干点别的 :)

挑选域名界面显示 75TRY/年，加入购物车变为 12TRY/年（约￥4），你可以按自己需要多续几年。

![谷歌域名2](https://img.iliy.net/i/2022/10/22/211711.jpg)

**3. 付款结算**

将域名移交给当前账户可能要一段时间

<br/>

### 2. 使用它（DNS设置）

DNS（Domain Name System）记录域名和IP的相互映射，现在我们来设置 域名 --> IP 

点击 Google Domains 左侧「我的域名」可以看到你刚刚购买的域名，点击它进入设置界面。点击左侧「DNS」，在新界面选择「自定义记录」→「管理自定义记录」

增加一条记录，主机名 alist，类型 A，TTL 按需设置（600是10分钟更新一次），数据是你的服务器IP地址（假设为 10.20.30.166）

![谷歌域名3](https://img.iliy.net/i/2022/10/22/213017.jpg)

**常用DNS记录类型：**

+ A：域名-->IPv4地址
+ AAAA：域名-->IPv6地址
+ CNAME：域名-->另一域名
+ MX：为邮件域名设置邮箱服务器
+ TXT：对域名进行标识和说明，可填写任意文本记录
+ NS：指定域名的权威DNS服务器

保存，过 10分钟（通常不需要这么久），整个互联网都知道当访问 "http://alist.你的域名 时，它指向 10.20.30.166:80

但我安装 alist 的端口不是 5244 么？

这就需要 Nginx了，由它将 IP-->真实服务器端口



### **3. 安装 Nginx**

怎么安装一个软件？

```
apt install nginx 
```

验证安装

```
curl -I 127.0.0.1
```

也可以

```
nginx -v
```

（你可以`screen -v`试试，这是查看软件版本的通用方式）

nginx 的配置文件通常是 /etc/nginx/nginx.conf，你可以在 /etc/nginx/conf.d 新增 .conf 结尾的文件，这样更方便修改

比如我们新增 alist.conf，怎么新增一个文件？

```
touch /etc/nginx/conf.d/alist.conf
```

现在编辑配置，怎么编辑一个文件？

```
vim /etc/nginx/conf.d/alist.conf
```

以下参考，请将 alist.030040.xyz 替换成你的子域名，5244 替换成你用的端口

```
server
    {
        listen 80;
        server_name alist.030040.xyz ;
        location / {
            proxy_pass http://127.0.0.1:5244;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded_For $proxy_add_x_forwarded_for;
        }
        access_log off; # 取消访问日志记录
    }
```

重要的是`{`、`}`和`;`，缩进的空格可以随意，但建议用 Tab 或 4个空格为一个缩进，方便查看和修改

怎么修改？`i`键进入 Insert模式，修改好怎么保存？`ESC`键退出 Insert模式，`:`进入命令模式，`wq`保存退出，如果改错了可以`q!`强制退出再 vim 打开。

修改完成后让 Nginx 重新加载配置

```
nginx -s reload
```

如果你写的配置有问题，比如缺了`{`、`}`、`;`，Nginx 会报错，修改后再重新运行上面的命令

完成后再访问 https://alist.030040.xyz 看看？（换成你的子域名）

我真的棒棒的！我的服务和 Google 这种大厂看起来都差不多了！但，好像 <u>https 缺个 s，我隐隐约约知道，https 比 http 更安全</u> ！

我会在后续的 ssl 证书中告诉你怎么申请和使用 ssl 证书，但你也许愿意先了解一下 docker？

</br>

**nginx 常用命令**

强制停止

```
nginx -s stop
```

安全退出

```
nginx -s quit
```

**netstat 命令**

监控TCP/IP网络的工具，常用

```
netstat -ntlp
```

列出被使用的 tcp 端口，如 Nginx 通常是 0.0.0.0:80，如果要查看 udp 端口改成 

```
netstat -nulp
```

如果提示未安装，怎么安装一个软件？如果你不知道一个软件包的名称，可以去搜索。

**常用的 Local Address：**

+ 127.0.0.1   本机地址，监听来自本地的 IPv4 请求

+ 0.0.0.0       本机地址，监听所有来源的 IPv4 请求

+ ::1               IPv6 的 127.0.0.1

+ localhost    通常被指向 127.0.0.1 和 ::1
+ ::                 IPv6 的 0.0.0.0

<br/>

## Docker

你可以把 Docker 看成 apt软件包管理、一键脚本、手动安装之外的一种安装服务的方式。

Docker 的优点是服务之间隔离，可以把复杂设置简单化，非常方便。已经安装好的服务可以轻易备份、迁移到其他服务器上。

<br/>

### 安装 docker engine

所有服务的安装等过程，都建议看服务的官方文档，Docker 的  [官方文档](https://docs.docker.com/engine/install/debian/) 

我仍然把 debian部分摘抄下来，但只是为了初次接触 Linux 的朋友便于对照查看官方文档

**1. 卸载安装过的版本**

```
apt-get remove docker docker-engine docker.io containerd runc
```

**2. 安装 yum-utils、docker源**

更新

```
apt-get update
```

（apt-get 通常等于 apt）

安装

```
apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

（注：整个复制粘贴，行末的空格和`\`表示换行，`\`后不能有空格，下一行前面有多少空格不影响）

添加 GPG key

```
mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

（注：官方默认非 root 用户安装，因此用 sudo）

设置官方源

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
```

（整个复制粘贴，3行是有两个换行）

**3. 安装 Docker engine**

更新

```
apt-get update
```

安装

```
apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

安装结束后运行 docker 镜像 hello-wordl测试

```
docker run hello-world
```

会提示镜像不存在，然后从 dockerhub 拉取镜像安装

安装完成后提示

```
Hello from Docker!
...	#后续省略
```

<br/>

### docker cli 安装 alist

安装好 docker 后，我们直接通过一个实例了解 docker 安装，还是 alist

```
docker run -d \
--restart=always \
-v /etc/alist:/opt/alist/data \
-v /sync:/sync1 \
-p 52444:5244 \
--name="alist" xhofe/alist:latest
```

查看管理员信息

```
docker exec -it alist ./alist admin
```

可以打开 http://ip:52444 使用你创建的 alist服务，你也可以为它再设置一个域名

安装命令中主要用到的参数：

+ -d 表示后台方式运行
+ --restart=always 自动重启容器
+ -v 文件夹的映射，<u>本机</u>的 /etc/alist 目录映射到<u>容器</u>的 /opt/alist/data，本机的 /sync 映射到容器的 /sync
+ -p 端口映射，本机的 52444 映射到容器的 5244
+ --name 容器命名为 alist
+ -e 环境设置，alist的安装没用到

注：

（1）如果不设置 -p 主机端口:容器端口，而是用`--net=host`，容器不虚拟出网卡，直接用 VPS的IP和端口

（2）alist 现在只能访问主机的 /etc/alist目录和 /sync 目录，且你打开 alist 设置访问本地 /sync1目录，会发现 /sync1里的文件是你在主机上看到的 /sync 目录里的

<br/>

**简述安装过程**

docker 安装服务（run）时，先在本地找<u>镜像</u>文件，找不到再从 dockerhub 拉取（pull）名称`xhofe/alist`，版本标签`latest`的镜像文件，然后通过镜像文件创建一个名为`alist`的<u>容器</u>，设置了相应的自动重启、目录映射、端口映射。





<br/>

我们已经学会了用 docker 安装服务，现在我们来了解一下** docker 常用的管理命令**

docker 的 images 和容器







<br/>docker 常用命令

<br/>

### docker cli 安装 简单图床



### docker cli 安装 nginx-proxy-manager



### docker cli 安装 音乐播放服务navidrome



### docker cli 安装视频聚合服务 Plex



<br/>

## WinSCP

<br/>

## ssl 证书

<br/>



## 安装 serverstatus 探针

探针是一个合格MJJ（hostloc论坛用户）必备的：）

探针可以简单理解为服务器监控，让你可以打开一个网页看到服务器的 CPU、内存、硬盘使用率、流量统计等信息。

[Githube](https://github.com/cokemine/ServerStatus-Hotaru)

一键脚本

```
wget https://raw.githubusercontent.com/cokemine/ServerStatus-Hotaru/master/status.sh
```

服务端安装

```
bash status.sh s
```

客户端安装（有问题可以手动安装 [Go版本](https://github.com/cokemine/ServerStatus-goclient)）

```
bash status.sh c
```



## 安装 web-notepad

网络便签，打开 https://note.030040.xyz 自动生成 https://note.030040.xyz/随机后缀，或者打开指定后缀生成指定后缀，随输入自动保存，记住这个网址可以在任意设备上打开继续编辑

有 docker cli 版本，但使用 Apache，整个镜像约 200MB，建议手动安装，10KB，需要 php

类似的项目也挺多的，还有增加了加密等功能的项目，但这个够用了

[Github](https://github.com/pereorga/minimalist-web-notepad)

没有提供release，点击 Github 项目 Code 按钮下拉的 Download ZIP，上传到 VPS 解压，或者直接用我上传的

切换到 /var/www/html目录

```
cd /var/www/html
```

下载

```
wget https://files.catbox.moe/74kqpr.zip
```

解压缩

```
unzip 74kqpr.zip
```

文件夹重命名，比如 notepad

```
mv minimalist-web-notepad-master notepad
```

在 Nginx 配置文件中增加：  

（  <>的内容根据你的替换，如果你的 php不是 7.4，位置和我不同，也请替换

下面 URL重写是项目位于 html子目录的写法，即按我上面的放法，如果是放在根目录，请按项目文档修改 URL重写）

```
server {
        listen 80;
        listen [::]:80;
        server_name <你的域名>;
        rewrite ^(.*) https://$server_name$1 permanent;
        access_log off;
}
server {
        listen 443;
        listen [::]:443;
        server_name <你的域名>;
        ssl_certificate /etc/letsencrypt/live/<你的位置>/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/<你的位置>/privkey.pem;
        root /var/www/html/<notepad>;
        index index.php index.html index.htm index.nginx-debian.html;
        location / {
            rewrite ^/([a-zA-Z0-9_-]+)$ /index.php?note=$1;
            #try_files $uri /notes/index.php?note=$1;
        }
        location ~ .*\.php(\/.*)*$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include fastcgi_params;
            fastcgi_intercept_errors  on;
         }
         access_log off;
}
```

不能保存通常是权限问题，修改`_tmp`目录权限

```
_/var/www/html/notepad/_tmp
```





## 安装 qbittorrent

一种方式是用 Docker



另一种方式是用别人已经编译好的版本

创建默认配置目录

	mkdir -p ~/.config/qBittorrent


创建配置文件

	touch ~/.config/qBittorrent/qBittorrent.conf

编辑配置文件

	vim ~/.config/qBittorrent/qBittorrent.conf

添加下面的内容，Web UI 端口可以自行定义

```
[LegalNotice]
Accepted=true

[Preferences]
WebUI\Port=58080
General\Locale=zh
```

然后下载别人编译好的二进制文件安装

```
mkdir -p ~/bin && source ~/.profile
wget -qO ~/bin/qbittorrent-nox https://github.com/userdocs/qbittorrent-nox-static/releases/download/release-4.3.3_v1.2.12/amd64-glibc-qbittorrent-nox
chmod 700 ~/bin/qbittorrent-nox
```

以上命令中是 4.3.3.版本，最新glibc版请自行替换：[qbittorrent-nox-static](https://github.com/userdocs/qbittorrent-nox-static/releases/)

运行（后天运行或者新开一个 screen会话）

```
~/bin/qbittorrent-nox
```



## 安装 frps



## 安装 Wordpress



## 更多

[SFTPGo](https://github.com/drakkan/sftpgo)	一个支持自定义 HTTP/S，FTP/S 和 WebDAV 的 SFTP 服务



## 关于宝塔

<u>这是一个简单好用的中文 Linux 运维面板，但它并不适合新手，这篇教程也不会使用宝塔</u>。它更适合 Linux 老手在明白问题在哪里的前提下，方便的解决问题，备份、维护网站。新手可以用宝塔快速搭建些服务，但不会熟悉 Linux，用宝塔的新手永远是新手，看基于宝塔教程的新手也通常没办法弄明白，自己的服务出问题是什么原因 —— 你要熟悉的是 Linux，不是宝塔。





## 扩展阅读   ------------此部分准备划分新文章

<img src="https://img.iliy.net/i/2022/10/23/163201.png" alt="小白Linux扩展阅读" style="zoom: 33%;" />



下述内容是更丰富但不必要的内容，仅简要提一下，可以通过网络更深入了解

</br>

### 我可以选择哪些 SSH客户端

Windows操作系统上 上 PuTTY 是一个最小工具，Windows Store 由微软官方提供的 windows Terminal 挺不错的，很多人喜欢多平台支持的 Termius，Termius 和 FinalShell、Xshell 一样，基础功能免费。

</br>

### Linux 命令中空格数量有影响吗

命令中的多个空格被视为一个空格

</br>

### 后台运行

`&`放在命令后表示设置此进程为后台进程，关闭终端窗口不影响后台进程运行

```

```

</br>

### 管道符`|`

`|`将两个命令隔开，管道符左边命令的正确输出会作为管道符右边命令的输入

</br>

### 多命令执行符`;`、`&&`、`||`和执行顺序

shell 在执行命令的时候会返回一个返回值，保存在 shell变量 $? 中，$?\=\=0 表示执行成功，$?==[1-255] 表示执行失败

```
多命令执行符              格式                        作用
     ;               命令1 ; 命令2             多个命令由左至右顺序执行，命令之间无任何逻辑关系
    &&               命令1 && 命令2            逻辑与：当命令1返回真（执行成功），命令2才会执行，否则命令2不执行
    ||               命令1 || 命令2            逻辑或：当命令1返回假（执行失败），命令2才会执行，否则命令2不执行
```

</br>

### 文件权限

rwx 421，

chmod（change mode）



赋予可执行权限

```
chmod +x <对象>
```

去掉可执行权限

```
chmod -x <对象>
```



chown （change owner），

```
chown -R www-data:www-data-group /var/www/html
```



### 开机自启和进程守护

Systemd 唤醒并维护各个程序的正常运行，

将`frps.service`放到`/etc/systemd/system/`文件夹中，使用以下命令

```
systemctl enable frps.service
systemctl start frps.service
systemctl status frps.service
systemctl restart frps.service
```

systemctl是systemd在系统中的程序名字，enable是指让这个程序能够开机自启，start为让程序现就运行，status是查看这个程序现在的状态，restart是重启程序。

<br/>

### man 帮助命令

每个命令都有更丰富的功能，你可以用帮助命令`man`来了解，比如`ls`

```
man ls
```

会输出（部分省略）：

```
#=>
NAME
       ls - list directory contents    # ls 的英文全称

SYNOPSIS  # 用法
       ls [OPTION]... [FILE]...     # ls [选项] [目录]

DESCRIPTION 详细说明
       List information about the FILEs (the current directory by default).  Sort entries alphabet‐
       ically if none of -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all    # -a 显示所有文件（. 开头的在没有这个参数时忽略，如 .bashrc）
              do not ignore entries starting with .

       -A, --almost-all  # 同 -a
              do not list implied . and ..  # 但不列出党前目录 . 和父目录 .. 

       -h, --human-readable    # 以人类容易理解的格式列出文件大小
              with -l and -s, print sizes like 1K 234M 2G etc.

       -l     use a long listing format    # 列出文件权限、所有者、文件大小等详细信息
```

你可以用键盘上的`方向键`移动阅读，按`q`离开帮助页面

Linux 的常用语法基本上是类似的：

```
command [option]...[argument]... 
# 命令...[选项]...[对象]
```

**具体说明:**

1、`command`： 表示命令的名称，如 ls

2、`option`：定义命令的执行特性，可以有长短两种选项：

- 长选项：用`--`引导，后面跟完整的单词，如 --help
- 短选项：用`-`引导，后面跟单个的字符， 如 -a

（1）多个短选项可以组合使用，例如： -l -h -a == -lha，但是长选项不能组合使用，如 --help后面就不能再跟另外一个单词。

（2）option 也可以有自己的参数，注意：选项与选项之间，选项与参数之间，参数与参数之间必须有空格。

3、`argument`：描述命令作用的对象，如上述示例`man ls`，ls 就是 man 命令作用的对象。

**命令格式中的符号含义**

在linux中，命令的选项和参数所使用的符号也有相应的含义：

+ `[]`：表示方框里的内容是可选的

+ `<>`：表示尖括号里面的内容必须提供，在选项内部必须用用`{ }`，在`{}`中有默认值用`()`

+ `a|b`：`|`分隔表示多选一的互斥参数

+ `...`：前面的内容可重复出现多次

**举例说明**

例1、`[ --atime-preserve ]`，表示一个可选选项

例2、`[ -B, --read-full-records ]`，表示<u>一个</u>可选选项，简写为-B，完整写法是--read-full-records，简写和完整写法等义。一般带`-`开头的选项都是简写，`--`开头的命令都是完整写法，简写和完整写法用`, `分隔。

例3、`[ -b, --blocking-factor N ]`，表示一个可选选项，简写为-b N，完整写法是--blocking-factor N，N代表这个参数需要一个值，用空格``和`-`或`--`开头的内容分隔，在详细描述中可以看到要求。大部分命令的选项相当于控制开关，是没有参数的。

例5、`[ -z, --gzip, --gunzip, --ungzip ]`，表示一个可选选项，它的写法有多种，除了-z之外，其他的都是它的完整写法。

例6、`[ -[0-7][lmh] ]`，表示嵌套的可选选项，0-7表示取值从0到7取一个。

在描述命令行参数的时候，一般采用的格式如下

```
命令 <必选参数1|必选参数2> [-option {必选参数1|必选参数2|必选参数3}] [可选参数…] {(默认参数)|参数|参数}
```

</br>

### [-] 和 [--] 的区别

Unix 从贝尔实验室的 AT&T Unix 系统继承下来的风格，`-`跟一个字母缩写就是一个参数，GUN风格是`--`跟多个字母的长命令。`-h`往往对应`--help`，还有一种情况是`--`代表后面的参数不解析。

GUN风格`--`和`-`混合的模式中，`--`后面就是一个参数，`-`是连字符的作用，就是为了把两个单词隔开，为了美观，例如：

```
npm install express --save-dev
```

还有一种BSD风格，不带`-`，如：

```l
ps aux
tar cjvf what.tar.bz2 .
```

</br>

### 打开 debian 的 bbr

修改系统变量

```
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
```

保存生效

	sysctl -p

查看内核是否已开启BBR

	sysctl net.ipv4.tcp_available_congestion_control

显示以下即已开启

	net.ipv4.tcp_available_congestion_control = bbr cubic reno

查看 BBR 是否启动

	lsmod | grep bbr

显示以下即启动成功：

	tcp_bbr                20480  14

</br>

### ssh 保持不断开

```
vim /etc/ssh/sshd_config
```

添加语句，让服务端每间隔120s向客户端发送一个空数据包，最大发送720次，保持120*720=24小时不断开

```
ClientAliveInterval 120
ClientAliveCountMax 720
```

重启sshd服务

```
systemctl restart sshd
```

<br/>

### ssh 代码高亮

“别人家终端上的彩色效果”，修改隐藏的配置文件（ls -a 可以看到）

```
vim ~/.bashrc
```

增加以下内容，或去掉默认配置 PS1 前面的 # 并做修改，粉金红黄配色：

```
PS1='\[\e[37;40m\]\[\e[1m\][\[\e[35;40m\]\u\[\e[33;40m\]@\h \[\e[31;40m\]\#  \[\e[37;40m\]\w]$\[\e[32;40m\]'
```

金绿配色：

```
PS1="\[\e[36m\][\[\e[m\]\[\e[33m\]\u\[\e[m\]\[\e[32m\]@\[\e[m\]\[\e[33m\]\h\[\e[m\]\[\e[36m\]\w\[\e[m\]\[\e[36m\]]\[\e[m\]\[\e[33m\]\\$\[\e[32;40m\] "
```

想要自己调色参考：

+ [ezprompt Linux自定义shell配色工具](https://ezprompt.net/)
+ [命令行高亮配置](https://www.jianshu.com/p/24953f723ad7)
+ [Xshell-设置命令行提示符&配色方案](https://juejin.cn/post/6979027211680481310)

### SSH 密钥登陆

密钥可以简单理解成是一串复杂且可以相互验证的密码，由公钥（.pub）和私钥成对组成

生成一对密钥（名称 rsa，可以改成自己喜欢的，配置里默认 id_rsa.pub 和 id_rsa）

```
ssh-keygen -t rsa
```

查看密钥文件，默认隐藏，因此需要用 -a 

```
ls -la /root/.ssh/
```

新建 authorized_keys ，将 id_rsa.pub 写入这个空白文件

```
touch /root/.ssh/authorized_keys
cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
```

授权

```
chmod 600 authorized_keys
chmod 700 ~/.ssh
```

将私钥文件 id_rsa 下载到本地，放进本机的 .ssh目录，Windows 通常为`C:\Users\<用户名>\.ssh\`

然后试着 SSH 登录你的 VPS，不再需要输入密码了！

测试成功后可以关闭密码登录，修改 ssh 配置文件 `/etc/ssh/sshd_config` 中以下内容：

```
PubkeyAuthentication yes	# yes 允许密钥登陆
AuthorizedKeysFile      .ssh/authorized_keys .ssh/authorized_keys2 # 指定密钥文件的位置，此行去掉开头的#
PasswordAuthentication no	# 不允许使用密码登陆
```

重启 ssh 服务

```
systemctl restart ssh
```

<br/>

### SSH 传输文件（scp命令）

在 Windows 上，将 VPS上的文件 /root/a 下载到本地 C:\sync\ 文件夹中，打开 PowerShell 输入：

```
scp root@ip:/root/a C:\sync\
```

在 Windows 上，将文件 C:\sync\b 传到 VPS上的 /root/ 目录下

```
scp C:\sync\b root@ip:/root/
```

在 Windows 上，将 C:\sync\ 文件夹中的所有文件上传到 VPS 的 /root/c 目录下，`-r`是递归传输，即将目录下所有文件夹和文件按结构传过去（如果含非英文的路径、名称可能报错，含空格的路径用 "" 整个包起来）

```
scp -r C:\Sync root@ip:/root\b/
```

将 Linux 上的整个文件夹下载到 Windows，Linux 和 Linux 之间传文件依次类推，你还可以使用功能更丰富的`rsync`命令

<br/>

### ncdu 可视化文件扫描

一个可以彩色显示的可视化增强的文件扫描工具，安装

```
apt install ncdu
```

扫描`/var`目录

```
ncdu /var
```

扫描`/var`目录，并排除 rclone挂载的硬盘，并彩色显示

```
ncdu /var -x --color dark
```

退出`q`，更多帮助，扫描完成后`?`键

<br/>

### rclone 网盘挂载和传输



### corntab 计划执行

### 



### MJJ 是什么

这涉及到另几个名词，相关名词也提一下：

**母鸡**   VPS（Virtual Private Server，虚拟专用服务器）的实体服务器，比如一台 8核-64G内存硬件的实体服务器，通过 KVM、HyperV 等虚拟化技术划分出 64台 1核-1G 的 VPS，这台实体服务器就是母鸡（机），生了很多小鸡

**小鸡**	母鸡划分下来的虚拟专用服务器（VPS）

**超售**	一台 1核-1G-10G-1Gbps-4TB流量的 VPS，1核CPU、1Gbps带宽是和多个在同一台母鸡的邻居共享的，硬盘的读写能力也是共享的。不同商家不同配置的不同价格通常来于此，优秀商家能在高超售的同时保证高可用性，同时提供合适的价格。不优秀的商家，可能 2核不如别人 1核，1Gbps 不如别人 100Mbps，因此商家的口碑很重要

**独服**	独立服务器，指和 VPS比硬件资源相对独立

**MJJ**	在 hostloc 论坛指用户，最初可能是买鸡鸡的意思，但一般被读作木鸡鸡，hostloc 论坛的互称和自称

**TOS**	服务条款，MJJ不会看的一个东西，可能说明了禁止挖矿、禁止bt、禁止CPU、网络长时间高占用，MJJ 被商家 ban 的一个原因

**传家宝**	性能不错、价格低、续费同价，已下架的 VPS服务，通常是黑色星期五、圣诞节等节日活动的限售机型

**大盘鸡**	硬盘大的VPS

**NAT**	没有独立 IPv4 的 VPS，通常提供少量 IPv4端口和独立的 IPv6，价格比 VPS 更低廉

**线路**	这个较复杂，比如购买的服务器在美国，人在上海，美西→上海是直连，美西→美东→欧洲→俄国→中国是绕路，不同线路体验有差异

**北岸**	备案的和谐版，在中国购买域名、VPS需要提供身份信息，公安备案

<br/>

------

## 参考



+ [Getting-Started-with-Linux](https://github.com/uselibrary/Getting-Started-with-Linux) MJJ 的 Linux入门教程，包括 ssh修改密钥登陆（更安全）、nano编辑器、Timer、宝塔等内容
+ 





### MJJ 提到的商家

我见识少，仅作记录

**kt11.11**   性价比最高，大厂，科学和建站兼得，带快照

**ion**  带宽大，大肠，科学和建站兼得，缺点是ip只能换一次，没有快照

**斯巴达**	建站稳，科学一般

**Dmit**	贵，建站稳

**RackNerd**	科学和建站一般，性价比高

**Cloudcone**	cpu 垃圾，性价比一般

**pqs**	台湾黑五性价比高

**hosthatch**	拉胯

**甲骨文**	白嫖真香

**Vir**	垃圾

[NATVPS LTD](https://clients.natvps.uk/index.php?rp=/store/uk-nat-vps)



------





### GCP免费层级

详见 [官方介绍](https://cloud.google.com/free?hl=zh-cn) 和 [文档-免费层级](https://cloud.google.com/free/docs/free-cloud-features?hl=zh-cn#free-tier-usage-limits)，不仅仅包括 VPS，对于新手可能过于复杂，注册和设置过程增加了难度。

如果你的 Google 帐号使用时间长，并且绑定过信用卡、在 GooglePlay 等服务付过费，通常被默认高信任，填写资料就开通了。如果没开通，不建议再尝试，免费内容包括（列出部分）：

+ 1个非独占式 e2- ，2核-1G-30G HDD-5GB/月快照存储-1GB出站流量/月（不包括至中国、澳洲）
+ App Engine 完全托管式无服务器平台 28个F实例小时/d，9个B实例小时/d，1GB出站流量/d
+ AutoML Natural Language 自定义机器学习模型 5000个单元测试/月
+ AutoML Tables 6个节点时的训练和预测
+ AutoML Translation 自定义翻译模型 50万个字符翻译/月
+ AutoML Video Intelligence 视频机器学习模型 40个节点时/月、5个节点时预测/月
+ AutoML Vision 图片机器学习模型 40个节点时的训练和在线预测
+ BigQuery 分析数据仓库 1TB查询/月 10GB存储/月
+ Cloud Buid 120构建分钟/d
+ Cloud Functions 轻量级计算解决方案
+ Cloud Storage 5GB/月 Regional 存储空间（仅限美国地区）5000次A类操作/月 50000次B类操作/月 1GB出站流量/月（不包括至中国、澳洲）
+ Pub/Sub 全托管实时消息传递服务 10GB消息/月

超出免费层级会按标准费率计费，这种商用服务，可能不小心少套房。

[linux 本地终端 SSH 连接 gcp配置教程](https://developer.aliyun.com/article/692581)



这个星球有数万个 VPS 商家，大商家找了个山洞或者平原之类的地方建机房，放了成千数万的服务器，对大客户提供服务。其中部分客户是 VPS中小商家，它们购买服务后转销给特定需求的客户，或者个人。也有中小商家自己买硬件，托管在机房里。

一台服务器是 “母鸡”，上面安装虚拟机运行的多个操作系统，是它生下的 “小鸡”，这些 “小鸡” 就是我们在用的 VPS（Virtual Private Server，虚拟专用服务器）。VPS 配置的常用参数是 CPU-内存-硬盘-带宽-流量，1CPU-1G-10G SSD-1Gbps-2TB/月 并不意味着你的 VPS 有 1核CPU、1Gbps 的带宽，而是你和多个用户共享 1核CPU、1Gbps 带宽。

不同商家用相同母鸡划出的小鸡数不一样，虚拟化技术方面也有差异。1台母鸡上塞 10个用户，用户体验肯定要比塞 20个用户要好，但前者也肯定要比后者贵。通过服务配置、资源配置能力、客服等方面的差异化，产生了不同的 VPS 商家。

大商家（AWS、谷歌、微软、甲骨文、腾讯、阿里巴巴等）提供的个人服务，通常要比中小商家的好，但更像是向大客户IT销售的体验服务，让你去熟悉IT流程和相关系统。
