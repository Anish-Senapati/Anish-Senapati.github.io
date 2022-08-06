---
layout: page
title: Signomial Optimization
description: Constraint generation of Power Cones
img: /assets/img/cut_generation.png
importance: 1
category: work
---

Certifying function nonnegativity is a prevalent problem in applied mathematics with applications in optimization and engineering. 

A signomial is a function $$f$$ defined by 

$$ \bf{x} \mapsto \sum_{i=1}^m c_i e^{(\bf{a}_i \cdot \bf{x})} $$ 

for $$c \in \mathbf{R}^m$$ and vectors $$ \bf{a}_i \in \mathbb{R}^n $$.

Signomial programming (SP) is a prevalent problem in aircraft design and structural engineering. Additional applications in EE, communications, and ML.

In general, a signomial optimization problem is intractable. So how do we approach solving these problems? We look at very specific cases of such signomial programs.
For instance, what is we limited ourself to signomials which only have one negative term? Or what if we limited the domain of the optimimization problem?

For a signomial $$f(\bf{x}) = \sum_{i=1}^m c_i \exp(\bf{a}_i^\intercal \bf{x})$$, if $$\bf{c} \in \mathbb{R}^m$$ has $$\bf{c}$$ has at most one negative term, then we call such a signomial $$ \textbf{AGE}$$. 
A signomial is called $$\textbf{SAGE}$$ if it is the sum of AGE signomials.


SAGE-based optimization techniques are traditionally done with a type of convex optimization called relative entropy programming.
This project focused on developing a new way to optimize SAGE signomials. We proposed and optimized an efficient cut generation approach to identify and add power cones into the nonnegativity cone of interest.


You can download the final paper for my work [here](https://anish-senapati.github.io/assets/pdf/SURF_2021.pdf). 