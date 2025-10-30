---
title:
draft: false
description:
aliases:
tags:
  - statistics
  - mathematics
date:
---
In general we can partition the $k$ characteristics contained in a $p \times 1$ random vector $X$ into several groups of arbitrary sizes.

$$
\begin{align}
X &= \begin{bmatrix}
X_{1} \\
X_{2} \\
X_{3} \\
\vdots \\
X_{n}
\end{bmatrix}
\end{align}
$$
Assume that $X_{1} \dots X_{q}$ belong to personal traits and $X_{p+1}\dots X_{n}$ belong to physical traits. Then we can denote $X$ as:
$$
X = \begin{bmatrix}
X_{(1), q \times 1} \\
X_{(2), n-q \times 1} \\
\end{bmatrix}_{n \times 1}
$$
Then the expectation is:
$$
\mu = E[X] = \begin{bmatrix}
\mu_{1} \\
\vdots  \\
\mu_{q} \\ 
\hline 
\mu_{q+1} \\
\vdots \\
\mu_{n}
\end{bmatrix}
= 
\begin{bmatrix} 
\mu_{(1)} \\
\hline
\mu_{(2)}
\end{bmatrix}
$$
and the $\Sigma$ is

$$
\Sigma_{n\times n} = 
E[ (X-\mu)_{n \times 1} (X-\mu)^T_{1 \times n} ] 
$$
$$
\Sigma = \begin{bmatrix}
\Sigma_{(11)}^{q \times q} & \Sigma_{(12)}^{q \times p-q} \\
\Sigma_{(21)}^{p-q \times q} & \Sigma_{(22)}^{p-q \times p-q}
\end{bmatrix}_{n \times n}
$$
