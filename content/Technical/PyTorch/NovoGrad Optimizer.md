A series of optimizers have been created to address this problem, and allow for scaling to very large batch sizes and learning rates. In this exercise we'll be using the [NovoGrad optimizer](https://arxiv.org/abs/1905.11286). NovoGrad has the standard form of an update to the weights,

Δ𝐰=−𝜆𝐦

but the 𝐦

term appropriately normalizes the gradients to avoid the [vanishing gradient (or exploding gradient) problem](https://en.wikipedia.org/wiki/Vanishing_gradient_problem), using a gradient-averaging scheme similar to how SGD uses momentum to do that normalization. NovoGrad ensures that the learning rate is scaled appropriately on each layer, which empirically is [important in the large batch regime](https://arxiv.org/abs/1708.03888). If you are interested in continuing this exploration after this course, the [LAMB optimizer](https://arxiv.org/abs/1904.00962) is another extremely promising recent method worth exploring, which is very similar to NovoGrad in that it combines both [Adam](https://arxiv.org/abs/1412.6980), a popular variant of SGD, and layer-wise learning rates.

If you want to learn more about the theory behind NovoGrad, you may optionally expand the cell below. Otherwise, feel free to continue on to the exercise.

#### Layer-wise learning rate control[](http://18.215.252.108/lab/lab/tree/02_Notebook_Exercising_Optimization_Strategies.ipynb#Layer-wise-learning-rate-control)

NovoGrad combines several insights about SGD. First, it recognizes that gradient updates should be decoupled from the absolute magnitude of the gradient -- the direction is more important than the size. The magnitude of an update should be of order the magnitude of the weight multiplied by the learning rate, and since the learning rate is sufficiently small, this means that we make relatively small updates as we search for the optimum. Unfortunately, traditional SGD does not enforce this; the update to the weights 𝐰

is in the form:

Δ𝐰=−𝜆𝐠

where 𝜆

is the learning rate and 𝐠

is the gradient of the loss function. The size of the gradient is determined by the loss function, which is not required to be commensurate with the scale of the weight. Furthermore, backpropagation tends to exacerbate this issue (i.e. the [vanishing gradient (or exploding gradient) problem](https://en.wikipedia.org/wiki/Vanishing_gradient_problem) that plagued deep CNNs until algorithmic improvements like [residual connections](https://arxiv.org/abs/1512.03385) were developed). Most SGD algorithms developed over the past few years attempt to solve this problem in one way or another.

An intuitive way to deal with this is simply to divide the gradients on each layer by the norm of the gradients of that layer:

Δ𝐰=−𝜆𝐠|𝐠|

where the norm |𝐠|

is typically the root-mean-square operation. This can generally be described as [stochastic normalized gradient descent](https://arxiv.org/abs/1507.02030).

Another way to think about this is that, in a sense, the update has the wrong units (see Section 3.2 in the [ADADELTA paper](https://arxiv.org/abs/1212.5701) for a more rigorous discussion than this one). That is, if we imagine that the weights have a dimension (say, meters) and we take the partial derivative with respect to time, then the gradient has units of meters per second (that is, a speed or velocity), and applying an update to a position by adding a velocity does not make sense. We need to update the distance by an amount in meters. Dividing by the gradient by a norm makes the update dimensionless, and we can recover the correct scale by scaling the update by the norm of the weights. That is, we could have an update of the form

Δ𝐰=−𝜆|𝐰|𝐠|𝐠|

which has the desired scale and units, but still points in the direction of the gradient of the loss function.

Both of these approaches largely prevent vanishing/exploding gradients from causing the optimization process to diverge, because the magnitude of the update is now uncoupled from the absolute scale of the gradient, which could be much larger or much smaller than the weights on that layer.

The second approach was taken with the [LARS optimizer](https://arxiv.org/abs/1708.03888), which defines the update on a given layer as:

Δ𝐰=−𝜆global𝜆local𝐠

where the "global" learning rate is the normal learning rate policy you're familiar with (some small number like 0.01 that may decay over time), and the "local" per-layer learning rate is defined as

𝜆local=𝜂|𝐰||𝐠|

Here 𝜂

is a "trust coefficient" which should be less than 1 and decides how much we want to update the weights on each layer during an update. Observe that this scheme is essentially equivalent to previous formulation. LARS and related methods have been influential in making possible large-batch SGD.

Note that LARS is very closely related to [LARC (Layer-wise Adaptive Rate Control)](https://nvidia.github.io/OpenSeq2Seq/html/optimizers.html) and the two terms are sometimes used interchangeably. LARC is a slight variant on LARS that "clips" the local learning rate so that it is not higher than the global learning rate; that is, the update is in the form

Δ𝐰=−𝜆𝐠

with the learning rate set by

𝜆=min(𝜆global,𝜆local)

As a side note, in this discussion we are neglecting [weight decay](https://papers.nips.cc/paper/563-a-simple-weight-decay-can-improve-generalization.pdf) for simplicity, but it is straightforward to add it to these optimizers.

#### Gradient averaging and momentum[](http://18.215.252.108/lab/lab/tree/02_Notebook_Exercising_Optimization_Strategies.ipynb#Gradient-averaging-and-momentum)

A separate set of efforts uses the concept of gradient averaging: the gradient we apply should be an average of the gradient in this step and the gradient in the previous step. As an illustration, we have already discussed how momentum can be used to avoid being trapped in local minima and to more efficiently escape saddle points. SGD with momentum can in fact be seen as a form of gradient averaging -- the effective gradient is a linear combination of the gradient in this step and the gradient from the last step. Optimizers such as [RMSprop](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf) implement this idea; the update looks a lot like the LARS update, except that the norm of the gradient used in the denominator is a linear combination of the gradient from this step and the gradient from the last step.

The most popular implementation of this concept is the [Adam](https://arxiv.org/abs/1412.6980) optimizer, which works as follows. Suppose we have an update in this form:

Δ𝐰=−𝜆𝐦𝑣⎯⎯√

where 𝐦

is a gradient-like term and 𝑣 is a term that is like the norm of the square of the gradient (so that we recover the earlier form if 𝐦=𝐠 and 𝑣=|𝐠2|

). We can implement gradient averaging in the following way:

𝐦=𝛽1𝐦prev+(1−𝛽1)𝐠

where 𝐦prev

was the "gradient" term on the previous step, and

𝑣=𝛽2𝑣prev+(1−𝛽2)|𝐠2|

where 𝑣prev

was the "gradient-squared" term on the previous step. This means that we are keeping a running average of the gradient, rather than simply applying the gradient from this step. Adam is thus quite robust as a training optimizer compared to simpler optimizers like traditional SGD; however, it also tends to [generalize worse](https://arxiv.org/abs/1712.07628) than SGD with momentum.

#### Combining layer-wise rate control and gradient averaging[](http://18.215.252.108/lab/lab/tree/02_Notebook_Exercising_Optimization_Strategies.ipynb#Combining-layer-wise-rate-control-and-gradient-averaging)

NovoGrad combines both of these concepts. The form of the update is back to

Δ𝐰=−𝜆𝐦

but the 𝐦

term appropriately normalizes the gradients:

𝐦=𝛽1𝐦prev+(1−𝛽1)𝐠𝑣⎯⎯√

(and we calculate the update to 𝑣

first so that we can use it in the update to 𝐦).