---
title: UCAS DFT Homework 2
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

此外，作业中包含一张石墨烯二维六角晶格WS原胞MP3x3抽样的k点图，可以通过以下链接下载。使用GeoGebra制作。
- [Graph of 3x3 MP sampling in the WS cell of graphene](https://www.geogebra.org/graphing/kv6h5v9u)

流程图取自课件，此处不附。

<div style="border: 1px solid #eaeaea; border-radius: 6px; padding: 10px; margin: 20px 0;">
  <h3 style="margin-top: 0;">📄 UCAS DFT Homework 2</h3>
  <embed 
    src="/assets/doc/UCAS-DFT-HW2.pdf" 
    type="application/pdf" 
    width="100%" 
    height="800px"
    style="border-radius: 6px;"
  />
  <p style="margin-top: 10px;">
    👉 如果无法预览，请点击这里下载： 
    <a href="/assets/doc/UCAS-DFT-HW2.pdf" target="_blank">UCAS-DFT-HW2.pdf</a>
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
\usepackage{mdframed}
    \newmdenv[
        backgroundcolor=blue!5,
        linecolor=blue,
        linewidth=1pt
    ]{bluebox}
\newcommand{\blue}[1]{\textcolor{blue}{#1}}
\newcommand{\red}[1]{\textcolor{red}{#1}}
\usepackage{subcaption}


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
\author{hidden}
\date{\today}
\maketitle

\section{Question 1}
\begin{bluebox}
说明赝势方法的理论基础，并列举构造模守恒赝势的四个条件
\end{bluebox}
    \subsection{理论基础}
        金原子总共有 79 个电子，在绝热近似下有 3081 项电子相互作用，
        直接求解没有希望。

        但实际经验总结中得到，对金原子物性起决定性作用的只有11个价电子，
        其余 68 个芯电子不参与化学反应，外界环境对于它们的影响也非常小，
        如果计算中不考虑芯电子，对于整体的计算将会节省很多资源。

        在研究固体或者分子中的电子结构时，不直接去处理原子核和所有内层电子的复杂影响，
        而是用一个简化的、等效的势函数来代替他们。

        这个等效的势函数就是赝势。

        赝势方法通过“伪装”内层电子和原子核的作用，让我们只需要关注价电子的行为，
        从而大大简化了计算。

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

\vskip 2 cm



\section{Question 2}
\begin{bluebox}
使用赝势方法为什么需要核修正
\end{bluebox}

    在使用赝势时，不再考虑内层电子和原子核的全部复杂结构，而是使用一个简化的势代替。
    
    在这个过程中，为了确保计算的准确性，我们需要对原子核的部分做一些修正或者调整，
    让这个赝势在描述价电子行为的时候更加合理。

    核修正的目的势让这个简化的模型更加精确，让赝势在很好的处理外层电子时，
    依然能够很好的反映出原子核的影响。

    来源于交换关联势在原子核附近的非线性效应。

    \[ 
        V_{xc}[\rho_v+\rho_c](r) \neq
            V_{xc}[\rho_v](r) + V_{xc}[\rho_c](r)
    \]

    解决方案是在计算交换关联势是，需要把芯电子加上去；
    考虑到芯电子在原子核附近是震荡的，所以在原子核附近使用平滑函数替代

\begin{bluebox}
使用构造赝势时为什么需要去屏蔽？
\end{bluebox}

    从波函数得到的势函数是 Kohn-Sham 有效势，包含了价电子的贡献。

    当使用赝势计算时，所有原子的价电子都是待解问题而会被明确处理，
    故价电子的效应并不会是赝势的一部分。

    构造赝势时所需要的是只含有原子核与内层电子的离子赝势，
    而不能包含其他价电子对正在处理的那个价电子的相互作用（即屏蔽效应）。

    \[
        V_{ion,l}^{PP}(\rho_{val}) = 
            V_{scr,l}^{PP}(\rho_{val}) - V_H^{PP}(\rho_{val}) - V_{xc}^{PP}(\rho_{val})
    \]




\section{Question 3}
\begin{bluebox}
写出平面波基组下的 Kohn-Sham 方程，详细说明其中每一项的物理意义
\end{bluebox}
    \subsection{平面波基组下的 Kohn-Sham 方程}
        \begin{equation*}
            \sum_{G'}\left[\frac{1}{2}|k+G'|^2\delta_{GG'}
            + V_{kGG'}^{eff}\right]\Phi_j(G') = \epsilon_j\Phi_j(G)
        \end{equation*}
        where,
        \begin{equation*}
            V_{kGG'}^{eff} = V_{coul}(G-G') + \hat{V_\mathrm{XC}}(G-G')
            + S(G'-G)\left(V^{core}(G-G') + \sum_\ell V_{\ell,k;G,G'}^{NL}\right)
        \end{equation*}
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

\begin{bluebox}
写出平面波基组的表达式，证明平面波基组满足布洛赫定理。
\end{bluebox}
    \subsection{平面波基组的表达式}
        \[
            \Phi_G(r) = e^{i(k+G)\cdot r}
        \]
    \subsection{平面波基组满足布洛赫定理}
        \begin{align*}
            \Phi_G(r+t_n) &= e^{i(k+G)\cdot(r+t_n)} \\
                          &= e^{i(k+G)\cdot t_n}\Phi_G(r)
        \end{align*}



\section{Question 4}
\begin{bluebox}
石墨烯是二维六角晶格，如果晶格基矢 $a_1$，$a_2$ 之间的夹角是120°，
写出以倒格矢 $b_1$，$b_2$ 为单位的 3×3 MP 抽样的 k 点坐标及权重
\end{bluebox}

    因为正空间中晶格基矢 $a_1$，$a_2$ 之间的夹角是120°，
    所以倒易空间中倒格矢 $b_1$，$b_2$ 之间的夹角是60°

    以二维六角晶格的正中心作为倒易原点，
    那么这个夹角为60°的倒格矢基矢将会分别经过这个二维六角晶格的两条临边的中点。
    因为正格矢 $a_1$, $a_2$ 具有相同的模长，所以倒易之后的倒格矢也具有相同的模长。

    这样，倒格矢基矢构成密铺的等边平行四边形。作图：

    \begin{figure}[htbp]
        \centering
        \includegraphics[scale=0.15]{3x3.eps}
        \caption{石墨烯二维六角晶格的 3×3 MP 抽样的 k 点分布图}
        \label{figure}
    \end{figure}

    k 点坐标：

    \[ \begin{matrix}
        (-\frac13,\frac13) & (0,\frac13) & (\frac13,\frac13) \\
        (-\frac13,0) & (0,0) & (\frac13,0) \\
        (-\frac13,-\frac13) & (0,-\frac13) & (\frac13,-\frac13)
    \end{matrix} \]

    $k = (0,0)$，有1个等价k点，$w_k = 1/9$

    $k = (\frac13,0)$，有6个等价k点，$w_k = 2/3$

    $k = (\frac13,\frac13)$，有2个等价k点，$w_k = 2/9$




\section{Question 5}
\begin{bluebox}
原子受力分为 Hellmann-Feynman 力和 Pauly 力，说明这两种受力的来源
\end{bluebox}

    经典力学中对于受力的求解，是通过对势能做梯度变分得到的。在原子模拟中，
    势能就是系统的总能量 $E_{tot}$，其中总能量包含核-核相互作用 $E_{nn}$

    总能量对于原子坐标 $R_\mu$、电子波函数 $\Phi_j$ 以及其共轭 $\Phi_j^*$
    相关，经过对波函数的变分后，得知电荷密度的改变对于力没有贡献，
    只需对显含的原子核坐标做微分，于是有下式：

    \begin{align}
    F_\mu &= - \frac{dE_{tot}}{dR_\mu}\\
          &= - \frac{dE_{nn}}{dR_\mu} 
             - \int dr \rho(r)\frac{\partial V_{ext}(r)}{\partial R_\mu}
             - \int dr \frac{\delta E_{tot}}{\delta\rho(r)}
               \frac{\partial\rho(r)}{\partial R_\mu}\\
          &= F_\mu^{HF} + F_\mu^{el}
    \end{align}

    上式中第1、2项中的 $E_{nn}$ 和 $V_{ext}$ 明确依赖于原子坐标 $R_\mu$，
    而电子密度 $\rho$ 不是显式依赖于原子坐标 $R_\mu$。

    前两项被称为 Hellmann-Feynman力，这部分来源于经典电磁势；
    第三项来自电荷密度的贡献，被称为变分力。

    上式中提到电荷密度的改变对于力没有贡献，
    但当展开波函数的基函数跟原子坐标有关时，这项不为零。

    即，对于平面波（PW）基函数来说，变分力与原子坐标无关，为零；

    对于原子轨道基组（AO）来说，不为零，这部分对于原子受力的贡献被称为 Pauly 力。



\section{Question 6}
\begin{bluebox}
说明 Car-Parrinello 分子动力学的原理，并画出计算流程图
\end{bluebox}

    对于最基本的分子动力学，他们是用经典牛顿运动方程，
    让原子在给定势能面上按受力运动，通过数值积分得到原子随时间演化，从中统计宏观物性。
    \[m_i\ddot{R}_i = \nabla_iV({R})\]

    其中 $V$ 来自经验力场，比如LJ势、EAM势等

    使用 DFT 方法后，产生了两条分支：
    
    其一为 Born-Oppenheimer 分子动力学。
    它的每步动力学演化都需要通过自洽计算得到原子受力，电子始终存于基态。
    其方程依然源自牛顿力学。
    \[m_i\ddot{R}_i = -\frac{\partial E_{DFT}}{\partial R_i}\]

    其二则为 Car-Parrinello 分子动力学。    
    它把电子波函数和原子坐标一起演化，
    不需要每步动力学演化都通过自洽计算得到原子受力，电子不是处于严格的基态。

    Car-Parrinello 分子动力学的计算流程图如下图所示：
    \begin{figure}[H]
        \centering
        \includegraphics[width=0.5\linewidth]{CPMD.png}
        \caption{Car-Parrinello 分子动力学计算流程图}
        \label{fig:CPMD}
    \end{figure}



\section{Question 7}
\begin{bluebox}
证明高斯型轨道下双中心积分可以化简为单中心积分
\end{bluebox}

    因为 Gaussian 型函数具有加法特性，
    \begin{equation}
        e^{-\alpha_1 r_1^2}e^{-\alpha_2 r_2^2} = 
            e^{-\frac{\alpha_1\alpha_2}{\alpha_1+\alpha_2}r_{12}^2}
            e^{-(\alpha_1+\alpha_2)r_p^2}
    \end{equation}

    其中，$r_{12}$ 是在两个中心 1,2 间的距离。
    \[r_1 = | r - R_1 |\]
    \[r_2 = | r - R_2 |\]
    \[r_p = \left|r-\frac{\alpha_1R_1+\alpha_2R_2}{\alpha_1+\alpha_2}\right|\]
    \[r_{12} = | R_1 - R_2 |\]

    因此，两中心积分可以约化为单中心积分，这意味着所有的多中心积分都可以约化。



\section{Question 8}
\begin{bluebox}
中性原子势包含哪些项？为什么中性原子势是短程的？
\end{bluebox}

    中性原子势定义为：
    
    \begin{equation}
        V^{NA}(r-R_I) \equiv V^{core}(r-R_I)
                             + \int\frac{n_{at}(r'-R_I)}{|r-r'|}dr'
    \end{equation}

    \subsubsection*{(1) $V^{\mathrm{core}}$：核与内层电子的有效势}

    $V^{\mathrm{core}}$ 包含：
    \begin{enumerate}
      \item 原子核的库仑吸引势
        \[
          -\frac{Z_I}{|\mathbf{r}-\mathbf{R}_I|} .
        \]
      \item 冻结内层电子对外层电子的有效作用，也称为
            ``核心势''。在赝势与 PAW 方法中，该项通常为
            已经软化后的有效势；在全电子方法中，则包含核
            库仑势与内层电子的 Hartree 与交换相关贡献。
    \end{enumerate}

    因此 $V^{\mathrm{core}}$ 描述了“核 + 不参与成键的内层
    电子”对空间中电子所产生的全部静电作用。

    \subsubsection*{(2) 中性原子电子密度的库仑势}

    第二项为中性原子的电子密度 $n_{\mathrm{at}}$ 所产生的
    Hartree 势：
    \[
      V_H^{\mathrm{at}}(\mathbf{r}) =
        \int \frac{n_{\mathrm{at}}(\mathbf{r}')}
                 {|\mathbf{r}-\mathbf{r}'|}\, d\mathbf{r}' .
    \]

    这里的 $n_{\mathrm{at}}$ 通常是孤立原子的价电子密度，
    有时也包含半芯态。该项的作用是补上价电子的库仑排斥，
    从而使整个原子势成为“电中性”的背景势。

    如果只有 $V^{\mathrm{core}}$，原子势将带正电；加入
    $V_H^{\mathrm{at}}$ 后，核与电子的电荷相互抵消，从而形
    成中性的原子势，用作赝势和 PAW 的参考势。

    \subsection*{为什么中性原子势是短程的？}

    中性原子势是局域赝势和参考电荷共同作用下的势场，
    在电中性的情况下把长程库伦相互作用的发散项相抵消。
    因为在截断半径之外总电荷为零，所以势场在截断半径之外也为零。
    因而中性原子势是短程的。



\section{Question 9}
\begin{bluebox}
写出原子轨道基组下的 Kohn-Sham 方程，详细说明其中每一项的物理意义
\end{bluebox}

    Kohn-Sham Equation

    \begin{align}
        \left[
        \begin{aligned}
            - \frac{1}{2}\nabla^2
           &+ \sum_I\left( V^{core}(r-R_I)
            + \sum_l V^{NL}(r-R_I)P_l \right) \\
           &+ \sum_I \int \frac{n_{at}(r'-R_I)}{|r-r'|}\,dr'
            + U_{cl}^\delta(r)
            + \hat{V}_{xc}(r)
        \end{aligned}
        \right]\Phi_i^{KS}(r)
        = \epsilon_i \Phi_i^{KS}(r)
    \end{align}

    \subsubsection*{(1) 动能算符 $-\tfrac{1}{2}\nabla^2$}

    表示价电子的量子动能，是 Kohn-Sham 单电子哈密顿量的
    基本组成部分，对所有电子均相同，对应自由粒子的拉普拉
    斯算符。

    \subsubsection*{(2) $V^{core}(r-R_I)$：核与冻结内层电子的势}

    该项包含原子核的库仑吸引势与内层电子的有效屏蔽作用。
    在赝势方法中，此势已被软化；在全电子方法中，则包含核
    库仑项以及核心电子的 Hartree 与交换相关贡献。

    \subsubsection*{(3) $V^{NL}(r-R_I) P_l$：非局域赝势项}

    非局域赝势通过投影算符 $P_l$ 实现轨道角动量依赖的修正，
    用以再现价电子在不同角动量通道中的散射特征，是赝势构
    造中不可缺少的部分。

    \subsubsection*{(4) $\displaystyle 
      \int\!\frac{n_{at}(r'-R_I)}{|r-r'|}\,dr'$：中性原子电子库仑势}

    $n_{at}$ 为孤立原子的电子密度，其产生的库仑势用于与核
    势配合，构成中性原子势，使原子整体电中性，是赝势与 PAW
    构造的参考背景势。

    \subsubsection*{(5) $U_{cl}^{\delta}(r)$：补偿电荷项（PAW/USPP）}

    在 PAW 或超软赝势中使用，用以修正平面波不能充分描述
    原子心附近电荷的误差，实现总能与力的严格可微性，并保
    持电荷守恒性质。

    \subsubsection*{(6) $\hat{V}_{xc}(r)$：交换相关势}

    由密度泛函中的交换相关能量函数导出，是决定电子结构与
    自旋极化性质的重要项，反映电子多体相互作用的有效场。



\section{Question 10}
\begin{bluebox}
列出课题组常用的第一性原理计算模拟软件，简单说明其理论方法和主要功能等特性
\end{bluebox}

    \begin{enumerate}

       \item \textbf{VASP（Vienna Ab~initio Simulation Package）}

        基于密度泛函理论，采用平面波基组与 PAW 方法。支持
        LDA/GGA/meta-GGA、DFT+U、杂化泛函以及 GW、RPA 等高
        级方法。主要功能包括结构优化、能带与态密度、声子、
        分子动力学、表面吸附、缺陷、扩散以及过渡态搜索等，
        是固体材料研究中最为成熟与广泛使用的平面波软件。

        \item \textbf{Quantum~ESPRESSO}

        基于平面波与赝势（USPP/PAW/NC），完全开源。实现 DFT、
        DFPT、NEB、AIMD、Wannier 化等工具。适用于周期体系的
        能量、力、声子谱、电子--声子耦合以及介电与光学性质
        计算，是高性能并行环境下常用的开源第一性原理平台。

         \item \textbf{ABINIT}

        采用平面波与赝势框架，支持 LDA/GGA/meta-GGA、DFT+U、
        PAW、GW 与 BSE。其优势在于激发态电子结构、光谱以及
        声子、热力学性质的统一处理框架，适合研究半导体与绝
        缘体的高级电子结构与光学响应。

        \item \textbf{LAMMPS（结合第一性原理势）}

        虽为经典分子动力学软件，但常与机器学习势（如 DP、
        GAP、SNAP、MTP）结合，实现具有第一性原理精度的大规
        模动力学模拟。适用于缺陷演化、辐照损伤、热输运以及
        大体系结构弛豫等多尺度材料问题。

        \item \textbf{WIEN2k}

        基于全势 LAPW+lo 方法，是严格的全电子计算程序。无需
        赝势，直接处理价电子与芯电子，适合高精度能带、磁性、
        电荷密度、微观电子结构以及强关联体系研究，是固体能
        带理论中精度最高的方案之一。

    \end{enumerate}



\section{Question 11}
\begin{bluebox}
附加题：写出 STO 基组和 GTO 基组的表达式，列举它们的优缺点。
\end{bluebox}

    \subsection{STO 基组}
    \[
        \frac{(2\zeta)^{n+1/2}}{[(2n)!]^{1/2}} r^{n-1} e^{-\zeta r} Y_{lm}(\theta,\phi)
    \]

    以 $e^{-\zeta r}$ 趋于零，作为基函数更符合实际。不过计算算法复杂，计算量大。

    \subsection{GTO 基组}
    \[
        \left[\sqrt{\frac2\pi}\frac{(4\alpha)^{n+1/2}}{(2n-1)!!}\right]^{1/2} 
            r^{n-1} e^{-\alpha r^2} Y_{lm}(\theta,\phi)
    \]

    以 $e^{-\alpha r^2}$ 趋于零，作为基函数不符合实际。可以直接解析计算多中心积分，算法简单计算量小。
    
\end{document}
```

