---
title:
draft: false
description:
aliases:
tags:
  - mathematics
date:
---
# Limit

>[!info] **Definition**
>
>Let $f: R^n \mapsto R$ where $D = dom(f) \subseteq R^n$, $p \in D$. We say that limit of f at $p_0$ is $L \in R$. We say that limit of $f$ at $p_0$ is $L \in R$ and we write 
>
> $$ lim_{p \to p_0} f(p)  = L $$
> 
> if $\forall \epsilon > 0, \exists \sigma > 0$ st. $0<|p-p_0|<\sigma \implies |f(p) - L| < \epsilon$.

Remember that if $h(X)$ is cont. then 
$$ lim_{p \to p_0} h(p) = h(lim_{p \to p_0}) $$


> [!warning]
> L'H is NOT applicable for two variable functions.
> 

> [!todo]
> - [ ] Examples and exercises in Week 3 Note 2

# Continuity

>[!info] Definition
> $z=f(x,y)$  is continuous at $p(x_0,y_0) \iff lim_{(x,y)\to(x_0,y_0)}f(x,y)=f(x_0,y_0)$
> 

Note that $z=f(x,y)$ is continuous at $D\subseteq R^2$  if $f(x,y)$ is continuous at each point of $D$.

>[!info] Theorem
> Let $f:R^n\to R^m$ be continuous on $R^n$. Then, for all open/closed subset $S\subseteq R^n$, $f^{-1}(S)$ is also open/closed.
>

Take $S=\{(x,y)\in R^2 | sin^2(xy) \leq 1 \text{ and } x^2 +y^2 \leq 1\}$. Observe that $S=(sin^2(x,y))^{-1}([0,1]) \cap (x^2 + y^2)^{-1}([0,1])$. Both functions are continuous on $R$ and the sets are closed. Then $S$ is closed. **Important part** here is that first you should check if the function is continuous on $R^n$.

## Uniform Continuity

>[!info] Theorem
>If $f:D\to R$ is continuous and $D$ is compact, then $f$ is uniformly continuous on $D$.

>[!info] Remark
>If $f: R \to R$ and $|f'(x)| \leq K$, $\forall x \in R$, then $f$ is uniformly continuous on $R$.

