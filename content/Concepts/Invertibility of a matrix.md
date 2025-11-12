---
title:
draft: false
description:
aliases:
tags:
  - linear-algebra
  - mathematics
date: 20.10.2025
---

>[!info] By determinant
>Let $A$ be an $n\times n$ matrix of real or complex numbers. Then the inverse of A exists if and only if $\det A \neq 0$.

>[!info] By row reduction
>A matrix $A$ is [[Invertibility of a matrix|invertible]] $\iff$ it can be row reduced into [[Identity matrix|identity matrix]].

>[!tip] 
>If a matrix $A$ cannot be row reduced into $I_{n}$ then it means that there are rows of zeroes in the reduced system, implying [[Determinant|determinant]] of reduced system is $0$. Knowing that elementary row operations do not create/remove zero determinant, this means that $\det A$ was actually $0 \implies$ $A$ is not invertible.

