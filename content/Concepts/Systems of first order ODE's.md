---
title:
draft: false
description:
aliases:
tags:
  - mathematics
  - linear-algebra
date:
---

>[!info] Definition
>Suppose that $x_{1}\dots x_{n}$ are functions of $t$. A set of $n$ differential equations of the form
>$$
>x_{i}' = f_{i}(x_{1}\dots x_{n}, t)
>$$
>is called a **system of first order [[Ordinary differential equation|ODE]]'s**. In all these equations $x_{i}'=\frac{dx_{i}}{dt}$.

A solution of a system of first order [[Ordinary differential equation|ODE]]'s is an $n$-tuple functions $(x_{1}(t)\dots x_{n}(t))$. Note that one cannot simply evaluate each function separately since each depend on others. 

We call an initial condition a specification of each function $x_{i}(t_{0}) = x_{i,0}$.

Check [[Existence-uniqueness theorem for differential equations#Existence-uniqueness for systems of first order ODE's|Existence-uniqueness for systems of first order ODE's]] for the conditions.

# Linear systems

>[!info] Recall that a first order [[Ordinary differential equation|ODE]] is said to be linear if it can be written as $y' + p(t)y = q(t)$. See [[Linear equations]].

>[!info] Definition
>A system of first order [[Ordinary differential equation|ODE]]'s said to be linear if it can be written in the form of 
>$$
>\begin{align*}
> x_{1}' &= a_{11}(t)x_{1} + a_{12}(t)x_{2} + \dots + a_{1n}(t)x_{n} + b_{1}(t) \\
> x_{i}' &= a_{i1}(t)x_{1} + a_{i2}(t)x_{2} + \dots + a_{in}(t)x_{n} + b_{i}(t) \\
> x_{n}' &= a_{n1}(t)x_{1} + a_{n2}(t)x_{2} + \dots + a_{nn}(t)x_{n} + b_{n}(t)
\end{align*}
>$$
>for some functions $a_{ij}(t)$ and $b_{i}(t)$. 
>
>Furthermore if $b_{i}(t) = 0$ for $\forall i$ then system is called a **homogeneous system**.
>
>Check [[Existence-uniqueness theorem for differential equations#Existence-uniqueness for systems of first order ODE's|Existence-uniqueness for systems of first order ODE's]] for the conditions.





