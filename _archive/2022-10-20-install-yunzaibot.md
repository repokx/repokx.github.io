---
title: 安装云崽bot，以及可能出现的问题
date: 2022-10-20 13:00:00 +0800
categories: [开发, 其他]
tags: [qqbot, 云崽, 原神]
author: repo
# math: true
# mermaid: true
# pin: false 
img_path: /src/
# image:
#     path: 
#     alt: 
---

## 1. 下载与基本安装

### 1.1 node.js

`http://nodejs.cn/download/`

至少**v14**以上

![node](/node.jpg)

### 1.2 redis

`https://github.com/tporadowski/redis/releases`

解压后，双击`redis-server.exe` 保持运行即可，会产生一个代码棱柱如图。

![redis-config](/redis-config.png)

如果没有，说明没运行，尝试：

1. 在redis根目录下新建start.bat，并写入

   ``` sh
   redis-server.exe redis.windows.conf
   ```

   运行即可

2. 曾经运行过redis，打开`redis-cli.exe`，输入`shutdown`，回车，输入`exit` ，回车，然后重复上述步骤即可。

### 1.3 yunzai-bot

1. clone

   ``` sh
   git clone https://gitee.com/Le-niao/Yunzai-bot.git
   cd Yunzai-Bot
   ```

2. 安装

   + 配置

     ````sh
     npm install --location=global cnpm --registry=https://registry.npmmirror.com
     ````

     此处可能出现`npm:command not found`的错误，使用管理员权限打开shell即可，因为非cmd权限无法访问node

     具体操作方法：按住shift，打开右键菜单，选择使用powershell打开，重复上述配置即可。

   + 安装

     ``` sh
     cnpm install
     ```

### 1.4 miao-plugin

在yunzai根目录下，bash运行

``` sh
# 1.clone
git clone https://github.com/yoimiya-kokomi/miao-plugin.git ./plugins/miao-plugin/

# 2.安装pnpm
npm i pnpm -g
# 安装image-size
pnpm add image-size -w

# 3.或者直接
npm i image-size -w
```

## 2. 获取米游社cookie

浏览器打开`https://bbs.mihoyo.com/ys`

F12访问网页后台，控制台输入代码`document.cookie`

复制产生的cookie 备用

## 3. 运行

``` sh
node app
```

按照提示输入qq号，推荐密码留空，扫码登录

## 4. 再次运行

1. 先打开redis（**步骤1.2**）
2. 在云崽bot根目录下，进入cmd（或者管理员下的powershell、管理员下的gitbash）
3. `node app`



完

---

# reference

[1] [bilibili - **原神机器人Yunzai-Bot window搭建教程**](https://www.bilibili.com/read/cv15119056)

[2] [github - **Yunzai-Bot**](https://github.com/Le-niao/Yunzai-Bot)

[3] [github - **miao-plugin**](https://github.com/yoimiya-kokomi/miao-plugin)