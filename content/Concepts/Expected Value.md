---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---

>[!info] Definition
>Centeroid of $f_{X}(x)$. 
> 	
>Mathematical expectation of a discrete random variable $X$ is defined as:
>$$
>E[X] = \sum_{i=1}^{\infty} x_{i} P(X=x_{i})
>$$
>if $\sum_{i=1}^{\infty} |x_{i}| P(X=x_{i}) < \infty$, in other words if it converges. Otherwise $E[X]$ doesn't exist.
>Similarly,
>$$
>E[X] = \int xf(x)dx
>$$
>if $\int |x|f(x)dx < \infty$.

>[!tip] Existence with bounded random variable.
>If $X$ is bounded, $P(|X|<M)=1$, then the $E[X]$ exists.

>[!info] Existence 
>For any [[rv]] $X$, $E[X] < \infty$ if and only if the integrals $\int_{0}^{\infty} P(X>x)dx$ and $\int_{-\infty}^{0}P(X\leq x)$ both converge. Then
>$$
>E[X] = \int_{0}^{\infty} P(X>x)dx - \int_{-\infty}^{0}P(X\leq x)
>$$

>[!info] Definition
>Let $Y=\{y_{ij}\}$ be $n \times p$ [[Matrix|matrix]]. Then,
>$$
>E[Y] = \{ E[y_{ij}] \}
>$$

# Properties

- $E[X+Y] = E[X] + E[Y]$
- $E[aX + bY] = aE[X] + bE[Y]$
- $E[A X B ] = A E[X] B \neq A B E[X]$ (multivariate case)
- $L \leq X \leq U \implies L \leq E[X] \leq U$
- $|E[X]| \leq E[|X|]$
- $Y=g(X)\implies E[Y] = E[g(X)] = \int g(x)f(x)dx$

Note that if $g(x) < h(x)$ then $E[g(x)] < E[h(x)]$ for all $x$.

>[!tip] Expectation for non-negative [[rv]]
>Let $X$ be a non-negative [[rv]]. Then 
>$$
>E[X] = \int_{0}^{\infty} [1-F(X)]dx
>$$

