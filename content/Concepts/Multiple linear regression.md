---
title:
draft: false
description:
aliases:
tags:
  - statistics
date:
---
>[!tip] Check [[Simple linear regression]] for basics.

Formulation is as follows

$$
y_{i} = \beta_{0} + \sum_{i=1}^k \beta_{i} x_{i} + \varepsilon_{i}
$$
where $i=1,2\dots,k$ is the number of regressors.

$$
LSE: \frac{\partial}{\partial \beta_{i}} SSE = 0
$$
Let $X \in R^{1\times k}$ and $B \in R^{k+1 \times 1}$. Then we need $k+1$ equations.

Now follow:

$$
\begin{align*}
y_{i} &= \beta_{0} + \sum_{i=1}^k \beta_{i} x_{i} + \varepsilon_{i} \\
\hat{y_{i}} &= \beta_{0} + \sum_{i=1}^k \beta_{i} x_{i} \\
\end{align*}
$$
Then we replace $y$ with $Y$ vector, combining all the equations

$$
Y = \begin{bmatrix}
y_{1}  \\
y_{2} \\
\vdots \\
y_{n} 
\end{bmatrix}
\text{ , }
X= \begin{bmatrix}
1 & x_{1} \\
1 & x_{2} \\
\vdots & \vdots  \\
1 & x_{n}
\end{bmatrix}
\text{ , }
B = \begin{bmatrix}
\beta_{0} \\
\beta_{1}
\end{bmatrix}
\text{ , }
\epsilon = \begin{bmatrix}
\epsilon_{1} \\
\epsilon_{2} \\
\vdots \\
\epsilon_{n}
\end{bmatrix}
$$
then 
$$
Y = XB + \epsilon
$$
is our multiple linear model.

$SSE$ here is 
$$
SSE = (Y-XB)^T(Y-XB) = \epsilon^T\epsilon
$$
and LSE is 

$$
\begin{align*}
\frac{d}{dB} SSE &= 0 \\
\frac{d}{dB} (Y-XB)^T(Y-XB) &= 0 \\
-2X^T(Y-XB) &=0 \\
X^TXB-X^TY &= 0 \\
(X^TX)B &= X^TY \\
\hat{B}_{LSE} &= (X^TX)^{-1}X^TY
\end{align*} 
$$
Here $\hat{B}_{LSE}$ is [[Best Linear Unbiased Estimator]] for $B$.

$$
\begin{align*}
E[\hat{B}] &= B \\
V(\hat{B}) &= \begin{bmatrix}
V(\hat{\beta}_{0}) & Cov(\hat{\beta}_{0}, \hat{\beta}_{1})  \\
Cov(\hat{\beta}_{1}, \hat{\beta}_{0})) & V(\hat{\beta}_{1})
\end{bmatrix} \\
 &= \sigma^2(X^TX)^{-1} \\
 SE(\hat{B})&= \sqrt{ \sigma^2 \text{diag}(X^TX)^{-1} }
\end{align*}
$$
And sums of square are

$$
\begin{align*}
SST &= Y^TY - \frac{1}{n} Y^TJY \text{ , } J=(\begin{bmatrix}
1 & 1 & \dots & 1
\end{bmatrix}^T)_{n\times 1} \\
SSE &= \varepsilon^T\varepsilon = (Y-X\hat{B})^T(Y-X\hat{B}) \\
SSR &= SST - SSE
\end{align*}
$$

>[!tip] R
>In R use 
>1. `solve(A)` to find $A^{-1}$. 
>2. `t(A)` for $A^T$
>3. `lm(y~x1+x2+...xn)` for multiple linear regression



