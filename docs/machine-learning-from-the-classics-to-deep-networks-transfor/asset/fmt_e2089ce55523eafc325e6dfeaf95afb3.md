
where the notation above means that `f` acts on each one of the respective vector components, individually, and the extension of the vector by one is to account for the bias terms in the standard practice.

For large networks, with many layers and many nodes per layer, this type of connectivity turns out to be very costly in terms of the number of parameters (weights), which is of the order of `k[r] * k[r - 1]`. For example, if `k[r - 1] = 1000` and `k[r] = 1000`, this amounts to an order of 1 million parameters. Note that this number is the contribution from the parameters of only one of the layers. However, a large number of parameters makes a network vulnerable to overfitting, when training is involved, as has already been discussed in Section [3.8](#Chp003_65-117_B9780443292385000093.xhtml).

In contrast, one can employ the so-called *weight sharing* techniques (e.g., [156,204]), where a set of parameters is *shared* among a number of connections, via appropriately built-in constraints. The convolutional networks, to be discussed in Section [18.12](#Chp018_885-995_B978044329238500024X.xhtml#s0170), belong to this family of weight sharing networks. As we will see, in a convolutional network, convolutions replace the inner product operations, which allows for a significant weight sharing that leads to a substantial reduction in the required number of parameters.

### Remarks 18.2

*   **Shallow and deep networks**: From now on, we will refer to the number of layers in a network as the *depth* of the network. Networks with up to three (two hidden) layers are known as *shallow*, whereas those with more than three layers are called *deep* networks.

## 18.4 The backpropagation algorithm

A feed-forward neural network consists of a number of layers of neurons, and each neuron is determined by the corresponding set of synaptic weights and its bias term. From this point of view, a neural network realizes a nonlinear parametric function, `ŷ = f_θ(x)`, where `θ` stands for all the weights/biases present in the network. Thus, training a neural network seems not to be any different from training any other parametric prediction model. All that is needed is (a) a set of training samples, (b) a loss function, `L(y, ŷ)`, and (c) an iterative scheme, for example, gradient descent, to perform the optimization of the associated cost function (empirical loss; see Section [3.14](#Chp003_65-117_B9780443292385000093.xhtml), Chapter [3](#Chp003_65-117_B9780443292385000093.xhtml)),

```
J(θ) = Σ_{n=1}^{N} L(y_n, f_θ(x_n)).
```

The difficulty with training neural networks lies in their multilayer structure that complicates the computation of the gradients, which are involved in the optimization. Moreover, the McCulloch–Pitts neuron is based on the discontinuous Heaviside activation function, which is not differentiable. A first step in developing a practical algorithm for training a neural network is to replace the Heaviside activation function with a differentiable approximation of it.

**The logistic sigmoid neuron**: One possibility is to adopt the logistic sigmoid function, that is,

```
f(z) = σ(z) := 1 / (1 + exp(-a z)).
```

The graph of the function is shown in [Fig. 18.8](#Chp018_885-995_B978044329238500024X.xhtml#f0045). Note that the larger the value of the parameter `a` is, the closer the corresponding graph gets to that of the Heaviside function. Another possibility would be to use

```
f(z) = a tanh(c z / 2),
```
