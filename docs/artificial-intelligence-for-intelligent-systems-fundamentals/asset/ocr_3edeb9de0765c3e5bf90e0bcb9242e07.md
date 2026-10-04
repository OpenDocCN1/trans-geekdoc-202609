# Disadvantage:

Expensive in terms of computation.

# 2.2.2.10 ELU

Another variant of the ReLU is the exponential linear unit (ELU), which attempts to get activations closer to zero to speed up learning. It outperforms the ReLU in terms of classification accuracy. ELUs have negative values, bringing the activa-tion closer to zero.

```
$f(x) = \begin{cases} x & if \ x>0 \ \alpha(e^x-1) & \text{otherwise} \end{cases} \(2.10)$
```

# 2.3 TRAINING A NEURAL NETWORK

Due to the fact that each neural network is the approximation of a function, they will not be equal to the intended function but will differ by a factor called error. The purpose of training is to minimize this error. We attempt to minimize the asso-ciated with the weights, the error is a function of the weights in the network. The error function is dependent on a large number of weights and, thus, on a large number of variables. In mathematics, the collection of points where this function is zero is referred to as a hyper-surface, and we aim to identify a minimum on this surface by selecting a point and tracing a curve in the direction of the minimum.

# 2.3.1 Backpropagation

Backpropagation is a common training technique for artificial neural networks, particularly DNNs.
Backpropagation, as shown in Figure 2.14, is required to compute the gradi-ent, and the weights of the weight matrices must be adjusted. The gradient of the loss function is used to modify the weights of the neural network's neurons (i.e. nodes). A gradient descent optimization technique is employed for this. Backward propagation of mistakes is another name for it. Backpropagation networks may be divided into two categories:

+   Backpropagation in a static state.
Recurrent backpropagation is a kind of backpropagation that occurs repeatedly.

In backpropagation in a static state, static input to output mapping is generated via a backpropagation network. For example, optical character recognition issues that need static classification may be solved using this technique.