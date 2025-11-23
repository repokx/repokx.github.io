---
layout: post
title:  使用 oh my posh 美化 terminal 基础教程
date:   2022-02-19 18:08:00 +0800
categories: [Developing, System Development]
tag: [terminal, oh my posh, nerd fonts]
---
> 参考微软doc：[教程：使用 Oh My Posh 为 PowerShell 或 WSL 设置自定义提示符](https://docs.microsoft.com/zh-cn/windows/terminal/tutorials/custom-prompt-setup)
### terminal 执行以下步骤。
``` shell
Set-ExecutionPolicy Bypass
Install-Module oh-my-posh -Scope CurrentUser
Install-Module posh-git -Scope CurrentUser
```
> 注1：此处 terminal 在管理员模式下运行
> 注2: 后两条install，记得输y表同意
### 生成 profile 文件
``` shell
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
code $PROFILE
```
### 往生成的 profile 文件中加入以下段落
``` shell
Import-Module posh-git
Import-Module oh-my-posh
Set-PoshPrompt -Theme JanDeDobbeleer
```
> 注: JanDeDobbeleer 替换成需要的主题

### 使用nerd字体处理乱码
+ 下载几个喜欢的字体，就普遍理性而论，只要上面找的主题文件名字没有 `minimal`，都必须安装nerd字体
+ 所有的nerd字体均默认适配现有主题，不适配的话要考虑更换主题
+ 下载好的字体，解压，全选，安装 即可

### 配置进terminal
参考[这一部分](https://ohmyposh.dev/docs/config-fonts)
terminal界面下按 `ctrl + shift + , ` 进入settings，在defaults后的花括号内添加`font`、 `face`如下：

``` json
{
    "profiles":
    {
        "defaults":
        {
            "font":
            {
                "face": "MesloLGM NF"
            }
        }
    }
}
```
官方默认推荐的是上面写的 `MesloLGM NF`，但其实都可以
注意，这个名字必须跟nerd网页上的名字一致，否则可能无法加载

+ 注意重启terminal

![ompterminalbeautify](https://s4.ax1x.com/2022/02/19/HbIDJS.png)_omp 美化效果图（我使用的theme是bubbles，font是cousine nf)_

### 完成。

>
>
>后记：
>
>加了这个玩意之后，terminal变得奇慢无比
>
>后来觉得华而不实，删了。。。
>
>