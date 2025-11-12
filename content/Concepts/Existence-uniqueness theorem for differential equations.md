---
title:
draft: false
description:
aliases:
tags:
  - mathematics
date:
---

# Existence-uniqueness for systems of first order ODE's

>[!info] Theorem
>Consider a system of first order [[Ordinary differential equation|ODE]]'s. $\frac{dx_{i}}{dt} = f_{i}(x_{1}\dots x_{n, t})$ together with the initial condition vector $X(t_{0}) = X_{0}$. Now assume that
>- Each $f_{i}(x_{1}\dots x_{n,t})$ and
>- Each $\frac{\partial f_{i}}{\partial x_{j}}(x_{1}\dots x_{n}, t)$ is continuous on a open rectangular box $\in R^{n+1}$ containing $X_{0}$.
>Then there is a unique solution of this initial value problem and the solution is valid in some open interval containing $t_{0}$.

>[!info] Theorem for linear systems
>Consider a system of first order [[Ordinary differential equation|ODE]]'s. $\frac{dx_{i}}{dt} = f_{i}(x_{1}\dots x_{n, t})$ together with the initial condition vector $X(t_{0}) = X_{0}$. 
>$$
>\begin{align*}
> x_{1}' &= a_{11}(t)x_{1} + a_{12}(t)x_{2} + \dots + a_{1n}(t)x_{n} + b_{1}(t) \\
> x_{i}' &= a_{i1}(t)x_{1} + a_{i2}(t)x_{2} + \dots + a_{in}(t)x_{n} + b_{i}(t) \\
> x_{n}' &= a_{n1}(t)x_{1} + a_{n2}(t)x_{2} + \dots + a_{nn}(t)x_{n} + b_{n}(t)
\end{align*}
>$$
>Now assume that
>- Each $a_{ij}$ and $b_{i}$ are continuous for $t$ in an open interval $(\alpha,\beta)$.
>Then there is a unique solution of this initial value problem and the solution is valid over whole interval $(\alpha,\beta)$.


