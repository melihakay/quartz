---
title:
draft: false
description:
aliases:
tags:
  - statistics
  - mathematics
date:
---
# Definition

Our objective is to explore the effect of regressor $x$ on the response variable $y$. In this context we define our model as the following:

$$
y = h(x, \varepsilon)
$$
Here, y is the dependent and observable variable. 

All of our assumptions are based on the $\varepsilon$, which is the error term in the model. It is also called as *residual*. Our assumptions are:

1. $E[\varepsilon]=0$
2. $V(\varepsilon)=\sigma^2$
3. $Cov(\varepsilon_{i}, \varepsilon_{j})=0$, $i \neq j$
4. $\varepsilon \sim NID(0, \sigma^2)$

Observe that $y$ is a function of a random variable, $\varepsilon$. Thus $y$ itself is a random variable.

In the case of SLR we have one scalar response variable and one regressor. We define our model as following:
$$
y = \beta_{0} + \beta_{1}x + \varepsilon
$$
One can interpret $\beta_{0}$ as intercept and $\beta_{1}$ as the slope of the fitted line.

At the time we construct our model, we do not know parameters $\beta_{0}$ and $\beta_{1}$ and our aim is to estimate these from the data using [[Least squares estimation]].

# Model Analysis

## Estimation by LSE

We estimate $\beta_{0}$, $\beta_{1}$ and $\sigma^2$. To do so we say that data is paired as $(x_{i},y_{i})$. Observe that
$$
\varepsilon_{i} = y_{i} - (\beta_{0} + \beta_{1}x)
$$
We define **sum of squared errors** as
$$
SSE=\sum_{i=1}^n{\varepsilon_{i}^2}
$$
### LSE for $\beta_{0}$
$$
\frac{d}{d \beta_{0}}SSE = 0
$$
$$
\frac{d}{d \beta_{0}}\sum_{i=1}^n \varepsilon^2 = 0
$$
$$
\frac{d}{d \beta_{0}}\sum_{i=1}^n (y_{i} - \beta_{0} - \beta_{1}x_{i})^2 = 0
$$
Derivative of a sum is sum of the derivatives.
$$
\sum_{i=1}^n \frac{d}{d \beta_{0}} (y_{i} - \beta_{0} - \beta_{1}x_{i})^2 = 0
$$
$$
\sum_{i=1}^n -2(y_{i} - \beta_{0} - \beta_{1}x_{i}) = 0
$$
$$
-2\sum_{i=1}^n y_{i} - \beta_{0} - \beta_{1}x_{i} = 0
$$
$$
\sum_{i=1}^n y_{i} - \sum_{i=1}^n\beta_{0} - \sum_{i=1}^n\beta_{1}x_{i} = 0
$$
$$
\sum_{i=1}^n y_{i} - \sum_{i=1}^n\beta_{1}x_{i} = n\beta_{0}
$$
$$
\beta_{0} = \sum_{i=1}^n \frac{y_{i}}{n} - \sum_{i=1}^n \frac{\beta_{1}x_{i}}{n}
$$
$$
\hat{\beta_{0}} = \bar{y} - \hat{\beta_{1}} \bar{x}
$$
### LSE for $\beta_{1}$
$$
\sum_{i=1}^n \frac{d}{d \beta_{1}} (y_{i} - \beta_{0} - \beta_{1}x_{i})^2 = 0
$$
$$
\sum_{i=1}^n -2x_{i}(y_{i} - \beta_{0} - \beta_{1}x_{i}) = 0
$$
$$
\sum_{i=1}^n x_{i}y_{i} - x_{i}\beta_{0} - \beta_{1}x_{i}^2 = 0
$$
$$
\sum_{i=1}^n x_{i}y_{i} - \beta_{0}\sum_{i=1}^n x_{i} - \beta_{1} \sum_{i=1}^n x_{i}^2 = 0
$$
$$
\sum_{i=1}^n x_{i}y_{i} - (\bar{y} - \hat{\beta_{1}} \bar{x})\sum_{i=1}^n x_{i} - \beta_{1} \sum_{i=1}^n x_{i}^2 = 0
$$
$$
\sum_{i=1}^n x_{i}y_{i} - \bar{y}\sum_{i=1}^n x_{i}  + \hat{\beta_{1}} \bar{x}\sum_{i=1}^n x_{i} - \beta_{1} \sum_{i=1}^n x_{i}^2 = 0
$$
$$
\hat{\beta_{1}} (\bar{x}\sum_{i=1}^n x_{i} - \sum_{i=1}^n x_{i}^2) = \bar{y}\sum_{i=1}^n x_{i} - \sum_{i=1}^n x_{i}y_{i}
$$
$$
\hat{\beta_{1}} = \frac{\left( \bar{y}\sum_{i=1}^n x_{i} - \sum_{i=1}^n x_{i}y_{i}\right)}{(\bar{x}\sum_{i=1}^n x_{i} - \sum_{i=1}^n x_{i}^2)}
$$
Substitute $\sum x_{i} = \bar{x}n$
$$
\hat{\beta_{1}} = \frac{
\sum_{i=1}^n (x_{i}- \bar{x})(y_{i}-\bar{y})
}{
\sum_{i=1}^n (x_{i} - \bar{x})^2 
}
$$
$$
\hat{\beta_{1}} = \frac{Cov(x, y)}{V(x)}
$$
$$
\hat{\beta_{1}} = \frac{S_{XY}}{S_{XX}}
$$
where 
$$
S_{XY} = \sum_{i=1}^n (x_{i} - \bar{x})(y_{i} - \bar{y})
$$
### LSE for $\sigma^2$

$$
\hat{\sigma^2} = \frac{SSE}{n-2}
$$
Here $n-2$ is the degrees of freedom.

### Distribution of least squares estimates

We have estimated $\beta_{0}$, $\beta_{1}$ and $\sigma^2$ using random samples from the data. Thus, they are random variables too.

Since the [[Least squares estimation|LSE]] is [[Best Linear Unbiased Estimator|BLUE]] we have:

#### $\beta_{0}$
1. $E[\beta_{0}] = \beta_{0}$
2. $V(\beta_{0})=\left( \frac{\hat{\sigma^2}}{S_{XX}} \frac{\sum^n x_{i}^2}{n} \right)$
3. $SE(\beta_{0}) = \sqrt{ \left( \frac{\hat{\sigma^2}}{S_{XX}} \frac{\sum^n x_{i}^2}{n} \right) }$
Then 
$$
\beta_{0} \sim N\left(
\beta_{0}, 
\sqrt{ \left( \frac{\hat{\sigma^2}}{S_{XX}} \frac{\sum^n x_{i}^2}{n} \right) }
\right)
$$
#### $\beta_{1}$
1. $E[\beta_{1}] = \beta_{1}$
2. $V(\beta_{1})=\frac{\hat{\sigma^2}}{S_{XX}}$
3. $SE(\beta_{1}) = \sqrt{\frac{\hat{\sigma^2}}{S_{XX}}}$
Then 
$$
\beta_{1} \sim N\left(
\beta_{1}, 
\sqrt{ \frac{\hat{\sigma^2}}{S_{XX}} }
\right)
$$

#### t-values

$$
T_{i} =\frac{ \hat{\beta_{i}} - \bar{\beta_{i}}}{SE(\beta_{i})} \sim t_{(n-2)}
$$

### Test of hypothesis

In the test of hypothesis for each $\beta_{i}$ we use their $t$ statistics. 

$$
\begin{align*}
\hat{\beta_{i0}} &\text{ , } i \in \{0,1\} \\
H_{0i} &: \beta_{i} = \beta_{i0} \\
H_{1i} &: \beta_{i} \neq \beta_{i0} \text{ or } \beta_{i} > \beta_{i0} \text{ or } \beta_{i} < \beta_{i0}
\end{align*}
$$

our test statistic is

$$
T^* = \frac{\hat{\beta_{i}}-\beta_{i0}}{SE(\hat{\beta_{j}})}
\sim t_{(n-2)} \text{ , } n-2= \text{degrees of freedom of } \varepsilon
$$
decision rule is 

$$
\text{Reject } H_{0} \text{ when } |T_{i}| \geq t_{n-2}
$$
Rejection means that $\beta_{i}$ differ from $H_{i0}$ significantly.

### Test for significance

We use same test with [[Simple linear regression#Test of hypothesis|test of hypothesis]] bu instead of using $\beta_{i0}$ we say that 

$$
\begin{align*}
\hat{\beta_{i0}} &\text{ , } i \in \{0,1\} \\
H_{0i} &: \beta_{i} = 0 \\
H_{1i} &: \beta_{i} \neq 0
\end{align*}
$$

### Properties of LSE

1. LSE is linear on $y_{i}$
2. Unbiased, $E(\hat{\beta}_{i}) = \beta_{i}$
3. Best st. $V(\hat{\beta}_{i})$ is minimum for each $i$


## Goodness-of-fit

>[!question]
>We question whether the data match the model or not.

One would say that the model is a good fit for the data if 
$$
\hat{y_{i}} \approx y_{i}
$$
Thus 
$$
\varepsilon_{i} \approx 0
$$
>[!info] Sums of squares
>
>- $SST = \sum^n(y_{i} - \bar{y})^2$, total deviation in $y$.
>- $SSE=\sum^n(y_{i}-\hat{y_{i}})^2$, sum of residuals.
>- $SSR= SST-SSE$, deviation caused by regression.
>
>If $\hat{y_{i}} \approx y_{i}$ then $SSE \approx 0$.

>[!info] Coefficient of determination
> It is defined as:
> $$
>R^2 = 1 - \frac{SSE}{SST}
>$$
>$R^2$ represents the share due to $x$ in total variation in $y$. So $R^2=0.95$ means that 95% variation in $y$ is due to $x$ and 5% of the variation is due to model residuals. Such a model is considered as a good fit.
>
>Observe that $SSE \sim 0 \implies R^2 \sim 1$
>Thus we say
>- $R^2 \sim 1 \implies$ model is a good-fit
>- $R^2 \sim 0 \implies$ model  may not be a poor-fit. You need to conduct goodness-of-fit test.

### Goodness-of-fit Test

>[!question] Hypothesis
>$H_{0}$: $\beta_{1}=0$, means that $x$ has no effect on $y$.
>$H_{1}$: $\beta_{1}\ne_{0}$, $x$ has effect on $y$.
>We test this hypothesis with [[Analysis of Variances | ANOVA]].

We construct our [[Analysis of Variances|ANOVA]] table:

| Source     | DoF   | Sum of Squares | Mean of SS            | $F^*$             |
| ---------- | ----- | -------------- | --------------------- | ----------------- |
| Regression | 1     | $SSR$          | $MSR=\frac{SSR}{1}$   | $\frac{MSR}{MSE}$ |
| Error      | $n-2$ | $SSE$          | $MSE=\frac{SSE}{n-2}$ |                   |
| Total      | $n-1$ | $SST$          |                       |                   |
Thus one can deduct that:
$$
F^*=\frac{\frac{SSR}{1}}{
\frac{SSE}{n-2}
}
=
\frac{(n-2)(SST-SSE)}{SSE}
$$
$$
F^* \sim F_{(\alpha, 1, n-2)}
$$
Usual $\alpha$ (significance level) values are:
- 0.01
- 0.05
- 0.10

>[!info] Rule of decision
> Let $cv = F_{(\alpha, 1, n-2})$
> 
> - **Reject** $H_{0}$ if $F^* \geq cv$. Thus conclude that $x$ has statistically significant effect on $y$ at $\alpha$ significance level.
> - **Fail to reject** $H_{0}$ if $F^* < cv$. Therefore say that there is not enough evidence to state the effect of $x$ on $y$.

# R

We use `lm()` function to create a linear model.

```r
y <- c(...)
x <- c(...)
model <- lm(y~x)
modelSummary <- summary(model)
print(modelSummary) 
```
