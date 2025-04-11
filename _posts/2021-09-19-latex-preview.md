---
title: LaTeX 初探
date: 2021-09-19 15:00:00 +0800
categories: [研究, 工具]
tags: [LaTeX]
author: repo
# math: true 
# mermaid: true
# pin: false 
# img_path: /src/
# image:
#     path: 
#     alt: 
---

### A. Introduction

Latex 在文章排版中有着极其重要的地位，之前借过刘海洋老师的《Latex 入门》这本书，看过但是没有看明白，这次从网上找到了 pdf 版，想起了以前做过的《勾股定理》这篇文章，今天复现了一下，发现效果不错，代码与结果附下：

### B. Latex Code

#### 1. main.tex 文件主体

```latex
\documentclass[UTF8,a6paper]{ctexart}   % documentclass为对文章整体的定义，ctexart指的是中文版的文章
\usepackage{graphicx}                   % 调用插图包
\usepackage{float}                      % 调用浮动体，作用于图片和表格区块
\usepackage{amsmath}                    % 排版数学符号与公式的包
\usepackage{geometry}                   % 设置页面大小与页边距，详细内容见下
\geometry{a6paper,centering,scale=0.8}  % A6纸张，居中，scale为放缩因子
\usepackage[format=hang,font=small,textfont=it]{caption}    % caption：图表标题包
\usepackage[nottoc]{tocbibind}          % 在目录中加入目录项本身，参考文献，索引等项目
\newtheorem{thm}{定理}                  % 对后文中的定理区块作预定义
\newenvironment{myquote}                % 自定义引用文本的特殊格式，后文中可以直接调用这种文本
    {\begin{quote}\kaishu\zihao{-5}}    % 楷书 字号5
    {\end{quote}}
\newcommand\degree{^\circ}              % latex 中没有给“度数”单独定义，此处预定义度数为degree
\title{\heiti 杂谈勾股定理}              % 标题行
\author{\kaishu 张三}                   % 作者行
\date{\today}                           % 日期行，today 为关键字
\bibliographystyle{plain}               % 参考文献的格式，plain为标准格式

\begin{document}                        % 文章主体内容

    \maketitle                          % 上文中预定义的标题区块（title/author/date...）将在此处显示

    \begin{abstract}                    % 摘要必须位于 title 之后
        这是一篇关于勾股定理的小短文。
    \end{abstract}

    \tableofcontents                    % 目录插入于此处

    \newpage                            % 强制换页

    \section{勾股定理在古代}             % 分章节，此处为第一章，
    \label{sec:ancient}                 % 章节标签名，方便引用
        西方称勾股定理为毕达哥拉斯定理，将勾股定理的发现归功于公元前 6 世纪的毕达哥拉斯学派 \cite{Kline}。该学派得到了一个法则，可以求出可拍成直角三角形三边的三元数组。毕达哥拉斯学派没有书面著作，该定理的严格表述和证明则见于欧几里得\footnote{欧几里得，约公元前 330--275 年。}《几何原本》的命题 47：“直角三角形斜边上的正方形等于两直角边上的两个正方形之和。”证明是用面积做的。\par
        % cite 为注释内容，花括号为注释题目。footnote 为脚注，默认本页底端。
        我国《周髀算经》载商高（约公元前 12 世纪）答周公问：

        \begin{myquote}                 % 预定义的引用内容格式，特化为 myquote
            勾广三，股修四，径隅五。
        \end{myquote}                   % quote 不会改变内容，只起到内容单独分行，增加缩进与上下间距的作用，其他内容需要预定义或者临时定义。

        又载陈子（约公元前 7--6 世纪）答荣方问：

        \begin{myquote}
            若求邪至日者，以日下为勾，日高为股，勾股各自乘，并而开方除之，得邪至日。
        \end{myquote}

        都较古希腊更早。后者已经明确道出勾股定理的一般形式。图 \ref{fig:xiantu} 是我国古代对勾股定理的一种证明 \cite{quanjing}。
        % ref 引用内容，可以引用公式、章节、等等任何已经加 label 的区块

        \begin{figure}[ht]              % 图像区块
            \centering                  % 居中
            \includegraphics[width=3cm]{xiantu.png}
            \caption{宋赵爽在《周髀算经》注中作的弦图（仿制），该图给出了勾股定理的一个极具对称美的证明。}      % caption为图标标题、描述
            \label{fig:xiantu}          % 设置标签，方便引用
        \end{figure}

    \section{勾股定理的近代形式}         % new section
        勾股定理可以用现代语言表述如下：

        \begin{thm}[勾股定理]           % 定理区块，方括号为定理名称
            直角三角形斜边的平方等于两腰的平方和。\par
            可以用符号语言表述为：设直角三角形 $ ABC $，其中 $ \angle C = 90\degree $，则有
            \begin{equation}\label{eq:gougu}
                AB^2 = BC^2 + AC^2
            \end{equation}
        \end{thm}

        满足式 \eqref{eq:gougu} 的整数称为\emph{勾股数}。第 1 节所说毕达哥拉斯学派得到的三元数组就是勾股数。下表列出一些较小的勾股数：
        % eqref 公式交叉引用
        % emph 突出强调 emphasis

        \begin{table}[H]
            \begin{tabular}{|rrr|}      % 三列，右对齐，一列前/三列后有竖线分隔
                \hline                  % 横线
                直角边 $a$ & 直角边 $b$ & 斜边 $c$ \\   % “&” 分列， “\\” 分行
                \hline                  % 横线，分割标题栏
                3 &   4 &   5 \\
                5 &  12 &  13 \\
                \hline
            \end{tabular}%
            \qquad                      % 空格，宽度两个M
            ($a^2 + b^2 = c^2$)
        \end{table}
        
    \nocite{Shiye}                      % 未展示ID为shiye的文献名的引用内容
    \bibliography{math}                 % 参考文献，来自文档 math.bib
\end{document}
```

#### 2. math.bib 参考文献

```bib
% This file was created with JabRef 2.6.
% Encoding: UTF8

@BOOK{Kline,
    title = {古今数学思想},
    publisher = {上海科学技术出版社},
    year = {2002},
    author = {克莱因}
}

@ARTICLE{quanjing,
    author = {曲安京},
    title = {商高、赵爽与刘徽关于勾股定理的证明},
    journal = {数学传播},
    year = {1998},
    volume = {20},
    number = {3}
}

@BOOK{Shiye,
    title = {几何的有名定理},
    publisher = {上海科学技术出版社},
    year = {1986},
    author = {矢野健太郎}
}
```

### C. 生成效果

![gougu_1](https://z3.ax1x.com/2021/09/19/43BWYF.png)_**图 1**  《杂谈勾股定理》part 1_

![gougu_2](https://z3.ax1x.com/2021/09/19/43BRFU.png)_**图 2**  《杂谈勾股定理》part 2_
