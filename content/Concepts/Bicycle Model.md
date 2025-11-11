---
title:
draft: false
description:
aliases:
tags:
  - vehicle-dynamics
date:
---
# Simple Kinematic

Most simple one. Used for planning in the literature. See [[Motion Planning and Control Pipeline for a Formula Student Autonomous Vehicle.pdf#page=23&selection=27,0,29,23|Motion Planning and Control Pipeline for a Formula Student Autonomous Vehicle, page 23]]

> This model is well known in the literature (e.g. [14]) to perform well at low speed profiles (less than 5 m/s) [[Motion Planning and Control Pipeline for a Formula Student Autonomous Vehicle.pdf#page=23&selection=33,49,38,1|Motion Planning and Control Pipeline for a Formula Student Autonomous Vehicle, page 23]]

![[Pasted image 20251108114717.png]]

Here we use $\psi$ instead of $\theta$.

State space 

$$
X = \begin{bmatrix}
x \\
y \\
\psi \\
v
\end{bmatrix}
$$

and the state derivative is 

$$
\dot{X} = \begin{bmatrix}
\dot{x}  \\
\dot{y} \\
\dot{\psi} \\
\dot{v}
\end{bmatrix}
=
\begin{bmatrix}
v \cos(\psi+\beta) \\
v \sin(\psi+\beta) \\
v \tan \delta \cos \beta / L \\
a
\end{bmatrix}
$$
where 
$$
\beta = \arctan \left( \frac{L_{r}}{L_{r} + L_{f}} \tan \delta \right)
$$
and the control inputs are

$$
U = \begin{bmatrix}
a \\
\delta
\end{bmatrix}
$$


# AMZ

## Kinematic

This is model to be used in blending.

$$
X = 
\begin{bmatrix}
x \\
y \\
\psi \\
v_{x} \\
v_{y} \\
\omega
\end{bmatrix}
\text{ , }
U=
\begin{bmatrix}
a \\
\delta
\end{bmatrix}
$$
and
$$
\dot{X} = f(X,U,\dot{U}) =
\begin{bmatrix}
v_{x}\cos \psi - v_{y}\sin \psi \\
x_{x}\sin \psi + v_{y}\cos \psi \\
\omega \\
\frac{F_{x}}{m} \\
\frac{L_{r}}{L_{r}+L_{f}} (\dot{\delta}v_{x} + \delta \dot{v_{x}}) \\
\frac{1}{L_{r}+L_{f}} (\dot{\delta}v_{x} + \delta \dot{v_{x}})
\end{bmatrix}
$$


## Dynamic
![[Pasted image 20251108124237.png]]

> The used vehicle model is derived under the following assumptions, 
> - the vehicle drives on a flat surface
> - load transfer can be neglected
> - combined slip can be neglected
> - the longitudinal drive-train forces act on the center of gravity. 
[[AMZ Driverless, The Full Autonomous Racing System.pdf#page=26&selection=9,95,13,1|AMZ Driverless, The Full Autonomous Racing System, page 26]]


$$
X = 
\begin{bmatrix}
x \\
y \\
\psi \\
v_{x} \\
v_{y} \\
\omega
\end{bmatrix}
\text{ , }
U=
\begin{bmatrix}
a \\
\delta
\end{bmatrix}
$$
and
$$
\dot{X} = f(X,U) = 
\begin{bmatrix}
v_{x}\cos \psi - v_{y}\sin \psi \\
x_{x}\sin \psi + v_{y}\cos \psi \\
\omega \\
\frac{1}{m} (F_{r,x} - F_{f,y}\sin \delta + mv_{y}\omega) \\
\frac{1}{m} (F_{r,y} + F_{f,y}\cos \delta - mv_{x}\omega) \\
\frac{1}{I_{z}} (F_{f,y}\cos \delta L_{f}-F_{r,y}L_{r})
\end{bmatrix}
$$

where we find lateral tire force by using simplified [[Pajecka tire model]]:

$$
\begin{align*}
\alpha_{r} &= \arctan\left( \frac{v_{y}-L_{r}\omega}{v_{x}} \right) \\
F_{r,y} &= D_{r}\sin(C_{r}\arctan(B_{r}\alpha_{r}))
\end{align*}
$$

and

$$
\begin{align*}
\alpha_{f} &= \arctan\left( \frac{v_{y}+L_{f}\omega}{v_{x}} \right) - \delta \\
F_{f,y} &= D_{f}\sin(C_{f}\arctan(B_{f}\alpha_{f}))
\end{align*}
$$

Where $F_{X}=f_{M}(P) - C_{r} - \frac{1}{2}\rho_{air}A C_{d}v_{x}^2$. Here $f_{M}(P)$ stands for motor force where $f_{M}$ is motor model and $P \in [-1,1]$ is the pedal position. These parameters are identified from the experiments.

## Hybrid-Bicycle Model

This model blends the [[Bicycle Model#Kinematic|kinematic model]] and [[Bicycle Model#Dynamic|dynamic model]] based on the vehicle longitudinal speed. 

Here observe that both models use the same state vector. Therefore we blend these model dynamics by

$$
\dot{X} = f(X,U,\dot{U}) =  \lambda f_{dyn}(X,U) + (1-\lambda)f_{kin}(X,U,\dot{U})
$$
where $\lambda=min\left( max\left( \frac{v_{x}-3}{5-3},0 \right), 1 \right)$ when model is blended between $(3,5)$ m/s. 
## Discretization

We use 4th order [[Runge-Kutta method]] to discretize the the system.

# Numerically Stable Dynamic Bicycle

$$
X = 
\begin{bmatrix}
x \\
y \\
\psi \\
v_{x} \\
v_{y} \\
\omega
\end{bmatrix}
\text{ , }
U=
\begin{bmatrix}
a \\
\delta
\end{bmatrix}
$$

and we discretize that model using something similar to [[Backwards Euler method]]. See [[Numerically Stable Dynamic Bicycle Model for Discrete-time Control.pdf#page=2&selection=799,0,814,30|Numerically Stable Dynamic Bicycle Model for Discrete-time Control, page 2]]

$$
X_{k+1} = 

\begin{bmatrix}
x_{k+1} \\
y_{k+1} \\
\psi_{k+1} \\
v_{x,k+1} \\
v_{y,k+1} \\
\omega_{k+1}
\end{bmatrix} =

\begin{bmatrix}
x_{k} + \Delta t(v_{x,k}\cos \psi_{k}-v_{y,k}\sin \psi_{k}) \\
y_{k}+\Delta t(v_{y,k}\cos \psi_{k} + v_{x,k}, \sin \psi _{k}) \\
\psi_{k} + \Delta t \omega_{k} \\
v_{x,k} + \Delta t a_{k} \\
\frac{m v_{x,k} + \Delta t \left[ \omega_{k}(L_{f}k_{f} -L_{r}k_{r}) - k_{f}\delta_{k}v_{x,k} - mv_{x,k}^2\omega_{k} \right]}{mv_{x,k} - \Delta t(k_{f}+k_{r})} \\
\frac{I_{z}v_{x,k}\omega_{k} + \Delta t \left[ v_{y,k}(L_{f}k_{f}-L_{r}k_{r}) - L_{f}k_{f}\delta_{k}v_{x,k} \right]}{I_{z}v_{x,k}-\Delta t(L_{f}^2k_{f}+L_{r}^2k_{r})}
\end{bmatrix}
$$
