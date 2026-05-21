---
title: UCAS DFT Homework 1
# description: >-
author: repo
date: 2025-11-05 23:40:00 +0800
categories: [Computational Physics, DFT]
tags: [DFT]
# math: true
# mermaid: true
# pin: false 
# img_path: 
image:
    path: /assets/img/Dirac-Cylinder.png
    alt: 晶体的二维能带结构示意图，展示两个能带在布里渊区交汇处形成狄拉克锥的线性色散关系。
---

## UCAS DFT Homework 1

2025 ucas dft homework 1, written by repo, using LaTeX to compile.

正如标题所见，这是中国科学院大学2025年秋季学期的 `Density Functional Theory` 课程的第一次作业。

说实话，我认为课程讲授的不是特别精彩，但是来自 `iop` 的这位老师对于几乎每一个公式都做了相当详尽的推导，包括但不限于：`Born-Oppenheimer Approximation` or commonly used `Adiabatic Approximation`、`Hartree/Hartree-Fork Approximation`、`Thomas-Fermi-Dirac Theory`、`Hohenberg-Kohn Theorems`、`Kohn-Sham Equations`、`Local-Density Approximation`、`Pseudo-Potentials`。

周五上午早八，一路在黑板上推公式，一直推到11点。每次上他的课我都觉得是一种享受，一种看着结果一步步算出来的安心感。虽然每次上课都要写超级多的公式，但是说实话，我完全不觉得累，虽然是这么一个对于工科的我硬到不能再硬的课，但他的这种讲授方式确实可以在我的记忆里停留一段时间，也许。

本文的写作，一定程度上是作为 `latex` 的练习使用的，不枉我敲这么多公式，觉得发到博客上来也不错，供君参考。

内容可能有错误，我就在此直言了，因为部分习题实际上是由 `AI(GPT)` 生成的，对于 `DFT` 这门课程的学习，我也是一知半解，目前还没能做到熟稔于心。

等我学艺更精通一些之后，可能会回来补全。

<div style="border: 1px solid #eaeaea; border-radius: 6px; padding: 10px; margin: 20px 0;">
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
</div>


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

\title{《密度泛函理论及应用》习题1}
\author{hidden}
\date{\today}
\maketitle

\section{阅读 “A half century of density functional theory”文章，翻译几段你认为有意义的或重要的话}
\begin{quote}
	In 1929 Paul Dirac made a famous announcement: The general theory of quantum mechanics is now almost complete.... The underlying physical laws necessary for the mathematical theory of a large part of physics and the whole of chemistry are thus completely known.... It therefore becomes desirable that approximate practical methods of applying quantum mechanics should be developed, which can lead to an explanation of the main features of complex atomic systems without too much computation.'
\end{quote}

1929年，保罗·狄拉克发表了一篇著名的声明：“量子力学的一般理论现在几乎已经完成……物理学的大部分和整个化学所需的基本物理定律因此被完全了解……因此，有必要开发近似的实用方法来应用量子力学，这些方法可以在不进行过多计算的情况下解释复杂原子系统的主要特征。”
\begin{quote}
	It is important to appreciate the revolutionary nature of that question. In the Schrödinger equation, the ionic potential $v_{ext}(r)$ is the only term that distinguishes one alloy from another. That potential determines the wavefunction, which in turn determines the electron density and the total energy. The energy is thus a functional of $v_{ext}(r)$. Kohn contemplated a radical inversion of that thinking. Is it possible that the total energy depends only on the electron density $n(r)$? Years earlier Llewellyn Thomas and Enrico Fermi had proposed approximate theories of the total energy where that was the case, but no one had seriously suggested that the exact total energy of any many-electron system could be a functional of the electron density alone. If it were true, knowledge of $n(r)$ was sufficient to determine the external potential, the many-particle wavefunction, and all the ground-state properties—even the Green functions of many-body theory! That was a very deep question. Kohn realized he wasn’t doing alloy theory anymore.
\end{quote}

理解这个问题的革命性本质是很重要的。在薛定谔方程中，离子势$v_{ext}(r)$是区分一种合金与另一种合金的唯一项。该势决定了波函数，而波函数又决定了电子密度和总能量。因此，总能量是$v_{ext}(r)$的泛函。科恩考虑了一种彻底颠倒这种思维方式的可能性。总能量是否仅依赖于电子密度$n(r)$？多年前，Llewellyn Thomas和Enrico Fermi提出了总能量的近似理论，但没有人认真建议任何多电子系统的精确总能量可以仅仅是电子密度的泛函。如果这是真的，那么对$n(r)$的了解就足以确定外部势、多粒子波函数以及所有基态性质——甚至是多体理论的格林函数！这是一个非常深刻的问题。科恩意识到他不再是在做合金理论了。
\begin{quote}
	General questions require general solution methods, and Kohn was particularly well trained in one class of them: the variational methods of mathematical physics. Such methods were a particular specialty of the department of applied mathematics at the University of Toronto, where Kohn had earned his BA and MA degrees. The local experts there were chairperson John Lighton Synge and two of Kohn’s mentors, Alexander Weinstein and Arthur Stevenson. Another virtuoso of variational methods, Julian Schwinger, supervised his Harvard PhD thesis, which introduces what is today called the Kohn variational principle. From the reminiscence paper, or from any technical review of DFT, one can learn how variational methods are central to the proof of the Hohenberg–Kohn theorem and to the derivation of the Kohn–Sham equations.
\end{quote}

一般性的问题需要一般性的解决方法，而科恩在其中一类方法上受过特别好的训练：数学物理的变分方法。这些方法是多伦多大学应用数学系的一个特殊专业，科恩在那里获得了他的学士和硕士学位。当地的专家有系主任John Lighton Synge和科恩的两位导师Alexander Weinstein和Arthur Stevenson。另一位变分方法的大师Julian Schwinger监督了他的哈佛博士论文，该论文引入了今天称为Kohn变分原理的方法。从回忆录论文或任何关于DFT的技术评论中，人们可以了解到变分方法在Hohenberg-Kohn定理的证明和Kohn-Sham方程的推导中是多么重要。

\section{写出静电场下单个氢气分子的精确哈密顿量（使用原子单位）}
\begin{align*}
	\hat{H} & = \hat{T_n} + \hat{T_e} + \hat{V_{nn}} + \hat{V_{ee}} + \hat{V_{en}} + \hat{V_{ext}}                                                                                                                                                                                                                \\
	        & = \sum_\alpha -\frac{1}{2M_\alpha} \nabla_\alpha^2 - \sum_i \frac{1}{2} \nabla_i^2 + \sum_{\alpha < \beta} \frac{Z_\alpha Z_\beta}{\left|R_\alpha - R_\beta\right|} + \sum_{i < j} \frac{1}{\left|r_i - R_j\right|} + \sum_{\alpha, i} \frac{-Z_\alpha}{\left| R_\alpha - r_i \right|} - E\cdot \mu \\
	        & = -\frac{1}{2M_p}(\nabla_{R_1}^2 + \nabla_{R_2}^2) - \frac{1}{2}(\nabla_{r_1}^2 + \nabla_{r_2}^2) + \frac{1}{\left| R_1 - R_2 \right|} + \frac{1}{\left| r_1 - r_2 \right|}                                                                                                                         \\
	        & \quad - (\frac{1}{\left| R_1 - r_1 \right|} + \frac{1}{\left| R_1 - r_2 \right|} + \frac{1}{\left| R_2 - r_1 \right|} + \frac{1}{\left| R_2 - r_2 \right|}) + E(r_1 + r_2) - E(R_1 + R_2)                                                                                                           \\[-1mm]
	        & \textcolor{gray}{\text{注：此处的 $E$ 为外电场强度。}}                                                                                                                                                                                                                                  
\end{align*}

\section{把上一题中的哈密顿量，利用绝热近似分成原子核部分和电子部分}  
\subsection*{电子部分}
\begin{align*}
	\hat{H_{el}} & = \hat{T_e} + \hat{U_{ee}} + \hat{V_{en}} + \hat{V_{ext}}                                                                                                     \\
	             & = -\frac{1}{2}(\nabla_{r_1}^2 + \nabla_{r_2}^2) - \sum_{i=1}^2\sum_{j=1}^2 \frac{1}{\left|R_i - r_j\right|} + \frac{1}{\left|r_1 - r_2\right|} + E(r_1 + r_2) 
\end{align*}
\subsection*{原子核部分}
\begin{align*}
	\hat{H_{nl}} & = \hat{T_n} + \hat{V_{nn}} + \hat{V_{ext}}                                                             \\
	             & = -\frac{1}{2M_p}(\nabla_{R_1}^2 + \nabla_{R_2}^2) + \frac{1}{\left| R_1 - R_2 \right|} - E(R_1 + R_2) 
\end{align*}

\section{在 Hartree--Fock 近似下，推导\texorpdfstring{$\langle \Psi(r_1,r_2)\vert \dfrac{1}{\lvert r_1 - r_2\rvert} \vert \Psi(r_1,r_2)\rangle$}{<Psi(r1,r2) | 1/|r1 - r2| | Psi(r1,r2)>}的表达式}
\begin{align*}
	  & \langle \Psi(r_1,r_2)\vert \dfrac{1}{\lvert r_1 - r_2\rvert} \vert \Psi(r_1,r_2)\rangle                                                                                                                                               \\
	  & = \frac{1}{2} \int (\phi_1(r_1)\phi_2(r_2) - \phi_2(r_1)\phi_1(r_2))^* \frac{1}{\lvert r_1 - r_2 \rvert} (\phi_1(r_1)\phi_2(r_2) - \phi_2(r_1)\phi_1(r_2))dr_1 dr_2                                                                   \\
	  & = \frac{1}{2} \int \phi_1^*(r_1)\phi_2^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_1(r_1)\phi_2(r_2)dr_1 dr_2 - \frac{1}{2} \int \phi_1^*(r_1)\phi_2^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_2(r_1)\phi_1(r_2)dr_1 dr_2       \\
	  & \quad - \frac{1}{2} \int \phi_2^*(r_1)\phi_1^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_1(r_1)\phi_2(r_2)dr_1 dr_2 + \frac{1}{2} \int \phi_2^*(r_1)\phi_1^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_2(r_1)\phi_1(r_2)dr_1 dr_2 \\
	  & = \frac{1}{2} \int \phi_1^*(r)\phi_2^*(r') \frac{1}{\lvert r - r' \rvert} \phi_1(r)\phi_2(r')drdr' - \frac{1}{2} \int \phi_1^*(r)\phi_2^*(r') \frac{1}{\lvert r - r' \rvert} \phi_2(r)\phi_1(r')drdr'                                 \\
	  & \quad - \frac{1}{2} \int \phi_2^*(r')\phi_1^*(r) \frac{1}{\lvert r' - r \rvert} \phi_1(r')\phi_2(r)drdr' + \frac{1}{2} \int \phi_2^*(r')\phi_1^*(r) \frac{1}{\lvert r' - r \rvert} \phi_2(r')\phi_1(r)drdr'                           \\
	  & = \int \frac{\phi_1^*(r)\phi_1(r)\phi_2^*(r')\phi_2(r')}{\lvert r - r' \rvert}drdr' - \int \frac{\phi_1^*(r)\phi_1(r')\phi_2^*(r')\phi_2(r)}{\lvert r - r' \rvert}drdr'                                                               
\end{align*}

\section{在Hartree-Fock近似下，说明关联能的来源及其定义，说明关联能不会大于零，并列举解决电子关联问题的常用方法}

所谓的“关联”指波函数不能写为单粒子波函数的乘积形式：
\[ \Phi(r_1,r_2,\ldots，r_n) \neq \phi(r_1)\phi(r_2)\cdots\phi(r_n)\]

因为使用单电子波函数的乘积不是系统的基态，计算出来的总能量比真实基态的总能量高，它们之间差值就是关联能。
\[E_c = \langle H\rangle - \langle H\rangle_{HF} \leq 0\]

常用的修正电子的关联相互作用的方法有：
Configuration Interaction (CI), Coupled Cluster (CC), M{\o}ller-Plesset Perturbation Theory ...

\section{利用变分原理推导Hartree-Fock方法交换积分的变分导数}
\begin{align*}
	\delta\left[\frac{1}{2}\sum_{ij}K_{ij}\right] & = \frac{1}{2}\delta\left[\sum_{ij}\iint\phi_i^*(r_1)\phi_j^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_i(r_2)\phi_j(r_1)dr_1 dr_2\right] \\
	                                              & = \frac{1}{2}\sum_j\iint\delta\phi_a^*(r_1)\phi_j^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_a(r_2)\phi_j(r_1)dr_1 dr_2                 \\
	                                              & \quad + \frac{1}{2}\sum_i\iint\delta\phi_i^*(r_1)\phi_a^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_i(r_2)\phi_a(r_1)dr_1 dr_2           \\
	                                              & = \sum_i\iint\delta\phi_a^*(r_1)\phi_i^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_a(r_2)\phi_i(r_1)dr_1 dr_2                            
\end{align*}
\begin{align*}
	\frac{\delta\left[\frac{1}{2}\sum_{ij}K_{ij}\right]}{\delta\phi_a^*(r_1)} & = \sum_i\iint\phi_i^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_a(r_2)\phi_i(r_1)dr_1 dr_2 \\
	                                                                          & = \sum_i\phi_i(r_1)\int\phi_i^*(r_2) \frac{1}{\lvert r_1 - r_2 \rvert} \phi_a(r_2)dr_2       \\
	                                                                          & = \sum_i\phi_i(r_1)\int\frac{\phi_i^*(r_2)\phi_a(r_2)}{\lvert r_1 - r_2 \rvert}dr_2          
\end{align*}

\section{对比Thomas-Fermi理论和密度泛函理论，说明密度泛函理论在哪些方面做了改进}

TFD 理论提出总能量是电子密度的泛函，但是其中电子动能项的密度泛函形式过于简单，导致计算误差较大。

DFT 理论不是使用电子密度，而是使用电子波函数来计算动能项。这种方法计算精度高，避免动能项没有精确泛函的问题，
同时把动能项和电子间库仑相互作用的误差都放在交换关联势中，这部分能量占比较小。

\section{写出Kohn-Sham 方程，详细说明其中每一项物理意义}
Kohn-Sham equation:
\begin{align*}
	\left[-\frac{1}{2}\nabla^{2} + \hat{V_{ext}}+ \hat{U_{cl}}+ \hat{V_{xc}}(r)\right]\phi_{i}^{KS}(r)                                                                                                                   & = \varepsilon_{i}\phi_{i}^{KS}(r) \\
	\left[-\frac{1}{2}\nabla^{2} + \sum_{\alpha}-\frac{Z_{\alpha}}{\left|R_{\alpha} - r\right|}+ \int\frac{\rho(r')}{\left|r - r'\right|}dr' + \frac{\delta E_{xc}[\rho(r)]}{\delta\rho(r)}\right]\phi_{i}^{KS}(r) & = \varepsilon_{i}\phi_{i}^{KS}(r)
\end{align*}

其中，第一项$-\frac{1}{2}\nabla^{2}$表示电子的动能算符，描述电子在空间中的运动行为。

第二项$\hat{V_{ext}}$表示外势场算符，通常由原子核对电子的吸引作用构成，决定了电子在原子或分子中的分布。

第三项$\hat{U_{cl}}$表示经典库伦势算符，描述电子之间的静电相互作用，即电子间的排斥效应。

最后一项$\hat{V_{xc}}(r)$表示交换-关联势算符，包含了电子间的交换和关联效应，是密度泛函理论中最复杂且关键的部分。

右侧的$\varepsilon_{i}$是Kohn-Sham轨道的能量本征值，$\phi_{i}^{KS}(r)$是对应的Kohn-Sham轨道波函数。

\section{当前流行的交换关联函主要有哪些？试比较它们的各自应用特点}

\begin{itemize}
	\item LDA \\
        共价系统，简单金属
	\item DFT+U \\
        Mott绝缘体，强关联材料
	\item GGA \\
        分子，氢键材料，密度变化大的 d 态及 f 态，大多数磁性材料，特殊的金属
	\item Non-local hybrids and sX \\
        带隙，特殊的磁性材料
	\item van der Waals \\
        层状材料等
\end{itemize}

\section{以氢原子为例，根据量子力学求解出来的波函数，计算其在LDA下的动能、外势场能、库伦能、交换能和关联能（PW92）}

    \[
        \nabla^2 = \frac{\partial^2}{\partial x^2}
                   + \frac{\partial^2}{\partial y^2}
                   + \frac{\partial^2}{\partial z^2}
                 = \frac{1}{r^2} \frac{\partial}{\partial r}\left(r^2\frac{\partial}{\partial r}\right)
                   + \frac{1}{r^2\sin\theta}\frac{\partial}{\partial\theta}\left(\sin\theta\frac{\partial}{\partial\theta}\right)
                   + \frac{1}{r^2\sin^2\theta}\frac{\partial^2}{\partial\phi^2}                    
    \]
    \[dr = r^2 \sin\theta dr d\theta d\phi\]
    \[\Phi = \frac{1}{\sqrt\pi}e^{-r}\]
    \[\rho = \Phi^*\Phi = \frac1\pi e^{-2r}\]
    \begin{align*}
        T &= \int \Phi^*(-\frac12\nabla^2)\Phi dr
           = -\frac{1}{2\pi}\int e^{-r} \left[\frac{1}{r^2}\frac{\partial}{\partial r}(r^2\frac{\partial}{\partial r})e^{-r}\right] dr \\
          &= \frac{1}{2\pi} \int e^{-r} \frac{2r-r^2}{r^2}e^{-r}r^2dr\sin\theta d\theta d\phi
           = 2\int(2r-r^2)e^{-2r}dr
           = \frac12
    \end{align*}
    \[
        E_{ext} = \int\Phi^*(-\frac1r)\Phi dr
                = -\frac1\pi \int \frac1r e^{-r}r^2dr\sin\theta d\theta d\phi
                = -4\int re^{-2r} dr
                = -1
    \]
    \begin{align*}
        E_x &= \int\rho\varepsilon_x(\rho)dr
             = -\frac34\left(\frac3\pi\right)^{\frac13}\int\rho^{\frac43}r^2dr\sin\theta d\theta d\phi \\
            &= -3\left(\frac{3}{\pi^2}\right)^{\frac13}\int r^2e^{-\frac83r}dr
             = -\left(\frac34\right)^4\left(\frac{3}{\pi^2}\right)^{\frac13}
             = -0.2127
    \end{align*}
    \[
        \rho\varepsilon_c(\rho)
        	= \rho(-2A)(1+\alpha_1 r_s)
        		\ln\left(1+\frac{1}{2A(\beta_1 r_s^{\frac12} + \beta_2 r_s + \beta_3 r_s^{\frac32}
				+ \beta_4 r_s^2)}\right)
    \]
    \[
        r_s = \left(\frac{3}{4\pi\rho}\right)^{1/3},
        \qquad
        \rho = \frac1\pi e^{-2r}
    \]
    \[
        A = 0.031091,\quad
        \alpha_1 = 0.2137,\quad
        \beta_1 = 7.5957,\quad
        \beta_2 = 3.5876,\quad
        \beta_3 = 1.6382,\quad
        \beta_4 = 0.49294
    \]
    \[
        E_c = \int \rho\varepsilon_c(\rho)dr
            = \int \rho\varepsilon_c(\rho)r^2dr\sin\theta d\theta d\phi
            = 4\pi\int \rho\varepsilon_c(\rho)r^2dr
            = -0.0414
    \]

    \begin{align*}
        E_{cl}
        	&= \frac12\iint \frac{\rho(r)\rho(r')}{|r-r'|}drdr'
        	 = \frac12\int dr\rho(r)\int \frac{\rho(r')}{|r-r'|}dr' \\
        	&= \frac12\int dr\rho(r)U(r)
    \end{align*}

    \begin{align*}
        U(r)
			&= \int \frac{\rho(r')}{|r-r'|}dr' \\
			&= \frac1\pi\int\frac{e^{-2r'}}{\sqrt{r^2+r'^2-2rr'\cos\theta'}}
				r'^2\sin\theta' dr'd\theta'd\phi' \\
			&= 2\int dr' r'^2e^{-2r'}\int \frac{\sin\theta' d\theta'}
				{\sqrt{r^2+r'^2-2rr'\cos\theta'}} \\
			&= 2\int dr' r'^2e^{-2r'}\frac{1}{2rr'}
				\int\frac{d(r^2+r'^2-2rr'\cos\theta')}{\sqrt{r^2+r'^2-2rr'\cos\theta'}} \\
			&= \int dr' r'^2e^{-2r'}\frac{2}{rr'}\sqrt{r^2+r'^2-2rr'\cos\theta'}\bigg|_0^\pi \\
			&= \int dr' r'^2e^{-2r'}\frac{2}{rr'}(r+r'-|r-r'|)
    \end{align*}

    \[
        U(r) =
        	\begin{cases}
            	\dfrac4r\displaystyle\int dr' r'^2e^{-2r'}, & r>r' \\[1.2em]
            	4\displaystyle\int dr' r'e^{-2r'}, & r\leq r'
        	\end{cases}
        	=
        	\frac1r-\frac1r e^{-2r}-e^{-2r}
    \]

    \begin{align*}
        E_{cl}
			&= \frac12\iint \frac{\rho(r)\rho(r')}{|r-r'|}drdr'
			 = \frac12\int dr\rho(r)U(r) \\
			&= \frac12\int dr\rho(r)\left(\frac1r-\frac1r e^{-2r}-e^{-2r}\right) \\
			&= \frac{1}{2\pi}\int e^{-2r}\left(\frac1r-\frac1r e^{-2r}-e^{-2r}\right)
				r^2dr\sin\theta d\theta d\phi \\
			&= 2\int (re^{-2r}-re^{-4r}-r^2e^{-4r})dr \\
			&= \frac{5}{16}
    \end{align*}



\end{document}
```

2026 年 5 月 21 日 更新 Q10 正确解