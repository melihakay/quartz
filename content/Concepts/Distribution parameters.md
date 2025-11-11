---
title:
draft: false
description:
aliases:
  - parameter
tags:
  - statistics
  - mathematics
  - probability-theory
date:
---

>[!info] Definition
>A **parameter** $\theta$ is a quantity which characterizes the distribution $f(x, \theta)$. 
>
>In the presence of multiple parameters we say that $\theta$ is vector containing these parameters. An example would be $N(\mu, \sigma^2) \rightarrow N(\theta_{1}, \theta_{2})$.
>
>**Parameter space** $\Omega$ is set of all possible values for the $\theta$.

>[!info] Parametric family of distributions
>Let $\theta \in \Omega$. Then such a family is defined by $\{f(x, \theta): \theta \in \Omega\}$. Any member of this family of distribution is denoted by $f(x, \theta)$ given that $\theta \in \Omega$.
>
>In other words to each $\theta \in \Omega$ there exists a pdf.

>[!example] Normal distribution as a parametric family
>Observe that 
>$$
>f(x, \theta) = \frac{1}{\sqrt{ 2 \pi } \theta_{2}} 
>\exp\left(-\left( \frac{x-\theta_{1}}{\theta_{2}} \right)^2 \right)
>$$
>$$
>\Omega = dom(\mu) \times dom(\sigma^2) = \mathbf{R} \times (0, \infty)
>$$
>A parametric family of distributions would be $\{N(\theta, 1): \theta \in \Omega\}$ given that $\Omega=\mathbf{R}$. 
