---
title:
draft: false
description:
aliases:
  - linear equation
tags:
  - mathematics
date:
---

>[!info] Definition
>A first order [[Ordinary differential equation|ODE]] is called **linear** if it can be written as the following
>$$
>\frac{dy}{dt} + p(t)y = q(t)
>$$
>Notice that linearity is enforced by $y$ term being at first power.

Notice that one can integrate the right hand side with respect to $t$ while left hand side is much trickier to do so.

So assume that there exists a $u(t)$ such that

$$
\frac{d(u(t)y)}{dt} = \frac{dy}{dt}u(t) + y\frac{du}{dt} = u(t)q(t)
$$
Now multiply the original equation with $u(t)$
$$
u(t) \frac{dy}{dt} + u(t)p(t)y = u(t)q(t)
$$
this equation holds if and only if $u(t)p(t) = du/dt$. Notice that this a [[Separable equations|separable equation]] for the $u$
$$
\begin{align*}
\frac{du}{dt} &= \frac{p(t)}{\frac{1}{u}} \\
\int \frac{1}{u}du &= \int p(t) dt \\
\ln|u| &= \int p(t) dt \\
u &= \exp\left( \int p(t) dt \right)
\end{align*}
$$
such a function $u(t)$ is called the **integrating factor** for the [[Ordinary differential equation|ODE]].

>[!warning] Notice that $u(t)>0$.

Then one can see that

$$
\begin{align*}
u(t)y &= \int u(t)q(t) dt \\
y &= \frac{\int u(t) q(t) dt}{u(t)}
\end{align*}
$$
