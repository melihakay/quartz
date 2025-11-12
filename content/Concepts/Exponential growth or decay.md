---
title:
draft: false
description:
aliases:
tags:
  - mathematics
date:
---

Let us say we have a [[Linear equations|linear equation]] $\frac{dy}{dt} +ay = q(t)$. In that case $u(t)=\exp(at)$. Then

$$
\begin{align*}
(e^{at}y)' &= e^{at}q(t) \\
e^{at}y &= \int  e^{at}q(t) \\
y &= e^{-at} \int  e^{at}q(t)
\end{align*}
$$
Now if $q(t)=b$ is constant
$$
\begin{align*}
e^{at}y &= \int be^{at} dt \\
e^{at}y &= \frac{b}{a}e^{at} + c \\
y &= \frac{b}{a} + ce^{-at} 

\end{align*}
$$
Now observe that 
$$
\lim_{ t \to \infty } y = \frac{b}{a} 
$$
if $a>0$. And $\lim_{ t \to \infty }y$ doesn't exist if $a<0$.

So that, a function of the form 
$$
y(t) = d + ce^{at}
$$ is called **growing exponentially** while the function of the form 
$$
y(t) = d + ce^{-at}
$$
is called **decaying exponentially**.

Note that in the original equation $\frac{dy}{dt} +ay = q(t)$, it is growing if $a<0$ and decaying if $a>0$.