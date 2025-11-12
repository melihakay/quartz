---
title:
draft: false
description:
aliases:
  - inner product
tags:
  - mathematics
  - linear-algebra
date:
---

>[!info] Definition
>Standard inner product is defined as following for two vectors $x,y\in C^n$
>$$ \langle x,y \rangle = xy^*$$
>Observe that $x\in C^{1\times n}$ and $y \in C^{n\times 1}$. Then the result is a single [[Complex Numbers|complex number]].
>$$ \langle x,y \rangle = \sum_{i=1}^n x_{i}\bar{y}_{i} $$

# Properties

- $\langle x,y \rangle = \overline{\langle y,x \rangle}$
- $\langle x,y+z \rangle=\langle x,y \rangle + \langle x,z \rangle$
- $\langle cx,y \rangle = c\langle x,y \rangle$
- $\langle x,cy \rangle=\bar{c}\langle x,y \rangle$
- $\langle x,x \rangle \geq 0$
- $\langle x,x \rangle=0 \iff x=0$

