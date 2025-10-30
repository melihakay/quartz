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
>[!success] Recall
>Recall the univariate case: [[Univariate normal distribution]].
>$$
>f(x|\mu,\sigma^2) = 
>\frac{1}{\sqrt{ 2\pi \sigma^2 }} \exp\left( -\frac{1}{2} \frac{(x-\mu)^2}{\sigma^2} \right)
>$$

Now here, $\sqrt{ 2\pi \sigma^2 }$ and $\frac{(x-\mu)^2}{\sigma^2}$ both should result in scalar.

>[!note] Note that $\frac{(x-\mu)^2}{\sigma^2}=(x-\mu)\sigma^{-2}(x-\mu)$ is the square distance between $x$ and $\mu$. See [[Mahalanobis Distance|Statistical Distance]].
>a
>Let us generalize this to a random vector of size $p\times 1$:
>$$
>(x-\mu)^T\Sigma^{-1}(x-\mu)
>$$
>Here, $\Sigma^{-1}$ is called [[Precision matrix]].

Then for any random vector $X$, p-dimensional multivariate normal density is:
$$
f(X|\mu, \Sigma) =
\frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}}
\exp\left( -\frac{1}{2} (X-\mu)^T\Sigma^{-1}(X-\mu) \right)
$$
and it is denoted by
$$
X \sim N_{p}(\mu, \Sigma)
$$
One can show a $N_{2}$ distribution visually as following:

![[Multivariate normal.png]]

## Bivariate Normal Density 

![[Pasted image 20251030145514.png]] 

First check $\Sigma^{-1}$:

$$
\Sigma^{-1} = \frac{1}{\det \Sigma}adj(\Sigma)
$$
where $adj$ is the [[Adjugate Matrix]].

Recall that $\rho_{12} = \frac{\sigma_{12}}{\sqrt{ \sigma_{11} \sigma_{22} }}$. Then,

$$
\begin{align} 

\Sigma^{-1} &= \frac{1}{\sigma_{11}\sigma_{22} - \sigma_{12}^2}
\begin{bmatrix}
\sigma_{22} & -\sigma_{12} \\
-\sigma_{21} & \sigma_{11}
\end{bmatrix} \\
&=\frac{1}{\sigma_{11}\sigma_{22}(1-\rho_{12}^2)}
\begin{bmatrix}
\sigma_{22} & -\rho_{12}\sqrt{ \sigma_{11}\sigma_{22}}  \\
-\rho_{21} \sqrt{ \sigma_{11}\sigma_{22} } & \sigma_{11}
\end{bmatrix} \\
&=\frac{1}{1-\rho_{12}^2}  
\begin{bmatrix}
\frac{1}{\sigma_{11}} & -\frac{\rho_{12}}{\sqrt{ \sigma_{11}\sigma_{22} }} \\
-\frac{\rho_{12}}{\sqrt{ \sigma_{11}\sigma_{22} }} & \frac{1}{\sigma_{22}}
\end{bmatrix}
\end{align}
$$
Then,

$$
\begin{align}
(X-\mu)^T\Sigma^{-1}(X-\mu) &= 
\begin{bmatrix}
x_{1}-\mu_{1} & x_{2}-\mu_{2}
\end{bmatrix}
\Sigma^{-1}
\begin{bmatrix}
x_{1}-\mu_{1} \\
x_{2}-\mu_{2}
\end{bmatrix} \\
&=\frac{1}{1-\rho_{12}^2}\left[ 
\left( \frac{x_{1}-\mu_{1}}{\sqrt{ \sigma_{11} } } \right)^2 + 
\left( \frac{x_{2}-\mu_{2}}{\sqrt{ \sigma_{22} }} \right)^2 - 
2\rho_{12}\left(\frac{x_{1}-u_{1}}{\sqrt{ \sigma_{11} }} \right)\left(\frac{x_{2}-u_{2}}{\sqrt{ \sigma_{22} }} \right)
\right]
\end{align}
$$
So the general form is
$$
f_{X}(X) = 
\frac{\exp\left[
\frac{-1}{2(1-\rho_{12}^2)}\left[ 
\left( \frac{x_{1}-\mu_{1}}{\sqrt{ \sigma_{11} } } \right)^2 + 
\left( \frac{x_{2}-\mu_{2}}{\sqrt{ \sigma_{22} }} \right)^2 - 
2\rho_{12}\left(\frac{x_{1}-u_{1}}{\sqrt{ \sigma_{11} }} \right)\left(\frac{x_{2}-u_{2}}{\sqrt{ \sigma_{22} }} \right)
\right]\right]}
{2\pi \sqrt{ \sigma_{11}\sigma_{22}(1-\rho_{12}^2) }}
$$
One can memorize that  by
$$
f_{X}(X) = \frac{\left( \exp \left[
-\frac{1}{2(1-\text{correlation}^2)}
\left[
d(x_{1})^2 + d(x_{2})^2 -2\text{ correlation }d(x_{1})d(x_{2})
\right]
\right] \right)}
{2\pi \sqrt{ \sigma_{11}\sigma_{22}(1-\text{correlation}^2) }}
$$
where $d()$ is [[Mahalanobis Distance|Statistical Distance]].

If $\rho_{12} = 0$ then,

$$
\begin{align}
f(x_{1},x_{2}) &= 
\frac{\left( \exp \left\{-\frac{1}{2} (d(x_{1})^2 + d(x_{2})^2) \right\} \right)}{2\pi \sqrt{ \sigma_{11}\sigma_{22} }} \\
&=\frac{1}{\sqrt{ 2\pi \sigma_{11} }}\exp\left( -\frac{1}{2}d(x_{1})^2 \right)\frac{1}{\sqrt{ 2\pi \sigma_{22} }}\exp\left( -\frac{1}{2}d(x_{2})^2 \right) \\
&=f(x_{1})f(x_{2})
\end{align}
$$
where $X_{1} \sim N(u_{1}, \sigma_{11})$ and $X_{2} \sim N(u_{2}, \sigma_{22})$ and they are independent.
