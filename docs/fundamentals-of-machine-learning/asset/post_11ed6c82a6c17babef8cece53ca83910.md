
big data. However, the challenge of this approach is greater in situations where there is a limited supply of data. Bayesian models and neural networks are often seen as extreme poles in a modeling approach; here we try to reconcile these views.

Let us now to the second important subject with our desire to build probabilistic models. This connection can be made easily when viewing a percept as an implementation of a logistic regression, as outlined in this chapter. The essence was that a logistic function describes the probability that a data point belongs to one class versus another. In the same way, we are now treating the neural network itself as $p(class=true|w)$. For this we need to adapt a one-hot representation of training data in multiclass problems where each class is represented by a single output node. The value of each output node of the neural network is assumed to represent the probability that the input is from the corresponding class. We argue that the computational layers leading up to this output layer represent transformations of features that is necessary to learn the probabilistic function on which we can base our decision of class membership in classification.

In order to train the network we have already introduced the log-likelihood principle. We are now taking the opportunity to show an alternative of deriving the learning rule of a neural network which is equivalent to maximum likelihood but which is a more common derivation in the neural network community. Indeed, we will take this opportunity to relate this to several common formulations: that of minimizing the log-likelihood, maximizing the cross-entropy, and of minimizing the Kullback-Leibler divergence.

We start by assuming that the true nature of data is given by the unknown density function

True distribution: evenq(y|\mathbf{x})$.

The neural network model represents the probability

Model distribution: $p(y|\mathbf{x}; \mathbf{w})$,

which hope to be a good approximation of $q(y|\mathbf{x})$. The negative log-probability of the given label under the current model is given by

```
$H(p, q) = -\sum_{y} p(y) \log q(y),$
```

where we omitted writing arguments to see the structure more clearly. This quantity is called the cross-entropy. The term $p \log q$ is in essence as the log-likelihood estimate, which we want to maximize. That is, we want to maximize the log probability of the data given labels. The cross-entropy is the negative of this, maximizing the log-probability of the data given the labels is equivalent of minimizing the cross-entropy. Furthermore, since

```
$p \log(q) = p \log \frac{q}{p} + p \log p$
```

and $p \log \frac{q}{p}$ is the Kullback-Leibler (KL) divergence, we can relate this cross-entropy to the entropy of the distribution $p$ an the KL divergence,

```
$H(p, q) = H(p) + KL(p||q). \quad (7.62)$
```

```
$KL(p||q) = \int p(x) \log \frac{p(x)}{q(x)} dx. \quad (7.63)$
```

Since changing model parameters does not affect the true data, minimizing the cross-entropy is equivalent to minimizing the KL divergence. This has an interesting interpretation as we consider the learning as looking for the parameters to minimize the distribution by the data and the distribution given by the model. There are therefore many ways to develop the learning rule in neural network, and we hope it became that they are equivalent and these are closely related to the (max-) likelihood principle.

Let us apply this to a binary classification model which is described by Bernoulli variables that take the value 0 or 1. For this density, the cross-entropy is given by

```
$H(p, q) = -p(y=0;\mathbf{w}) \log q(y=0;\mathbf{w}) - p(y=1;\mathbf{w}) \log q(y=1|\mathbf{w}) \quad (7.64)$
```

or

```
$H(p, q) = -p \log q - (1-p) \log (1-q) \quad (7.65)$
```

for short, if we consider that $p$ stands for $p(y=0;\mathbf{w})$. We now assume a sigmoidal function for the probability of the class membership around a decision point,

```
$p(y=0;\mathbf{w}) = \frac{1}{1+e^{-xw}} \quad (7.66)$
```

```
$\tilde{p}(y=0;\mathbf{w}) = \frac{1}{1+e^{-w}} \quad (7.67)$
```

Hence, minimizing the cross-entropy between the network output $\tilde{p}$ and the given labels $y$ is given by minimizing the Loss function

```
$L = -y \log \tilde{p}(y) - (1-y) \log (1-\tilde{p}(y)) \quad (7.68)$
```

```
$L = y \log(1+e^{-w}) + (1-y) \log(1+e^{w}) \quad (7.69)$
```

The derivative of the function is

```
$\frac{dL}{d(\mathbf{w})} = y \frac{e^{-w}}{1+e^{-w}} + (1-y) \frac{e^{w}}{1+e^{w}} \quad (7.70)$
$= -y \frac{1}{1+e^{w}} + (1-y) \frac{1}{1+e^{-w}} \quad (7.71)$
$= -y(1-\tilde{p}(y)) + (1-y)\tilde{p}(y) \quad (7.72)$
$= -y + y\tilde{p}(y) + \tilde{p}(y) - y\tilde{p}(y) \quad (7.73)$
$= \tilde{p}(y) - y. \quad (7.74)$
```

from which we can derive the gradient we need for the learning rule

```
$\frac{dL}{d(\mathbf{w})} = \frac{dL}{d(xw)} \frac{d(xw)}{d(\mathbf{w})} = (\tilde{p}(y) - y)\mathbf{x}. \quad (7.75)$
```

This expression has the now familiar form of the perceptron learning rule. For multiclass problems, the equivalent of the sigmoid is the softmax function

```
$p(\tilde{y}=i|\mathbf{x};\mathbf{w})=\frac{e^{xW_i}}{\sum_{j=1}^N e^{xW_j}} \quad (7.76)$
```

$N$ is the number of classes. You can easily see the equivalence to the sigmoid in the case of having two classes,

```
$p(\tilde{y}=0)=\frac{e^0}{e^0+e^{xw}}=\frac{1}{1+e^{xw}}=1-\frac{1}{1+e^{xw}}$
$p(\tilde{y}=1)=\frac{e^{xw}}{e^0+e^{xw}}=\frac{e^{xw}}{1+e^{xw}}=\frac{1}{1+e^{-xw}}$
```

The derivation of the gradient for this multi-class case works out the same as the binary classification,

```
$\frac{dL}{d(x\mathbf{W})}=(p(\tilde{y})-\mathbf{y}) \quad (7.77)$
$\frac{dL}{d\mathbf{x}}=(p(\tilde{y}))\mathbf{W}^T \quad (7.78)$
$\frac{dL}{d\mathbf{W}}=\mathbf{x}^T(p(\tilde{y})-\mathbf{y}) \quad (7.79)$
```

Thus, in summary. A neural network, regardless of having many or fewer, is in this case implementation of a probabilistic model for classification or logistic regression when the output layer is chosen to be a softmax function and the loss function is the negative entropy. This concludes the conclusion of our second point, how neural networks are linked to probabilistic regression.

## 7.6.2 Stochastic and Bayesian neural networks

We have outlined how we can use a neural network as parameterized function approximator $y=f(\mathbf{x};\mathbf{w})$. We have used this to approximate a probability function $p(y|\mathbf{x})$ where we determined the parameters from a learning rule such as maximum likelihood estimation. In a Bayesian inference we want to go a step further where we want not just to use a point estimate of the parameters but know the posterior probability of all kind of values of the parameters that could have generated the training data, $p(\mathbf{w}|\mathbf{x};y)$. With this function we can make true estimates of the probability of predictions of the label $y^0$ for a new data point $\mathbf{x}^0$.

```
$p(y^0|\mathbf{x}^0)=\int p(y|\mathbf{x}^0;\mathbf{w})p(\mathbf{w}|\mathbf{x};y)d\mathbf{w} \quad (7.80)$
```

Unfortunately, the posterior $p(\mathbf{w}|\mathbf{x};y)$ is usually not tractable, and approximate techniques like variational inference have to be used. While a detailed discussion is beyond the scope of this book, we recommend work by David McKay, Radford Neal, and Zoubin Ghahramani for further studies.

Another way of looking into this is to consider the neurons themselves as stochastic so that the neural network forms a Bayesian network itself. For example, we could change the gain function of the artificial neuron to a stochastic rule, like

```
$p(y=1|x,w) = \frac{1}{1+e^{-xw}} \quad (7.81)$
```

While this looks equivalent to Eq 7.66, the difference now is that the output of the neuron is $y=1$ only with a certain probability and $y=0$ with the complementary probability. Hence, this neuron is a binary neuron with only binary states, on and off.
This seems better to remember the spiking nature of real neurons.

Networks of probabilistic neurons have been studied earlier, in particular within bi-directional recurrent neural networks that we will review in Chapter 9. If the neurons are stochastic nodes in a network, then we can view this network as an undirected Bayesian network where the weights represent some form of conditional probability to influence the firing of the receiving neuron. We will get back to this point in Chapter 9.

There is strong evidence that real neurons are stochastic in nature, and there is also a lot of evidence of the stochastic nature of synapses. While it is sometimes argued that noise in synaptic processes should be expected as this is a biological system, Enoki and Fine showed that the probabilities of neurotransmitter releases can be modulated with classical synaptic plasticity experiments. This area is largely unexplored.
