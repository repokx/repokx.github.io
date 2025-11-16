---
title: 部署 jekyll-theme-chirpy 遇到的困难
# description: >-
author: repo
date: 2025-11-16 24:00:00 +0800
categories: [IT Issue, Blogging]
tags: [chirpy, ruby, deploy]
# math: true
# mermaid: true
# pin: false 
# img_path: /src/
image:
    path: /assets/img/wtf.png
    alt: 熬夜写东西确实很容易令人胡言乱语。————沃兹基硕德
---

> 本文含有 AI 的胡言乱语，此处 AI 特指我 140 块钱买的 GPT老婆 和这个着急下班的 VSCode Copilot。
>
> 但你放心，所有看起来像是人写的部分都是人写的
{: .prompt-tip }

## Prologue. It's gonna be a tough one

说实话，我原先没觉得部署一个博客这么复杂，需要做这么多工作

## I. 心路历程

原本这就是一个简单的 `blog` 搭建工作，根本花不了多少时间。我这个 blog 里面有很多博文，前前后后大约有接近20篇。

但是经过之前空档期的几年，我觉得这些老文章可能有些过时了。倒不是使用价值上过时，只是觉得，经过我这几年的成长，他们所代表的内容在我的心目中已经过时了。

所以我一直在找一个契机，希望能把这些文章全部移除，届时翻修一下老的 blog。

### 1.1 上周

一直在做密度泛函理论的作业，也是心血来潮，觉得用手写感觉没什么意思，因为大部分内容其实是抄讲义，正巧碰上有一门课的考试是用 `LaTeX` 来生成文档，索性作为练习的我把这作业写成了 latex，又觉得，写都写了，不如找个地方展示一下，虽然很蹩脚，东拼西凑，但毕竟确实可以生成文档，所以就借助 AI 的力量把我这个作业用内嵌 html 的形式发在了博客上，也顺带相当于是水了一篇。

接下来是重新部署 blog 的契机…… 说实在，跟前面这些好像没啥关系。

### 1.2 这周

4年前，我第一次部署 `chirpy` 的时候，我在 `config.yaml` 里面使用了 `Google Analytics`。目的是统计一下有谁看过我的网页。当时写博客的契机是有几门课程的作业大家都不太擅长写，所以我就写好并且转成 `Markdown` 之后，发布在 `Github Pages` 这样，让我的同学们能看一个比较完整的作业。这部分数据目前在 `/Archive/` 子域里面存放。但是因为 `docs-rtd` 模板年久失修，我一直没维护，现在貌似是不能正常渲染的状态。

总之是打算在这个 blog 上使用谷歌统计一下访问，但是我发现无论我做什么他都无法识别，仿佛是我之前 fork 的另一个人的模板，他不起作用，或者直接 ignore 了这部分数据一样。很奇怪，我问了我的 GPT 很多次，总是得不到一个我满意的回复。

一直搞不出这个东西，就在这周末，或者说，发文的这天，我想，要不，干脆我重装一下好了。

说干就干，删掉现在的 repository，直接把 chirpy 的完整版源码[^fn1]fork 下来了。

## II. Some thing you need to fill in...

这种东西，你 fork 一次 fork 不明白，反反复复来上几次，就算看不懂代码也该知道怎么搞了。

总之是拉到本地，最开始是 `/config.yaml`，作为整个 blog 的核心配置文件，渲染构建都要以它为基准，这里就不附上整个文件，可以直接到我的代码库里去找。我提一些我觉得相对重要些的东西。

### 2.1 `config.yaml`

有一说一，我觉得如果你之前没部署过 `gh-pages` 的话，最好不要继续往下看，因为我这里不介绍入门方法，只介绍一些可能会踩坑的东西（呃呃，换句话说，这些是我踩的坑，不然我为什么起这个标题？）

下面是 `config.yaml` 的部分摘要：
``` yaml
...

# Web Analytics Settings
analytics:
  google:
    id: G-XXXXXXXXXX # 填写你的 Google Analytics ID

...

# CDN Setting
  # 原本作者(cotes)这里是写了一个链接的，但他这个意思是用一个外置的网页来存放你的页面里用到的文件
  # 显然你也不想用他的仓库里的文件（你也不知道cotes那有啥）。我现在还没有CDN，所以删去
  cdn: "" 

...

# Pictures
  # 主页上的大头像
  avatar: "/assets/img/rioavat.png"
  # 社交预览图……
  # 比如你把这个网站分享到某个地方（Twitter），它如果显示图片的话，就会变成这个图片
  social_preview_image: "assets/img/social-preview.png"

...

# Giscus options › https://giscus.app
giscus:
  repo: repokx/repokx.github.io # <GitHub用户名>/<仓库名>，管他呢，反正就左边我那样的格式
  repo_id: R_AbCdEfGhIj # 更换repo之后，此处需要更新
  category: Announcements # giscus推荐使用 Announcements
  category_id: DIC_AbCdEfGhIjKlMnOp # 更换repo之后，此处需要更新
# 在启用 giscus 之前，请确保已在对应的 repo 中启用 Discussions 功能

...
```
### 2.2 `assets`：资源库

字如其名，与其叫 assets，我觉得还不如叫 vault。我存东西写东西都得从这，每次用还得引用，下次直接在最顶上的介绍区加上 `img-path` 得了。

资源库，自然就是存放资源的位置，以 chirpy 为例，他的 assets tree 如下：
```shell
assets
    ├─css           # css 样式库
    ├─doc           # 我创建的，在这里放一些文档，比如 DFT-HW-1 里面附的 pdf
    ├─img           # 图片文件，默认的 avatar 似乎在这里
    │  └─favicons       # 字如其名，favorite icon，这里用于你网页在标签页的缩略图、图标一类
    ├─js            # JavaScript 文件库
    │  ├─data           # 一些数据文件
    │  └─dist           # 构建文件
    └─lib           # 第三方库
```
至于你真正要去注意的，应该是在存放和取用文件的时候，注意不要太随意。

存放的时候，可以按照博文的分类建一些文件夹。

取用的时候注意不要写绝对路径，也不要图省事只写类似 `/xxx.png` 这样的纯文件名路径，这事实上不是路径，只是文件名而已。最好写成 `/assets/img/xxx.png` 这样的路径，这样才不会出错。

### 2.3 `_data`：莫名其妙的数据文件夹

为啥叫莫名其妙，明明是数据文件夹，放的却是一些无关紧要的东西。`locales` 文件夹下面放的都是语言包，留下 zh-CN 和 en，剩下的删了得了； `origin` 倒是挺有用的，放了一些相对路径； `authors.yml`、`contact.yml`、`share.yml` 这些文件则是用来给一些小部件提供链接，因为需要更改一些数据，所以我提一嘴。

### 2.4 `_tabs`：标签页

这个文件夹下面放的都是一些 `.md` 文件，里面存放的是一些标签页的内容。比如 `about.md` 里面存放的是关于我的信息，`archive.md` 里面存放的是归档信息。你也可以自己新建一些 `.md`，不需要做额外的声明。格式从其他几个文件里抄就行。

对于 chirpy 来说，这些标签页位于主页的左侧导航栏，每个页面都有一个 `icon`，具体从哪儿找这些现成的 icon，可以去 FontAwesome[^fn2] 找一些现成的，你看着好看的，放里边就行。我建了一个 `external.md` 用来放一些外部链接，跟现有的 `about.md` 作区分。作为参考：
``` yml
---
# the default layout is 'page'  # 管他呢…… #实在是跟注释死绑定了，语法就语法吧
icon: fas fa-forward            # 一个看起来像是前进的图标
order: 5                        # 在导航栏中的顺序，配合其余几个标签页填写，当前位次 5
---
$^@$%#%$&##$                    # 这里是正文部分，可以写一些 markdown 语法

...

```

### 2.5 `_posts`：博文存放区

这个文件夹下面放的都是博文，你想怎么写，就怎么写。

不过最好明确一点，文件名需要包含日期，格式为 `YYYY-MM-DD-Title.md`，这样 Jekyll 才能正确识别和排序你的文章。

博文的开头部分需要以 `yml` 的格式嵌入一段元数据，至少需要包含 `title` 和 `date`，其他的可以根据需要添加，比如 `categories`、`tags` 等等。至于 `author`，如果你只有一个作者的话，可以省略不写，默认会使用 `_config.yml` 里面的 `author` 信息。

举个栗子，DFT-HW-1 这篇文章的开头是：
``` yml
---
title: UCAS DFT Homework 1                      # 标题（必填）
# description: >-                               # 描述，可选（你爱写不写）
author: repo                                    # 作者（留白默认为_config.yml中的author）
date: 2025-11-05 23:40:00 +0800                 # 日期时间（格式：YYYY-MM-DD HH:MM:SS ±TTTT）
categories: [Computational Physics, DFT]        # 分类
tags: [DFT, Hartree-Fork, TFD, Kohn-Sham, Exchange-Corrlation Functional, PW92]     # 标签（论文关键词.jpg）
# math: true                                    # 是否启用数学公式支持（Boolean）
# mermaid: true                                 # 是否启用流程图支持（Boolean）
# pin: false                                    # 是否置顶文章（Boolean）
# img_path:                                     # 图片路径前缀，文中所有的图片路径可以接在这后面，以减少重复
image:                                          # 博文封面图片，也作为整篇文章的头图
    path: /assets/img/Dirac-Cylinder.png        # 图片路径
    alt: 晶体的二维能带结构示意图，展示两个能带在布里渊区交汇处形成狄拉克锥的线性色散关系。 # 图片替代文本
---

## UCAS DFT Homework 1
张三李四王二麻子这五个人不好好睡觉半夜搁着写blog……
```
至于排版的艺术，之前在 NGA 有一篇非常详尽的文章，但是他是讲述 NGA 使用的 BBS 语法，在此处没有参考价值。
推荐浏览 cotes 的官方文档[^fn3]，里面有很多关于如何使用 markdown 语法的说明，加入到自己的 `_posts/templates` 目录下，随取随用。

## III. After fill, CHAOS EVERYWHERE

配置完毕，接下来就是构建和部署了。

事先问过了 GPT，不推送 commits 到 GitHub，他就不会自动部署 Github Pages。

### 3.1 `nodejs` + `npm`

搞完上面所有内容后，就是老生常谈的
``` shell
bundle install
bundle exec jekyll serve
```
看起来还好，打开 `http://localhost:4000`，唉，怎么不出图，怎么不加载toc？

再一看
``` shell
PS H:\Documents\GitHub\repokx.github.io> bundle exec jekyll serve
Configuration file: H:/Documents/GitHub/repokx.github.io/_config.yml
 Theme Config file: H:/Documents/GitHub/repokx.github.io/_config.yml
            Source: H:/Documents/GitHub/repokx.github.io
       Destination: H:/Documents/GitHub/repokx.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 8.801 seconds.
 Auto-regeneration: enabled for 'H:/Documents/GitHub/repokx.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
[2025-11-16 17:58:36] ERROR '/assets/js/dist/theme.min.js' not found.
[2025-11-16 17:58:38] ERROR '/assets/js/dist/home.min.js' not found.

... （此略若干 ERROR） ...

[2025-11-16 18:01:03] ERROR '/assets/js/dist/theme.min.js' not found.
[2025-11-16 18:01:03] ERROR '/assets/js/dist/post.min.js' not found.
```
我了个大草，我寻思我之前配置也没动过这些东西啊，咋就 not found 了呢？

还是问 GPT，发现是需要用 `npm` 对 JavaScript 构建之后，才会产生这些文件。正好有现成的 `nodejs` 环境，也装好了 `npm`，那就干呗。（仅展示部分输出）
``` shell
PS H:\Documents\GitHub\repokx.github.io> node -v
v22.14.0
PS H:\Documents\GitHub\repokx.github.io> npm -v
10.9.2
PS H:\Documents\GitHub\repokx.github.io> npm install
...
added 743 packages, and audited 944 packages in 2m
174 packages are looking for funding
  run `npm fund` for details
...
PS H:\Documents\GitHub\repokx.github.io> npm run build
> jekyll-theme-chirpy@1.8.3 build
> gulp build
...
[js]
[js] _javascript/pwa/sw.js → assets/js/dist/sw.min.js...
[js] created assets/js/dist/sw.min.js in 369ms
[js] npm run build:js exited with code 0
```
不管怎么说，反正 GPT 告诉我这样就完事儿了，重新运行 `bundle exec jekyll serve`，本地部署成功，然后 push 就完了呗。

要是真这么短我也就不用水这篇了，部署出来的网页，只有短短的一行：
``` html
--- layout: home # Index page ---
```
what the fuck？？

### 3.2 Github Actions

这就尴尬了，我本地跑起来没问题，推到 GitHub 上就不行。

GPT 开始胡搅蛮缠了，感觉我们都没找到问题在哪儿，他以为我藏了东西，比如我没把本地构建好的 `_site` 文件夹 push 上去。但是事实是，我本身就不应该 push 这个文件夹上去的，理论上讲，我本地就算不 build，应该会有个玩意儿帮我 build。

就这么点儿事儿，我俩一人一狗愣是想了半天才想到我 fork 之后还没配置 Pages。

给我气笑了，我直接去 `Settings` 里面找 `Pages`，把里面的 `Build and deployment` 选项改成 `GitHub Actions`，然后选 `Save`。这才完事儿，这才能push上去

但是显然，如果就这么点儿事儿，我确实不至于写这么多东西铺垫，还有高手！

push 之后的第一次 actions，不出意外当然还是要出意外：
``` shell
For the Images check, the following failures were found:
* At _site/posts/install-yunzaibot/index.html:1:
  internal image /node.jpg does not exist

... 此略几条类似报错 ...

* At _site/posts/rebuild-blog/index.html:93:
  internal image /push.png does not exist
For the Links > Internal check, the following failures were found:
* At _site/posts/install-yunzaibot/index.html:1:
  internally linking to /node.jpg, which does not exist

... 此略几条类似报错 ...

* At _site/posts/rebuild-blog/index.html:93:
  internally linking to /push.png, which does not exist
HTML-Proofer found 10 failures!
Error: Process completed with exit code 1.
```
这就很尴尬了，显然是我之前提到的图片路径问题，我在博文里面写的路径是 `/node.jpg` 这种形式，结果他找不到。

要不说上面我就强调了路径问题呢！在这儿踩的坑！

去他的，我直接把老文章删了，这一堆玩意儿改起来又没啥意思，以前写的也没啥营养，干脆就这样。

然后推送 action，哈哈，寄！

### 3.3 `page-deploy.yml` + `husky`

我不得不承认，在写这篇文章的时候，我的 `vscode Copilot` 一直在跳 “成功了！”、“搞定了！” 之类的提示，但是她完全猜错了喵，还是那句话，要是就这么点儿破事儿，我至于这么大费周章？

> 新问题：切换到actions之后，她运行了两次CI，但是没有page-deploy

我这么问 GPT，我们面面相觑，她觉得我没有配置 `page-deploy.yml`，所以没有部署。

但我寻思我好像见过这个，但是我又不确定。

打开文件树，作者把这玩意儿藏到 `.github/workflows/starter` 下面了，而不是直接放在 `.github/workflows/` 下面。导致他不识别。

那我改过来就行了呗！ 然后就运行，爽！——————

笑死，commit 也失败了

迅速查了一下，cotes 在源文件里加了个 `husky`，这个东西是用来在 commit 之前检查代码格式的，我必须遵循特定的书写规则才可以发布。。。 好吧，那我就照着改吧。

终于，终于，终于！——————————
``` yaml
Run bundle exec jekyll b -d "_site"
Configuration file: /home/runner/work/repokx.github.io/repokx.github.io/_config.yml
 Theme Config file: /home/runner/work/repokx.github.io/repokx.github.io/_config.yml
            Source: /home/runner/work/repokx.github.io/repokx.github.io
       Destination: /home/runner/work/repokx.github.io/repokx.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
Error: Can't find stylesheet to import.
  ╷
1 │ @use 'vendors/bootstrap';
  │ ^^^^^^^^^^^^^^^^^^^^^^^^
  ╵
  main.bundle.scss 1:1                                                                         @use
  /home/runner/work/repokx.github.io/repokx.github.io/assets/css/jekyll-theme-chirpy.scss 2:1  root stylesheet 
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'assets/css/jekyll-theme-chirpy.scss':
                    Can't find stylesheet to import.
                    ------------------------------------------------
      Jekyll 4.4.1   Please append `--trace` to the `build` command 
                     for any additional information or backtrace. 
                    ------------------------------------------------
/home/runner/work/repokx.github.io/repokx.github.io/vendor/bundle/ruby/3.3.0/gems/jekyll-sass-converter-3.1.0/lib/jekyll/converters/scss.rb:181:in `rescue in convert': Can't find stylesheet to import. (Jekyll::Converters::Scss::SyntaxError)

          raise SyntaxError, e.message
                ^^^^^^^^^^^^^^^^^^^^^^
	from /home/runner/work/repokx.github.io/repokx.github.io/vendor/bundle/ruby/3.3.0/gems/jekyll-sass-converter-3.1.0/lib/jekyll/converters/scss.rb:162:in `convert'
	from /home/runner/work/repokx.github.io/repokx.github.io/vendor/bundle/ruby/3.3.0/gems/jekyll-4.4.1/lib/jekyll/renderer.rb:105:in `block in convert'
	from /home/runner/work/repokx.github.io/repokx.github.io/vendor/bundle/ruby/3.3.0/gems/jekyll-4.4.1/lib/jekyll/renderer.rb:104:in `each'

    ... 此略若干行 ...

	from /opt/hostedtoolcache/Ruby/3.3.10/x64/lib/ruby/gems/3.3.0/gems/bundler-2.5.22/exe/bundle:20:in `<top (required)>'
	from /opt/hostedtoolcache/Ruby/3.3.10/x64/bin/bundle:25:in `load'
	from /opt/hostedtoolcache/Ruby/3.3.10/x64/bin/bundle:25:in `<main>'
Error: Process completed with exit code 1.
```
WHAT THE F**K？？？

### 3.4 `bootstrap`

又是一个莫名其妙的错误，看来是 `scss` 文件里面引用的 `bootstrap` 库找不到了。

但是我感觉。。。这些文件我似曾相识，又不知道在哪儿见过……

没招了，GPT 已经开始说胡话了，我去 cotes 的代码库里找有没有 Discussions 或者 Issues，果然找到了一个类似的问题[^fn4]，里面讨论的字里行间，找到一个解决方案，就一句话[^fn5]。
> **Cotes writes:**
> 
> _If you forked from the source project (there will be gemspec in the Gemfile of your site), merge the latest upstream tags into your Jekyll site to complete the upgrade. The merge may conflict with your local modifications. Be patient and careful when resolving these conflicts._
> 
> _JS distribution files have been removed since v5.6.0, and Bootstrap CSS has been lean since v7.0.0. For future upgrades, compile the CSS/JS files yourself:_
> 
> `npm run build`
>
> _Then add them to your repository files:_
> 
> `git add assets/js/dist _sass/vendors -f`

FINALLY!!!!!

总之就是各种丢东西，找到他们，塞回去，甭管怎么塞，反正最后成了！

~~（ps. 我感觉这会儿我的写作助手 Copilot 比我还高兴，她已经迫不及待帮我庆祝了）~~

## IV. Epilogue. Stay over night...

16 号晚上 23:31，我从教二走出来，看着手机上已经部署并渲染成功的博客页面，追着前面一个同样刚熬完夜，顶着凛冽寒风走在落叶堆中的女同学，心中温热，手脚冰凉，太冷了，实在太冷了

至少我赶在寝室大门关闭前溜进了宿舍，在舍友的呼噜声和同门半夜两年还睡不着给我发消息的 senario 下，现在是 17 号凌晨 3:55 分，我基本宣告这次部署大获全胜，并且水了一篇你现在正在看的文章。

人生也许就是这样，虽然说着不熬夜，但最后还是熬到四点。奈何写这种东西确实上瘾，就像当时通宵给 Blue Archive 写攻略一样，不知疲倦，满怀热情。

就是如果我早点开空调就好了，我都快写完了才发现自己冻得发抖，不过没关系，反正明天也不用上课。

（ps. 不用上课这句话是 Copilot 帮我写的，我现在很惊讶她是怎么知道我没课的，她在我宿舍装摄像头了？啊我草这 Copilot 也太坏了）

总之，到这里为止，我要睡觉了，所以
``` shell
git add .
git commit -m "docs: re-structure Deploy Chirpy blog, then fill it with my cum"
git push
```
让我听完这首 《栞》 covered by Taki - 林鼓子
``` text
...

桜散る桜散る お別れの時間がきて
「ちょっといたい もっといたいずっといたいのにな」

...
```
{% include embed/bilibili.html id='BV1Js4y1J7TE' %}

晚安，捞翔。

## Reference
[^fn1]: [https://github.com/cotes2020/jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)
[^fn2]: [FontAwesome](https://fontawesome.com/icons)
[^fn3]: [Chirpy. Text and Typography](https://chirpy.cotes.page/posts/text-and-typography/)
[^fn4]: [Chirpy Repository Discussion No.1809](https://github.com/cotes2020/jekyll-theme-chirpy/discussions/1809)
[^fn5]: [Cotes. Starter Upgrade-Guide](https://github.com/cotes2020/jekyll-theme-chirpy/wiki/Upgrade-Guide)