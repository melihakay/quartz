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

Let us have a linear system of

$$
\sum_{j=1} a_{ij}x_{j} = b_{i}
$$

where we have $m$ equations about $n$ variables. One can construct a matrix form as the following
$$
A_{m\times n}x_{n \times 1} = b_{m\times 1}
$$
>[!info] Definition
>We call 
>$$ \begin{bmatrix}
> A|b
>\end{bmatrix} $$
>the **augmented form** for the linear system.

# Solutions of square systems

Suppose that $A \in R^{n\times n}$. First we reduce the $A$ to [[Echelon form|row echelon form]] using [[Gaussian elimination]]. 

There are two scenarios

1. Some columns do note have leading $1$'s $\implies$ there are free variables
2. All columns have leading $1$'s $\implies$ system can be reduced into $I_{n}$ $\implies$ there are no free variables.
>[!info] Theorem
>A matrix $A$ is [[Invertibility of a matrix|invertible]] $\iff$ it can be row reduced into [[Identity matrix|identity matrix]].

Is the system is invertible then there exists a unique solution
$$
A^{-1}Ax = A^{-1}b \implies x = A^{-1}b
$$
Now, if the system is not invertible we have two possibilities

1. There are **no solutions** since a contradictory equation of $0 = c$, $c\neq 0$.
2. There are **infinitely many solutions** when there aren't any contradictory equations.

If the system is [[Homogeneous equations|homogeneous]], meaning that $b=0$ then there is only two possibilities:

1. $A$ is invertible $\iff Ax=0$ has a unique solutions, namely $x=0$, which is the **trivial solution**
2. $A$ is not invertible $\iff Ax=0$ has infinitely many solutions ($\det A=0$). Then the system is said to have **non-trivial solutions**.