
the hidden units given the visible units—by some reasonably simple family of distributions. In the case of the mean field approximation, the approximating family is the set of distributions where the hidden units are conditionally independent.

We now develop the mean field approach for the example with two hidden layers. Let $Q(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v})$ be the approximation of $P(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v})$. The mean field assumption implies that

$$Q(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v}) = \prod_{j} Q(h_{j}^{(1)} \mid \boldsymbol{v}) \prod_{k} Q(h_{k}^{(2)} \mid \boldsymbol{v}).\tag{20.29}$$

The mean field approximation attempts to find a member of this family of distributions that best fits the true posterior $P(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v})$. Importantly, the inference process must be run again to find a different distribution $Q$ every time we use a new value of $\boldsymbol{v}$.

One can conceive of many ways of measuring how well $Q(\boldsymbol{h} \mid \boldsymbol{v})$ fits $P(\boldsymbol{h} \mid \boldsymbol{v})$. The mean field approach is to minimize

$$\mathrm{KL}(Q\|P) = \sum_{\boldsymbol{h}} Q(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v}) \log \left( \frac{Q(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v})}{P(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v})} \right).\tag{20.30}$$

In general, we do not have to provide a parametric form of the approximating distribution beyond enforcing the independence assumptions. The variational approximation procedure is generally able to recover a functional form of the approximate distribution. However, in the case of a mean field assumption on binary hidden units (the case we are developing here) there is no loss of generality resulting from fixing a parametrization of the model in advance.

We parametrize $Q$ as a product of Bernoulli distributions; that is, we associate the probability of each element of $\boldsymbol{h}^{(1)}$ with a parameter. Specifically, for each $j$, $\hat{h}_{j}^{(1)} = Q(h_{j}^{(1)}=1 \mid \boldsymbol{v})$, where $\hat{h}_{j}^{(1)} \in [0,1]$, and for each $k$, $\hat{h}_{k}^{(2)} = Q(h_{k}^{(2)}=1 \mid \boldsymbol{v})$, where $\hat{h}_{k}^{(2)} \in [0,1]$. Thus we have the following approximation to the posterior:

$$Q(\boldsymbol{h}^{(1)},\boldsymbol{h}^{(2)} \mid \boldsymbol{v}) = \prod_{j} Q(h_{j}^{(1)} \mid \boldsymbol{v}) \prod_{k} Q(h_{k}^{(2)} \mid \boldsymbol{v})\tag{20.31}$$ $$= \prod_{j} \bigl(\hat{h}_{j}^{(1)}\bigr)^{h_{j}^{(1)}} \bigl(1-\hat{h}_{j}^{(1)}\bigr)^{(1-h_{j}^{(1)})} \times \prod_{k} \bigl(\hat{h}_{k}^{(2)}\bigr)^{h_{k}^{(2)}} \bigl(1-\hat{h}_{k}^{(2)}\bigr)^{(1-h_{k}^{(2)})}.\tag{20.32}$$

Of course, for DBMs with more layers, the approximate posterior parametrization can be extended in the obvious way, exploiting the bipartite structure of the graph to update all the even layers simultaneously and then to update all the odd layers simultaneously, following the same schedule as Gibbs sampling.

Now that we have specified our family of approximating distributions Q, it remains to specify a procedure for choosing the member of this family that best fits P. The most straightforward way to do this is to use the mean field equations specified by equation 19.56. These equations were derived by solving for where the derivatives of the variational lower bound are zero. They describe in an abstract manner how to optimize the variational lower bound for any model, simply by taking expectations with respect to Q.

Applying these general equations, we obtain the update rules (again, ignoring bias terms):

$$\hat{h}_j^{(1)} = \sigma\left(\sum_i v_i W_{i,j}^{(1)} + \sum_{k'} W_{j,k'}^{(2)} \hat{h}_{k'}^{(2)}\right), \quad \forall j, \qquad (20.33)$$ $$\hat{h}_k^{(2)} = \sigma\left(\sum_{j'} W_{j',k}^{(2)} \hat{h}_{j'}^{(1)}\right), \quad \forall k. \qquad (20.34)$$

At a fixed point of this system of equations, we have a local maximum of the variational lower bound L(Q). Thus these fixed-point update equations define an iterative algorithm where we alternate updates of \hat{h}_j^{(1)} (using equation 20.33) and updates of \hat{h}_k^{(2)} (using equation 20.34). On small problems such as MNIST, as few as ten iterations can be sufficient to find an approximate positive phase gradient for learning, and fifty usually suffice to obtain a high-quality representation of a single specific example to be used for high-accuracy classification. Extending approximate variational inference to deeper DBMs is straightforward.

## 20.4.3 DBM Parameter Learning

Learning in the DBM must confront both the challenge of an intractable partition function, using the techniques from chapter 18, and the challenge of an intractable posterior distribution, using the techniques from chapter 19.

As described in section 20.4.2, variational inference allows the construction of a distribution Q(h | v) that approximates the intractable P(h | v). Learning then proceeds by maximizing L(v, Q, θ), the variational lower bound on the intractable log-likelihood, log P(v; θ).

For a deep Boltzmann machine with two hidden layers, $\mathcal{L}$ is given by

$$\mathcal{L}(Q,\boldsymbol{\theta}) = \sum_i \sum_{j'} v_i W_{i,j'}^{(1)} \hat{h}_{j'}^{(1)} + \sum_{j'} \sum_{k'} \hat{h}_{j'}^{(1)} W_{j',k'}^{(2)} \hat{h}_{k'}^{(2)} - \log Z(\boldsymbol{\theta}) + \mathcal{H}(Q). \tag{20.35}$$

This expression still contains the log partition function, $\log Z(\boldsymbol{\theta})$. Because a deep Boltzmann machine contains restricted Boltzmann machines as components, the hardness results for computing the partition function and sampling that apply to restricted Boltzmann machines also apply to deep Boltzmann machines. This means that evaluating the probability mass function of a Boltzmann machine requires approximate methods such as annealed importance sampling. Likewise, training the model requires approximations to the gradient of the log partition function. See chapter 18 for a general description of these methods. DBMs are typically trained using stochastic maximum likelihood. Many of the other techniques described in chapter 18 are not applicable. Techniques such as pseudolikelihood require the ability to evaluate the unnormalized probabilities, rather than merely obtain a variational lower bound on them. Contrastive divergence is slow for deep Boltzmann machines because they do not allow efficient sampling of the hidden units given the visible units—instead, contrastive divergence would require burning in a Markov chain every time a new negative phase sample is needed.

The nonvariational version of the stochastic maximum likelihood algorithm is discussed in section 18.2. Variational stochastic maximum likelihood as applied to the DBM is given in algorithm 20.1. Recall that we describe a simplified variant of the DBM that lacks bias parameters; including them is trivial.

## 20.4.4 Layer-Wise Pretraining

Unfortunately, training a DBM using stochastic maximum likelihood (as described above) from a random initialization usually results in failure. In some cases, the model fails to learn to represent the distribution adequately. In other cases, the DBM may represent the distribution well, but with no higher likelihood than could be obtained with just an RBM. A DBM with very small weights in all but the first layer represents approximately the same distribution as an RBM.

Various techniques that permit joint training have been developed and are described in section 20.4.5. However, the original and most popular method for overcoming the joint training problem of DBMs is greedy layer-wise pretraining. In this method, each layer of the DBM is trained in isolation as an RBM. The first layer is trained to model the input data. Each subsequent RBM is trained to model samples from the previous RBM’s posterior distribution. After all the
