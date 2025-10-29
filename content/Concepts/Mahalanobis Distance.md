---
title:
draft: false
description:
aliases:
  - Statistical Distance
tags:
  - statistics
  - mathematics
date:
---
# Mahalanobis Distance

>[!info] Definition
>Let X be the probability distribution, then
>$$
>d(P, Q; X) = (P-Q)^T \Sigma^{-1}_{X} (P-Q)
>$$
>and,
>$$
>d(P; X) = d(P, \bar{x}; X)
>$$
>See statistical distance below.

# Statistical Distance

>[!info] Definition
>Assume that $x_{1}\dots x_{n}$ are independent. In statistical distance we give importance to each axis that is inversely proportional to the standart deviation in the axis.
>$$
>d(p, q) = \sqrt{ \sum_{i=1}^n \frac{(p_{i} - q_{i})^2}{s_{ii}} }
>$$
>where $s$ is the [[Variance & Covariance|variance]] of $i$th observation.
>Actually such distance can be stated as 
>$$
>d(p, q) = \sqrt{ \sum_{i=1}^n \left( \frac{p_{i} - q_{i}}{\sqrt{ s_{ii} }} \right)^2 }
>$$
>where $\frac{p_{i} - q_{i}}{\sqrt{ s_{ii} }}$ is the standardized coordinate in that axis.

Now consider that $x_{1}\dots x_{n}$ are **not** independent. Then we rotate the coordinate system $(x_{1}, x_{2})$ with an angle of $\theta$ so that 
$$
\begin{align}
\tilde{x_{1}} &= x_{1}\cos \theta + x_{2} \sin \theta \\

-\tilde{x_{2}} &= x_{1}\sin \theta + x_{2} \cos \theta
\end{align}
$$
so that 
$$
d(0,p) = \sqrt{ \sum_{i=1}^k \frac{\tilde{x_{i}}^2}{\tilde{s}_{ii}} }
$$
where $\tilde{s}_{ii}$ is the sample [[Variance & Covariance|variance]] computed with respect to $\tilde{x}_{i}$'s.

