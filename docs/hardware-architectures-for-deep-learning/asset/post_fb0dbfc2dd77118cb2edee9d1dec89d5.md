
# An introduction to artificial neural networks 13

![](img/e6e752b99eb1621488c89445a57e2a86_38_0.png)

Figure 1.12 A simple diagram of a NN applied in a regression problem

![](img/e6e752b99eb1621488c89445a57e2a86_38_1.png)

Figure 1.13 An illustrative example that shows how NN acts in a regression process

an effective feature space is obtained. It is expected that by designing an appropriate mapping part, a regression function with sufficient degree of smoothness and equivalency with the target samples is obtained.

# 1.2.3 Relation between classification and regression

By imposing some constraints, a regression problem can be converted to a classification problem. Actually, by quantizing the output of a regression problem and considering each quantized level as an individual class (while there is nearness among different classes), a regression problem is represented as a classification problem. Assume that the output of the regression function is scalar, and consider that y_min and y_sup denote the minimum and supremum of the output, respectively. The output can be quantized to $n_C$ levels with equal distance $\rho = (y_{max} - y_{min})/n_C$. Consequently, each output $y^a$ can be indicated by label $I^a \in \{1, 2, ..., n_C\}$, which is computed

```
I^a = label(y^a) = y_min + (I^a - 1)ρ \leq y < y_min + I^a
```

Figure 1.14 shows a simple example where the real output signal (dot line) has been quantized into $n_c = 5$ levels (solid line). From Figure 1.14, it is understood that the classification problem converges to a regression problem if $n_C \to \infty$.

# Hardware architectures for deep learning

![](img/e6e752b99eb1621488c89445a57e2a86_39_0.png)

# 1.3 Widely used NN models

In this section, well-known and widely used NN models are introduced and their potentials and limitations are discussed.

# 1.3.1 Simple structure networks

A simple structure network is a network without any hidden layers. The activation functions of the output neurons are bipolar or binary step functions. Actually, a simple structure network can include a set of modified M&P neurons having equal number of inputs. Figure 1.15 shows a simple structure network with one M&P neuron, where the input-output function of the network is defined as

```
$y_{in}=\sum_{i=1}^{n}w_{ix}i+b\quad y=f(y_{in})=\left\{\begin{array}{cc}1&y_{in}\geq0\\0(\text{or-1)}&y_{in}<0\end{array}\right\}$
```

Since the simple structure network does not provide enough complexity, it cannot be used for feature extracting in a classification problem. However, considering the sign of $y_{in}$ as the equation of a hyperplane, in (2.2), each M&P neuron can partition the input (n-dimensional) space into two parts. Therefore, simple structure networks can be used for potentially separating pairs. Figure 1.16 shows a 2D illustrative example where a simple structure network by specifying a line in the 2D has separated circles and triangle patterns.

Generally, simple structure networks are capable to perform the classification problems, when all patterns with equal labels are linearly separable. In this way, if the number of classes is more than 1, an individual M&P neuron is required for each output class. There are several learning methods for class of these NNs. Table 1.2 summarizes these methods and outlines their convergence and generalization properties.

“Hebb Net” uses a modified version of the earliest and simplest learning rule, which was proposed by Donald Hebb in natural NNs [3]. Although this learning rule is important in studying natural NNs, it practically works in a few examples.

# An introduction to artificial neural networks 15

![](img/e6e752b99eb1621488c89445a57e2a86_40_0.png)

Figure 1.15 A simple structure network with one M&P neuron

![](img/e6e752b99eb1621488c89445a57e2a86_40_1.png)

Figure 1.16 A simple structure network that (a) by making a line separates circles and (b) triangle patterns

| Network | Learning method | Convergence | Generalization |
| :--- | :--- | :--- | :--- |
| Hebb Net [3] | Hebb rule | No | No |
| Perceptron [4, 5] | Perceptron rule | Yes | No |
| Adaline [6] | Delta rule (least square) | Conditional* | Conditional* |

Table 1.2 Some learning methods for simple structure networks

* If pattern distribution of two classes is similar in shape and density

The Perceptron rule is one of the common methods in learning simple structure works and is backed by a convergence theorem that shows a separable hyperplane between patterns of a certain class and other classes will be found in a limited number updating rule iterations [4, 5], provided that they are linearly separable. However, its drawback is that it stops by finding any separable hyperplane, so it cannot maximize the margins of the separating hyperplane with training patterns. Therefore, its generalization for new patterns is not guaranteed. Adaline (adaptive linear neuron) is another suggested method to tune parameters of a simple structure network [6]. This method minimizes the square error between the target labels of each pattern and the arguments of neurons. Adaline finds a separating hyperplane between the patterns of two classes, when their pattern distributions are similar in shape and density.

# 16 Hardware architectures for deep learning

# 1.3.2 Multilayer and deep NNs

Simple structure networks cannot offer any solution for the challenges and constraints of real-world classification or regression problems. Some major challenges are:

- Patterns of each class are not necessarily linearly separable from patterns of other classes. In this case, the patterns are localized in some convex- or non-convex-shaped regions.
- The dimension of many real-world input patterns is high and there are nonlinear correlations among them.
- In real-world input patterns, there are plenty of disturbances with different scales
- The input patterns of the same class have distortions in size, shape, position, and perspective.
- In some cases when there are certain sequences between input patterns, the applied input itself may not be sufficient.

The above-mentioned challenges render the input patterns insufficient for the partitioning and mapping. This led to the emergence of multilayer NNs and deep NNs.

# 1.3.2.1 Multilayer perceptron

To handle the case when patterns are not linearly separable, it is required to add one or two hidden layers. Actually, adding one hidden layer enables the network to generate label for patterns, which are localized in convex-shaped region. Figure 1.17 shows ANNs with one hidden layer and two hidden layers

![](img/e6e752b99eb162148c89445a57e2a86_41_0.png)

Figure 1.17 ANNs with (a) one hidden layer and (b) two hidden layers

# An introduction to artificial neural networks

To learn such networks, the former learning rules (developed for simple structure networks) cannot be applied. For this purpose, it has been shown that gradient-based methods (e.g., error back propagation [7]) or evolutionary-based methods (such as genetic algorithms [8]) can train the network. In gradient-based methods, it is essential to use derivable activation functions as bipolar or sigmoid.

# 1.3.2 Autoencoders and stacked RBMs

To handle the case when there are correlations among different dimensions of the input patterns, it is required that the network input to some space with a sufficiently lower dimension. In certain cases, if the dimension reduction is not applied, the partitioning and mapping of the input patterns may suffer from overfitting and the network misses its generalization for new patterns. Autoencoder networks [9] and restricted Boltzmann machine (RBM) [10] are two networks with the data-encoding capability. In these networks, in order to remove correlations, a variant of nonlinear principal component analysis (PCA, [11]) is performed, where the null spaces are removed to get a maximum variance space. Figure 1.18 shows a diagram of a typical autoencoder.

In the autoencoder model, the network includes two sequenced parts: encoding and decoding. The encoding part performs the dimension reduction. The decoding part is added to reconstruct the former patterns and ensure that no information from input patterns is lost due to encoding.

Another alternative network for dimension reduction is RBM. An RBM is a simple two-layered network (including visible and hidden layers) by which an encoding algorithm is performed. The model RBM is trained in a bidirectional state. Actually, the given input pattern (as a visible layer) should make a hidden layer with a lower dimension than the initial input pattern. By stacking some RBMs, the dimension of the input patterns is reduced accordingly [12]. Figure 1.19 shows a sample RBMs encoding flow.

To train autoencoders in an unsupervised manner, the encoding and decoding parts are trained first. Then, the encoding part is added to a partitioning or mapping

![](img/e6e752b99eb1621488c89445a57e2a86_42_0.png)

Figure 1.18 Diagram of an autoencoder network with encoding and decoding parts
