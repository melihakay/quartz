---
title:
draft: false
description:
aliases:
tags:
  - statistics
  - mathematics
date:
---
# [[Maximum likelihood estimation]]

There are no explicit solutions for $\hat{\alpha}_{MLE}$ and $\hat{\beta}_{MLE}$. One should use numerical methods to find the estimations.

# [[Method of moments]] estimation

Let $\alpha$ and $\beta$ unknown for $\text{Gamma}(\alpha,\beta)$. We need two moments to estimate both these

$$
\begin{align*}
m_{1} &= \bar{x} = \hat{\alpha} \hat{\beta} \\
m_{2} &= s^2 + \bar{x}^2 = \hat{\alpha} \hat{\beta}^2 + (\hat{\alpha} \hat{\beta})^2 \\
\bar{x} &= \hat{\alpha} \hat{\beta} \\
s^2 &= \hat{\alpha} \hat{\beta}^2 \\
\frac{s^2}{\bar{x}} &=  \frac{\hat{\alpha}\hat{\beta}^2}{\hat{\alpha}\hat{\beta}} \implies \hat{\beta}_{MME} = \frac{s^2}{\bar{x}} \\
\hat{\alpha} \frac{s^2}{\bar{x}} &= \bar{x} \implies \hat{\alpha}_{MME} = \frac{\bar{x}^2}{s^2}
\end{align*}
$$
