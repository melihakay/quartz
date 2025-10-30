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
>We say that $B$ is an inverse of $A$ if 
>$$
>AB=BA=I
>$$
>and it is denoted as $A^{-1}$ if it exists.

>[!tip] Check [[Invertibility of a matrix]] for the existence of $A^{-1}$

>[!warning] Inverse of matrix is unique, if it exists
>Suppose that both $B_{1},B_{2}$ are inverses of $A$. Then
>$$
>B_{1} = B_{1}I = B_{1}(AB_{2}) = (B_{1}A)B_{2} = IB_{2} = B_{2}
>$$

$$
A^{-1} = \frac{1}{\det{A}}adj(A)
$$
where $adj(A)$ is [[Adjugate Matrix]] of $A$.