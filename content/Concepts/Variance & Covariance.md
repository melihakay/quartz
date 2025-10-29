---
title:
draft: false
description:
aliases:
  - covariance
  - variance
tags:
  - statistics
date:
---
>[!warning] TODO
# Variance

$$
V(X) = E[(X-\mu)^2]
$$

# Covariance

>[!warning] If $x_{i}, x_{j}$ are independent then $\Sigma_{ij}=0$. Converse is not true in general. But if both follow independent normal distributions, then $\Sigma_{ij} \implies \text{ independence }$.

$$
Cov(x_{1}, x_{2}) = E[x_{1}x_{2}] - E[x_{1}]E[x_{2}]
$$

# Standard Deviation

$$
\sigma = \sqrt{ \text{variance} } = \sqrt{ V(x) } = \sqrt{ E[X-\mu]^2 }
$$
# Variance-Covariance Matrix

We denote variance-covariance in a matrix of size $p \times p$ by 
$$
Cov(X) = \Sigma = E[(x-\mu)(x-\mu)^T]
$$
$$
\Sigma = E\begin{bmatrix}
(x_{1}-\mu_{1})^2 & (x_{1}-\mu_{1})(x_{2}-\mu_{2}) & \dots  & (x_{1}-\mu_{1})(x_{p}-\mu_{p}) \\
\vdots & \ddots \\
(x_{p}-\mu_{p})(x_{1} - \mu_{1}) & (x_{p}-\mu_{p})(x_{2}-\mu_{2}) & \dots  & (x_{p}-\mu_{p})^2
\end{bmatrix}
$$
$$
\Sigma = \begin{bmatrix}
E[(x_{1}-\mu_{1})^2] & E[(x_{1}-\mu_{1})(x_{2}-\mu_{2})] & \dots  & E[(x_{1}-\mu_{1})(x_{p}-\mu_{p})] \\
\vdots & \ddots \\
E[(x_{p}-\mu_{p})(x_{1} - \mu_{1})] & E[(x_{p}-\mu_{p})(x_{2}-\mu_{2})] & \dots  & E[(x_{p}-\mu_{p})^2]
\end{bmatrix}
$$
$$
\Sigma = \begin{bmatrix}
\sigma_{11} & \sigma_{12} & \dots  & \sigma_{1p} \\
\vdots & \ddots \\
\sigma_{p1} & \sigma_{p2} & \dots  & \sigma_{pp} \\
\end{bmatrix}
$$
Here any $s_{ii}$ denote the variance of variable $i$ and any $s_{ij}$ denote the covariance between variable $i$ and $j$.

>[!tip] $\Sigma_{p \times p}$ is a [[Symmetric matrix|symmetric]] and positive semi-[[Definite matrix|definite]].

# Standard Deviation Matrix

$$
V^{1/2} = \begin{bmatrix}
\sqrt{ \sigma_{11} } & 0 & \dots & 0  \\
0 & \sqrt{ \sigma_{22} } & \dots & 0 \\
\vdots & \ddots & \ddots & 0 \\
0 & 0 & 0 & \sqrt{ \sigma_{pp} }
\end{bmatrix} = diag(\sqrt{ \sigma_{11} }, \dots, \sqrt{ \sigma_{pp} })
$$
## Relation with variance-covariance matrix

$$
\Sigma = v^{1/2}Pv^{1/2}
$$
thus, 
$$
P = (v^{1/2})^{-1} \Sigma (v^{1/2})^{-1}
$$
Think about univariate case:
$$
\begin{align}
\rho &= \frac{\sigma_{12}}{\sqrt{ \sigma_{11} }\sqrt{ \sigma_{22} }} \\
&= \sigma_{12} \sigma_{11}^{-1/2} \sigma_{22}^{-1/2} \\
&=  \sigma_{11}^{-1/2} \sigma_{12}  \sigma_{22}^{-1/2} 
\end{align}
$$