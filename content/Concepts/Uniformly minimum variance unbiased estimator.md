---
title:
draft: false
description:
aliases:
  - UMVUE
tags:
  - statistics
date:
---

>[!info] Definition
>An estimator $\hat{\theta}$ is called UMVUE if 
>- $\hat{\theta}$ is an [[Unbiased estimator|unbiased estimator]] and
>- For any other [[Unbiased estimator|unbiased estimator]] $\hat{\theta}^{\ast}$, $V(\hat{\theta})\leq V(\hat{\theta}^\ast)$ for $\forall \hat{\theta}^\ast \in \Omega$.

Sometimes we can come up with a lower bound such that any [[Unbiased estimator|unbiased estimator]] having it's variance equal to that bound would be the [[Uniformly minimum variance unbiased estimator|UMVUE]]. 

One of such bounds is [[Crame'r-Rao lower bound]].
