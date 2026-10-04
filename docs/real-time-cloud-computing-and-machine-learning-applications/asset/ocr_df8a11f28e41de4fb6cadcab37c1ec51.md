170 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonadon

Weights are assigned to the connections between layers to specify their importance. The training of MLP consists of optimizing the weights of the connections through a process called backpropagation. Initially, random weights are assigned to the connections and test signals are propagated through the MLP, producing an output. The difference between the produced output and the expected output, defined as the error, is then fed back to the input layer which the MLP uses to automatically readjust the weights of the connections at multiple iterations until the error is minimized. The computations at the hidden and output layers are as follows for an MLP with 2 hidden layers [38]:

```
$h^{(1)} = \phi^{(1)}(W^{(1)}x + b^{(1)})$
```

```
$h^{(2)} = \phi^{(2)}(W^{(2)}h^{(1)} + b^{(2)})$
```

```
$y = \phi^{(3)}(W^{(3)}h^{(1)} + b^{(3)})$
```

Where,

+   - $x$ - Activation vector for neurons in the input layer
- $y$ - Activation vector for neurons in the output layer
- $h^{(1)}, h^{(2)}$ - Activation vectors for neurons in first and second hidden layer respectively
- $b^{(1)}, b^{(2)}, b^{(3)}$ - Bias vectors for first hidden layer, second hidden layer and output layer respectively
- $\phi^{(1)}, \phi^{(2)}, \phi^{(3)}$ - Non-linear activation functions

# Short-hand Example 8

In this example, MLP is used to operate as an AND gate. The AND gate's truth table is given in Table 3.16:

# Table 3.16. Multi-layered perceptron- AND gate's truth table

| Input, $X_1$ | Input 2, $X_2$ | Output, $Y$ |
|---|---|--|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |