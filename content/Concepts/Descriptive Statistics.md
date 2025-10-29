---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---
Let our data be:

$$
X =
\begin{bmatrix}
x_{1,1} &x_{1,2} &x_{1,3} &\dots &x_{1,p} \\

\dots \\
x_{n,1} &x_{n,2} &x_{n,3} &\dots &x_{n,p} \\
\end{bmatrix}
$$

# Sample mean

$$
\bar{X} = \begin{bmatrix}
\bar{x_{1}}  \\
\bar{x_{2}} \\
\vdots  \\
\bar{x_{p}}
\end{bmatrix}_{p \times 1}
$$
where each $x_{i}$ is another random variable. [[Expected Value]].
$$
\bar{x_{i}} = \frac{1}{n}\sum_{j=1}^n x_{ji} \text{ for } i=1,2,\dots,p
$$
# Variance-Covariance Matrix

We denote sample [[Variance & Covariance]] in a matrix of size $p \times p$.

$$
S_{n} = \begin{bmatrix}
s_{11} & s_{12} & \dots  & s_{1p} \\
\vdots & \ddots \\
s_{p1} & s_{p2} & \dots  & s_{pp}
\end{bmatrix}
$$
Here any $s_{ii}$ denote the variance of variable $i$ and any $s_{ij}$ denote the covariance between variable $i$ and $j$.

$$
s_{ij} = \frac{1}{n} \sum_{k=1}^n
[
(s_{ki} - \bar{x_{k}})
(s_{kj} - \bar{x_{j}})
]
\text{ for }
i,j \in 1,2,\dots,p
$$
## Sample Correlation

$$
R = \begin{bmatrix}
1 & r_{12} & \dots & r_{1p} \\
r_{21} & 1 & \dots & r_{2p} \\
\vdots & \vdots & \ddots & r_{3p} \\
r_{p1} & \dots & \dots & 1
\end{bmatrix}_{p \times p}
$$
where,
$$
r_{ij} = 
\frac{Cov(x_{i},x_{j})}
{\sqrt{ V(x_{i}) } \sqrt{ V(x_{j}) }}
= 
\frac{s_{ij}}
{\sqrt{ s_{ii} } \sqrt{ s_{jj} }}
$$
See [[Pearson correlation coefficient]].