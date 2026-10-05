framework. For regression we usually set $L=1$ for $L$-class classification each $l$, with $l=1,\dots,L$, corresponds to one of the classes.

The application of a neural network is a two-stage procedure:

+   - The first stage: Map between the input features and the hidden layer.
- The second stage: Map between the hidden layer and the dependent variable.

The neural network is frequently depicted using the following scheme:

```
$$\begin{matrix} X_0 \ X_1 \ \vdots \ X_M \end{matrix} \text{ Stage 1: } \to \begin{matrix} Z_0 \ Z_1 \ \vdots \ Z_N \end{matrix} \text{ Stage 2: } \to \begin{matrix} Y_1 \ \vdots \ Y_L \end{matrix} \quad (22.1)$
```

We have added $X_0$ and $Z_0$, respectively. These variables are referred to as the bias and represent a constant shift in the model. The vector $Z$ corresponds to the hidden layer. This layer is not visible outside of the model and corresponds to the latent variables of the model. For more complex neural network topologies, the hidden layers encapsulate memory and perception of general features.

# The first stage

First, the map between the $X_0, X_1, \dots, X_M$, and the hidden layer, $Z_1, \dots, Z_N$, is provided. The model is modelled as:

```
$Z_n = \eta(\alpha_0^{(n)}X_0 + \alpha_1^{(n)}X_1 + \dots + \alpha_M^{(n)}X_M), \quad (22.2)$
```

where $n=1,\dots,N$, and $\alpha_m$ are parameters of the model. The activation function $\eta$ can be thought of as neurons. There are a number of popular choices:

+   - Sigmoid function: $\eta(x) = \frac{1}{1+\exp(-x)}$
- Hyperbolic tangent function: $\eta(x) = \frac{\exp(x)-\exp(-x)}{\exp(x)+\exp(-x)}$
- RELU, rectified linear function: $\eta(x)=max(0,x)$.

Thus, in general, every node of the hidden layer, $Z_n$, is a function of all input nodes and the bias node. The hidden layers serve as input for the second stage with the output layer.

# The second stage

Second, the map between the hidden layer, $Z_0, Z_1, \dots, Z_N$, and the dependent variable(s), $Y_1, \dots, Y_L$, is defined. The form of the function $\tau depends on the problem at