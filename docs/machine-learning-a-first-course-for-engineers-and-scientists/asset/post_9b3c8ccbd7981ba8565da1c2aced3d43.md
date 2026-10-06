
## 5.7 Further reading

1000, but that is of course only example. One could induce some manual work by first selecting a coarse grid to get an initial guess, and thereafter refine the grid only around the promising candidates. In practice, the problem has more than one dimension, and could also be beneficial to select the grid points randomly instead of using an equally spaced linear or logarithmic grid.

The manual procedure of choosing a grid method, however, become quite tedious, and one could wish for an automated method. That is, in fact, possible by treating the grid point selection as a machine learning problem. If we consider the method in which we use a regression method to learn a model for the objective function then that model can, in turn, be used to answer questions on where to evaluate the objective function, and by selecting the next grid point. A concrete method built from this is the Gaussian process optimization method, which uses Gaussian processes (Chapter 9) for learning a model of the objective function.

A mathematically more thorough discussion on loss functions is provided by Gneiting and Raftery (2007). Some of the asymptotic properties, also referred to as population minimizers, are derived by Hastie et al. (2009, Section 10.5-10.6).

A standard reference for optimization, covering much more than this chapter, is the book by Nocedal and Wright (1991), and two overviews of its modern use in machine learning are given by Botton et al. (2018) and Rudicker (2017). For Gaussian process optimization, see Frazier (2018) and Snell et al. (2012). $L^2$ regularization was introduced independently in statistics by Hoer and Kendall (1970) and earlier in numerical analysis by Andrey Nikolevich Tikonov. The $L^2$ regularization was first introduced by Tibshirani (1996). Early stopping has been used as a regularizer for long time in the neural network practice and has been analyzed by Bishop (1995) and Sjoberg and Ljung (1995). For the regularizing effect of stochastic gradient descent, see Hardt et al. (2016) and Mandi et al. (2017). A list has been written about adaptive methods and many different algorithms are available. The ADAGRAD algorithm was introduced by Duchi et al. (2011) and ADAM was derived by D. P. Kingma and Ba (2015). Interesting insights about these algorithms are offered by Reddi et al. (2018).

## 6 Neural networks and deep learning

In Chapter 3 we introduced linear regression and logistic regression as the two parametric models for solving the regression and classification problems. A neural network extends this by stacking multiple of these models to construct a hierarchical model that can describe more complicated relationships between inputs and outputs than the linear or logistic regression models can do. Deep learning is a subfield of machine learning that deals with deep neural networks.

We will start in Section 6.1 by generalizing linear regression to a two-layer neural network (that is, a neural network with one hidden layer), and then generalize it further to a deep neural network. In Section 6.3 we present a special neural network tailored for images and in Section 6.2 we look into some details on how to train neural networks. Finally, in Section 6.4, we provide one technique for how to regulate neural networks.

### 6.1 The neural network model

In Section 5.1 we introduced concept of nonlinear parametric functions for modeling the relationship between the input variables $x_1, \dots, x_p$ and the output $y$. We denote this nonlinear relationship on its prediction format as

```
$$\widehat{y} = f(x_1, \dots, x_p), \quad (6.1)$$
```

where the function $f$ is parametrized by $\theta$. Such a nonlinear function can be parametrized in many ways. In a neural network, the strategy is to use layers of linear regression models and nonlinear activation functions. We will explain clearly how these are made step by step.

### Generalized linear regression

We start the description of the neural network model with the linear regression model

```
$$\widehat{y} = W_1x_1 + W_2x_2 + \dots + W_px_p + b, \quad (6.2)$$
```

Here we denote the parameters with weights $W_1, \dots, W_p$ and the offset term $b$. We choose to use this notation instead of used in (3.2) we will later handle the weights slightly different from the offset term. Each input variable $x_i$ is represented with a node and each character $W_j$ with a link. Furthermore, the output $\widehat{y}$ is described as the sum of all $W_{ij}x_j$. Note that we use the constant value 1 as the input variable corresponding to the intercept term.

To describe nonlinear activation functions between $x = [x_1, x_2, \dots, x_p]^T$ we introduce a nonlinear scalar activation function $h : \mathbb{R} \to \mathbb{R}$. The regression model (6.2) is now modified into a generalized linear regression (see Section 3.4) where the linear combination of the inputs is transformed by the activation function

```
$$\widehat{y} = h(W_1x_1 + W_2x_2 + \dots + W_px_p + b). \quad (6.3)$$
```

This extension to the generalized linear regression model is visualized in Figure 6.1. Common activation functions are the logistic function and

- Logistic: $h(z) = \frac{1}{1+e^{-z}}$
- ReLU: $h(z) = \max(0, z)$

The generalized linear regression model (6.3) is very simple and itself incapable of describing very complicated relationships between the input $x$ and the output $\hat{y}$. Therefore, we make two further extensions to increase the generality of the model: we first make use of *several parallel* linear regression models to build a *two-layer network* and then stack these layers in a *sequential* construction (which will result in a deep neural network).

### Two-layer neural network

In (6.3), the output $\hat{y}$ is constructed by one scalar regression model. To increase its flexibility and turn into a two-layer neural network, we instead let its output be a sum of $U$ generalized linear regression models, each of which has its own set of parameters. The parameter for the $k^{th}$ regression model are $b_k, W_{k1}, \dots, W_{kd}$ and we denote our output by $q_k$.

```
$q_k = h_k(W_{k1}x_1 + W_{k2}x_2 + \dots + W_{kd}x_p + b_k), \quad k=1, \dots, U.$
```

These intermediate outputs $q_k$ are called hidden units, which are not the output of the model. The $U$ different hidden units $\{q_k\}_{k=1}^U$ instead act as inputs to an additional linear regression model

```
$\hat{y} = W_1q_1 + W_2q_2 + \dots + W_Uq_U + b.$
```

To distinguish the parameters in (6.4) and (6.5) we add the superscripts (1) and (2), respectively. The equations describing this two-layer neural network (or equivalently, a neural network with one
