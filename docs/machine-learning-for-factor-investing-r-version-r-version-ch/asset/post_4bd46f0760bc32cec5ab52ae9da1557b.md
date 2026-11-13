
## 6.6 Coding exercises

- 1. Using the formula in the chunks above, build two simple trees on the training sample with only one parameter: cp. For the first tree, take cp=0.001 and for the second take cp=0.01. Evaluate the performance of both models on the testing sample. Comment.

- 2. With the smaller set of predictors, build random forests on the training sample. Restrict the learning on 30,000 instances and over 5 predictors. Construct the forests on 10, 20, 40, 80 and 160 trees and evaluate their performance on the training sample. Is complexity worthwhile in this case and why?

- 3. Plot a tree based on data from calendar year 2008 and then from 2009. Compare.

## Neural networks

Neural networks (NNs) are an immensely rich and complicated topic. In this chapter, we introduce the simple ideas and concepts behind the most simple architectures of NNs. For more exhaustive treatments on NN idiosyncrasies, we refer to the monographs by Haykin (2009), Du and Swamy (2013) and Goodfellow et al. (2016). The latter is available freely online: www.deeplearningbook.org. For a practical introduction, we recommend the great book of Chollet (2017).

For starters, we briefly comment on the qualification “neural network”. Most experts agree that the term is not very well chosen, as NNs have little to do with how the human brain works (of which we know not that much). This explains why they are often referred to as “artificial neural networks” - we do not use the adjective for notational simplicity. Because we consider it more appropriate, we recall the definition of NNs given by François Chollet: “chains of differentiable, parameterised geometric functions, trained with gradient descent (with gradients obtained via the chain rule)”.

Early references of neural networks in finance are Bansal and Viswanathan (1993) and Eakins et al. (1998). Both have very different goals. In the first one, the authors aim to estimate a **nonlinear form** for the pricing kernel. In the second one, the purpose is to identify and quantify relationships between institutional investments in stocks and the attributes of the firms (an early contribution towards factor investing). An early review (Burrell and Boralín (1997)) lists financial applications of NNs during the 1990s. More recently, Sezer et al. (2019), Jiang (2020) and Lim and Zohren (2020) survey the attempts to forecast financial time series with deep-learning models, mainly by computer science scholars.

The pure predictive ability of NNs in financial markets is a popular subject and we further cite for example Kimoto et al. (1990), Enke and Thawornwong (2005), Zhang and Wu (2009), Guresen et al. (2011), Krauss et al. (2017), Fischer and Krauss (2018), Aldridge and Avellaneda (2019) and Soleymani and Paquet (2020).¹ The last reference even combines several types of NNs embedded inside an overarching reinforcement learning structure. This list is very far from exhaustive. In the field of financial economics, recent research on neural networks includes:

- Feng et al. (2019) use neural networks to find factors that are the best at explaining the cross-section of stock returns.
- Gu et al. (2020b) map firm attributes and macro-economic variables into future returns. This creates a strong predictive tool that is able to forecast future returns very accurately.
- Chen et al. (2020) estimate the pricing kernel with a complex neural network structure

¹Neural networks have also been recently applied to derivatives pricing and hedging, see for instance the work of Buehler et al. (2019) and Andersson and Oosterlee (2020) and the survey by Ruf and Wang (2019). Limit order book modelling is also an expanding field for neural network applications (Sirignano and Cont (2019), Wallbridge (2020)).

### 7.1 The original perceptron

The origins of NNs go back at least to Rosenblatt (1958). Its aim is binary classification. For simplicity, let us assume that the output is {0 = do not invest} versus {1 = invest} (e.g., derived from return, negative versus positive). Given the current nomenclature, a perceptron can be defined as an activated linear mapping. The model is the following:

```
f(x) = \begin{cases} 1 & \text{if } \mathbf{x}'\mathbf{w} + b > 0 \\ 0 & \text{otherwise} \end{cases}
```

The vector of weights **w** scales the variables and the bias \( b \) shifts the decision barrier. Given values for \( b \) and \( w_i \), the error is \( \epsilon_i = y_i - 1 \quad \sum_{j=1} x_{i,j}w_j + w_0 > 0) \). As is customary, we set \( b = w_0 \) and add an initial constant column to \( x \): \( x_{i,0} = 1 \), so that \( \epsilon_i = y_i - 1 \quad \sum_{j=0} x_{i,j}w_j > 0) \). In contrast to regressions, perceptrons do not have closed-form solutions. The optimal weights can only be approximated. Just like for regression, one way to derive good weights is to minimize the sum of squared errors. To this purpose, the simplest way to proceed is to

- 1. compute the current model value at point \(\mathbf{x}_i\): \(\tilde{y}_i = 1 \quad \sum_{j=0} w_j x_{i,j} > 0)\),
- 2. adjust the weight vector: \( w_j \leftarrow w_j + \eta(y_i - \tilde{y}_i)x_{i,j}\) ,

which amounts to shifting the weights in the *right* direction. Just like for tree methods, the scaling factor \( \eta \) is the learning rate. A large \( \eta \) will imply large shifts: learning will be rapid but convergence may be slow or may even not occur. A small \( \eta \) is usually preferable, as it helps reduce the risk of overfitting.

In Figure 7.1, we illustrate this mechanism. The initial model (dashed grey line) was trained on 7 points (3 red and 4 blue). A new black point comes in.

![](img/8861a37f775d09b4ba7a5151f604d9f5_113_0.png)

FIGURE 7.1: Scheme of a perceptron.

- if the point is red, there is no need for adjustment: it is labelled correctly as it lies on the right side of the border.
- if the point is blue, then the model needs to be updated appropriately. Given the rule mentioned above, this means adjusting the slope of the line downwards. Depending on η, the shift will be sufficient to change the classification of the new point - or not.

At the time of its inception, the perceptron was an immense breakthrough which received an intense media coverage (see Olazaran (1996) and Anderson and Rosenfeld (2000)). Its rather simple structure was progressively generalized to networks (combinations) of perceptrons. Each one of them is a simple unit, and units are gathered into layers. The next section describes the organization of simple multilayer perceptrons (MLPs).

### 7.2 Multilayer perceptron

### 7.2.1 Introduction and notations

A perceptron can be viewed as a linear model to which is applied a particular function: the Heaviside (step) function. Other choices of functions are naturally possible. In the NN jargon, they are called activation functions. Their purpose is to introduce nonlinearity in otherwise very linear models.

Just like for random forests with trees, the idea behind neural networks is to combine perceptron-like building blocks. A popular representation of neural networks is shown in Figure 7.2. This scheme is overly simplistic. It hides what is really going on: there is a perceptron in each green circle and each output is activated by some function before it is sent to the final output aggregation. This is why such a model is called a Multilayer Perceptron (MLP).

![](img/8861a37f775d09b4ba7a5151f604d9f5_114_0.png)

FIGURE 7.2: Simplified scheme of a multi-layer perceptron.

A more faithful account of what is going on is laid out in Figure 7.3.

![](img/8861a37f775d09b4ba7a5151f604d9f5_114_1.png)

FIGURE 7.3: Detailed scheme of a perceptron with 2 intermediate layers.

Before we proceed with comments, we introduce some notation that will be used throughout the chapter.

- The data is separated into a matrix \(\mathbf{X} = x_{i,j}\) of features and a vector of output values \(\mathbf{y} = y_i\). \(\mathbf{x}\) or \(\mathbf{x}_i\) denotes one line of \(\mathbf{X}\).
- A neural network will have \(L \ge 1\) layers and for each layer \(l\), the number of units is \(U_l \ge 1\).
- The weights for unit \(k\) located in layer \(l\) are denoted with \(\mathbf{w}_k^{(l)} = w_{k,j}^{(l)}\) and the corresponding biases \(b_k^{(l)}\). The length of \(\mathbf{w}_k^{(l)}\) is equal to \(U_{l-1}\). \(k\) refers to the location of the unit in layer \(l\) while \(j\) to the unit in layer \(l - 1\).
