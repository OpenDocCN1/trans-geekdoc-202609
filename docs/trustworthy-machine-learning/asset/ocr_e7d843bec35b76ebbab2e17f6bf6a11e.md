output node sums the weighted inputs, so computes $w^T x$, and then passes the sum through the step function. This overall procedure is exactly the same as logistic regression described earlier, but described in a graphical way.

In the regular case of a neural network with one or more hidden layers, nodes in the hidden layers also start with a weighted summation. However, instead of following the summation with an abrupt step function, hidden layer nodes use softer, more gently changing *activation functions*. A few different activation functions are used in practice, whose choice contributes to the inductive bias. Two examples, the sigmoid or logistic activation function $1/(1 + e^{-z})$ and the rectified linear unit (ReLU) activation function $\max\{0, z\}$, are shown in Figure 7.14. The ReLU activation is typically used in all hidden layers of deep neural networks because it has favorable properties for optimization techniques that involve the gradient of the activation function.

![](bbox=[0.1, 0.45, 0.55, 0.68])

Figure 7.14. *Activation functions*. Accessible caption. A plot with activation function on the vertical axis and input on the horizontal axis. The sigmoid function is a gently rolling S-shaped curve that equals 0.5 at input value 0, approaches 0 as the input goes to negative infinity, and approaches 1 as the input goes to positive infinity. The ReLU function is 0 for all negative inputs and increases linearly starting at 0.

When there are several hidden layers, the outputs of nodes in one hidden layer feed into the nodes of the next hidden layer. Thus, the neural network's computation is a sequence of compositions of weighted sum, activation function, weighted sum, activation function, and so on until reaching the output layer, which finally applies the step function. The number of nodes per hidden layer and the number of hidden layers is a design choice for JCN Corporation's data scientists to make.

You and your team have analyzed the hypothesis space. Cool beans. The next thing for you to analyze is the loss function of neural networks. Recall that margin-based loss functions multiply the true label $y_j$ by the distance $w^T x_j$ (not by the predicted label $\hat{y}(x_j)$), before applying the step function. The *cross-entropy loss*, the most common loss function used in neural networks, does kind of the same thing. It compares the true label $y_j$ to a soft prediction $\varphi(x_j)$ in the range $[0,1]$ computed in the output node before the step function has been applied to it. The cross-entropy loss function is:

$L(y_j, \varphi(x_j)) = - \big( y_j \log(\varphi(x_j)) + (1 - y_j) \log(1 - \varphi(x_j)) \big).$

Equation 7.5