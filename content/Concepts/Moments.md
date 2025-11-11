---
title:
draft: false
description:
aliases:
  - moment
  - central moment
tags:
  - statistics
  - mathematics
date:
---

>[!info] Definition
>$r$-th moment is defined as
>$$
>m_{r} = E[X^r]
>$$

>[!info] Definition
>$r$-th central moment is defined as 
>$$
>\mu_{r} = E[(X-\mu)^2]
>$$

## Mean and variance

First moment is the $m_{1} = \mu$ [[Expected value|mean]]. And the first central moment is $0$.
$$
m_{1} = \mu = E[X^{1}]
$$
$$
\mu_{1} = E[X-\mu] = E[X] - E[\mu] = \mu - \mu = 0
$$
Second central moment is [[Variance & Covariance|variance]]
$$
\mu_{2} = E[(X-\mu)^2] = E[X^2] - E[X]^2 = m_{2} - m_{1}^2
$$
then
$$
m_{2} = E[X^2] = \mu_{2} + m_{1}^2 = \sigma^{2} + \mu^2
$$
Note that $V(X)=0$ if $X$ is [[Degenerate random variable |degenerate]]

>[!tip] Recursive calculation
>If one knows $m_{1},m_{2} \dots m_{k}$ then $\mu_{1},\mu_{2} \dots \mu_{k}$ can be computed
>$$
>\mu_{k} = E[(X-\mu)^k] 
> = m_{k} 
> - \begin{pmatrix}k \\ 1\end{pmatrix}\mu m_{k-1}
> +  \begin{pmatrix}k \\ 2\end{pmatrix}\mu^{2} m_{k-2}
> \dots
> + (-1)^k\mu^{k}
>$$
>and vice versa
>$$
>m_{k} = E[(X-\mu+\mu)^k] 
> = \mu_{k} 
> + \begin{pmatrix}k \\ 1\end{pmatrix}\mu \mu_{k-1}
> +  \begin{pmatrix}k \\ 2\end{pmatrix}\mu^{2} \mu_{k-2}
> \dots
> +\mu^{k}
>$$
 
 # Remarks

1. For some random variables moments up to some order exists.
2. If the moment of order $k$ exists for a [[Random variable|rv]] then $m_{s}$ exists for all $0 \leq s \leq k$.