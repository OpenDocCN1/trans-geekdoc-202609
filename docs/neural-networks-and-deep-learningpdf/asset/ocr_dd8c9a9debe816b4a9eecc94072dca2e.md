Okay, so we now know how to use neural networks to approximate a real-valued function of many variables. What about vector-valued functions \(f(x_1, ..., x_m) \in R^n\)? Of course, such a function can be regarded as just \(n\) separate real-valued functions, \(f^1(x_1, ..., x_m), f^2(x_1, ..., x_m)\), and so on. So we create a network approximating \(f^1\), another network for \(f^2\), and so on. And then we simply glue all the networks together. So that's also easy to cope with.

# Problem

+   • We've seen how to use networks with two hidden layers to approximate an arbitrary function. Can you find a proof showing that it's possible with just a single hidden layer? As a hint, try working in the case of just two input variables, and showing that: (a) it's possible to get step functions not just in the x or y directions, but in an arbitrary direction; (b) by adding up many of the constructions from part (a) it's possible to approximate a tower function which is circular in shape, rather than rectangular; (c) using these circular towers, it's possible to approximate an arbitrary function. To do part (c) it may help to use ideas from a bit later in this chapter.

# Extension beyond sigmoid neurons

We've proved that networks made up of sigmoid neurons can compute any function. Recall that in a sigmoid neuron the inputs \(x_1, x_2, ...\) result in the output \(\sigma(\sum_j w_j x_j + b)\), where \(w_j\) are the weights, \(b\) is the bias, and \(\sigma\) is the sigmoid function:

![](bbox=[0.18, 0.68, 0.6, 0.8])

What if we consider a different type of neuron, one using some other activation function, \(s(z)\):