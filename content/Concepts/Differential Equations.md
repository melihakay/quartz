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
>A differential equation is a equation that contains derivatives and algebraic operations.

>[!warning] Solutions to differential equations are functions, not numbers!

>[!example]
>$$
>\frac{dx}{dt} + 5x = e^t
>$$

>[!example] System of differential equations
>$$
> \frac{dx}{dt} + y = t
>$$
>$$
> \frac{dy}{dt} + xy = \sin(t)
>$$
>In that case we say that solution is an ordered pair of functions $(x(t), y(t))$ such that both of these equations simultaneously hold.

>[!example] Partial differential equations
> $$
> \frac{\partial u }{\partial x} + \frac{\partial u}{\partial y} = x + y
> $$
> Solutions would be $u(x,y)$ that satisfy the above equation.

>[!info] Definition
>A differential equation in which there is only one independent variable is called and [[Ordinary differential equation]]. If there are more than one independent variable then it is called [[Partial differential equation]].

>[!info] Definition
>Largest number $n$ such that $n$th derivative appears in a differential equation is called **order** of the equation.
>$$
> \left( \frac{dx}{dt} \right)^5 + \frac{d^3x}{dx^3} + x^2 = 1
>$$
>is a 3rd order differential equation.

>[!info] Definition
>Suppose that we have a first order [[Ordinary differential equation|ODE]] with dependent variable $y$ and independent variable $t$. Then, a condition of the form $y(t_{0})=y_{0}$ is called an **initial condition**.

Initially we do not know the solution curve of a differential equation. But we can infer some tangents in the domain. This gives us a approximate graph for the given equation. This tangent graphs are called [[Direction fields| a direction field]] like this one:

![[Pasted image 20251112151839.png]]

# METU MATH219 Curriculum

1. This introduction
2. [[Separable equations]]
3. [[Homogeneous equations]]
4. [[Linear equations]]
5. [[Principle of superposition]]
6. Existence-uniqueness theorems [TO BE]
7. [[Exact equations]]
8. 