# 6.6.3.6 Knowledge gradient

So far the acquisition functions we have considered are all greedy, in that they only look one step ahead. The **knowledge gradient** acquisition function, proposed in [FPD09], looks two steps ahead by considering the improvement we might expect to get if we query \(\boldsymbol{x}\), update our posterior, and then exploit our knowledge by maximizing wrt our new beliefs. More precisely, let us define the best value we can find if we query one more point:

```
\( V_{n+1}(\boldsymbol{x}, y) = \max_{\boldsymbol{x}'} \mathbb{E}_{p(f|\boldsymbol{x}, y, \mathcal{D}_n)} [f(\boldsymbol{x}')] \qquad (6.184) \)
\( V_{n+1}(\boldsymbol{x}) = \mathbb{E}_{p(y|\boldsymbol{x}, \mathcal{D}_n)} [V_{n+1}(\boldsymbol{x}, y)] \qquad (6.185) \)
```

We define the KG acquisition function as follows:

```
\( \alpha_{KG}(\boldsymbol{x}; \mathcal{D}_n) = \mathbb{E}_{\mathcal{D}_n} [(V_{n+1}(\boldsymbol{x}) - M_n) \mathbb{I}(V_{n+1}(\boldsymbol{x}) > M_n)] \qquad (6.186) \)
```

Compare this to the EI function in Equation (6.176).) Thus we pick the point \(\boldsymbol{x}_{n+1}\) such that observing \(f(\boldsymbol{x}_{n+1})\) will give us knowledge which we can then exploit, rather than directly trying to find a better point with better \(f\) value.

# 6.6.3.7 Optimizing the acquisition function

The acquisition function \(\alpha(\boldsymbol{x})\) is often multimodal (see e.g., Figure 6.11), since it will be 0 at all the previously queried points (assuming noise-free observations). Consequently maximizing this function can be a hard subproblem in itself [WHD18; Rub+20].

In the continuous setting, it is common to use multirestart BFGS or grid search. We can also use the cross-entropy method (Section 6.7.5), using mixtures of Gaussians [BK10] or VAEs [Fau+18] as the generative model over \(\boldsymbol{x}\). In the discrete, combinatorial setting (e.g., when optimizing biological sequences), [Bel+19] use regularized evolution, (Section 6.7.3), and [Ang+20] use proximial policy optimization (Section 35.3.4). Many other combinations are possible.

# 6.6.4 Other issues

There are many other issues that need to be tackled when using Bayesian optimization, a few of which we briefly mention below.

# 6.6.4.1 Parallel (batch) queries

In some cases, we want to query the objective function at multiple points in parallel; this is known as **batched Bayesian optimization**. Now we need to optimize over a set of possible queries, which is computationally even more difficult than the regular case. See [WHD18; DBB20] for some recent papers on this topic.

# 6.6.4.2 Conditional parameters

BayesOpt is often applied to hyper-parameter optimization. In many applications, some hyperparameters are only well-defined if other ones take on specific values. For example, suppose we are trying to automatically tune a classifier, as in the **Auto-Sklearn** system [Feu+15], or the **Auto-WEKA**