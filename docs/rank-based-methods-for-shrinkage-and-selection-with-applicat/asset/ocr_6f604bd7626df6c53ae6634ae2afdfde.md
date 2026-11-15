\( D_n(\boldsymbol{\beta}) = \sum_{i=1}^n (y_i - f(\boldsymbol{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(\boldsymbol{\beta})), \quad (12.2.8) \)

where the nonlinear function is

\( f(\boldsymbol{x}_i^T \boldsymbol{\beta}) = \frac{1}{1 + \exp(-\boldsymbol{x}_i^T \boldsymbol{\beta})}. \quad (12.2.9) \)

Then, the resulting estimator for the rank neural network (RNN) is

\( \hat{\boldsymbol{\beta}}_n^{\text{RNN}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ \sum_{i=1}^n (y_i - f(\boldsymbol{x}_i^T \boldsymbol{\beta})) a_n(R_{n_i}(\boldsymbol{\beta})) \right\}. \)

The penalized R-estimator for neural networks with ridge is

\( \hat{\boldsymbol{\beta}}_n^{\text{RNN-ridge}} = \underset{\boldsymbol{\beta}}{\operatorname{argmin}} \left\{ D_n(\boldsymbol{\beta}) + \lambda_2 \sum_{j=1}^p \beta_j^2 \right\}. \)

Thus far, the neural network appears to be the same as logistic regression, with the attendant consistency and asymptotic normality conditions satisfied. However this is because we are considering a neural network with an input layer and an output layer. There are no hidden layers or hidden units as yet. For this case, the neural network and logistic regression are identical, considering the sigmoid activation function. When we begin to add layers between the inputs and outputs, and then furnish each layer with a specified number of hidden units, it becomes a proper neural network. The number of layers, \( L \), and the number of units in each hidden layer, \( U_k \), where \( k = 1, ..., L \), define the architecture of a fully connected neural network. The details of the architecture of neural networks and how to implement them are described in the next section.

# 12.3 Implementing Neural Networks

In this section, we describe practical aspects of the implementation of neural networks in the traditional log-likelihood form and the new rank-based approach. Any description of statistical learning algorithms in software involves the use of several tuning parameters, called hyper-parameters (to distinguish them from regression parameters), that are adjusted when applied to specific use cases. For example, the learning rate (\( \ell \)), penalty factor (\( \lambda \)), number of layers (\( L \)), number of units in each layer (\( U_k, k = 1, ..., L \)), momentum factor (\( \gamma \)) and ROC threshold (\( p_{\text{T}} \)) are among the many possible hyper-parameters.