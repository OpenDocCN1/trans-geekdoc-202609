
The complicated task in the above equation is to compute the gradient (derivative) which tells in which direction the adjustment should be done. The problem is that the successive nested layers and associated activations require many iterations of the chain rule for differentiation.

![](img/8861a37f775d09b4ba7a5151f604d9f5_118_0.png)

**FIGURE 7.5:** Outline of gradient descent.

The most common way to approximate a derivative is probably the finite difference method. Under the usual assumptions (the loss is twice differentiable), the centered difference satisfies:

```
\(\frac{\partial D(\tilde{y}_i(w_k))}{\partial w_k} = \frac{D(\tilde{y}_i(w_k + h)) - D(\tilde{y}_i(w_k - h))}{2h} + O(h^2),\)
```

where \(h > 0\) is some arbitrarily small number. In spite of its apparent simplicity, this method is costly computationally because it requires a number of operations of the magnitude of the number of weights.

Luckily, there is a small trick that can considerably ease and speed up the computation. The idea is to simply follow the chain rule and recycle terms along the way. Let us start by recalling

```
\(\tilde{y}_i = f^{(L+1)} \left( \mathbf{o}_i^{(L)} \right)' \mathbf{w}^{(L+1)} + b^{(L+1)} = f^{(L+1)} \ b^{(L+1)} + \sum_{k=1}^{U_L} w_k^{(L+1)} o_{i,k}^{(L)} ,\)
```

so that if we differentiate with the most immediate weights and biases, we get:

```
\(\frac{\partial D(\tilde{y}_i)}{\partial w_k^{(L+1)}} = D'(\tilde{y}_i) \ f^{(L+1)} ' \ b^{(L+1)} + \sum_{k=1}^{U_L} w_k^{(L+1)} o_{i,k}^{(L)} \ o_{i,k}^{(L)} \quad (7.3)\)
\(= D'(\tilde{y}_i) \ f^{(L+1)} ' \ v_{i,k}^{(L+1)} \ o_{i,k}^{(L)} \quad (7.4)\)
\(\frac{\partial D(\tilde{y}_i)}{\partial b^{(L+1)}} = D'(\tilde{y}_i) \ f^{(L+1)} ' \ b^{(L+1)} + \sum_{k=1}^{U_L} w_k^{(L+1)} o_{i,k}^{(L)} .\quad (7.5)\)
```

This is the easiest part. We must now go back one layer and this can only be done via the chain rule. To access layer \(L\), we recall identity \(v_{i,k}^{(L)} = \left( \mathbf{o}_i^{(L-1)} \right)' \mathbf{w}_k^{(L)} + b_k^{(L)} = b_k^{(L)} + \sum_{j=1}^{U_L} o_{i,j}^{(L-1)} w_{k,j}^{(L)}\). We can then proceed:

```
\(\frac{\partial D(\tilde{y}_i)}{\partial w_{k,j}^{(L)}} = \frac{\partial D(\tilde{y}_i)}{\partial v_{i,k}^{(L)}} \frac{\partial v_{i,k}^{(L)}}{\partial w_{k,j}^{(L)}} = \frac{\partial D(\tilde{y}_i)}{\partial v_{i,k}^{(L)}} o_{i,j}^{(L-1)} \quad (7.6)\)

\(= \frac{\partial D(\tilde{y}_i)}{\partial o_{i,k}^{(L)}} \frac{\partial o_{i,k}^{(L)}}{\partial v_{i,k}^{(L)}} o_{i,j}^{(L-1)} = \frac{\partial D(\tilde{y}_i)}{\partial o_{i,k}^{(L)}} (f^{(L)})'(v_{i,k}^{(L)}) o_{i,j}^{(L-1)} \quad (7.7)\)

\(= \underbrace{D'(\tilde{y}_i) f^{(L+1)\prime}}_{computed \ above!} v_{i,k}^{(L+1)} w_k^{(L+1)} (f^{(L)})'(v_{i,k}^{(L)}) o_{i,j}^{(L-1)}, \quad (7.8)\)
```

where, as we show in the last line, one part of the derivative was already computed in the previous step (Equation (7.4)). Hence, we can recycle this number and only focus on the right part of the expression.

The magic of the so-called back-propagation is that this will hold true for each step of the differentiation. When computing the gradient for weights and biases in layer $l$, there will be two parts: one that can be recycled from previous layers and another, local part, that depends only on the values and activation function of the current layer. A nice illustration of this process is given by the Google developer team: playground.tensorflow.org.

When the data is formatted using tensors, it is possible to resort to vectorization so that the number of calls is limited to an order of the magnitude of the number of nodes (units) in the network.

The back-propagation algorithm can be summarized as follows. Given a sample of points (possibly just one):

- 1. the data flows from left as is described in Figure 7.6. The blue arrows show the **forward pass**;
- 2. this allows the computation of the error or loss function;
- 3. all derivatives of this function (w.r.t. weights and biases) are computed, starting from the last layer and diffusing to the left (hence the term back-propagation) - the green arrows show the **backward pass**;
- 4. all weights and biases can be updated to take the sample points into account (the model is adjusted to reduce the loss/error stemming from these points).

![](img/8861a37f775d09b4ba7a5151f604d9f5_120_0.png)

**FIGURE 7.6:** Diagram of back-propagation.

This operation can be performed any number of times with different sample sizes. We discuss this issue in Section 7.3.

The learning rate \(\eta\) can be refined. One option to reduce overfitting is to impose that after each epoch, the intensity of the update decreases. One possible parametric form is \(\eta = \alpha e^{-\beta t}\), where \(t\) is the epoch and \(\alpha, \beta > 0\). One further sophistication is to resort to so-called *momentum* (which originates from Polyak (1964)):

```
\(\mathbf{W}_{t+1} \leftarrow \mathbf{W}_t - \mathbf{m}_t\) with

\(\mathbf{m}_t \leftarrow \eta \frac{\partial D(\tilde{y}_i)}{\partial \mathbf{W}_t} + \gamma \mathbf{m}_{t-1},\) (7.9)
```

where \(t\) is the index of the weight update. The idea of momentum is to speed up the convergence by including a memory term of the last adjustment (\(\mathbf{m}_{t-1}\)) and going in the same direction in the current update. The parameter \(\gamma\) is often taken to be 0.9.

More complex and enhanced methods have progressively been developed:

- Nesterov (1983) improves the momentum term by forecasting the future shift in parameters;
- Adagrad (Duchi et al. (2011)) uses a different learning rate for each parameter;
- Adadelta (Zeiler (2012)) and Adam (Kingma and Ba (2014)) combine the ideas of Adagrad and momentum.

Lastly, in some degenerate case, some gradients may explode and push weights far from their optimal values. In order to avoid this phenomenon, learning libraries implement gradient clipping. The user specifies a maximum magnitude for gradients, usually expressed as a norm. Whenever the gradient surpasses this magnitude, it is rescaled to reach the authorized threshold. Thus, the direction remains the same, but the adjustment is smaller.

## 7.2.4 Further details on classification

In decision trees, the ultimate goal is to create homogeneous clusters, and the process to reach this goal was outlined in the previous chapter. For neural networks, things work differently because the objective is explicitly to minimize the error between the prediction \(\tilde{\mathbf{y}}_i\) and a target label \(\mathbf{y}_i\). Again, here \(\mathbf{y}_i\) is a vector full of zeros with only one *one* denoting the class of the instance.

Facing a classification problem, the trick is to use an appropriate activation function at the very end of the network. The dimension of the terminal output of the network should be equal to \( J \) (number of classes to predict), and if, for simplicity, we write \(\mathbf{x}_i\) for the values of this output, the most commonly used activation is the so-called *softmax* function:

```
\(\tilde{\mathbf{y}}_i = s(\mathbf{x})_i = \frac{e^{x_i}}{\sum_{j=1}^J e^{x_j}}.\)
```

The justification of this choice is straightforward: it can take any value as input (over the real line) and it sums to one over any (finite-valued) output. Similarly as for trees, this yields a ‘probability’ vector over the classes. Often, the chosen loss is a generalization of the entropy used for trees. Given the target label \(\mathbf{y}_i = (y_{i,1}, \dots, y_{i,L}) = (0, 0, \dots, 0, 1, 0, \dots, 0)\) and the predicted output \(\tilde{\mathbf{y}}_i = (\tilde{y}_{i,1}, \dots, \tilde{y}_{i,L})\), the cross-entropy is defined as

```
\(\text{CE}(\mathbf{y}_i, \tilde{\mathbf{y}}_i) = - \sum_{j=1}^J \log(\tilde{y}_{i,j}) y_{i,j} . \quad (7.10)\)
```

Basically, it is a proxy of the dissimilarity between its two arguments. One simple interpretation is the following. For the nonzero label value, the loss is \(-\log(\tilde{y}_{i,l})\), while for all others, it is zero. In the log, the loss will be minimal if \(\tilde{y}_{i,l} = 1\), which is exactly what we seek (i.e., \(y_{i,l} = \tilde{y}_{i,l}\)). In applications, this best case scenario will not happen, and the loss will simply increase when \(\tilde{y}_{i,l}\) drifts away downwards from one.

## 7.3 How deep we should go and other practical issues

Beyond the ones presented in the previous sections, the user faces many degrees of freedom when building a neural network. We present a few classical choices that are available when constructing and training neural networks.

### 7.3.1 Architectural choices

Arguably, the first choice pertains to the structure of the network. Beyond the dichotomy feed-forward versus recurrent (see Section 7.5), the immediate question is: how big (or how deep) the networks should be. First of all, let us calculate the number of parameters (i.e., weights plus biases) that are estimated (optimized) in a network.

- For the first layer, this gives \((U_0 + 1)U_1\) parameters, where \(U_0\) is the number of columns in \(\mathbb{X}\) (i.e., number of explanatory variables) and \(U_1\) is the number of units in the layer.

- For layer \(l \in [2, L]\), the number of parameters is \((U_{l-1} + 1)U_l\).

- For the final output, there are simply \(U_L + 1\) parameters.
