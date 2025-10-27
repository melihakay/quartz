---
title: Eigendecomposition
draft: false
description:
aliases:
tags:
  - linear-algebra
  - "#mathematics"
date:
---

>[!info] Definition
>Eigendecomposition is factorization of a [[Matrix|matrix]] into the canonical form, where it is written by using it's [[Eigenvectors|eigenvectors]] and [[Eigenvalues|eigenvalues]]. 

>[!tip] Spectral decomposition
>If the factorized matrix $A$ is a [[Normal Matrix|normal]] or a [[Symmetric matrix|symmetric]] matrix, then the related decomposition if called [[Spectral Decomposition]].

Let $A$ be square $n \times n$ [[Matrix|matrix]] with $n$ [[Linear independence|linearly independent]] [[Eigenvectors|eigenvectors]] $e_{i}$. Then it can be factored as:

$$
Av = \lambda v
$$
$$
AQ = Q \Lambda
$$
$$
A = Q \Lambda Q^{-1}
$$
Note that only [[Diagonalizable Matrix|diagonalizable matrices]] can be factorized in this way.