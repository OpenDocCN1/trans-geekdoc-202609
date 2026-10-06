
Example 6.1 (See [150, Section 3]) This example is discussed in detail in Example 6.7. We assume the mini-dataset:

| Instance 1: | -2 | -1 | 1 |
| Instance 2: | 25 | 6 | -1 |
| Instance 3: | 17 | 4 | -1 |
| Instance 4: | -15 | -6 | 1 |

There are four instances in this dataset, and each instance consists of two features $a$ and a classification number, which is either -1 or 1. As function for predicting the classification number, we choose

$\mathcal{F}(p_1,p_2,p_3) := \{f \in \mathbb{R}^2 \mid f(x_1, x_2) = \tanh(p_1x_1 + p_2x_2 + p_3) \forall (x_1, x_2) \in \mathbb{R}^2$

where $p_1, p_2, p_3 \in \mathbb{R}$ are arbitrarily chosen parameters and $x_1, x_2$ denote the features. Every function of this class depends on the parameters $p_1, p_2, p_3 \in \mathbb{R}$. Within this class, our goal is to find optimal parameters for each instance, the function value at the given feature approximates the classification number. This can be achieved by solving the unconstrained optimization problem

$$\min_{p_1,p_2,p_3 \in \mathbb{R}} (\tanh(-2p_1 - p_2 + p_3) - 1)^2 + (\tanh(25p_1 + 6p_2 + p_3) + 1)^2 + (\tanh(17p_1 + 4p_2 + p_3) + 1)^2 + (\tanh(-15p_1 - 6p_2 + p_3) - 1)^2.$$

For $p_1 = -4.5504, p_2 = -1.7752$ and $p_3 = 3.7752$, the objective value of this optimization problem is $1.4132 \times 10^{-5}$. Consequently, the formula

$y = \tanh(-4.5504x_1 - 1.7752x_2 + 3.7752)$ gives a good approximation of the classification number $y$ for the given features $x_1$ and $x_2$ of each of the four instances. In practice, a dataset naturally consists of a large number of instances, which makes the objective of the associated optimization problem very complex. For example, the well-known dataset collection [84] contains a dataset with over 250,000 instances and one with more than 60,000 features. Thus, real-world problems in AI lead to challenging optimization problems also require complex functions, which can be systematically constructed using deep neural networks.

## 6.2 Artificial Neurons

A *neuron*, of the nervous system, is an excitable cell that receives electrical signals and in turn generates signals that are transmitted to other neurons. Figure 6.1 shows a special neuron called a multipolar neuron, which has many dendrites but only a single axon. It is estimated that the human brain has 86 billion neurons (compare [58]). An artificial neuron is a mathematical formalization of a biological neuron, as shown in Fig. 6.2. For simplicity, an artificial neuron is often simply called a neuron when there is no confusion with biological situation. Each artificial neuron can have several inputs $x_1, \dots, x_k \in \mathbb{R}$ (with $k \in \mathbb{N}$) and one output $\hat{y} \in \mathbb{R}$. Inside this artificial neuron, each input $x_i$ (with $i \in \{1, \dots, k\}$) is multiplied by some weight $w_i \in \mathbb{R}$. The sum of these terms is added with some bias $b \in \mathbb{R}$. Then a so-called activation function $\varrho : \mathbb{R} \to \mathbb{R}$ is applied to this final result, which gives the output of this artificial neuron. In other words, the output $\hat{y}$ can be written as

$$\hat{y} = \varrho\left(\sum_{i=1}^{k} w_ix_i + b\right) = \varrho(w^T x + b)$$

$w := (w_1, \dots, w_k)$ and $x := (x_1, \dots, x_k)$. The activation function $\varrho$ should be chosen in an appropriate way; some common examples of activation functions are discussed in Sect. 6.4. For a given input vector $x$, the output $\hat{y}$ is determined by the choice of the weight vector $w$, the bias $\hat{b}$, and the activation function $\varrho$.

## 6.3 Deep Neural Network

Solving complex AI problems typically requires a sophisticated network of artificial neurons. Figure 6.3 shows a so-called *feedforward neural network* (FNN), which means that the information flows forward, *i.e.*, from the input nodes (without cycles or loops) through the hidden nodes to the output nodes. In a neural network, a collection of elements aligned vertically on a straight line is called a *layer*.

![](img/e4a2491dbba09f71ab293f149cd5b_105_0.png)
Fig. 6.1 Illustration of a multipolar neuron, given by Blausen and taken from Wikimedia [20]

![](img/e4a2491dbba09f71ab293f149cd5b_105_1.png)
Fig. 6.2 Illustration of an artificial neuron with inputs $x_1, x_2, \dots, x_k$ and one output $\hat{y}$

## 6.4 Activation Functions

In this section, we discuss activation functions that are crucial for deep learning.

### 6.4.1 Sigmoid Function

The sigmoid function is probably one of the best known functions. Definition 6.1 The function $\varrho : \mathbb{R} \to (0, 1)$ given by

$$\varrho(x) = \frac{1}{1 + e^{-x}}$$

is called *sigmoid* function.

![](img/e4a2491dbba09f71ab293f149cd5b_108_0.png)
Fig. 6.4 sigmoid function $\rho$ from Definition 6.1 together with its derivative $\rho'$

The range of the function $\rho$ equals the open interval $(0, 1)$. If one prefers a range $(-1, 1)$, then one can consider the modified function given

$$2\rho(x) - 1 = \frac{1-e^{-x}}{1+e^{-x}}$$

### 6.4.2 tanh Function

The hyperbolic tangent is also used as an activation function. It is obvious it can also be written in the form

$$tanh(x) = \frac{e^x-e^{-x}}{e^x+e^{-x}} = \frac{1-e^{-2x}}{1+e^{-2x}} = 2\rho(2x)-1$$

