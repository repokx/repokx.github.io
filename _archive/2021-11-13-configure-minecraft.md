---
title: 如何使用HMCL启动器配置Java版Minecraft
date: 2021-11-13 22:22:00 +0800
categories: [游戏, Minecraft]
tags: [Java, Minecraft]
author: repo
# math: true 
# mermaid: true
# pin: false 
# img_path: /src/
# image:
#     path: 
#     alt: 
---

## 1. Backgroud

Minecraft，我的世界，众所周知，分为 Java 版和基岩版。Java 版在运行时必须安装 Java 运行环境。

对于官方版本的游戏，官方包中自带了 Java Runtime Environment。但是对于启动器版本，启动器一般不会集成这些元件，并且有些启动器在使用的时候就需要调用 Java 来启动，所以 Java 是必须要安装的。

Java 分为 jre (Java Runtime Environment) 与 jdk (Java Development Kit)。事实上，jdk 涵盖了 jre 的全部功能。Oracle 官网对于这两种工具包给出了图形解释。

![jrenjdk](https://z3.ax1x.com/2021/11/13/Iy47AP.png)_*图1* Oracle 对于 jre 和 jdk 的定义 [docs.oracle.com](https://docs.oracle.com/javase/7/docs/)_

非常明显，jdk 相较于 jre，多了 `Java Language` 与 `Tools & Tool APIs` ，也就是 Java 的开发部分。

问题来了，对于 Minecraft，我们到底需要 jdk 还是 jre 呢？

一位 BMCL 的开发者给出了说法

> **MC需要启动器的原因说到底只有一个，因为他是用Java写成的。**
>
> Java的运行需要JVM，但是JVM需要传入相应的参数才能让一个Java程序正确的运行。
> 举个简单的例子，网上下载得到的一个可执行的jar包，是不能像exe一样双击运行的。需要用命令行调用java -jar a.jar才能够执行，而启动器最核心的功能就是完成这个过程。
>
> 但是如果一个程序复杂到一定程度之后，是不可能一个jar搞定所有功能的，否则会有很复杂的依赖以及人员之间的协调成本，这种时候就需要将一个完整的程序拆成模块，各个模块之间可以按照一定的约定协同工作。
>
> 仔细看一些比较大的软件，比如 QQ，除了一些exe以外还有大量的dll文件存在，这就是拆开后的结果。这种跑到Java下就会成为一个一个的jar包，但是Java允许jar包内嵌jar包解决依赖的问题。
>
> **然而实际上，如果将一个程序所需要的所有jar包全部打包起来，那么最终得到的jar包体积会非常恐怖**，而且有一些软件的用户协议不允许这么打包，所以在启动阶段就需要加载许多jar包，开启一个Java程序的命令就会变成java -cp a.jar:b.jar:c.jar，需要一个一个将所用到的jar包列清楚。
>
> 这是MC启动器的**最大**的作用，也是 1.6版本之前的启动器主要在做的事情。
>
> ---
>
> *作者：bangbang93*
> *链接：https://www.zhihu.com/question/49997128/answer/119951802*
> *来源：知乎*
> *著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。*

不难看出，我们需要的是 jre，也就是运行环境。



## 2. Followed Steps

### 2.1 Java Environment Configuration

经过上文介绍，我们只需要下载 jre 即可运行。

既然如此，你可以选择从 Java 官网进行安装。

[**Java.com**](https://www.java.com/en/download/manual.jsp)（选择 windows offline）

另外，也可以通过 MMP 的 Oracle 安装（这玩意儿老连不上 tmd）

**[Oracle.com](https://www.oracle.com/java/technologies/downloads/)**

无脑安装即可



### 2.2 Java Development Kit

同样的，因为 jdk 内含 jre，所以安装 jdk 也有同等效力。但是 jdk 只能从 oracle 上安装，这样就导致我这样的人根本连进都进不去。

所以我找到了一系列的链接

1. jdk 下载

   **[jdkdownload.com](https://www.jdkdownload.com/)**

2. 清华大学开源镜像站 Tsinghua TUNA

   **[mirrors.tuna.tsinghua.edu.cn](https://mirrors.tuna.tsinghua.edu.cn/AdoptOpenJDK/)**

3. 中国科学技术大学 USTC

   **[mirrors.ustc.edu.cn](https://mirrors.ustc.edu.cn/AdoptOpenJDK/)**

4. Oracle 官方源

   **[Oracle.com](https://www.oracle.com/java/technologies/downloads/)**
   
   

### 2.3 HMCL Installer

**[Hello Minecraft! Launcher](https://hmcl.huangyuhui.net/download/)**

安装后运行即可



## 3. Warnings

用这个方法安装 jdk 还是 jre，都会造成一个问题，那就是在安装高版本的 java 的时候，会发生警告。

![hmclwarning](https://z3.ax1x.com/2021/11/13/Iy4o7t.png)_*图2* 报错。。。_

我感觉这个问题是由于过高的 Java 版本造成的，因为 Minecraft 官方给出的解答是在 1.17版（21w19a）之后，必须使用 java 16 或更高版本，我认为是不是因为 Java 1.18 版本过高造成的这个问题。

但是这个问题事实上不影响运行。第三方平台给出的解释是：

> DST Root CA X3 证书将于 2021年9月30日到期。这意味着在此之后那些不信任 ISRG Root X1 证书的旧设备在访问使用 Let's Encrypt 证书的网站时将开始出现证书警告。不过有一个例外很重要：多亏了 DST Root CA X3 的特殊 "交叉签名" 机制，Let's Encrypt 的证书依然可以在不信任 ISRG Root X1 证书的较旧的 Android 设备上正常工作。
>
> 交叉签名机制使得 Let's Encrypt的证书的有效期限可以超过根证书的到期时间，此例外仅适用于 Android。
>
> 那该怎么办呢？对于大多数人来说，什么也不用做！我们已经准备好了新的证书发行机制，因此您的网站在大多数情况下会做正确的事，兼容非常广泛。

之后我会试验是否低版本的 Java 会使得这个错误消失。虽然这个警告无关紧要，但是毕竟看着难受。

至此，所有的安装过程全部结束。



## 4. References

+ [minecraft.fandom.com. **教程/成功地启动游戏**](https://minecraft.fandom.com/zh/wiki/%E6%95%99%E7%A8%8B/%E6%88%90%E5%8A%9F%E5%9C%B0%E5%90%AF%E5%8A%A8%E6%B8%B8%E6%88%8F?variant=zh#.E6.AD.A3.E7.A1.AE.E5.9C.B0.E5.AE.89.E8.A3.85.E5.8F.8A.E9.85.8D.E7.BD.AEJava)

