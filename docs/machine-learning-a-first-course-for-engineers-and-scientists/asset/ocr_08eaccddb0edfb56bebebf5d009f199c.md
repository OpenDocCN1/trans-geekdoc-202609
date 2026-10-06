# 6.1 The neural network model

Input variables Hidden units Output

![](bbox=[0.335, 0.126, 0.664, 0.269])

**Figure 6.3:** A two-layer neural network, or equivalently, a neural network with one intermediate layer of hidden units.

hidden units) are thus

```
$q_1 = h(W_{11}^{(1)}x_1 + W_{12}^{(1)}x_2 + \dots + W_{p1}^{(1)}x_p + b_1^{(1)})$,
q_2 = h(W_{21}^{(1)}x_1 + W_{22}^{(1)}x_2 + \dots + W_{p2}^{(1)}x_p + b_2^{(1)})$,
:
qq_U = h(W_{U1}^{(1)}x_1 + W_{U2}^{(1)}x_2 + \dots + W_{pU}^{(1)}x_p + b_U^{(1)})$.\quad (6.6a)
```

```
$\tilde{y} = W_1^{(2)}q_1 + W_2^{(2)}q_2 + \dots + W_U^{(2)}q_U + b^{(2)}.$\quad (6.6b)
```

Extending the graphical illustration from Figure 6.1, this model can be depicted as a graph with two layers of links (illustrated using arrows), see Figure 6.3. As before, each link has a parameter associated with it. Note that we include an offset not only in the input layer, but also in the hidden layer.

# Vectorization over units

The two-layer network model in (6.6) can be written more compactly using matrix notation, where the parameters in each layer are stored in a weight matrix **W** and an offset vector **b**

```
$\mathbf{q}^{(1)} = \begin{bmatrix} W_{11}^{(1)} & W_{p1}^{(1)} \ \vdots & \vdots \ W_{U1}^{(1)} & W_{pU}^{(1)} \end{bmatrix}^T \mathbf{x} + \begin{bmatrix} b_1^{(1)} \ \vdots \ b_U^{(1)} \end{bmatrix} = \mathbf{W}^{(1)}\mathbf{x} + \mathbf{b}^{(1)}, \quad \mathbf{b}^{(2)} = [\mathbf{b}^{(2)}].\quad (6.7)
```

The full model can then be written as where we have stacked the components in **x** and **q** = $[x_1, \dots, x_p]^T$ and **q** = $[q_1, \dots, q_U]^T$. Note that the activation function $h$ in (6.8) acts element-wise on the input vector, and results in an output vector of the same dimension. The two weight matrices and the two offset vectors are the parameters of the model, which can be written as

```
$\boldsymbol{	heta} = [\text{vec}(\mathbf{W}^{(1)})^T \mathbf{b}^{(1)})^T \text{vec}(\mathbf{W}^{(2)})^T \mathbf{b}^{(2)})^T].\quad (6.9)
```

> The word "bias" is used for the offset in neural network literature, but this is really just a model parameter and not a bias in the statistical. To avoid confusion we refer it as an offset.

This material may be published by Cambridge University Press. This pre-publication version is free to view and for personal use only. At no re-distribution, re-sale or in other uses.