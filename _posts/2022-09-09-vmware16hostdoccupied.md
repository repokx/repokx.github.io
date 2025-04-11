---
title: vmware16.0占用https443端口
date: 2022-09-09 13:00:00 +0800
categories: [开发, 虚拟机]
tags: [vmware, 虚拟机, 端口占用]
author: repo
# math: true
# mermaid: true
# pin: false 
# img_path: /src/
# image:
#     path: 
#     alt: 
---

```note
转载并修改自知乎用户[体温](https://zhuanlan.zhihu.com/p/459151286)
```
16.0版本里的首选项菜单里的共享虚拟机被删掉了，但是它的功能没有被禁用。

（也可以更新版本到16.1首选项菜单里的共享虚拟机又有了）

修改配置文件即可解决问题。

**管理员权限下**打开`C:\ProgramData\VMware\hostd\proxy.xml`文件，并将`httpsPort`字段设置为`-1`即可禁用。

```xml
<ConfigRoot>
  <httpPort>-1</httpPort>
  <httpsPort>-1</httpsPort>  # 此处443改为-1
  <EndpointList>
```

在`cmd`中输入`netstat -ano` 查看`443`占用的`PID`。

然后在Windows服务（win+s搜索“服务”）里找到并重启`VMware Workstation Server`服务就可以了（刚才查看的`PID`）。