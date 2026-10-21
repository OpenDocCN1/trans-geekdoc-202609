![](bbox=[0.07, 0.15, 0.95, 0.78])

Figure 101.5: Illustration of a neural network with four layers.

# Table 101.1: List of activation functions.

| Activation function | Definition |
|---|---|
| The identity function | $f(x)=x$ |
| The logistic function | $f(x)=1/(1+\exp(-x))$ |
| The hyperbolic tan function | $f(x)=\tanh(x)$ |
| The rectified linear units (ReLU) function | $f(x)=\max\{x,0\}$ |

features. We explicitly describe a deep learning architecture as follows. For a hidden layer, various activation functions, such as logistic, sigmoid, and radial basis function (RBF), can be applied. We summarize some activation functions and their definitions in Table 101.1.

Let $f^{(0)}, f^{(1)}, \dots, f^{(L)}$ be given univariate activation functions for these layers. For notational simplicity, let $f$ be a given activation. Suppose