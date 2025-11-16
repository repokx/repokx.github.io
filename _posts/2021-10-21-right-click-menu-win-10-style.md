---
title: 修改注册表使原生 win11 右键菜单更改为 win10 样式
date: 2021-10-21 23:06:00 +0800
categories: [开发, 系统配置]
tags: [win11]
author: repo
# math: true 
# mermaid: true
# pin: false 
# img_path: /src/
# image:
#     path: 
#     alt: 
---

# 背景

win11 什么都挺好的，就是它的右键菜单实在是... 没话说。

正常使用 windows 一般可能用不太多右键菜单的附加功能，比如压缩文件，用 bash 编辑，code 打开之类的功能。但是作为业余开发者... 实在忍受不了 win11 的“智能”简约折叠右键菜单... 忍无可忍寻求解决方案。

于是就找到了这么一个 YouTube 视频：

[![Windows 11: Enable old context menu (Windows 10 right-click style)](https://res.cloudinary.com/marcomontalbano/image/upload/v1634865607/video_to_markdown/images/youtube--GM5FUqufT1w-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=GM5FUqufT1w "Windows 11: Enable old context menu (Windows 10 right-click style)"){:target="_blank"}_Youtube Video [^1]_

# 实现方法

预先强调：

> **注意：**
> 进行注册表编辑之前**必须**对注册表进行备份，并且**了解**注册表的备份恢复方法，以免发生注册表**重大错误导致系统崩溃**

---

1. 在任意界面下，按下 `Windows 徽标键 + R`，打开**运行**窗口

2. 输入 `regedit`，进入注册表编辑窗口

   ![run dock](https://z3.ax1x.com/2021/10/22/5yjZDI.png)_**图1**  运行窗口界面_

3. 在以下目录中：

   ```
   HKEY_CURRENT_USER\Software\Classes\CLSID
   ```

   新建目录：

   ```
   {86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32
   ```

   ![New Directories](https://z3.ax1x.com/2021/10/22/5yjDxJ.png)_**图2**  创建图示目录_

4. 你将发现新建的 `InprocServer` 默认生成了一个“默认”变量，它的值为“数值未设置”

   ![Data Unset](https://z3.ax1x.com/2021/10/22/5yj6q1.png)_**图3**  变量默认预设_

5. 双击该条目并打开，确认数据栏内容为空，确认，保存注册表如下：

   ![Edit Reg](https://z3.ax1x.com/2021/10/22/5yj5xH.png)_**图4**  确认内容为空_

6. 重启电脑，得到原生 win10 样式的圆角完整右键菜单

   ![contract](https://z3.ax1x.com/2021/10/22/5yxQXj.png)_**图5**  新旧菜单对比_

# 还原方法

毕竟直接修改注册表的方法对于系统更新可能造成比较大的问题（不兼容等）

当你需要升级系统时，建议将上述新建的目录即

```
{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32
```

**完全删除**，保存重启即可

实测安全，放心使用

# Tips

在 markdown 文件中插入一段 HTML 代码就能添加带图片的视频链接

``` html
[![Windows 11: Enable old context menu (Windows 10 right-click style)](https://res.cloudinary.com/marcomontalbano/image/upload/v1634865607/video_to_markdown/images/youtube--GM5FUqufT1w-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=GM5FUqufT1w "Windows 11: Enable old context menu (Windows 10 right-click style)")
```

这段代码事实上是网站生成的，原理是生成一个带播放按键的图片，点击图片即会直接链接到视频地址，这个网站如下：[^2]

[**Video to Markdown**](https://video-to-markdown.netlify.app/)

当然，这个链接点击后会覆盖当前页面，解决方案是在上面这串代码后边加一句：

``` html
{:target="_blank"}
```

新建一个页面，打开新的窗口。具有普适性。

# References

[^1]:["Windows 11: Enable old context menu (Windows 10 right-click style)"](https://www.youtube.com/watch?v=GM5FUqufT1w). YouTube.
[^2]:["将Youtube视频插入Github Markdown文本中"](https://www.cnblogs.com/hupo376787/p/12736679.html). cnblogs.com.