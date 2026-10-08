Schematically, this is illustrated as

![](bbox=[0.258, 0.218, 0.765, 0.465])

In the process of training a neural network, the weights are first initialized, most randomly. In forward propagation, the training samples are passed through the neural network, calculating all intermediate activations and latent variables, well as the output for each. Then the errors of each training point are calculated in a backward pass through the network. After this, the derivative with respect to each weight in the network of the contribution to the error function of each training sample is calculated. We form the gradient, either batch, mini-batch or stochastic. The weights are updated by the chosen optimization method.

To get some intuition of what is happening, consider binary classification. We denote the weights in the layer by $w^{(L)}$, since there is only one output neuron. Because of $a^{(l)} = \sum_{i=1}^n w_{i}^{(l)} a_i^{(l-1)}$, the derivatives with respect to the weights in the last layer of the $n^{th}$ contribution to the error sum are

> $$\frac{\partial}{\partial w_i^{(L)}} E_n(w) = (y(x_n) - t_n)\delta_i^{(L)}$

where $(x_n, w_i)$ is interpreted as the probability of $x_n$ belonging to the positive class, the difference classifies $x_n$ correctly as belonging to the positive class, and between $[-0.5, 1]$ for $t_n = 1$, and $[-1, -0.5]$ otherwise. If on the other hand, $w_i = 0$, the difference lies in $[0, 1]$, if the network incorrectly puts this sample in the positive class, and in the interval $[0, 0.5]$ otherwise. This means that, when the weights get updated by this component of the gradient vector, they are adjusted in a positive direction if the sample is in the negative class, and in a negative direction if it is in the positive class. The adjustments are weighted by $\delta_i^{(L)} \ge 0$