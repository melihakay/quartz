---
title:
draft: false
description:
aliases:
tags:
  - mathematics
  - statistics
date:
---

$$
P = \begin{bmatrix}
1 & \rho_{12} & \dots & \rho_{1p} \\
\rho_{21} & 1 & \dots & \rho_{2p} \\
\vdots & \vdots & \ddots & \rho_{3p} \\
\rho_{p1} & \dots & \dots & 1
\end{bmatrix}_{p \times p}
$$
where,
$$
\rho_{ij} = 
\frac{Cov(x_{i},x_{j})}
{\sqrt{ V(x_{i}) } \sqrt{ V(x_{j}) }}
= \frac{\sigma_{12}}{\sqrt{ \sigma_{11} } \sqrt{ \sigma_{22} }}
$$
observe that 
$$
\rho_{ii} = \frac{\sigma_{11}}{\sqrt{ \sigma_{11}^2 }} = 1
$$
>[!tip] R is [[Symmetric matrix|symmetric matrix]].

>[!warning] $R$ measures [[Linear Association]]. If $r_{ij}=0$, it means that there is no linear association but there might be any non-linear effect.

>[!info] R doesn't have any units of measurement and $r_{ij} \in [-1, 1]$. And it is invariant under linear transformation.
>$$
>\begin{align}
>y_{ij} &= ax_{ij} + b \\
> \implies cor(y_{i}, y_{j}) &= cor(x_{i}, x_{j})
>\end{align}
>$$

