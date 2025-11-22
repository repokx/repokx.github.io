---
title: UCAS Academy Ethics - Detailed Discussion - Latex Exam
description: >-
author: repo
date: 2025-11-23 00:58:00 +0800
categories: [Writing Skills, LaTeX]
tags: [LaTeX]
# math: true
# mermaid: true
# pin: false 
# img_path: /src/
# image:
#     path: 
#     alt: 
---

This article is actually about `some specific exam`.

the following `LaTeX` code is well-designed,

copy it after you actually know what you wanna do.

> DO NOT SPREAD.
{: .prompt-warning}

<div style="border: 1px solid #eaeaea; border-radius: 6px; padding: 10px; margin: 20px 0;">
  <h3 style="margin-top: 0;">📄Latex_Test.pdf</h3>
  <embed 
    src="/assets/doc/Latex_test.pdf" 
    type="application/pdf" 
    width="100%" 
    height="800px"
    style="border-radius: 6px;"
  />
  <p style="margin-top: 10px;">
    👉 If preview is unavailable, click here to download the original pdf file： 
    <a href="/assets/doc/Latex_test.pdf" target="_blank">Latex_test.pdf</a>
  </p>
</div>

``` latex
\documentclass[aps,prd,showpacs,superscriptaddress,preprintnumbers]{revtex4}

\usepackage{graphicx,float,wrapfig,subfigure}
\usepackage{amsfonts,amsmath,amssymb,amstext,esint}
\usepackage{latexsym}
\usepackage{bm}
\usepackage{xcolor}
\usepackage[normalem]{ulem}
\usepackage{booktabs}
\usepackage{makecell,multirow,longtable,rotating,diagbox}

\newbox\pippobox
\usepackage{amssymb,amsfonts}
%\usepackage{subfig}
\newcommand{\be}{\begin{equation}}
\newcommand{\ee}{\end{equation}}
\newcommand{\ba}{\begin{eqnarray}}
\newcommand{\ea}{\end{eqnarray}}
\newcommand{\diag}{\text{diag}}
\newcommand{\tr}{\,\mbox{tr}}
\newcommand{\sign}{\,\mbox{sign}}
\newcommand{\non}{\nonumber\\}
\newcommand{\tri}{\triangle}
\definecolor{red}{rgb}{0.7,0,0}
\definecolor{green}{rgb}{0,0.5,0}
\newcommand{\revision}[1]{\textcolor{red}{#1}}
\newcommand{\revisionA}[1]{\textcolor{blue}{#1}}
\newcommand{\revisionB}[1]{\textcolor{green}{#1}}
\newcommand{\revisionC}[1]{\textcolor{magenta}{#1}}
%\topmargin0.0pt

\begin{document}

\title{Assessment for scientific writing}
\date{\today}

\author{Anonymous}
\email{example@mails.ucas.ac.cn}
\affiliation{Institute of \LaTeX, Chinese Academy of Sciences}

\begin{abstract}
{\rm The scientific writing course introduced the general IMRAD structure
for scientific papers, and introduced basic skills on how to use Latex
editing a scietific paper.}
{\it }
\end{abstract}
\pacs{12.38.Mh,25.75.-q,11.10.Wx,13.88+e }
\maketitle



\section{Introduction}
\label{sec:Introduction}
\textbf{\revisionC{Question 2.1}}
Please give a brief introduction on the general structure of scientific papers 
here,i.e. the IMRAD structure \cite{Alley1996}.  What kind of content should be addressed 
in each part?
\vskip 0.5 cm
\textbf{ANSWER:}

"IMRaD" format refers to a paper that is structured by four main sections: 
Introduction, Methods, Results, and Discussion. This format is often used for 
lab reports as well as for reporting any planned, systematic research in the 
social sciences, natural sciences, or engineering and computer sciences.
\begin{enumerate}
    \item \textbf{\revisionA{Introduction} – Make a case for your research}\\
          The introduction explains why this research is important or necessary 
          or important. Begin by describing the problem or situation that motivates 
          the research. Move to discussing the current state of research in the 
          field; then reveal a “gap” or problem in the field. Finally, explain 
          how the present research is a solution to that problem or gap. If the 
          study has hypotheses, they are presented at the end of the introduction.
    \item \textbf{\revisionA{Methods} – What did you do?}\\
          The methods section tells readers how you conducted your study. 
          It includes information about your population, sample, methods, 
          and equipment. The “gold standard” of the methods section is that 
          it should enable readers to duplicate your study. Methods sections 
          typically use subheadings; they are written in past tense, and they 
          use a lot of passive voice. This is typically the least read section 
          of an IMRaD report.
    \item \textbf{\revisionA{Results} – What did you find?}\\
          In this section, you present your findings. Typically, the Results 
          section contains only the findings, not any explanation of or commentary 
          on the findings (see below). Results sections are usually written in the 
          past tense. Make sure all tables and figures are labeled and numbered 
          separately. Captions go above tables and beneath figures.
    \item \textbf{\revisionA{Discussion} - What does it mean?}\\
          In this section, you summarize your main findings, comment on those 
          findings (see below), and connect them to other research. You also 
          discuss limitations of your study, and use these limitations as reasons 
          to suggest additional, future research.
\end{enumerate}

\textbf{\revisionC{Question 2.2}}
Please list some Academic Misconduct/Academic Dishonesty.(you can answer this part 
in Chinese and insert a .jpg file of your answer.)
\vskip 0.5 cm
\textbf{ANSWER:}

Here are some common types of academic dishonesty,
\begin{enumerate}
    \item \textbf{\revision{Plagiarism}}\\
          One of the most common forms of academic dishonesty is plagiarism. 
          The act of plagiarism occurs when you use someone else’s work without 
          citing it properly. If you’re not mindful, this can be easy to do — 
          especially when writing a paper or essay.\\
          You can avoid plagiarism by utilizing an appropriate style or citation 
          guide. This typically includes using both in-text citations and 
          references in your paper. Tools that can help students avoid plagiarism 
          include style guides, such as the AP Style Guide or Chicago Manual of 
          Style, and plagiarism detection software.
    \item \textbf{\revision{Cheating}}\\
          Cheating is another common form of academic dishonesty. It may consist 
          of copying answers from a classmate, selling or buying an academic paper 
          or assignment, or using unauthorized materials during a test.
\end{enumerate}



\section{Equations}
\label{sec:Equations}
\textbf{\revisionC{Question 3}}
Please type Equations shown in \revisionA{output20251122.pdf} file.
\vskip 0.5 cm
\textbf{ANSWER:}

The metric tensor reads

\begin{equation}
    g_{\mu\nu} = 
        \begin{pmatrix}
            1 - \vec{v}\,^2 & -v_1 & -v_2 & -v_3 \\
            -v_1          & -1   & 0    & 0    \\
            -v_2          & 0    & -1   & 0    \\
            -v_3          & 0    & 0    & -1
        \end{pmatrix}
\end{equation}

The detailed expressions for $N_\uparrow^{+}$, $N_\downarrow^{+}$, $N_\uparrow^{-}$,
$N_\downarrow^{-}$ are listed as follows:

\begin{equation}
    N_\uparrow^{+} = \frac{1}{2\pi^2} \sum_{n=-\infty}^{\infty} \int
        dp_t dp_z p_t J_n (p_t r)^2
        \frac{
            3\Phi\exp(-\frac{\epsilon_n-\mu}{T}) +
            6\bar{\Phi}\exp(-2\frac{\epsilon_n-\mu}{T}) +
            3\exp(-3\frac{\epsilon_n-\mu}{T})
        }{
            1 + 3\Phi\exp(-\frac{\epsilon_n-\mu}{T}) +
            3\bar{\Phi}\exp(-2\frac{\epsilon_n-\mu}{T}) +
            \exp(-3\frac{\epsilon_n-\mu}{T})
        },
\end{equation}

\begin{equation}
    N_\downarrow^{+} = \frac{1}{2\pi^2} \sum_{n=-\infty}^{\infty} \int
        dp_t dp_z p_t J_{n+1} (p_t r)^2
        \frac{
            3\Phi\exp(-\frac{\epsilon_n-\mu}{T}) +
            6\bar{\Phi}\exp(-2\frac{\epsilon_n-\mu}{T}) +
            3\exp(-3\frac{\epsilon_n-\mu}{T})
        }{
            1 + 3\Phi\exp(-\frac{\epsilon_n-\mu}{T}) +
            3\bar{\Phi}\exp(-2\frac{\epsilon_n-\mu}{T}) +
            \exp(-3\frac{\epsilon_n-\mu}{T})
        },
\end{equation}

\begin{equation}
    N_\uparrow^{-} = \frac{1}{2\pi^2} \sum_{n=-\infty}^{\infty} \int
        dp_t dp_z p_t J_n (p_t r)^2
        \frac{
            -3\bar{\Phi}\exp(-\frac{\epsilon_n+\mu}{T}) -
            6\Phi\exp(-2\frac{\epsilon_n+\mu}{T}) -
            3\exp(-3\frac{\epsilon_n+\mu}{T})
        }{
            1 + 3\bar{\Phi}\exp(-\frac{\epsilon_n+\mu}{T}) +
            3\Phi\exp(-2\frac{\epsilon_n+\mu}{T}) +
            \exp(-3\frac{\epsilon_n+\mu}{T})
        },
\end{equation}

\begin{equation}
    N_\downarrow^{-} = \frac{1}{2\pi^2} \sum_{n=-\infty}^{\infty} \int
        dp_t dp_z p_t J_{n+1} (p_t r)^2
        \frac{
            -3\bar{\Phi}\exp(-\frac{\epsilon_n+\mu}{T}) -
            6\Phi\exp(-2\frac{\epsilon_n+\mu}{T}) -
            3\exp(-3\frac{\epsilon_n+\mu}{T})
        }{
            1 + 3\bar{\Phi}\exp(-\frac{\epsilon_n+\mu}{T}) +
            3\Phi\exp(-2\frac{\epsilon_n+\mu}{T}) +
            \exp(-3\frac{\epsilon_n+\mu}{T})
        }.
\end{equation}

\begin{equation}
    \Phi^\pm = 
        \begin{pmatrix}
            [\tri_{uu}^{rr}]^\pm & 0 & 0 &
            0 & [\tri_{ud}^{rg}]^\pm & 0 &
            0 & 0 & [\tri_{us}^{rb}]^\pm\\
            0 & 0 & 0 & [\tri_{du}^{rg}]^\pm & 0 & 0 & 0 & 0 & 0 \\
            0 & 0 & 0 & 0 & 0 & 0 & [\tri_{su}^{rb}]^\pm & 0 & 0 \\
            0 & [\tri_{du}^{rg}]^\pm & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
            [\tri_{ud}^{rg}]^\pm & 0 & 0 &
            0 & [\tri_{dd}^{gg}]^\pm & 0 &
            0 & 0 & [\tri_{ds}^{gb}]^\pm\\
            0 & 0 & 0 & 0 & 0 & 0 & 0 & [\tri_{sd}^{gb}]^\pm & 0 \\
            0 & 0 & [\tri_{su}^{rb}]^\pm & 0 & 0 & 0 & 0 & 0 & 0 \\
            0 & 0 & 0 & 0 & 0 & [\tri_{sd}^{gb}]^\pm & 0 & 0 & 0 \\
            [\tri_{us}^{rb}]^\pm & 0 & 0 &
            0 & [\tri_{ds}^{gb}]^\pm & 0 &
            0 & 0 & [\tri_{ss}^{bb}]^\pm\\
        \end{pmatrix}
\end{equation}

\begin{equation}
    \begin{aligned}
        f_{n,p}^{+}(x) & \equiv
            e^{-i(\omega t - p_y y - p_z z)} \phi_n (x-p_y/|q_f|B), \quad
            (n=0,1,\ldots) \\
        f_{n,p}^{-}(x) & \equiv
            e^{-i(\omega t - p_y y - p_z z)} \phi_{n-1} (x-p_y/|q_f|B), \quad
            (n=1,2,\ldots)
    \end{aligned}
\end{equation}

with new notation $\tilde{p_\parallel} = (\omega, 0, 0, p_z)$ and 
$\tilde{p_\perp} = \left(0, 0, -\sqrt{2n|q_f|B}, 0\right)$ introduced. After some
simple calculations the dispersion relation reads

\begin{equation}
    E_{f,n,s}^2 =
        \begin{cases}
            p_z^2 + \left(\sqrt{M^2 + 2n|q_f|B} - s\xi\right)^2, & n \ge 1.\\[0.5cm]
            p_z^2 + (M + \xi)^2,                                 & n = 0.            
        \end{cases}
\end{equation}

Where $ M = \sigma + m $ and $ s = \pm 1 $ correspond to different spin projections.



\section{Figures}
\textbf{\revisionC{Question 4.1}}
Please use subfigure to insert two subfigures 
${\revisionA{\rm Divergence\_theorem\_in\_EM.png}}$ \\
and ${\revisionA{\rm Curl\_theorem\_in\_EM.png}}$ in attachment.

\begin{figure}[htbp]
    \centering
    \subfigure[The Gauss divergence theorem\label{fig:GDT}]{
        \includegraphics[width=0.35\textwidth]{Divergence_theorem_in_EM.png}
    }
    \subfigure[The Kelvin-Stokes theorem\label{fig:KST}]{
        \includegraphics[width=0.35\textwidth]{Curl_theorem_in_EM.png}
    }

    \caption{The Gauss divergence throrem and the Kelvin-Stokes theorem}
    \label{fig:GDT&KST}
\end{figure}

\textbf{\revisionC{Question 4.2}}
please show at least two different screenshots of your original textfile.

\begin{figure}[htbp]
    \centering
    \subfigure[.tex file with My Name\label{fig:name}]{
        \includegraphics[width=0.35\textwidth]{with_name.png}
    }
    \subfigure[.tex file with My Code\label{fig:code}]{
        \includegraphics[width=0.35\textwidth]{with_code.png}
    }

    \caption{.tex file with My Name and Code}
    \label{fig:name&code}
\end{figure}



\section{Tables}
\label{sec:Tables}
\textbf{\revisionC{Question 5}}
In this section, please make a Table  shown in \revisionA{output20251122.pdf} file.

Please make Table here.
\vskip 2cm

\begin{table}[!h]
    \begin{tabular}{|c|c|c|c|c|c|c|c|c|c|}
        \hline
        \multicolumn{2}{|c|}{\multirow{2}*{~}} & \multicolumn{4}{|c|}{Model A} & 
            \multicolumn{4}{|c|}{Model B}\\
        \cline{3-10}
        \multicolumn{2}{|c|}{~} & 
            $ N_{TC} = 3 $ & $ N_{TC} = 4 $ & $ N_{TC} = 5 $ & $ N_{TC} = 6 $ &
            $ N_{TC} = 3 $ & $ N_{TC} = 4 $ & $ N_{TC} = 5 $ & $ N_{TC} = 6 $\\
        \cline{1-10}
        \multirow{3}{*}{\begin{sideways}{\textbf{Input~~}}\end{sideways}} &
            $ z_m^{-1}(TeV) $ &
            1.072 & 1.079 & 1.083 & 1.088 &
            0.299 & 0.299 & 0.299 & 0.299\\
        \cline{2-10}
        ~ & $ c $ & 1.395 & 1.414 & 1.423 & 1.427 &
                    0.099 & 0.099 & 0.099 & 0.099\\
        \cline{2-10}
        ~ & $ M $ & 0.553 & 0.541 & 0.534 & 0.529 &
                    0.380 & 0.329 & 0.295 & 0.288\\
        \cline{1-10}
        \multirow{6}{*}{\begin{sideways}{\textbf{Output~~~~~}}\end{sideways}} &
            $ S $ & \multicolumn{4}{|c|}{0.15(fixed)} &
            0.721 & 0.888 & 1.034 & 1.120\\
        \cline{2-10}
        ~ & $T_*(GeV)$ & 356 & 358 & 360 & 362 & \multicolumn{4}{|c|}{100(fixed)}\\
        \cline{2-10}
        ~ & $m_{higgs}^{(1)}$ & 4.368 & 4.397 & 4.413 & 4.534 &
                                1.217 & 1.217 & 1.217 & 1.217\\
        ~ & $m_{techni-\rho}^{(0)}$ & 2.054 & 2.068 & 2.075 & 2.085 &
                                      0.586 & 0.586 & 0.586 & 0.586\\
        ~ & $m_{techni-\rho}^{(1)}$ & 5.722 & 5.759 & 5.780 & 5.792 &
                                      1.603 & 1.603 & 1.603 & 1.603\\
        ~ & $m_{II}^{(1)}$ & 5.531 & 5.521 & 5.515 & 5.502 &
                             3.135 & 2.686 & 2.385 & 2.185\\
        \hline
    \end{tabular}
    \caption{Input parameters and output results from Model A and Model B,
        respectively. Note that the unit of particle mass is TeV.}
    \label{tab:spectum}
\end{table}



\section{list 10 references}
\label{sec:References}
\textbf{\revisionC{Question 6}}
Please list 10 references from [2]-[10] shown in \revisionA{output20251122.pdf} file.

\begin{thebibliography}{99}
\bibitem{Alley1996}
Michael Alley, \emph{The Craft of Scientific Writing}, Springer, 1996.

\bibitem{Kiuchi2015}
K. Kiuchi, P. Cerd\'a-Dur\'an, K. Kyutoku, Y. Sekiguchi and M. Shibata,
Phys. Rev. D \textbf{92}, 124034 (2015),
doi:10.1103/PhysRevD.92.124034,
arXiv:1509.09205 [astro-ph.HE].

\bibitem{Baiotti2017}
L. Baiotti and L. Rezzolla,
Rept. Prog. Phys. \textbf{80}, 096901 (2017),
doi:10.1088/1361-6633/aa67bb,
arXiv:1607.03540 [gr-qc].

\bibitem{Andersen2016}
J. O. Andersen, W. R. Naylor and A. Tranberg,
Rev. Mod. Phys. \textbf{88}, 025001 (2016),
doi:10.1103/RevModPhys.88.025001,
arXiv:1411.7176 [hep-ph].

\bibitem{Miransky2015}
V. A. Miransky and I. A. Shovkovy,
Phys. Rept. \textbf{576}, 1 (2015),
doi:10.1016/j.physrep.2015.02.003,
arXiv:1503.00732 [hep-ph].

\bibitem{Kharzeev2016}
D. E. Kharzeev, J. Liao, S. A. Voloshin and G. Wang,
Prog. Part. Nucl. Phys. \textbf{88}, 1 (2016),
doi:10.1016/j.ppnp.2016.01.001,
arXiv:1511.04050 [hep-ph].

\bibitem{Kharzeev2007}
D. Kharzeev and A. Zhitnitsky,
Nucl. Phys. A \textbf{797}, 67 (2007),
arXiv:0706.1026 [hep-ph].

\bibitem{Kharzeev2008}
D. E. Kharzeev, L. D. McLerran and H. J. Warringa,
Nucl. Phys. A \textbf{803}, 227 (2008),
arXiv:0711.0950 [hep-ph].

\bibitem{Fukushima2008}
K. Fukushima, D. E. Kharzeev and H. J. Warringa,
Phys. Rev. D \textbf{78}, 074033 (2008),
arXiv:0808.3382 [hep-ph].

\bibitem{Kharzeev2011}
D. E. Kharzeev and D. T. Son,
Phys. Rev. Lett. \textbf{106}, 062301 (2011),
arXiv:1010.0038 [hep-ph].

\bibitem{Gusynin1996}
V. P. Gusynin, V. A. Miransky and I. A. Shovkovy,
Nucl. Phys. B \textbf{462}, 249 (1996),
doi:10.1016/0550-3213(96)00021-1,
hep-ph/9509320.

\end{thebibliography}
\end{document}
```
