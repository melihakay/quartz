---
title:
draft: false
description:
aliases:
tags:
  - linear-algebra
  - mathematics
date:
---

>[!info] Definition
>A [[Symmetric matrix|symmetric matrix]] $A$ is said to be
>- Positive definite $\iff$ $X^TAX>0$ for $X \neq 0$
>- Non-negative definite $\iff$ $X^TAX \geq 0$ for $X \neq 0$
>where $X^T A X$ is the [[Quadratic form]]

## Checking with Eigendecomposition

$$
A = \sum \lambda_{i}e_{i}e_{i}^T
$$
$$
X^TAX = \sum \lambda_{i}x^Te_{i}e_{i}^Tx
$$
$$
= \sum \lambda_{i}y_{i}y_{i}^T
$$
$$
= \sum \lambda_{i}y_{i}^2 > 0 \iff \forall \lambda_{i} \geq 0
$$
Thus, if all the [[Eigenvalues|eigenvalues]] of a [[Symmetric matrix|symmetric matrix]] if greater than the zero, then it is a positive definite matrix.

