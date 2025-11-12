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

>[!warning] Do not confuse with [[Matrices of functions]].

# Polynomials of functions

Let $A$ be matrix and $p(x) = x^3+2x+2$. Then
$$
p(A) = A^3+ 2A + 2I
$$

# Matrix exponential

>[!tip] Recall the [[Taylor expansion]] of the exponential function $e^x=\sum_{n=0}^\infty \frac{x^n}{n!}$.

Let $A$ be a $n\times n$ matrix. Then
$$
e^{At} = \sum_{n=0}^\infty \frac{A^nt^n}{n!} = I + At + \frac{A^2t^2}{2} + \frac{A^3t^3}{2\times 3} \dots
$$
>[!tip] Any constant matrix $A$ makes the above function convergent. Therefore $e^{At}$ is defined for any constant matrix $A$.

