---
layout: page
title: CVaR Optimization
description: Chance-constrained optimization for conditional value-at-risk problems
img: /assets/img/cvar_header.png
importance: 1
category: work
---
Within this project, we consider optimization problems with risk constraints, looking to confine the violation probability. These optimization problems can be formulated as,

$$
\begin{align}
\label{eq-chance-opt}
\begin{array}
[c]{ll}%
\mbox{minimize} & \textbf{c}^{T}
\textbf{x}\\
\mbox{subject to} & \mathrm{Prob} \{\phi(\textbf{x},\mathbf{\xi}) > 0\}\leq \delta.\\
\end{array}
\end{align}
$$

where $$\textbf{x}\in\mathbb{R}^{m}$$ is an $$m$$-dimensional decision variable, and $$\textbf{\xi}\in\mathbb{R}^{n}$$ is an $$n$$-dimensional random vector. 
The elements of $$\mathbf{\xi}$$ are often referred to as risk factors; the function $$\phi: \mathbb{R}^{m}\times\mathbb{R}^{n}
\rightarrow\mathbb{R}$$ is often assumed to be convex in $$\textbf{x}$$ and models a cost constraint; the parameter
$$\delta> 0$$ is the risk level of the tolerance.


The probabilistic constraint in $$\eqref{eq-chance-opt}$$ can be reformulated using a risk measure called value-at-risk (VaR). The VaR at level $$\alpha \in (0,1)$$ for a loss random variable $$X$$ is defined as


$$
\begin{align*}
    \mathrm{VaR}_{\alpha}{X}
    = \min\{z\in\mathbb{R}: F_X(z)\geq \alpha\},
\end{align*}
$$


where $$F_X: \mathbb{R}\rightarrow[0,1]$$ is the cumulative distribution function of $$X$$. Optimization with Var constraints has limitations in modelling and tractability aspects for various reasons including:
* VaR does not control scenarios exceeding VaR.
* VaR fails to meet the subadditivity axiom, so it is not 'coherent'. 'coherent' is a desirable properties for risk measures.
* Evaluation of $$\mathrm{VaR}_{1-\delta}\{\phi(\textbf{x},\mathbf{\xi})\}$$ usually involves integration over $$\textbf{\xi}$$, which is computationally intractable.


For these reasons, a second risk measure called conditional value at risk (CVar) is motivated for such risk-constrained optimization problems.
The CVaR at level $$\alpha \in (0,1)$$ for a loss random variable $$X$$ is defined as

$$
\begin{align*}
    \mathrm{CVaR}_{\alpha}{X} = 
    \frac{1}{1-\alpha}
    \int_{\alpha}^{1} 
    \mathrm{VaR}_{\beta}\{X\} d\beta.
\end{align*}
$$

The graph below displays a more intuitive difference between VaR and CVaR for the same loss function.

![image](/assets/img/cvar_header.png)

Initially introduced by Nemirovski and Shapiro, they showed CVaR is a tight convex approximation of VaR. Thus, the CVaR constrained optimization 
problem accounts for many of the limitations VaR constraints possess making it an appealing approximation to 
solve. Specifically, we concentrate on the following relaxed CVaR constrained optimization problem:

$$
\begin{align}
\label{eq-cvar-opt}
\begin{array}
[c]{ll}%
\mbox{minimize} & \textbf{c}^{T}
\textbf{x}\\
\mbox{subject to} & 
\mathrm{CVaR}_{1-\gamma}{\phi(\textbf{x},\mathbf{\xi})}
\leq 0.\\
\end{array}
\end{align}
$$

As CVaR is a convex approximation of VaR, $$\eqref{eq-cvar-opt}$$ is a convex approximation of 
$$\eqref{eq-chance-opt}$$

You can download the final paper for my work [here](https://anish-senapati.github.io/assets/pdf/SURF_2020_Final_Project.pdf). 