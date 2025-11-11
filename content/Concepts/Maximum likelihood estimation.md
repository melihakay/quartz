---
title:
draft: false
description:
aliases:
  - MLE
tags:
  - statistics
date:
---

# Definition

Consider a random sample $\tilde{X}$ where $X_{1}\dots X_{n}$ are iid. [[rv]]s. from a distribution with a probability density function $f_{X}(x;\theta)$, $\theta \in \Omega$. The joint pdf of $\tilde{X}$ is $\prod^n f_{X}(x_{i};\theta)$.

>[!info] Definition
>Likelihood function is defined by
>$$
>L(\theta; \tilde{X}) = \prod^n f_{X}(x_{i}; \theta) \geq 0
>$$
>and can be interpreted as probability that observed data $\tilde{X}$ can occur.

Our aim here is to maximize that likelihood function.

>[!info] Definition
>For a given observations $\tilde{X}$ a value $\hat{\theta}\in \Omega$  at which $L(\theta)$ is a maximum is called a **maximum likelihood estimate** for $\theta$.
>
>That is $\hat{\theta}_{MME}$ is the value of $\theta$ that satisfies 
>$$
>f(\tilde{X};\hat{\theta}) = \max_{\theta \in \Omega} L(\theta)
>$$

To find such $\theta$ one should:

- First solve $\frac{d}{d\theta}L(\theta) = 0$ for $\hat{\theta}$
- Then check maximum by $\frac{\partial^2}{\partial\theta^2} \ln L(\theta) < 0$.

In most cases differentiating the $L(\theta)$ is hard to do so. Therefore $\ln L(\theta)$ is used instead. Since $\ln L(\theta)$ is strictly increasing when $L(\theta)>0$, maximizing it will also maximize the $L(\theta)$.

## Multiple Parameters

If $\theta$ is a vector to be estimated, then solve
$$
\begin{align*}
\frac{\partial \ln L(\theta)}{\partial \theta_{1}} &= 0 \\
\frac{\partial \ln L(\theta)}{\partial \theta_{2}} &= 0 \\
\vdots \\
\frac{\partial \ln L(\theta)}{\partial \theta_{k}} &= 0
\end{align*}
$$
solve $k$ equations for $k$ estimations.

## Invariance property

If $\hat{\theta}$ is [[Maximum likelihood estimation|MLE]] for $\theta$ and $g(\theta)$ is a function of $\theta$, then $g(\hat{\theta})$ is MLE for $g(\hat{\theta})$.

## MLE at the boundary of $\Omega$

In such cases MLE exists but can not be obtained as a solution to the derivative.

>[!example] Example
>Take $X_{1}\dots X_{n} \sim U(0, \theta)$. What is the MLE of $\theta$?
>$$
> \frac{d}{d\theta} \ln L(\theta) = \frac{d}{d\theta}\ln \prod^n \left( \frac{1}{\theta} \right) = \frac{d}{d\theta} -n\ln \theta = 0
>$$
>$$
>\implies -\frac{n}{\theta} = 0
>$$
>there is no finite solution for $\theta$.
>
>But observe that $L(\theta) = \frac{1}{\theta^n}$ implying that minimizing $\theta$ would maximize the likelihood. But one should consider that $x_{(i)} \leq\theta$. So choosing the minimum value that covers all the values in $\tilde{X}$ would ensure the maximum likelihood.
>Then, 
>$$ \hat{\theta}_{MLE} = X_{(n)} $$

# Advantages-disadvantages

>[!success] Advantages
>- It makes sense.
>- Widely used
>- Can also be used where observed values are not independent or iid.
>- Gives good measures for large sample sizes.

>[!failure] Disadvantages
>- $f(x;\theta)$ must be known
>- MLE might not exist or may not be unique
>- Numerical methods might be needed.






