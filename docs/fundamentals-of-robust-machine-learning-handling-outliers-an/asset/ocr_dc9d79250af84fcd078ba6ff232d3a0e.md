another method called **rmsprop**. The Adam optimizer contains these methods as well as other heuristic techniques to improve convergence of neural networks. We will explore the details of the Adam optimizer in Chapter 10. For now, the goal is simply to understand the basics of neural network optimization.

The two objective functions to be considered are the cross-entropy loss and the log-cosh loss. The cross-entropy loss function is given by

```
J^{CE}(w, b) = - \sum_{i=1}^n [y_i \log(p_i) + (1 - y_i) \log(1 - p_i )]. \quad (9.4.1)
```

The log-cosh loss function is given by

```
J^{LC}(w, b) = \frac{1}{a} \sum_{i=1}^n \log(\cosh((a(y_i - p_i))). \quad (9.4.2)
```

Both of these loss functions were derived for logistic regression in Chapter 8. In this chapter, the two will be compared relative to their application in the training of neural networks. The two loss functions may be represented as functions of \(p_i\), \(w\) and/or \(b\). Therefore, we may use any of \(J(w, b)\), \(J(w)\), \(J(b)\), or \(J(p_i)\), depending on the circumstances.

Assume that we want to train a one-layer neural network. Then, \(w\) is a vector of weights and \(b\) is a scalar bias. For gradient descent, we start with some initial values, \(w^{(0)}\) and \(b^{(0)}\), then take a step toward the minimum, and then repeat this in each iteration until we reach the minimum. The weights and biases are updated at each iteration using some fraction of the gradient direction, controlled by \(\ell\), as follows:

```
w^{(t+1)} = w^{(t)} - \ell \times \left( \frac{dJ(w, b)}{dw} \right)^{(t)}, \quad (9.4.3)

b^{(t+1)} = b^{(t)} - \ell \times \left( \frac{dJ(w, b)}{db} \right)^{(t)}. \quad (9.4.4)
```

Here, \(t\) is the iteration count that starts at 0. At the end of the training process, we obtain the final weights and biases which represents the complete model. For multi-layer neural networks, the process is much more involved, as described in the next section.

# 9.5 Forward and Backward Propagation

The best way to understand the details of training a multilayered neural network is through a worked example. Suppose we have a training set with \(n\) rows and two data columns for the explanatory variables and one column for the binary response variable. We decide to build a model using a neural network with one hidden layer comprised of 4 relu units and an output layer with 1 sigmoid unit, as depicted in Figure 9.5. The training begins with some initial random values for the model parameters and then proceeds with forward and backward propagation to update the model in an iterative fashion until satisfactory convergence is achieved. Each pass through this network involves six steps for this small example: four steps in forward propagation to compute a new output, and then two steps for back propagation where the parameters are adjusted using gradients that are based on the size of the errors at the output. Before sequencing through the steps, the issue of gradient calculation is addressed.