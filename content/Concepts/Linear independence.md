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
>A set of vectors $x_{1}\dots x_{n}$ are said to be linearly independent if there is no vector in the set that is a linear combination of the others.

$$
\sum_{i=1}^n a_{i}v_{i} = 0
$$
System is linearly independent $\iff$ $\forall a_{i} = 0$.

System if dependent if there exists a linear combination with coefficients different from 0.

>[!tip]
>Suppose that you have a matrix $Ax=b$ and you would like to see if $A$ is linearly dependent. 
>Let $v_{1}\dots v_{n}$ be column vectors of $A$. Then $\sum c_{i}v_{i}$ yields 
>$$ Ac = 0 $$ 
>where $c$ is the coefficients for each row vector.  Then this matrix $A$ is linearly independent if $A$ doesn't have any zero-rows, meaning that $\det A\neq0$.
>One can say that here $A$ is the matrix for a [[Systems of linear equations|linear system]] and each $v_{i}$ denote the coefficients of $x_{i}$ on all equations.

>[!tip] By using [[Wronskian]]
>Theorem says that if the [[Wronskian]] of a set of functions is not zero even for one value of $t$ then the set of functions are linearly independent.
>

