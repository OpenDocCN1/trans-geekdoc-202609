
scaling of the covariates. For example, in the ridge case, suppose that X is such that X′X is diagonal. How much estimates get shrunk to zero when we add the ridge γI_K to X′X depends on the magnitude of the diagonal elements of X′X. For covariates with small variance and hence a small diagonal entry in X′X, the effect of adding γ to the diagonal element is much bigger than for covariates with large variance. For this reason, it is common to standardize inputs to unit standard deviation before computing the ridge estimates. But this may not always be the right approach. Sometimes prior knowledge about a learning problem can tell us that we actually should shrink the coefficients of some covariates more than those of others.

## 2.2.2 Trees and Random Forests

Regression trees approximate the nonlinear function f(x_i) with a multidimensional step function (Breiman, Friedman, Olshen, and Stone 1984). The feature space is divided into regions, or leaves, that contain a neighborhood around each point x_i at which we want to approximate f. Within each leaf h = 1, ..., H, the function f(x_i) is approximated as an equal-weighted average, \bar{y}_h, of the observations y_i in this leaf.

Finding a suitable general partition of the feature space can be difficult. For this reason, tree-based algorithms often use recursive binary partitions. The partitioning of the feature can then be represented as a decision tree; hence the name of the method. Panel (a) in Figure 2.1 presents an example.

How can we find a partition that approximates f well? Finding the globally optimal partition that minimizes the residual sum of squared errors can be computationally infeasible. Even if we restrict ourselves to recursive binary partitions, there may still be an enormous number of possible trees that we would have to evaluate to determine global optimality. Much of the success of tree-based methods has come from the development of algorithms that do a good job in finding partitions that work well in applications, even though they typically do not find the globally optimal partition.

One common approach is a greedy algorithm (see, e.g., Hastie, Tibshirani, and Friedman 2009). Instead of evaluating global optimality, the algorithm walks through the tree and determines the best split based on a local assessment of fit at each step. More precisely, we start with all the data and we check for each feature what the residual sum of squared errors would be if we partitioned the sample into two regions just based on this feature and with a threshold that maximizes fit. We then choose to split based on the feature where we get the best fit. Within each of the resulting two regions, we then repeat this process. We keep doing this

![](img/d6b658bf753df69fb65789651dc4a65e_28_0.png)

(a) Tree representation

![](img/d6b658bf753df69fb65789651dc4a65e_28_1.png)

(b) Fitted step function

Figure 2.1. Regression tree example

until we have grown the tree to the point at which the number of observations within each region reaches a minimum number that we have set as a termination criterion at the start of the process.

Concretely, for the example tree in Figure 2.1, suppose in the first step that splitting on x1 provides the biggest explanatory power compared with single splits based on the other features. We therefore split into two
tree and then draw another bootstrap sample from the original data to repeat the process. The fitted value at a point x_i is the average of the fitted values at x_i that we get from each individual tree. The constant m is a tuning parameter. Picking a value for it is similar to choosing a penalty parameter in penalized approaches.

Intuitively, each of the bootstrap samples has, to some extent, different noise. So if the fully grown trees are overfitting noise, their predictions will be affected by noise in different ways in different bootstrap samples. Moreover, the random selection of a subset of features in each bootstrap sample magnifies these differences. Taking the mean prediction across trees from different bootstrap samples averages out much of these noise-induced effects. Athey, Tibshirani, and Wager (2019) offer an interpretation analogous to kernel regression. Kernel regressions make predictions at point x_i by forming a weighted average of observations in a neighborhood around x_i, giving more weight to closer observations. Athey et al. show that averaging across trees in random forests has a somewhat similar effect in that closer points are included more often than distant points in the construction of the prediction at x_i.

## 2.2.3 Neural Networks

Neural networks are essentially methods to estimate highly nonlinear regression functions. For example, suppose we have J covariates x_i, which serve as inputs to the network and one dependent variable y_i, which is the output. Inputs and output are connected through a hidden layer of H nodes that we can think of as underlying latent variables. With y_i = f(x_i) + ε_i, the network can be expressed as

f(x_i) = a_2 + w_2' g(a_1 + W_1 x_i), (2.11)

where a_1 + W_1 x_i represents the vector of latent variables. The activation function g is nonlinear and operates element-wise on each latent variable. For example, a popular choice is the Rectified Linear Unit (ReLU) where g(z) = max(0, z), which is a piecewise linear function that outputs an element of z directly if the element is positive, and outputs zero otherwise. The output of the activation function is then weighted by w_2 and shifted by a_2 to produce the final output f(x_i) in the output layer.

The nonlinearity of g is crucial for the network to approximate nonlinear functions. If g were linear, e.g., g(z) = A z for some matrix A, the network would collapse into a linear regression model y_i = a + g' x_i + ε_i with g' = w_2' A W_1 and a = a_2 + w_2' A a_1.

The number of hidden nodes controls the flexibility of the function approximation. With a large number of hidden nodes, one can
approximate highly nonlinear functions arbitrarily well (Cybenko 1989; Hornik, Stinchcombe, and White 1989). Networks used for image recognition or natural language processing contain tens or hundreds of thousands of nodes (LeCun, Bengio, and Hinton 2015).

One can add additional layers. For example, with two hidden layers we have

$f(\mathbf{x}_i)=a_3+\mathbf{w}_3 g\big(a_2+\mathbf{W}_2 g(a_1+\mathbf{W}_1\mathbf{x}_i)\big).$ (2.12)

Deep neural networks add several such layers, often 10 to 20. The result is a network that has a sequence of linear mappings with interwoven nonlinear transformations. The number of parameters can be very large. For example, with a single hidden layer with $H$ nodes, one output, and $J$ inputs, the total number of parameters in $\mathbf{W}_1$, $a_1$, and $a_2$ is $H \times J + H + 1$. With $J=1000$ inputs and $H=10000$ hidden nodes, this would amount to more than ten million parameters. For a fully connected network, each added layer with the same number of hidden nodes adds another $H \times H + H$ parameters.

In principle, networks with a single hidden layer can approximate any nonlinear function. In practice, though, with typical data sets, adding layers to a network often seems to lead to better performance. Whether deep networks with many layers are generally better is still an open question (see, e.g., Ba and Caruana (2013)). Lin, Tegmark, and Rolnick (2017) argue that certain properties of the data and functions to be approximated matter. For example, deep networks are well suited for approximating functions that have a hierarchical structure.

Interaction effects—i.e., situations where the joint effect of multiple inputs on the output is not additive—are a type of nonlinearity that may be particularly relevant for the asset pricing applications that we start discussing in the next chapter. It is therefore useful to take a closer look at how such interactions can be captured by a neural network.

Consider a network with a single hidden layer as in (2.11) with two nodes. Suppose further that $a_2=0$, $\mathbf{w}_2=(1,1)'$, $\mathbf{a}_1=(-3/2,-3/2)'$, the first row of $\mathbf{W}_1$ is $(1,1)$ and the second row is $(-1,-1)$, and $g(z)=\max(0,z)$, i.e.,

$f(\mathbf{x}_i)=\max(0,-3/2+x_{i1}+x_{i2})+\max(0,-3/2-x_{i1}-x_{i2}).$ (2.13)

In this case, the first term only “activates” if the sum of the two features $x_{i,1}$ and $x_{i,2}$ is large enough; otherwise it is zero. The second term only “activates” if the sum of the two features $x_{i,1}$ and $x_{i,2}$ is small enough. The result is the function shown in Figure 2.2.

By adding additional hidden nodes, we could add additional piecewise linear parts to this function, for example for larger values of $x_{i,1}+x_{i,2}$ and more strongly negative values of $-x_{i,1}-x_{i,2}$. In this way, the neural
