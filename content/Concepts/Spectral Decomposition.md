---
title: Spectral Decomposition
draft: false
description:
aliases:
  - spectral analysis
tags:
  - linear-algebra
  - statistics
date:
---
>[!tip] Definition
>If the factorized matrix $A$ is a [[Normal Matrix|normal]] or a [[Symmetric matrix|symmetric]] matrix, then the related [[Eigendecomposition]] if called [[Spectral Decomposition]].


$$
Av = \lambda v
$$
$$
AQ = Q \Lambda
$$
$$
A = Q \Lambda Q^{-1}
$$

Suppose that $A$ is a [[Symmetric matrix|symmetric matrix]]. Then the $Q$ matrix consists on [[Orthogonal matrix|orthogonal]] [[Eigenvectors|eigenvectors]]. Then, 

$$
A = Q \Lambda Q^T
$$
>[!warning] In that case $Q$ should have normalized [[Eigenvectors|eigenvectors]] since we do not eliminate such constants by taking the inverse.

Alternatively,

$$
A_{k\times k} = \sum_{i=0}^n \lambda_{i}e_{i}e_{i}^T
$$
where each $e_{i}$ is the normalized [[Eigenvectors|eigenvector]] of $A$.
