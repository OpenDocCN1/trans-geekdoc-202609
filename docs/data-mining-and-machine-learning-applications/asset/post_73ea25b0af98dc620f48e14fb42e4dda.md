
![](img/48ffcb334b2fea865a1f194394911123_416_0.png)

Figure 15.2 Flow diagram of PCA algorithm used in our proposed methodology.

principle of least squares [28]. In this research work, we have utilized X as the input information matrix, whereas k is the number of variables that is 2,048, and t is the total observations i.e. 3,200. Allow us to consider the situation of ordinary PCA, which is discussed underneath:

- 1. Suppose we have k original variables: s1, s2, ..., Sk.
- 2. We need to produce k new variables: t1, t2, ..., tk.

```
t1 = a11s1 + a12s2 + ... + a1ksk

t2 = a21s1 + a22s2 + ... + a2ksk

tk = ak1s1 + ak2s2 + ... + akksk
```

such that: sk's are uncorrelated (orthogonal)
s1 explains as much as possible of original variance in the data set
s2 explains as much as possible of the remaining variance etc.
By applying the above algorithm, PCA transforms the multivariate data into a new configuration dataset that is easier to interpret.

Figure 15.2 shows how our input data is transformed while applying the PCA algorithm for dimensionality reduction.

## 15.3.5 Restricted Boltzmann Machine (RBM)

RBM is an undirected variant that assumes an important role in Deep Belief Networks (DBNs). It characterizes a bunch of rules in the method, which is useful in dimensionality decrease, pattern recognition, regression,
![](img/48ffcb334b2fea865a1f194394911123_417_0.png)
and collaborative filtering [29]. Rather than utilizing deterministic dispersion, RBM utilizes stochastic units of probability distribution represented in Section 15.3.1. RBM utilizes two different biases which make it not the same as auto-encoders:

- 1. The hidden bias which helps in to reproduce the activation on the forward pass.
- 2. The visible bias which helps in to reproduce the activation on the backward pass.

RBM is an external model that represents a two-layered network which is visible and hidden layer. Figure 15.3 shows the architecture of RBM, where each circle represents the neuron-like unit where calculation takes place. One of the most important features of RBM is that there is no communication between the internal layers which is there as a restriction in RBM model. Each node in this model performs stochastic decisions on whether to send that to the input or not. Low level features are taken by the visible layer for the data to be learned.

## 15.3.6 Stochastic Binary Units (Bernoulli Variables)

Stochastic Binary Units or we simply say Bernoulli variables are the units that have a state of 0s and 1s. The probability of turning on is determined by the weighted input from the other inputs (plus a bias) [30]. Let us suppose s be the stochastic unit variable, b be the bias, and w be the weights used, then the formula is given by:

```
p(s_i = 1) = \frac{1}{1 + \exp\left(-b_i - \sum_j s_j w_{ji}\right)}
```

The above formula is used to calculate the probability distribution when the input is in a state 0 or 1. Stochastic binary units utilize similar conditions which are used by logistic units, however they represent the output of the logistic as generating a spike in a brief timeframe.

## Working Principle of RBM

As we all know that low level feature is being taken by the RBM in order to learn the data. Restricted Boltzmann Machine is a deep learning model that comprises of two layers, the first layer to a hidden layer and the second layer to be a hidden layer. Suppose x is the input layer at a particular node, and w is the weights that are fed into each input layer, and b is the bias used. Now to produce the node's output, we use the formula given below:

Output a = Activation f ((weight w * input X) + biasb)

where ‘a’ represents the output, and this proceeds for all other layers which are available in the network. In the instance of numerous hidden layers, the weights are changed until that layer is able to approximate the input from the previous layer [31]. Proper initial value of weights to later training and performing classification is one of the benefits of a Restricted Boltzmann machine (RBM).

In our proposed methodology, we have made an algorithm in which three layers of RBM are used, which is shown in Figure 15.1. Each output of the RBM layer becomes an input to the succeeding input layer of RBM, which are shown in the form of a hidden layer in the proposed methodology. The input layer is in which all the initial calculation of the weights is done and are fed into the hidden layer, and from there, new weights are calculated, and this process continues until all the hidden layers update their weights likewise in backpropagation network. Finally, the output is fetched from the last layer, which is present in the restricted Boltzmann machine network [32].

## 15.3.7 Training

The training of RBM is different than another neural network as this neural network works on the stochastic gradient descent method. There are two types of methods that are involved in training the data via restricted Boltzmann machine.

### 15.3.7.1 Gibbs Sampling

Gibbs Sampling is a Markov Chain Monte Carlo (MCMC) method used to get the observations in sequential from the multivariate probability distribution of information. It can also be used to approximate the joint probability distribution. Gibbs sampling generates the samples which are related to Markov Chains which are similar to the other samples which are generated.

Algorithm 15.1 described below shows how the Gibbs Sampling works on our proposed methodology. Gibbs Sampling is preferred for our methodology as it helps us to make accurate results while performing the training further [33].

```
Algorithm 15.1 Gibbs Sampling
Begin Gibbs-Sampler(y, Φ, P (0) (y), z )
// y—Sampling of the set of variables
// Φ—Number of factors which defines PΦ
// P (0) (y)—Distribution of the initial state
//z—Time steps calculation
...............................................
1. Sample y(0) from P (0)(y)
2. for z=1, ..., z
3. y(z)—y(z-1)
4. for each yi y
5. Sample yi(z) from PΦ(yi|y-i)
6. // Change yi in y(z)
7. return y(0), ..., y(T)
```

### 15.3.7.2 Contrastive Divergence (CD)

Contrastive Divergence is a Monte Carlo Markov Chain (MCMC) gradient descent learning method especially appropriate for learning products of experts (PoE) and energy-based model parameters. A general algorithm for contrastive divergence is described below, which is used in our proposed methodology [34]. Although contrastive divergence algorithm is very tricky to solve, it provides better results than any other convergence algorithm, which is better for our proposed methodology. Algorithm 15.2 describes how the CD algorithm works on our dataset, which is used in our proposed methodology.

```
Algorithm 15.2 Contrastive Divergence
1. Set the visible units to a training vector;
2. For k <- 1 to a maximum of iterations, do
3. For s <- 1 to the size of training, data do
4. Update in parallel each hidden units using Eq. 2;
5. Update in parallel each visible unit using Eq.3; to get “reconstruction”
6. Update all hidden units again in Eq. 2;
7. Update weight and biases with Eqs. 4–6;
8. Select another training vector;
9. End
10. End
```

## 15.4 Experimental Framework

In this research work, we have employed different ratios for training and testing data split as 90–10, 80–20, and 70–30. Additionally, we make a tenfold cross validation approach. Firstly, the signals are divided into ten equal parts. Then to perform the signals in the training phase, nine parts are used. For the testing phase, one-tenth of the part is used which is used for validation of our proposed algorithm. This methodology was sustained up to 10 times by changing the testing and training dataset. It fills in as a convolutional backpropagation where batch is 11. Evaluation of the gradient of loss function contrary to the weights in backpropagation is employed during training phase. It results feedback for error signals in backward direction to the network. In training phase, it helps in updating the weights of the network. Batch size is utilized for getting various signals for training updates. Gibbs Sampling is performed during training stage, which is utilized to get the observation sequentially for the multivariate probability distribution of information. A Contrastive divergence an algorithm which is useful in giving better results while in the training phase of the algorithm. The whole dataset is tuned with multiple training and testing parameters so that results can be improved during the calculation of the various measures.
