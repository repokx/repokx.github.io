---
layout: post
title:  重新学习建立网站
author: Repo Xu
date:   2021-06-30 22:38:00 +0800
categories: [Developing, Blogging]
tag: [Jekyll, Github Pages]
math: false
mermaid: false
pin: false
---

# 1.缘起

之前在考试周的时候就一直想着做一个博客，所以在做课设的闲暇之余，以至于之前通了几次宵。我都一直在抽出时间来做我自己的博客，但是苦于自己并没有相关的编程基础，也没学过 CSS，也不了解 html，甚至连 markdown 的语法都不是很清楚。又缘于前两天因为 OneDrive 配置失败搞得自己电脑的 document 文件夹也乱了，把电脑强制重置了 21H1 的版本，重置了所有的应用，也算是为了迎接马上要到来的 Win11 更新。今天又准备来搞一搞自己的博客。

其实是有这么回事的，本来想着自己再按照之前的方法用官网的教程再装一个 ruby、Jekyll，然后直接重新做一个网页。但是总有种重蹈覆辙的方法，于是今天从 YouTube 上找到了这么一个人的视频，也算是好好学习一下到底怎么建立一个网站。网站附下：

> [Jekyll 博客系列 - 01 快速入门 - YouTube](https://www.youtube.com/watch?v=Zt_QzSbyDcw&list=PLK2w-tGRdrj7vzX7Y-GqKPb2QPrHCYZY1)

***

# 2.入门操作 

## 2.1 搭建环境

### 2.1.1 安装ruby

[Ruby 2.7.3-1](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.7.3-1/rubyinstaller-devkit-2.7.3-1-x64.exe) 使用这个链接下载并安装到windows下

### 2.1.2 安装Jekyll

```ruby
$ gem install jekyll
```

### 2.1.3 安装bundler

bundler是Jekyll 3.3之后的版本使用的运行方式，所以在运行jekyll博客的时候必须使用bundler语句

```ruby
$ gem install bundler jekyll
or
$ gem install jekyll bundler
(顺序好像没有影响？？？)
```

这样基础的开发环境就已经搭建完毕

## 2.2 在本地搭建博客

两种方式

### 2.2.1 simple one

直接新建一个博客文件夹（需要在想要创建的地方shift进入powershell下）

如下，将myblog替换为你要创建的博客文件夹名

```console
$ jekyll new myblog
```

### 2.2.2 complicated one

新建一个空文件夹，然后用Jekyll在里面新建blog

```console
$ mkdir mblog
$ cd mblog
$ jekyll new .
```

删掉刚才新建的第二个文档。嘛就算是熟悉一下powershell的语法。

```console
$ cd ..
$ rm mblog
$ y
```

### 2.2.3 继续搭建基本文件

因为Jekyll在搭建系统的时候可能会有一些依赖文件，所以需要用bundler来搭建这些需要的依赖

```console
$ cd myblog
$ dir
$ bundle install
```

现在，这个博客就算是搭建完成并且可以在本地进行运行，使用如下操作：

```console
$ bundle exec jekyll serve
```

嘛，嫌麻烦也可以把serve改成s，这样减少代码输入量（并没有）

这时候就可以在本地的`127.0.0.1:4000`端口运行这个网站，`ctrl + click`打开这个链接就可以看到你建立的这个网站

```terminal
PS E:\Programfls_extra\myblog> bundle exec jekyll s
Configuration file: E:/Programfls_extra/myblog/_config.yml
            Source: E:/Programfls_extra/myblog
       Destination: E:/Programfls_extra/myblog/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.446 seconds.
 Auto-regeneration: enabled for 'E:/Programfls_extra/myblog'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

如果没有出现上面这个链接，你可能需要重新安装一下`webrick`这个组件

```console
$ bundle add webrick
```

这样你的网站就在本地建好了

如果你电脑上之前就有装 vs code 的话，快速查看博客文件的目录结构：

```console
$ code .
```

### 2.2.4 其他需要了解的事情

在Jekyll的文件目录库中包括很多文件，逐个阐明。

#### 2.2.4.1 _config,yml

众所周知，config是configuration的缩写，即站点配置文件。所有对网站属性的修改都从这里开始。每次使用bundle构建站点之后直到下一次构建之前，所有对于这个文件的修改都不会生效，换言之，想要修改它就必须重新发布。

比较重要的一些关键词包括：

+ title

  这个是整个博客的主标题，在初始模板上显示就是在header上的博客名

+ description

  这个是博客的介绍，显示在footer上。事实上只是一个内容关键词，你甚至可以把description放在posts里面。

+ baseurl

  默认不加的时候访问的是4000这个端口，但是如若你的博客域名下面有多个blog比如blog1/2/3 etc... 那么你就需要在这儿写一个基础站点指定一个二级path，比如/blog。那么Jekyll生成的站点的位置就在`127.0.0.1:4000/blog/`下。直接访问4000站点得到的网站应该是404网站。

  不建议直接修改，因为也用不着（暂时）

+ url

  默认就是生成的站点的内容，填与不填意义不大，但是还是建议填上（比如后面将要发布的地方`https://你的github名.github.io`

+ _username

  这个类型的，可以加很多个，只要你在模板文件中写好元素加好链接，可以链接不止两个社交帐号

+ theme

  这一项就是写这个默认主页使用的jekyll主题名称，默认这个很简洁的就是叫minima~

+ exclude

  exclude这一项写的是在发布网站的时候Jekyll不会往站点发布的文件，比如包括的内容在发布端应该是找不到的，后文中会详细分析。

#### 2.2.4.2 _posts

posts，就是发布的意思，你将要在端口发布的markdown格式的博文都会储存在这个地方。

#### 2.2.4.3 _drafts

drafts，就是手稿的意思。就是博文的草稿箱之类的东西，你并不想把这篇博文上传到端口，但是还没有写完还需要保留一部分以后继续编辑，那么你就可以把md文件暂时放在drafts文件夹里面，这样Jekyll在发布的时候也会自动地忽略这个文件夹中的博文，~~但是这篇文章仍然会被发布到云端？~~

#### 2.2.4.4 _site

site这个文件夹在上传到端的时候不会被上传。但是我们通过端口访问的网站事实上就是Jekyll生成的这个目录里面的静态网页。事实上，也就是一个映射。甚至你可以直接把这个文件夹里面的html代码直接拷到虚拟主机或者服务器里面来构建静态网页并运行发布，完全没有问题。

因为site不会被上传到端口，所以在`.gitignore`这个文件中包括这个`_site`的内容。

如果你想让Jekyll单独输出一个这样的站点文件夹，比如把他输出到这个目录下的dist文件夹，可以这样做：

```console
$ jekyll build --destination = ./dist
```

同样，上面的build可以缩写成b

***

# 3. fork 自己的 blog

经过上面的学习，相信大家已经了解到如何建立一个简单的自定义博客了，但是初始模板 mininal 毕竟是很朴素的，如果想要锦上添花一下，你就需要去找一找博客模板。

Jekyll 提供了巨量的网站模板，大多数都能够正常运行。由于开发人员包括各种行业的爱好者与程序员，难免存在质量较低者，不要灰心，可以寻找其他心仪的模板进行 fork。

以我使用的模板 [chirpy](https://github.com/cotes2020/chirpy-starter/) 为例，我将对这个模板的具体使用方法进行讲解。

## 3.1 find a template

Jekyll 官方提供了以下链接：

+ [GitHub.com #jekyll-theme repos](https://github.com/topics/jekyll-theme)
+ [jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
+ [jekyllthemes.org](http://jekyllthemes.org/)
+ [jekyllthemes.io](https://jekyllthemes.io/)
+ [jekyll-themes.com](https://jekyll-themes.com/)

本部分介绍 chirpy 模板的初始包 “chirpy-starter”，打开上文中提到的链接，点击 `Use This Template`，使用这个模板创建你自己的库。

![template](/assets/img/recreate_blog/template.png)_**图3.1**  使用模板创建库_

而后按照图3.2中的方式 fork 你的 blog 仓库，把其中的 “XXXXX” 改成你自己的 github 用户名，当然你换成别的也可以，但是你需要对 `_config.yml` 里的 `baseurl` 这一项作修改。

```yaml
baseurl: /your repository name
```

这样你生成的网页的名字将变成

```yaml
https://your_github_name.github.io/your_repository_name
# your_github_name: 你的 github 用户名
# your_repository_name: 你创建的仓库名称
```

![template1](/assets/img/recreate_blog/template_2.png)_**图3.2**  使用模板创建库_

## 3.2 change everything locally

将之前做好的库clone到本地

```console
$ git clone https://github.com/repo-kristx/repo-kristx.github.io.git
```

安装依赖

```console
$ bundle
or
$ bundle i
or
$ bundle install
(all the same effect...)
```

执行以下语句

```console
$ bash tools/init.sh
```

这条语句有以下作用：

1. 从你的本地库移除一系列文件 / 文件夹：
   + `.travis.yml`
   + `/_posts`
   + `/docs`

2. 将会在 GitHub 工作流下自动创建一个工作流，配置 GitHub Action：把 `.github/workflows/pages-deploy.yml.hook` 的后缀 `.hook` 去掉，删除 `.github` 文件夹下的其他目录与文件。
3. 自动提交一个 commit 以保存上述文件的更改，这将自动触发 GitHub 远端的工作流。

## 3.3 custom your blog

按照 2 中的教程，对你的 blog 的内容进行更改，注意保存。如果你不打算更改模板提供的框架，那么你大概只需要建立 `_posts` 文件夹与更改 `_config.yml` 中的内容，包括但不限于：

+ `url`
+ `avatar`
+ `timezone`
+ `lang`
+ `links`

完成更改后，记得在本地运行一下以确保内容正确无误：

```console
$ bundle exec jekyll serve
```

并在运行结束后按 `ctrl`+`c` 退出本地调试模式

## 3.4  deployment

刚才创建了 GitHub 的远程库，并且我们已经把他 pull 到了本地，现在我们再检查一下：

+ 确保 Jekyll 站点存在文件 `.github/workflows/pages-deploy.yml`。没有的话，新建并填入[示例工作流](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/.github/workflows/pages-deploy.yml.hook)的内容, 注意参数 `on.push.branches` 的值必须和您的仓库默认分支名相同。
+ 检查您的 Jekyll 站点是否有文件 `tools/test.sh` 和 `tools/deploy.sh`. 没有的话, 从本仓库拷贝到您的 Jekyll 项目

其实正常套用 template 的 fork 能够按照上面的步骤完成，完全可以省略这两步。

在近端使用 `git` 命令将你的更改发到远端：

```console
$ git add -A			# 添加本地更改记录到 /.git
$ git commit -m "XXX"		# 注释你的本次更改到 /.git
$ git push origin main		# 发布到 remote 端
```

推送任意一个 commit 如上到 `origin/main` 以触发 GitHub Actions workflow。一旦 build完毕并且成功，远端将会自动出现一个新分支 `gh-pages` 用来存储构建的站点文件。

回到 GitHub 上的仓库（远端），通过*Settings* → *Options* → *GitHub Pages* 选择分支 `gh-pages` 作为[发布源](https://docs.github.com/en/github/working-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)：

![push](/assets/img/recreate_blog/push.png)_**图3.3**  发布你的 blog_

大功告成！接下来就可以按照上图中的指引访问你的 blog 了~
