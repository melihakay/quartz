---
title:
draft: false
description:
aliases:
  - separable equation
tags:
  - mathematics
date:
---

>[!info] Definition
>Suppose that $f(y,t) = \dot{y}$ can be written in the form of $\frac{M(t)}{N(y)}$ for some $M,N$, then the differential equation
>$$
\frac{M(t)}{N(y)} = \frac{dy}{dt}
>$$
>is called a **separable equation**.

One can solve such equation as following

$$
\begin{align*}
\frac{M(t)}{N(y)} &= \frac{dy}{dt} \\
\int N(y)\frac{dy}{dt}dt &= \int M(t)dt \\
\int N(y)dy &= \int M(t)dt
\end{align*}
$$