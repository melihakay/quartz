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
>Let $A\in R^{n\times n}$ or $\in C^{n\times n}$. Then the determinant of $A$, denoted by $\det A$ can be computed on the first row by:
>$$
>\det A = \sum_{j=1}^n (-1)^{j-1} a_{1j}\det A_{1j}
>$$
>$$
>\det A = \sum_{j=1}^n (-1)^{j-1} a_{ij}M_{ij}
>$$
>where $M_{ij}$ is the [[Minor of a Matrix|minor]].

# Effects of elementary row operations on determinants

- $cR_{i} \to R_{i} \implies \det(A^*) = c\det(A)$
- $R_{i} \leftrightarrow R_{j} \implies \det(A^*) = -\det(A)$
- $cR_{i} + R_{j} \to R_{j} \implies \det(A^*) = \det(A)$