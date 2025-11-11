---
title:
draft: false
description:
aliases:
  - point estimation
  - interval estimation
tags:
  - statistics
date:
---

# Aim 

One can describe the aim of estimation as to identify the unknown parameter $\theta$ using [[Estimator|estimators]] which enables to identify the underlying population distribution $f_{X}(x; \theta)$.

# Types of estimation

# Point estimation

>[!info] Definition
>The quantity $T(X_{1}\dots X_{n})$ obtained from the observed values $X_{1}\dots X_{n}$ is called a "point" estimate of $\theta$.

# Interval Estimation

>[!info] Definition
>A confidence interval for parameter $\theta$ with confidence coefficient $1-\alpha$  is a **random** interval constructed by two [[Statistic|statistics]] $L(X_{1}\dots X_{n})<U(X_{1}\dots X_{n})$ such that:
>$$
>P(L(\tilde{X}) \leq \theta \leq U(\tilde{X})) \geq (1-\alpha)
>$$
>for $\forall \theta \in \Omega$

