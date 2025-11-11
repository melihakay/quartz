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
>We wish to approximate a solution to the first order [[Differential Equations|differential equation]]
>$$
> \frac{dy(t)}{dt} = y'(t) = f(y(t), t) \text{ given } y(t_{0})=y_{0}
>$$
>Then 4th order approximation would be 
>$$
>\begin{align*}
>k_{1} &= f(y_{0}, t_{0}) \\
>k_{2} &= f\left( y_{0}+k_{1}\frac{dt}{2}, t_{0} + \frac{dt}{2} \right) \\
>k_{3} &= f\left( y_{0}+k_{2}\frac{dt}{2}, t_{0} + \frac{dt}{2} \right) \\
>k_{4} &= f\left( y_{0}+k_{3}dt, t_{0} + dt \right) \\
\end{align*}
>$$
>Finally we get a weighted average of these slopes.>
>$$
>y(t_{0}+dt) =  y(t_{0}) + \frac{k_{1} + 2k_{2} + 2k_{3} + k_{4}}{6}dt
>$$

![[Pasted image 20251108121632.png]]
![[Pasted image 20251108121636.png]]
![[Pasted image 20251108121639.png]]
![[Pasted image 20251108121646.png]]

>[!tldr] Source
>[Swarthmore Edu](https://lpsa.swarthmore.edu/NumInt/NumIntFourth.html)

