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

Linear regression is a model that estimates the relationship (effect) between a **scalar** response and one or more independent variables. 

In the case of just one independent variable (regressor) we call such a model [[Simple linear regression]]. If there are more than one regressor then we call the model [[Multiple linear regression]]. This term should not be confused with [[Multivariate Linear Regression]]

If the $Y$ is not a scalar, rather a vector then we deal with [[General Linear Model]]

One might show a model in the following way:
$$
Y = X^T B + \varepsilon
$$
$$
Y= \beta_{0} + \beta_{1}x_{1} \dots + \beta_{n}x_{n} + \varepsilon
$$
where $E \sim NID(0, \sigma^2)$. 

As far as I understood one can state the model as:

$$
Y= \beta_{0} + \beta_{1}\phi_{1}(x_{1}) \dots + \beta_{n}\phi_{n}(x_{n}) + \varepsilon
$$
where $\phi_{n}(x_{n})$ can be a non-linear function of $x_n$.

# R

We use `lm()` function in R to create a linear regression model.

```r
results <- lm(Y~X) # returns parameter estimates (b0, b1, sigma)
```

