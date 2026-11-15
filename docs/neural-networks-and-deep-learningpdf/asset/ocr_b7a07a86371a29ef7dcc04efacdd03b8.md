trained, they will still find it extremely difficult to identify the input image, simply because they don't have enough information. And so it can't possibly be the case that not much learning needs to be done in the first layer. If we're going to train deep networks, we need to figure out how to address the vanishing gradient problem.

# What's causing the vanishing gradient problem? Unstable gradients in deep neural nets

To get insight into why the vanishing gradient problem occurs, let's consider the simplest deep neural network: one with just a single neuron in each layer. Here's a network with three hidden layers:

![](bbox=[0.145, 0.365, 0.625, 0.395])

Here, \(w_1, w_2, ...\) are the weights, \(b_1, b_2, ...\) are the biases, and \(C\) is some cost function. Just to remind you how this works, the output \(a_j\) from the \(j\)th neuron is \(\sigma(z_j)\), where \(\sigma\) is the usual sigmoid activation function, and \(z_j = w_ja_{j-1} + b_j\) is the weighted input to the neuron. I've drawn the cost \(C\) at the end to emphasize that the cost is a function of the network's output, \(a_4\): if the actual output from the network is close to the desired output, then the cost will be low, while if it's far away, the cost will be high.

We're going to study the gradient \(\partial C/\partial b_1\) associated to the first hidden neuron. We'll figure out an expression for \(\partial C/\partial b_1\), and by studying that expression we'll understand why the vanishing gradient problem occurs.

I'll start by simply showing you the expression for \(\partial C/\partial b_1\). It looks forbidding, but it's actually got a simple structure, which I'll describe in a moment. Here's the expression (ignore the network, for now, and note that \(\sigma'\) is just the derivative of the \(\sigma\) function):

```
\(\frac{\partial C}{\partial b_1} = \sigma'(z_1) \times w_2 \times \sigma'(z_2) \times w_3 \times \sigma'(z_3) \times w_4 \times \sigma'(z_4) \times \frac{\partial C}{\partial a_4}\)
```

![](bbox=[0.145, 0.815, 0.625, 0.845])

The structure in the expression is as follows: there is a \(\sigma'(z_j)\) term in the product for each neuron in the network; a weight \(w_j\) term for