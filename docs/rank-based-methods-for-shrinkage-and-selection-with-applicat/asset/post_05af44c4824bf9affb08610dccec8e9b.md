
occur. It is also used for multi-class classification. We will look at both types of classification in the context of image recognition. Both LNNs and RNNs have some advantages over support vector machines (SVMs), as described in Chapter 11, in that they both provide probability prediction and handle multi-class problems directly. Further, we will demonstrate that RNNs will outperform LNNs in image classification with outliers present and will provide equivalent performance when they are not present. We will present the loss functions for both methods that are used to estimate the parameters of the network. Optimization of these types of networks is carried out using gradient descent but they are usually accelerated using “momentum”, which will also be described. The method of creating the gradient terms through back propagation will also be included. In addition, accuracy metrics suitable for binary and multi-class classification will also be presented. Finally, three different applications will be used to compare and contrast RNNs and LNNs.

## 12.2 Set-up for Neural Networks

We begin with what appears to be a short review of logistic regression but actually forms the basis of neural networks. Recall that \(Y_i \in \{0, 1\}\) is the dichotomous dependent variable and \(\boldsymbol{x}_i = (1, x_{i1}, ..., x_{ip})^T\) is the \((p + 1)\)-dimensional vector of independent variables for the \(i\)th observation. Then, the conditional probability of \(Y_i = 1\) given \(\boldsymbol{x}_i\) is

\(P(Y_i = 1 | \boldsymbol{x}_i) = (1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta}))^{-1},\) (12.2.1)

where \(\boldsymbol{\beta} = (\beta_0, \beta_1, ..., \beta_p)^T\) is the (p+1)-dimensional vector of regression parameters. The corresponding logistic regression model is as follows

\(\log \frac{p(\boldsymbol{x}_i)}{1 - p(\boldsymbol{x}_i)} = \beta_0 + x_{i1}\beta_1 + ... + x_{ip}\beta_p,\) (12.2.2)

where the sigmoid function is

\(p(\boldsymbol{x}_i) = \frac{1}{1 + \exp(-\boldsymbol{x}_i^\top \boldsymbol{\beta})}.\) (12.2.3)

We can develop an estimator for \(\boldsymbol{\beta}\) using maximum likelihood principles starting with

\(\mathcal{L}(\boldsymbol{\beta}) = \prod_{i=1}^n (p_i)^{y_i} (1 - p_i)^{(1-y_i)},\) (12.2.4)

where

\( p_i = p(\mathbf{x}_i) = \frac{1}{1 + \exp(-z_i)}, \quad (12.2.5) \)

and

\( z_i = \beta_0 + x_{i1}\beta_1 + ... + x_{ip}\beta_p. \quad (12.2.6) \)

The (negative) log-likelihood loss function is

\( J(\boldsymbol{\beta}) = -\sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log (1 - p_i)]. \quad (12.2.7) \)

Then, the resulting estimator of log-likelihood neural network (LNN) is

\( \hat{\boldsymbol{\beta}}_n^{\text{LNN}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ -\sum_{i=1}^n [y_i \log p_i + (1 - y_i) \log (1 - p_i)] \right\}. \)

We minimize this convex function using some form of gradient descent to obtain the \(\boldsymbol{\beta}\) estimates.

In neural networks, parameter shrinkage is typically conducted using ridge penalty function. LASSO, aLASSO and Enet penalties we will not be covered in this chapter, although extensions of the equations to include these penalties are rather straightforward. We should mention that a method referred to as \(dropout^2\) is widely used for regularization and the reader should investigate this method and other penalties further, if interested. We will focus on the ridge form of the penalized log-likelihood estimator as follows,

\( \hat{\boldsymbol{\beta}}_n^{\text{LNN-ridge}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ J(\boldsymbol{\beta}) + \lambda_2 \sum_{j=1}^p \beta_j^2 \right\}. \)

Note that, typically, we only employ the penalty on \((\beta_1, ... , \beta_p)^\top\) and not on the intercept parameter, \(\beta_0\).

For rank-based methods, the same steps are applied except that the log-likelihood loss function above is replaced by the nonlinear dispersion function,

2 Dropout is a method whereby hidden units randomly selected in the neural network are literally dropped out of the network in each iteration to improve the generality of the model. Anywhere from 1% to 10% may be removed in a given iteration. This is probably the most well-known form of regularization in neural networks. Ridge is also used in conjunction with dropout for shrinkage and to control parameter magnitudes.

\( D_n(\boldsymbol{\beta}) = \sum_{i=1}^n (y_i - f(\boldsymbol{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(\boldsymbol{\beta})), \quad (12.2.8) \)

where the nonlinear function is

\( f(\boldsymbol{x}_i^T \boldsymbol{\beta}) = \frac{1}{1 + \exp(-\boldsymbol{x}_i^T \boldsymbol{\beta})}. \quad (12.2.9) \)

Then, the resulting estimator for the rank neural network (RNN) is

\( \hat{\boldsymbol{\beta}}_n^{\text{RNN}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ \sum_{i=1}^n (y_i - f(\boldsymbol{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(\boldsymbol{\beta})) \right\}. \)

The penalized R-estimator for neural networks with ridge is

\( \hat{\boldsymbol{\beta}}_n^{\text{RNN-ridge}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D_n(\boldsymbol{\beta}) + \lambda_2 \sum_{j=1}^p \beta_j^2 \right\}. \)

Thus far, the neural network appears to be the same as logistic regression, with the attendant consistency and asymptotic normality conditions satisfied. However this is because we are considering a neural network with an input layer and an output layer. There are no hidden layers or hidden units as yet. For this case, the neural network and logistic regression are identical, considering the sigmoid activation function. When we begin to add layers between the inputs and outputs, and then furnish each layer with a specified number of hidden units, it becomes a proper neural network. The number of layers, \( L \), and the number of units in each hidden layer, \( U_k \), where \( k = 1, ..., L \), define the architecture of a fully connected neural network. The details of the architecture of neural networks and how to implement them are described in the next section.

## 12.3 Implementing Neural Networks

In this section, we describe practical aspects of the implementation of neural networks in the traditional log-likelihood form and the new rank-based approach. Any description of statistical learning algorithms in software involves the use of several tuning parameters, called hyper-parameters (to distinguish them from regression parameters), that are adjusted when applied to specific use cases. For example, the learning rate (\( \ell \)), penalty factor (\( \lambda \)), number of layers (\( L \)), number of units in each layer (\( U_k, k = 1, ..., L \)), momentum factor (\( \gamma \)) and ROC threshold (\( p_{\text{T}} \)) are among the many possible hyper-parameters.

Figure 12.1 Computational unit (neuron) for neural networks. It is comprised of a set of inputs, a logit/activation function and an output. Neural networks are constructed by replicating this basic unit to form hidden layers to increase the feature space.

These hyper-parameters will all be defined in the sections to follow along with their purpose and typical ranges.

### 12.3.1 Basic Computational Unit

The basic building block of a neural network is comprised of a set of inputs, a logit/activation unit, and an output. The computation involves a linear combination of the inputs and the application of an activation function. The activation function is some type of nonlinear function that operates on the linear combination of inputs to produce the output. We can represent this two-step sequence of operations in terms of a data flow graph, as shown in Figure 12.1. The inputs are combined to form z and the output as determined by a(z), the activation function.

Figure 12.1 illustrates a specific example: the case of four independent variables (plus the bias term 3, \(\beta_0\)) and one dependent variable. Each input, \(x_i\), is multiplied by its respective edge weights, \(\beta_i\), and summed together to form z,

\(z = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \beta_3 x_3 + \beta_4 x_4.\) (12.3.1)

Then z is applied to the activation function, \(a(z)\), to produce the output of the computational unit. The reason for the data flow diagram representation will become clear shortly when it is used in a neural network diagram.

### 12.3.2 Activation Functions

The nonlinear part of the computational unit is referred to as the activation function. There are a number of possible choices for this function: sigmoid(z), relu(z), leaky-relu(z), elu(z), maxout(z), tanh(z), and so on. In Chapter 11, we

3 The bias term as used here can be viewed as an intercept term and is unrelated to the bias-variance tradeoff.
