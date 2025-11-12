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
>Eigenvalues can be interpreted as the scaling coefficients of the related [[eigenvectors]]. 
>
>They are defined by the solution of n-th degree polynomials $\det(A-\lambda I)=0$. 

Also known as characteristic roots and latent roots.

>[!tip] Complex eigenvalues
>Sometimes this polynomial have [[Complex Numbers|complex]] roots. In such case one should only find one root $\lambda_{1}$ and calculate other root as $\lambda_{2} = \bar{\lambda}_{1}$. Therefore we can say that complex eigenvalues and eigenvectors appear in [[Complex Conjugate|complex conjugate]] pairs.
>
>$$
\begin{align*}
Av &= \lambda v \\
\overline{Av} &= \overline{\lambda v} \\
A \bar{v} &= \bar{\lambda} \bar{v}
\end{align*}
$$
