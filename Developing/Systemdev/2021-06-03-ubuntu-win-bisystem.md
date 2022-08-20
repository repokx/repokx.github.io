---
layout: post
title:  Ubuntu-win 双系统配置心得
date:   2021-06-03 03:03:00 +0800
categories: [Developing, System Development]
tag: [Ubuntu, BiSystem]
---
### 1.缘起
之前听到老师们提到很多专业的软件后期还是需要在以linux为基础架构的设备上去跑，原因是linux的计算结构与windows不同。
之前也有安装linux的经历，三次安装，一次成功，一次把C盘给格了，一次无疾而终，总之是四处碰壁...
突然间觉得自己应该装一个试试，于是对Ubuntu 20.04.2.0下手了。

### 2.尝试：win10自带版本
之前听老牛说这玩意win10内置了一个，于是我百度（csdn）得到了直接在应用商店下一个ubuntu的想法。<br>
`win+s -> cp`<br>
进入控制面板，找到【卸载或更改程序】，左边栏的【打开或关闭windows功能】，滑到最下方，打开linux与windws的选项，并且打开，保存后关闭。<br>
`win+s -> set`<br>
进入设置，搜索【开发者】，进入后打开开发者权限。<br>
`win+s -> store`<br>
进入应用商店，下载ubuntu。等待安装，就得到了一个安装在C盘上的光杆ubuntu。
能够正常使用sudo命令行功能，但是没有图形界面刚开始还是很难受，且占了我大量C盘空间，搜索得到很多方案，但是嫌麻烦，遂放弃，走双系统的老路。

### 3.折腾：双系统版本
#### 1)下镜像
我老早就了解到[TUNA](https://mirrors.tuna.tsinghua.edu.cn/)有镜像下东西会很快，于是直接进TUNA准备下个20.04。
但是开始下才发现，2.7 GB的iso镜像速度居然都不到100 kB，我人傻了，只好去『[官网](https://ubuntu.com/download/desktop)』准备碰碰运气。
没想到这回校园网给力到不行，直接飙到8 MB/s，但是不稳定，断了好几次，又下了好几次，好不容易下完，半个点过去了。
#### 2)烧录USB启动盘
走老路，看了个[b站视频](https://www.bilibili.com/video/BV11k4y1k7Li?t=789)讲装ubuntu，我就下了个[rufus](https://rufus.ie/zh/)准备烧录USB启动盘。
烧也简单，导入包，选好路径，默认都不用更改，直接造。
#### 3)错误初现
按住shift点重启，使用USB设备启动，都没有问题，结果进去之后发现不能正常引导，导到了“GNU grub”里面。
我不知道这是什么东西，他跟我说按tab可以查看命令，可我输了exit之后没有动静，遂想可能是烧录出了问题，于是重新烧了两遍，但是报错依旧。
我寻思我也没用过rufus，万一这玩意跟我不兼容是不是？于是我下了个[UltraISO](https://cn.ultraiso.net/)接着烧。
可是还是不行。
#### 4)不稳定的校园网
再下一遍ubuntu。过了12点，没大有人跟我抢校园网了，于是我又下了一遍。果然又快又稳，虽然还是断了一次，但无大碍。
再烧，终于烧进去了...
#### 5)安装
走老路，引导，USB启动，进了似曾相识的骚紫色界面，开始配置。
之前早就给机械留了1/3的空间以备不时之需，现在用上了，330 GB的空间，都装到根目录“/”里面去，大功告成。

### 4.总结
网不好的锅。
之前大一的时候装ubuntu，光觉得牛逼了。现在发现，不过如此。
学了几句sudo命令，就记住一个<br>
`$ sudo apt-get update`<br>
ubuntu帮助网站上不少教程，还学到了.deb是linux下可行的安装包，也学到了tar.gz也是为了方便linux的一种安装格式。[ubuntu官网教程](https://help.ubuntu.com/kubuntu/desktopguide/zh_CN/manual-install.html)如参考。
希望以后越来越好。
