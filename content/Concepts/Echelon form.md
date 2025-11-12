---
title:
draft: false
description:
aliases:
  - row echelon form
tags:
  - mathematics
  - linear-algebra
date:
---
 
>[!info] Definition
> We say that a [[Matrix|matrix]] is in **row echelon form** if
> - The first non-zero entry of each row is $1$. (All zeroes are allowed)
> - All entries which are directly below a **leading $1$** are $0$.
> - If $i<j$ then the leading $1$ on row $i$ must be be to the left of the leading $1$ of the row $j$.
> - If there are $k$ rows of $0$'s in the matrix, then these must be the last $k$ rows.

$$
\begin{bmatrix}
1 & 1 &2  \\
0 & 1 & 0
\end{bmatrix}
$$
is an example.