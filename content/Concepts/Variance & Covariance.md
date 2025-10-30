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

# Variance

>[!info] Definition
>$$
>V(X) = E[(X-\mu)^2]
>$$
## Properties

$$
\begin{align}
V(aX +bY) &= E[ ((aX + bY) - (a\mu_{x} + b\mu_{y}) )^2] \\
&=E[ (a(X - \mu_{x}) + b(Y- \mu_{y}))^2] \\
&=E[a^2(X-\mu_{x})^2 + b^2(Y-\mu_{y})^2 + 2ab(X-\mu_{x})(Y-\mu_{y})] \\
&=a^2E[(X-\mu_{x})^2] + \dots \\
&=a^2V(X) + b^2V(Y) + 2abCov(X,Y) \\
&=a^2\sigma_{x} + b^2\sigma_{y} + 2ab\sigma_{12}
\end{align}

$$

# Covariance

>[!warning] If $x_{i}, x_{j}$ are independent then $\Sigma_{ij}=0$. Converse is not true in general. But if both follow independent normal distributions, then $\Sigma_{ij} \implies \text{ independence }$.

$$
\begin{align}
Cov(x_{1}, x_{2}) &= E[(x_{1}-\mu_{1})(x_{2}-\mu_{2})]\\
&= E[x_{1}x_{2}] - E[x_{1}]E[x_{2}]
\end{align}

$$
>[!tip] Remark
>Always keep in mind that $Var(x_{1}) = Cov(x_{1},x_{1})$  

## Properties

Observe that 

$$
\begin{align}
Cov(aX, bY) &= E[a(X-\mu_{X})b(Y-\mu_{Y})] \\
&= abE[(X-\mu_{X})(Y-\mu_{Y})] \\
&= abCov(X,Y)
\end{align}
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

# Linear combination of variables

Let $C = \begin{bmatrix}a & b\end{bmatrix}$. Then the linear combination $aX_{1} + bX_{2}$ can be written as 
$$
CX = aX_{1} + bX_{2}
$$
Then the [[Expected Value]] becomes
$$
E[CX] = CE[X] = C\mu _{X}
$$
And the variance we use [[Quadratic form]] to construct the variance matrix:

$$
V(aX_{1}, bX_{2}) = V(CX) = C\Sigma C^T
$$
Observe that 
$$
\begin{align}
C\Sigma C^T &= 
\begin{bmatrix}
a & b
\end{bmatrix} 
\begin{bmatrix}
\sigma_{11} & \sigma_{12} \\
\sigma_{21} & \sigma_{22}
\end{bmatrix} 
\begin{bmatrix}
a \\
b
\end{bmatrix}  \\
&= \sigma_{11}a^2 + \sigma_{22}b^2 + 2\sigma_{12}ab
\end{align}
$$

### Extension to linear systems

Let
$$
z_{i} = c_{i1}x_{1} + c_{i_{2}}x_{2} + \dots + c_{ip}x_{p}
$$
where $i \in 1 \dots q$. One can construct $C_{q\times p}$ matrix so that system becomes
$$
Z_{q \times 1} = C_{q \times p} X_{p \times 1} = \begin{bmatrix}
c_{11} & c_{12} & \dots & c_{1p} \\
\vdots & \vdots & \vdots & \vdots \\
c_{q1} & c_{q2} & \dots & c_{qp} \\
\end{bmatrix} 
\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots  \\
x_{p}
\end{bmatrix}
$$
then,
$$
\mu_{Z} = E[CX] = CE[X] = C\mu_{X}
$$
$$
\Sigma_{Z} = Cov(Z) = Cov(CX) = C^TCov(X)C = C\Sigma_{X}C^T
$$