---
title:
draft: false
description:
aliases:
tags:
  - mathematics
date:
---

>[!info] Definition
>A first order [[ODE]] is said to be homogeneous if it can be written in the form of
>$$
\frac{dy}{dt} = h\left( \frac{y}{t} \right)
>$$
>for some function $h$.

>[!tip] Test for homogeneity
>$$
\frac{dy}{dt} = h\left( \frac{y}{t} \right) \implies f(\lambda t, \lambda y) = h\left( \frac{\lambda y}{\lambda t} \right) = h\left( \frac{y}{t} \right) = f(t, y)
>$$

Let solve such a equation by letting $v=y/t$. Observe that $y=vt$.

$$
\begin{align*}
\frac{dy}{dt} &= h\left( \frac{y}{t} \right) \\
\frac{d(vt)}{dt} &= h(v) \\
v + t \frac{dv}{dt} &= h(v) \\
\frac{dv}{dt} &= \frac{h(v)-v}{t}
\end{align*}
$$
Now notice that this is a [[Separable equations|separable equation]] with respect to $v$.

$$
\begin{align*}
\frac{dv}{dt} &= \frac{\left( \frac{1}{t} \right)}{\frac{1}{h(v)-v}} \\
\implies \int \frac{1}{h(v)-v} dv &= \int \frac{1}{t} dt
\end{align*}
$$
One should solve this integrals and finally replace $v$ with $y/t$.
