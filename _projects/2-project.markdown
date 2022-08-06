---
layout: page
title: CVaR Optimization
description: Chance-constrained optimization for conditional value-at-risk problems
img: /assets/img/cvar_header.png
importance: 1
category: work
---
Within this project, we consider optimization problems with risk constraints, looking to confine the violation probability. These optimization problems can be formulated as,
\begin{equation}
\begin{align}
\label{eq-chance-opt}
\begin{array}
[c]{ll}%
\mbox{minimize} & \bm{c}^{T}
\bm{x}\\
\mbox{subject to} & \mathrm{Prob} \{\phi(\bm{x},\bm{\xi}) > 0\}\leq \delta.\\
\end{array}
\end{align}
\end{equation}
where $\bm{x}\in\mathds{R}^{m}$ is an $m$-dimensional decision variable, and $\bm{\xi}\in\mathds{R}^{n}$ is an $n$-dimensional random vector. The elements of $\bm{\xi}$ are often referred to as risk factors; the function 
$\phi: \mathds{R}^{m}\times\mathds{R}^{n}
\rightarrow\mathds{R}$ is often assumed to be convex in $\bm{x}$ and often models a cost constraint; the parameter
$\delta> 0$ is the risk level of the tolerance.


The probabilistic constraint in \eqref{eq-chance-opt} can be reformulated using a risk measure called value-at-risk (VaR). The VaR at level $\alpha \in (0,1)$ for a loss random variable $X$ is defined as
\begin{align*}
    \var{\alpha}{X}
    = \min\{z\in\mathds{R}: F_X(z)\geq \alpha\},
\end{align*}
where $F_X: \mathds{R}\rightarrow[0,1]$ is the cumulative distribution function of $X$. Optimization with Var constraints has limitations in modelling and tractability aspects for various reasons including:
\begin{itemize}
    \item VaR does not control scenarios exceeding VaR.
    \item VaR fails to meet the subadditivity axiom, so it is not ``coherent''. ``coherent'' is a desirable properties for risk measures proposed by \cite{artzner1999coherent}.
    \item Evaluation of $\mathrm{VaR}_{1-\delta}\{\phi(\bm{x},\bm{\xi})\}$ offen involves integration over $\bm{\xi}$, which is computationally intractable.
\end{itemize}


For these reasons, a second risk measure called conditional value at risk (CVar) is motivated for such risk-constrained optimization problems.
The CVaR at level $\alpha \in (0,1)$ for a loss random variable $X$ is defined as
\begin{equation}
\begin{align*}
    \cvar{\alpha}{X} = 
    \frac{1}{1-\alpha}
    \int_{\alpha}^{1} 
    \mathrm{VaR}_{\beta}\{X\} d\beta.
\end{align*}
\end{equation}

Specifically, we concentrate on the following CVaR constrained optimization problem:
\begin{equation}
\begin{align}
\label{eq-cvar-opt}
\begin{array}
[c]{ll}%
\mbox{minimize} & \bm{c}^{T}
\bm{x}\\
\mbox{subject to} & 
\cvar{1-\gamma}{\phi(\bm{x},\bm{\xi})}
\leq 0.\\
\end{array}
\end{align}
\end{equation}


You can download the final paper for my work [here](https://anish-senapati.github.io/assets/pdf/SURF_2020_Final_Project.pdf) here. 