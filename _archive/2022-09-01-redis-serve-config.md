---
title: redis服务器启动 6379 - bind No such file or directory
date: 2022-09-01 13:00:00 +0800
categories: [开发, 服务器]
tags: [redis]
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
摘要

对于redis启动服务后，出现6379端口无法使用的问题的解决方案：

运行redis-cli.exe，然后对6379端口shutdown，再exit，即可解决端口占用，从而使得redis服务可以启动。
```



### 1 问题复现

```shell
PS D:\Devtools\Redis> redis-server.exe
[8812] 21 Jul 22:39:12.624 # Warning: no config file specified, using the default config. In order to specify a config file use D:\Devtools\Redis\redis-server.exe /path/to/redis.conf
[8812] 21 Jul 22:39:12.624 # Creating Server TCP listening socket *:6379: bind: No such file or directory
PS D:\Devtools\Redis> redis-server.exe redis.windows.conf
[9324] 21 Jul 22:39:22.587 # Creating Server TCP listening socket *:6379: bind: No error
```

### 2 问题解决方法
```shell
PS D:\Devtools\Redis> redis-cli.exe
127.0.0.1:6379> shutdown
not connected> exit
PS D:\Devtools\Redis> redis-server.exe
```

### 3 成功运行的结果
```shell
PS D:\Devtools\Redis> redis-server.exe
[10400] 21 Jul 22:40:19.622 # Warning: no config file specified, using the default config. In order to specify a config file use D:\Devtools\Redis\redis-server.exe /path/to/redis.conf
                _._
           _.-``__ ''-._
      _.-``    `.  `_.  ''-._           Redis 3.0.504 (00000000/0) 64 bit
  .-`` .-```.  ```\/    _.,_ ''-._
 (    '      ,       .-`  | `,    )     Running in standalone mode
 |`-._`-...-` __...-.``-._|'` _.-'|     Port: 6379
 |    `-._   `._    /     _.-'    |     PID: 10400
  `-._    `-._  `-./  _.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |           http://redis.io
  `-._    `-._`-.__.-'_.-'    _.-'
 |`-._`-._    `-.__.-'    _.-'_.-'|
 |    `-._`-._        _.-'_.-'    |
  `-._    `-._`-.__.-'_.-'    _.-'
      `-._    `-.__.-'    _.-'
          `-._        _.-'
              `-.__.-'

[10400] 21 Jul 22:40:19.622 # Server started, Redis version 3.0.504
[10400] 21 Jul 22:40:19.622 * DB loaded from disk: 0.000 seconds
[10400] 21 Jul 22:40:19.622 * The server is now ready to accept connections on port 6379
```

### 4 原理
重启6379端口，关闭已经占用的线程，重启后port分配给redis使得程序能够运行