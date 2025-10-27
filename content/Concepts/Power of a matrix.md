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
# Using [[Spectral Decomposition]]

Suppose that $A$ is a [[Symmetric matrix|symmetric matrix]]. Then it can be written as 
$$
A = \sum \lambda_{i}e_{i}e_{i}^T
$$
where $e_{i}$'s are normalized [[Eigenvectors|eigenvectors]].

Then a n-th power of $A$ can be expressed as 
$$
A^n = \sum \lambda_{i}^n e_{i} e_{i}^T
$$
$$
A^n = Q \Lambda^nQ^T
$$
and since $\Lambda$ is a [[Diagonal Matrix|diagonal matrix]] it's power can be found by
$$
(\Lambda^n)_{ii} = (\Lambda_{ii})^n
$$
One can even find the [[Inverse of a matrix]] by setting $n=-1$:
$$
A^n = Q \Lambda^{-1} Q^T
$$
>[!example] Square root of a matrix
>$$ A^{1/2} = Q \Lambda^{1/2} Q^T $$

