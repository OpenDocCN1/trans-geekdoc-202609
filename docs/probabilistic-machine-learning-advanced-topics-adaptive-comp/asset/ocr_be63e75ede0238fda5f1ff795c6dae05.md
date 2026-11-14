system [Kot+17]. If the method chooses to use a neural network, it also needs to specify the number of layers, and number of hidden units per layer; but if it chooses to use a decision tree, it instead should specify different hyperparameters, such as the maximum tree depth.

We can formalize such problems by defining the search space in terms of a tree or DAG (directed acyclic graph), where different subsets of the parameters are defined at each leaf. Applying GPs to this setting requires non-standard kernels, such as those discussed in [Swe+13; Jen+17]. Alternatively, we can use other forms of Bayesian regression, such as ensembles of random forests [HHLB11], which can easily handle conditional parameter spaces.

# 6.6.4.3 Multifidelity surrogates

In some cases, we can construct surrogate functions with different levels of accuracy, each of which may take variable amounts of time to compute. In particular, let \( f(\boldsymbol{x}, s) \) be an approximation to the true function at \( \boldsymbol{x} \) with fidelity \( s \). The goal is to solve \( \max_{\boldsymbol{x}} f(\boldsymbol{x}, 0) \) by observing \( f(\boldsymbol{x}, s) \) at a sequence of \( (\boldsymbol{x}_i, s_i) \) values, such that the total cost \( \sum_{i=1}^n c(s_i) \) is below some budget. For example, in the context of hyperparameter selection, \( s \) may control how long we run the parameter optimizer for, or how large the validation set is.

In addition to choosing what fidelity to use for an experiment, we may choose to terminate expensive trials (queries) early, if the results of their cheaper proxies suggest they will not be worth running to completion (see e.g., [Str19; Li+17c; FKH17]). Alternatively, we may choose to resume an earlier aborted run, to collect more data on it, as in the **freeze-thaw algorithm** [SSA14].

# 6.6.4.4 Constraints

If we want to maximize a function subject to known constraints, we can simply build the constraints into the acquisition function. But if the constraints are unknown, we need to estimate the support of the feasible set in addition to estimating the function. In [GSA14], they propose the weighted EI criterion, given by \( \alpha_{wEI}(\boldsymbol{x}; \mathcal{D}_n) = \alpha_{EI}(\boldsymbol{x}; \mathcal{D}_n) h(\boldsymbol{x}; \mathcal{D}_n) \), where \( h(\boldsymbol{x}; \mathcal{D}_n) \) is a GP with a Bernoulli observation model that specifies if \( \boldsymbol{x} \) is feasible or not. Of course, other methods are possible. For example, [HL+16b] propose a method based on predictive entropy search.

# 6.7 Derivative-free optimization

**Derivative-free optimization** or **DFO** refers to a class of techniques for optimizing functions without using derivatives. This is useful for blackbox function optimization as well as discrete optimization. If the function is expensive to evaliate, we can use Bayesian optimization (Section 6.6). If the function is cheap to evaluate, we can use stochastic local search methods or evolutionary search methods, as we discuss below.

# 6.7.1 Local search

In this section, we discuss heuristic optimization algorithms that try to find the global maximum in a discrete, unstructured search space. These algorithms replace the local gradient based update, which has the form \( \boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t + \eta_t \boldsymbol{d}_t \), with the following discrete analog:

```
\(\boldsymbol{x}_{t+1} = \underset{\boldsymbol{x} \in \text{nbr}(\boldsymbol{x}_t)}{\text{argmax}} \mathcal{L}(\boldsymbol{x})\)
```