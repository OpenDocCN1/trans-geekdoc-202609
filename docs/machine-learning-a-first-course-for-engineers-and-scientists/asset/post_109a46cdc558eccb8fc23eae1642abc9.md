
## Supervised learning: a first approach

## Fully grown tree

## Tree with max depth 4

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_33_0.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_33_1.png)

(a) Decision boundaries for the music classification problem for a fully grown classification tree with Gini index. This model overfits data.

(b) The same problem and data as in 2.1a for a tree restricted to 4 depth has been learned, using Gini index. This model will make better predictions for new data.

## Fully grown tree

## Tree with max depth 3

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_33_2.png)

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_33_3.png)

(e) The prediction for a fully grown regression tree. As for the classification problem above, this model overfits the training data.

(d) The same prediction and data as in 2.1c for a tree restricted to 3 depth has been learned.

**Figure 2.11**: Decision trees applied to the music classification Example 2.1 (a and b) and the car stopping distance Example 2.2 (c and d).

hyperparameter $k$ in k-NN. We use the music classification and car stopping distance problems from Example 2.1 and 2.2 to study how the decision boundaries changing on the depth of the trees. In Figure 2.11 the decision boundaries are illustrated for two different trees. In Figure 2.11a we have not restricted the depth of the tree, and it grows until each region contains data points with the same output value, a fully grown tree. In Figure 2.11b and 2.11d the maximum depth is restricted to 4 and 3, respectively.

Similar to choosing $k = 1$ in k-NN, a fully grown tree data points will be correctly predicted each region only data points with the same output. As a result, the music classification problem we get thin and small regions adapted to single training data points and for the car stopping distance we get very irregular line passing through the observations. Even though these trees get excellent performance on the training data, they are not likely to be the best for new unseen data. As we discussed in the context of k-NN, we refer to this as overfitting.

In decision trees we can mitigate overfitting by using smaller trees. Consequently we get larger and larger regions with an increased averaging, resulting in decision boundaries that are less adapted to the noise in the training data. This is illustrated in Figure 2.11b and 2.11d for the two examples. As as in k-NN, the optimal size of the tree depends on many properties of the problem and it is a trade-off between flexibility and rigidity. Similar trade-offs have be made for almost all methods presented in this book and will user be discussed systematically in Chapter 4.

How can the user control the growth of the tree? Here we have different strategies. The most straightforward strategy is to adjust the stopping criterion, that is, the condition should be fulfilled for not proceeding with further splits in a node. As mentioned above, this criterion could be that we do not attempt splits if there are less than a certain number of training points in the corresponding region, or as in Figure 2.11, stop splitting when we reach a certain depth. Another strategy of controlling the depth is to use pruning. In pruning we prune a fully grown tree and then in a second post-processing step prune it back to a smaller one. We will, however, not discuss pruning further.

## 2.4 Further reading

The reason why we start this book by k-NN is that it perhaps the most intuitive and straightforward way to solve a classification problem. The ideas is, at least, yours and was described already by Hassan Ibn al-Haytham (latinized as Alhazen) around year 1030 in Kitāb al-Manāzir (book of optics) (Pelillo 2014), as an explanation of how the human brain perceives objects. With many good ideas, the nearest neighbor idea has been re-invented many times, and a more modern description of k-NN is found in Cover and Hart (1967).

Also the basic idea of decision trees is relatively simple, but there are many possible ways to improve and extend them, as well as different options in how to implement them in detail. A somewhat longer introduction to decision trees is found in Hastie et al. (2009), and a historically oriented overview is found in Loh (2014). Of particular significance is perhaps CART (Classification and Regression Trees, Breiman et al. 1984) as ID3 and C4.5 (Quinlan 1986, Quinlan 1993).

## 3 Basic parametric models and a statistical perspective on learning

In the previous chapter we introduced the supervised machine learning problem, as well as two methods for solving it. In this chapter we will consider a generic approach to learning referred to as parametric modeling. In particular, we will introduce linear regression and logistic regression which are two such parametric models. The key point of a parametric model is that it contains some parameters $\theta$, which are learned from training data. However, once the parameters are learned, the training data may be discarded, since the prediction only depends on $\theta$.

### 3.1 Linear regression

Regression is one of the two fundamental tasks of supervised learning. We will now introduce the linear regression model, which might (at least historically) the most popular method for solving problems. Despite its simplicity, it is surprisingly useful and is an important stepping stone for advanced methods, such as deep learning, see Chapter 6.

As discussed in the previous chapter, regression amounts to learning the relationships between input variables $x = [x_1, x_2, \dots, x_p]^T$ and a numerical output $y$. The inputs can be categorical or numerical, but we will be assuming that all $p$ inputs are numerical, and discuss categorical later. In a more mathematical framework, regression is learning a model
$y = f(x) + \varepsilon, \quad (3.1)$

mapping the output, where $\varepsilon$ is an error term that describes everything about the input-output relationship that cannot be captured by the model. With a statistical perspective, we consider $\varepsilon$ as a random variable, referred to as noise, that is independent of $x$ and has mean value of zero. As running example we use the car stopping distance problem Example 2.2.

### The linear regression model

The linear regression model assumes that the output variable $y$ (a scalar) can be described as an affine combination of the $p$ input variables $x_1, x_2, \dots, x_p$ plus a noise term $\varepsilon$.
$y = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_px_p + \varepsilon, \quad (3.2)$

We refer to the coefficients $\theta_0, \theta_1, \dots, \theta_p$ as the parameters of the model, and sometimes we refer to $\theta_0$ specifically as the intercept (or offset) term. The noise term $\varepsilon$ accounts for errors in the data not captured by the model. The noise is assumed to have mean zero and to be independent of $x$. The zero-mean assumption is nonrestrictive, so any (constant) non-zero can be incorporated into the offset term $\theta_0$. To have a more compact notation, we introduce the parameter vector $\theta = [\theta_0, \theta_1, \dots, \theta_p]^T$ and extend the vector $x$ with a constant in its first position, so that we can write the linear regression model compactly as
$y = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_px_p + \varepsilon = [\theta_0, \theta_1, \dots, \theta_p]^T \mathbf{x} + \varepsilon. \quad (3.3)$

This notation means that the symbol $x$ is used for both the $p+1$ and $p$ dimensional version of the input vector, or without the constant in the leading position, respectively. This is only a matter of book-keeping for handling the intercept term $\theta_0$. Which definition is used will be clear from context and carries no deeper meaning.

> An affine function is a linear function plus a constant.

The linear regression model is a parametric function of the model (3.3). The parameters $\theta$ can take arbitrary values, and those we assign will control the input–output relationship described by the model. Learning of the model therefore amounts to finding suitable values for $\theta$ based on observed data. Before discussing how to do this, however, let us first look at how to use the model once it has been learned.

The goal in supervised learning is making predictions $\widehat{y}(\mathbf{x}^*)$ for new, unseen inputs $\mathbf{x}^* = [1, x_1^*, \dots x_p^*]^T$. Let us assume that we have already learned some parameter values $\hat{\theta}$ for the linear regression model. We use the symbol $\hat{}$ to indicate that $\hat{\theta}$ contains learned values of parameters. Since the noise $\varepsilon$ is random with zero mean and independent of all observed variables, we must replace $\varepsilon$ with $0$ in the prediction. That is, a prediction from the linear regression model takes the form
$\widehat{y}(\mathbf{x}^*) = \hat{\theta}_0 + \hat{\theta}_1x_1^* + \hat{\theta}_2x_2 + \dots + \hat{\theta}_px_p^* = \hat{\theta}^T \mathbf{x}^*. \quad (3.4)$

The noise $\varepsilon$ is often referred to as an irreducible error or aleatory uncertainty in the prediction. We illustrate the predictions made by a linear regression model in Figure 3.1.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_37_0.png)

**Figure 3.1:** Linear regression with $p=1$: The black dots represent $n=3$ data points, from which a linear regression model (blue line) is learned. The model does not fit the data perfectly, so there is a remaining error corresponding to the noise $\varepsilon$ (red). The model can be used to **predict** (blue circle) the output $\widehat{y}(\mathbf{x}^*)$ for a test input $\mathbf{x}^*$.

## Learning linear regression from training data

Let us now discuss how to learn a linear regression model, that is learn $\theta$, from training data $\mathcal{T} = \{\mathbf{x}_i, y_i\}_{i=1}^n$. We collect the training data, which consists of $n$ data points with inputs $\mathbf{x}_i$, and outputs $y_i$, in the $n \times (p+1)$
