
# Nearest Neighbours

The weights for three features are coord1:1.122086, coord2:1.209277, and coord3:1.036502. The second feature gets the highest weight, suggesting the largest importance, while least importance is on the third feature. This conforms with the underlying data structure.

Let us depict the evolution of weights:

```select
select cnt, w1:weight[0], w2:weight[1], w3:weight[2] from kNNLab
```

Figure 21.4 depicts the evolution of three weights corresponding to the three features as a function of the number of iterations taken. The three lines are coord1 (light gray line), coord2 (black line), and coord3 (dark gray line). The figure shows that the difference between three weights is growing in absolute value. The values are not by any means saturated and the system is still evolving. The weights are not forced to be normalised, the value of interest is rather the relative difference between the weights.

The exercise can be further extended for more complex problems. It is also interesting to investigate the evolution of weights. They are random as we are using only a fraction (random one) of the data set in each iteration. It is worth considering renormalisation of the weights in every iteration step, for instance, to fix ||w||=1. The absolute values of weights could then be used to assess the importance of features across different problems.

To readers the presented exercise. Figure 21.5 depicts the evolution of three weights corresponding to the three features as a function of the number of iterations taken for 10,000 steps. The three lines are coord1 (light gray line), coord2 (black line), and coord3 (dark gray line). Compared to Figure 21.4, current figure has weights normalised as ||w||=1, where normalisation was done ex post. The dynamics

![](img/97f7581128bd0bdf85683d4c69d242_459.png)
**FIGURE 21.4** Evolution of weights for three features coord1 (light gray line), coord2 (black line), and coord3 (dark gray), as a function of number of iterations

![](img/97f7581128bd0bdf85683d4c69d242_460.png)
**FIGURE 21.5** Evolution of normalised weights for three features coord1 (light gray line), coord2 (black line), and coord3 (dark gray), as a function of number of iterations, for 10,000 weights get more stable after approximately 1000 runs. The weight for the third feature tends to 0 while the other two features have weights different from zero, both sorted by their importance. The figure suggests an extension towards an algorithm where we iterate for as long as we eliminate features with weights reaching 0.

# Neural Networks

The focus of this chapter is neural networks. The chapter covers a number of related methods and techniques and represents one of the most rapidly growing domains in machine learning. In this chapter, we aim to convince the reader that neural networks can be used well. We will implement a neural network-based classifier and regressor with a few lines of code and successfully apply it in practice.

We do not claim that its own is the language of choice for their applications to complex problems. Deep networks, convoluted networks, or long short-term memory (LSTM) could be programmed, but their implementation would require a significant time. This is beyond the scope of our book, and we keep this for future work. The terminology of neural networks comes from their original purpose: to model the functions of the human brain. The model was microscopic, modelling each neuron explicitly how the signal spreads across the network; further, it gives the neural network a certain flavour.

## INTRODUCTION

Let us start with an introduction to neural networks. Our objective is to acquire an understanding of neural networks. A single hidden layer is called hidden because it is neither the input nor the output layer, but appears inside the neural network. This is a slightly simplified setup until there are a plethora of setups. We encourage interested readers to fulfil their curiosity in specialised publications; see, for instance, Agarwal (2018).

Despite the simplicity of our choice, neural networks with a single hidden layer capture all nonlinear relationships between the dependent variable and features. We are provided with M-dimensional array of features $X_1, ..., X_M$, and our aim is to predict $L$ dependent variables $Y_1, ..., Y_L$. The general dimension of the dependent variable allows us to formulate regression and L-class classification within the framework. For regression we usually set $L=1$; for $L$-class each $l=1, ..., L$ corresponds to one of the classes.

The application of a neural network is a two-stage procedure:

- The first stage: Map between the input features and the hidden layer.
- The second stage: Map between the hidden layer and the dependent variable.

The neural network is frequently depicted using the following scheme:

$$\begin{matrix} X_0 \\ X_1 \\ \vdots \\ X_M \end{matrix} \text{ Stage 1: } \to \begin{matrix} Z_0 \\ Z_1 \\ \vdots \\ Z_N \end{matrix} \text{ Stage 2: } \to \begin{matrix} Y_1 \\ \vdots \\ Y_L \end{matrix} (22.1)$$

We have added $X_0$ and $Z_0$, respectively. These variables are referred to as bias and represent a constant shift in the model. The vector $Z$ corresponds to the hidden layer. This layer is not visible outside the model and corresponds to the latent variables. For more complex neural network topologies, the hidden layers encapsulate memory and perception of general features.

### The first stage

First, the map between the $X_0, X_1, \dots, X_M$, and the hidden layer $Z_1, \dots, Z_N$, is provided. The model is modelled as:

$$Z_n = \eta(\alpha_0^{(n)}X_0 + \alpha_1^{(n)}X_1 + \dots + \alpha_M^{(n)}X_M), \quad (22.2)$$

where $n=1,\dots,N$, and $\alpha_m$ are parameters of the model. The activation function $\eta$ can be thought of as neurons. There are a number of popular choices:

- Sigmoid function: $\eta(x) = \frac{1}{1+\exp(-x)}$
- Hyperbolic tangent function: $\eta(x) = \frac{\exp(x)-\exp(-x)}{\exp(x)+\exp(-x)}$
- ReLU, rectified linear function: $\eta(x)=max(0,x)$.

Thus, in general, every node of the hidden layer, $Z_n$, is a function of all input nodes and the bias node. The hidden layers serve as input for the second stage with the output layer.

### The second stage

Second, the map between the hidden layer, $Z_0, Z_1, \dots, Z_N$, and the dependent variable(s), $Y_1, \dots, Y_L$, is defined. The form of the function $\tau$ depends on the problem at hand and the particular neurons can have the form (the function in the output layer is usually also called an activation function):

- Regression with $L = 1$: Linear activation function:

$$\tau(\beta_0 Z_0 + \beta_1 Z_1 + \dots + \beta_N Z_N) = \beta_0 Z_0 + \beta_1 Z_1 + \dots + \beta_N Z_N. (22.3)$$

- Classification with $L$: Softmax function assigning probability to each class:

$$\tau_l = \frac{\exp(\beta_0^{(l)} Z_0 + \beta_1^{(l)} Z_1 + \dots + \beta_N^{(l)} Z_N)}{\sum_{j=1}^L \exp(\beta_0^{(j)} Z_0 + \beta_1^{(j)} Z_1 + \dots + \beta_N^{(j)} Z_N)}. (22.4)$$
