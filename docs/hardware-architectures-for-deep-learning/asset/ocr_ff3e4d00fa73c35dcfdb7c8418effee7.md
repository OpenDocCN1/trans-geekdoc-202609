# Hardware architectures for deep learning

![](bbox=[0.175, 0.085, 0.825, 0.303])

# 1.3 Widely used NN models

In this section, well-known and widely used NN models are introduced and their potentials and limitations are discussed.

# 1.3.1 Simple structure networks

A simple structure network is a network without any hidden layers. The activation functions of the output neurons are bipolar or binary step functions. Actually, a simple structure network can include a set of modified M&P neurons having equal number of inputs. Figure 1.15 shows a simple structure network with one M&P neuron, where the input-output function of the network is defined as

```
$y_{in}=\sum_{i=1}^{n}w_{ix}i+b\quad y=f(y_{in})=\left{\{egin{array}{cc}1&y_{in}\geq0\\0(or-1)&y_{in}<0\end{array}\right\}$
```

Since the simple structure network does not provide enough complexity, it cannot be used for feature extracting in a classification problem. However, considering the sign of $y_{in}$ as the equation of a hyperplane, in (2.2), each M&P neuron can partition the input (n-dimensional) space into two parts. Therefore, simple structure networks can be used for potentiallyriating pairs. Figure 1.16 shows a 2D illustrative example where a simple structure network by specifying a line in the 2D has separated circles and triangle patterns.

Generally, simple structure networks are capable to perform the classification problems, when all patterns with equal labels are linearly separable. In this way, if the number of classes is more than 1, an individual M&P neuron is required for each output class. There are several learning methods for class of these NNs. Table 1.2 summarizes these methods and outlines their convergence and generalization properties.

“Hebb Net” uses a modified version of the earliest and simplest learning rule, which was proposed by Donald Hebb in natural NNs [3]. Although this learning rule is important in studying natural NNs, it practically works in a few examples.