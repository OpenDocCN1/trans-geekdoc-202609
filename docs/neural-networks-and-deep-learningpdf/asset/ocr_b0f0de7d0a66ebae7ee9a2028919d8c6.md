multi-neuron network. Suppose all the neurons in the final layer are *linear neurons*, meaning that the sigmoid activation function is not applied, and the outputs are simply \(a_j^L = z_j^L\). Show that if we use the quadratic cost function then the output error \(\delta^L\) for a single training example \(x\) is given by

```
\(\partial^L = a^L - y.\) (68)
```

Similarly to the previous problem, use this expression to show that the partial derivatives with respect to the weights and biases in the output layer are given by

```
\(\frac{\partial C}{\partial w_{jk}^L} = \frac{1}{n} \sum_x a_k^{L-1}(a_j^L - y_j)\) (69)
\(\frac{\partial C}{\partial b_j^L} = \frac{1}{n} \sum_x (a_j^L - y_j).\) (70)
```

This shows that if the output neurons are linear neurons then the quadratic cost will not give rise to any problems with a learning slowdown. In this case the quadratic cost is, in fact, an appropriate cost function to use.

# Using the cross-entropy to classify MNIST digits

The cross-entropy is easy to implement as part of a program which learns using gradient descent and backpropagation. We'll do that later in the chapter, developing an improved version of our earlier program for classifying the MNIST handwritten digits, network.py. The new program is called network2.py, and incorporates not just the cross-entropy, but also several other techniques developed in this chapter*. For now, let's look at how well our new program classifies MNIST digits. As was the case in Chapter 1, we'll use a network with 30 hidden neurons, and we'll use a mini-batch size of 10. We set the learning rate to \(\eta = 0.5*\) and we train for 30 epochs. The interface to network2.py is slightly different than network.py, but it should still be clear what is going on. You can, by the way, get documentation about network2.py's interface by using commands such as help(network2.Network.SGD) in a Python shell.

> *The code is available on GitHub.

> *In Chapter 1 we used the quadratic cost and a learning rate of \(\eta = 3.0\). As discussed above, it's not possible to say precisely what it means to use the "same" learning rate when the cost function is changed. For both cost functions I experimented to find a learning rate that provides near-optimal performance, given the other hyper-parameter choices.

> There is, incidentally, a very rough general heuristic for relating the learning rate for the cross-entropy and the quadratic cost. As we saw earlier, the gradient terms for the quadratic cost have an extra \(\sigma' = \sigma(1 - \sigma)\) term in them. Suppose we average this over values for \(\sigma\). \(\int_0^1 d\sigma \sigma(1 - \sigma) = 1/6\). We see that (very roughly) the quadratic cost learns an average of 6 times

```
>>> import mnist_loader
>>> training_data, validation_data, test_data = \
... mnist_loader.load_data_wrapper()
>>> import network2
>>> net = network2.Network([784, 30, 10], cost=network2.CrossEntropyCost)
>>> net.large_weight_initializer()
```