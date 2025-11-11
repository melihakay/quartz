---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---

>[!info] Definition
>If $X_{1}\dots X_{n} = \tilde{X}$ is random sample from $f(x;\theta)$ then the $k^{th}$ [[Moments|moment]] of the sample is given by
>$$
>m_{k} = E[(X-\mu)^k] = \sum_{i} \frac{x_{i}^k}{n}
>$$

>[!warning] Number of moments to calculate
>You need $n$ moments if you wish to estimate $n$ parameters.

Now let us walk through an example.

>[!example] Example
>Consider a [[rv]] with [[Expected value|mean]] $\mu$ and [[Variance & Covariance|variance]] $\sigma^2$. Now we say that we have two unknowns $(\mu, \sigma^2) = (\theta_{1}, \theta_{2})$. So we need to consider moments up to second order.
>
>Let us first calculate the sample moments.
>$$
>\begin{align*}
>m_{1} &= \sum \frac{x_{i}}{n} \\
>m_{2} &= \sum \frac{x_{i}^2}{n}
\end{align*}
>$$
>Now the theoretical moments
>$$
>\begin{align*}
> E[X] &= \mu \\
> E[X^2] &= \sigma^2 + \mu^2
\end{align*}
>$$
>Now equate these two.
>$$
>\begin{align*}
> E[X] = m_{1} &\implies \hat{\mu}_{MME} = \sum \frac{x_{i}}{n} \\
> E[X^2] = m_{2} &\implies \hat{\sigma}^2 + \hat{\mu}^2 = \sum \frac{x_{i}^2}{n} \\
> &\implies \hat{\sigma^2} =  \sum \frac{x_{i}^2}{n} - \hat{\mu}^2\\
> &\implies \hat{\sigma^2} =  \sum \frac{x_{i}^2}{n} - \left( \sum \frac{x_{i}}{n} \right)^2 \\
> &\implies \hat{\sigma^2}_{MME} = \sum \frac{(x_{i} - \bar{x})^2}{n}
\end{align*}
>$$

For another example see [[Gamma distribution#Method of moments estimation|gamma distribution]].
