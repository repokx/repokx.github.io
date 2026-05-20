---
title: UCAS DFT Homework 2 (建设中)
# description: >-
author: repo
date: 2025-11-22 17:54:00 +0800
categories: [Computational Physics, DFT]
tags: [DFT]
# math: true
# mermaid: true
# pin: false 
# img_path: 
# image:
#     path: /assets/img/xxx.png
#     alt: xxx
---

## UCAS DFT Homework 2

2025 ucas dft homework 2, written by repo, using LaTeX to compile.

> this HW file is unfinished, COPY BEFORE YOU KNOW WHAT YOU ARE DOING.
{: .prompt-warning }

<!-- <div style="border: 1px solid #eaeaea; border-radius: 6px; padding: 10px; margin: 20px 0;">
  <h3 style="margin-top: 0;">📄 UCAS DFT Homework 1</h3>
  <embed 
    src="/assets/doc/UCAS-DFT-HW1.pdf" 
    type="application/pdf" 
    width="100%" 
    height="800px"
    style="border-radius: 6px;"
  />
  <p style="margin-top: 10px;">
    👉 如果无法预览，请点击这里下载： 
    <a href="/assets/doc/UCAS-DFT-HW1.pdf" target="_blank">UCAS-DFT-HW1.pdf</a>
  </p>
</div> -->

```latex
\documentclass[10pt,a4paper]{ctexart} % 中文环境，若全英文可改为 article

% ======= 基本宏包 =======
\usepackage{amsmath, amssymb, amsfonts} % 数学公式
\usepackage{graphicx}                   % 插图
\usepackage{geometry}                   % 页边距
\usepackage{hyperref}                   % 超链接（可选）
\usepackage{siunitx}                    % 科学计数和单位（可选）
\usepackage{float}                      % 控制图表浮动位置
\usepackage{xcolor}                     % 颜色支持（可选）
\usepackage{titlesec}
\titleformat{\subsection}[block]
{\normalfont\large\bfseries}
{\thesubsection}{1em}{\hspace*{2em}} % 在标题文本前硬塞 2em
\usepackage{braket} % 提供 \bra, \ket, \braket 等
\usepackage{mdframed}
    \newmdenv[
        backgroundcolor=blue!5,
        linecolor=blue,
        linewidth=1pt
    ]{bluebox}
\newcommand{\blue}[1]{\textcolor{blue}{#1}}
\newcommand{\red}[1]{\textcolor{red}{#1}}


% ======= 页面设置 =======
\geometry{margin=2.5cm}
\setlength{\parindent}{2em}  % 段首缩进
\setlength{\parskip}{0.5em}  % 段间距
\ctexset{
	section = {
		format = \zihao{-4}\bfseries,  % 调整字号和加粗，可改成 \zihao{-4} 更小
		name = {},                    % 不要“第X节”
		number = \arabic{section},    % 节号样式
		beforeskip = 1ex,            % 前距
		afterskip = 0.5ex,            % 后距
		indent = 0pt,                 % 不缩进
		aftername = \quad,            % 章节号后空格
	}
}



% ======= 文档开始 =======
\begin{document}

\title{《密度泛函理论及应用》习题2}
\author{unknown}
\date{\today}
\maketitle

\section{Question 1}
\begin{bluebox}
说明赝势方法的理论基础，并列举构造模守恒赝势的四个条件
\end{bluebox}
    \subsection{理论基础}

    \subsection{构造模守恒赝势的四个条件}
        \begin{enumerate}
            \item \blue{价电子的}赝波函数在原子核附近没有
                  径向节点{\small\blue{（与 r 轴的交点）}}：以减少计算量
            \item 在截断半径外，对给定角动量的\blue{价电子}
                  赝波函数与全电子的\blue{价电子}\red{径向}波函数相同
                  \[R_l^{PP}(r) = R_l^{AE}(r) \qquad r > r_c\]
            \item 在截断半径内，赝波函数与全电子波函数给出的 \red{总电荷数}
                  要相同 \quad \blue{[模守恒特有条件]}
                  \[\int_0^{r_c}\left|R_l^{PP}(r)\right|^2r^2dr
                    = \int_0^{r_c}\left|R_l^{AE}(r)\right|^2r^2dr\]
            \item 对给定角动量的赝波函数与全电子波函数要有
                  \blue{相同的\red{价电子}本征值}
                  \[E_l^{PP} = E_l^{AE}\]
        \end{enumerate}


\section{Question 2}
\begin{bluebox}
使用赝势方法为什么需要核修正
\end{bluebox}

\section{Question 3}
\begin{bluebox}
写出平面波基组下的 Kohn-Sham 方程，详细说明其中每一项的物理意义
\end{bluebox}
    \subsection{平面波基组下的 Kohn-Sham 方程}
        \begin{equation}
            \sum_{G'}\left[\frac{1}{2}|k+G'|^2\delta_{GG'}
            + V_{kGG'}^{eff}\right]\Phi_j(G') = \epsilon_j\Phi_j(G)
        \end{equation}
        where,
        \begin{equation}
            V_{kGG'}^{eff} = V_{coul}(G-G') + \hat{V_\mathrm{XC}}(G-G')
            + S(G'-G)\left(V^{core}(G-G') + \sum_\ell V_{\ell,k;G,G'}^{NL}\right)
        \end{equation}
    \subsection{各项物理意义}
        \begin{enumerate}
            \item $\frac{1}{2}|k+G'|^2\delta_{GG'}$ 为动能项：\\
                  平面波基底动能为 $T = \frac{1}{2}|k+G'|^2$，\\
                  而动能算符 $-\frac{1}{2}\nabla^2$ 在平面波下是对角的，
                  所以有 $\delta_{GG'}$
            \item $V_{kGG'}^{eff}$ 为有效势的矩阵元，可以分为4项
            \begin{enumerate}
                \item $V_{\mathrm{coul}}(G-G')$ 为库伦项（Hartree 势） \\
                    来自电子密度 $n(r)$ 产生的 Hartree potential：
                    \[V_H(r)=\int\frac{n(r')}{|r-r'|}\,dr'\]
                    傅里叶变换后得到 $V_H(G-G')$，表示电子–电子平均库伦排斥。
                \item $\hat{V}_{\mathrm{xc}}(G-G')$ 为交换–关联势 \\
                    来自交换关联泛函的变分：
                    \[V_{\mathrm{xc}}(r)=\frac{\delta E_{\mathrm{xc}}[n]}{\delta n(r)}\]
                    在平面波表象下变为矩阵元 $\hat{V}_{\mathrm{xc}}(G-G')$，
                    描述量子多体效应（交换、动相关、自旋极化等），
                    是 DFT 中最关键的项之一。
                \item $S(G'-G)$ 为重叠矩阵 \\
                    数学形式与晶体学结构因子的傅里叶展开相似，
                    但物理意义完全不同。此项源于超软赝势/PAW 的基底非正交性修正，
                    或补偿电荷项的傅里叶系数。
                \item $V^{\mathrm{core}}(G-G')$ 为外势中的局域部分（local PP） \\
                    近似核库仑势以及 core-electron 屏蔽后的“光滑核势”，
                    对价电子给出径向对称的局域吸引势。
                \item $\sum_\ell V^{\mathrm{NL}}_{\ell,k;G,G'}$ 为外势中的非局域部分（nonlocal PP） \\
                    通过投影子（projectors）编码原子在不同角动量通道
                    下的散射特征，是赝势最核心的修正项。
            \end{enumerate}
        \end{enumerate}

\section{Question 4}
\begin{bluebox}
石墨烯是二维六角晶格，如果晶格基矢 $a_1$，$a_2$ 之间的夹角是120°，
写出以倒格矢 $b_1$，$b_2$ 为单位的 3×3 MP 抽样的 k 点坐标及权重
\end{bluebox}

\section{Question 5}
\begin{bluebox}
原子受力分为 Hellmann-Feynman 力和 Pulay 力，说明这两种受力的来源
\end{bluebox}

\section{Question 6}
\begin{bluebox}
说明 Car-Parrinello 分子动力学的原理，并画出计算流程图
\end{bluebox}

\section{Question 7}
\begin{bluebox}
证明高斯型轨道下双中心积分可以化简为单中心积分
\end{bluebox}

\section{Question 8}
\begin{bluebox}
中性原子势包含哪些项？为什么中性原子势是短程的？
\end{bluebox}

\section{Question 9}
\begin{bluebox}
写出原子轨道基组下的 Kohn-Sham 方程，详细说明其中每一项的物理意义
\end{bluebox}

\section{Question 10}
\begin{bluebox}
列出课题组常用的第一性原理计算模拟软件，简单说明其理论方法和主要功能等特性
\end{bluebox}

\end{document}
```

