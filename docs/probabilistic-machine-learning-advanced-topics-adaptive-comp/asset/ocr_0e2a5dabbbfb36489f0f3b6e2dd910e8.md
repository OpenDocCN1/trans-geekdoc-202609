# 24.2.2.2 Persistent CD

One variant of CD that sometimes performs better is **persistent contrastive divergence** (PCD) [Tie08; TH09; You99]. In this approach, a single MCMC chain with a persistent state is employed to sample from the EBM. In PCD, we do not restart the MCMC chain when training on a new datapoint; rather, we carry over the state of the previous MCMC chain and use it to initialize a new MCMC chain for the next training step. See Line 12 for some pseudocode. Hence there are two dynamical processes running at different time scales: the states \(\mathbf{x}\) change quickly, and the parameters \(\boldsymbol{\theta}\) change slowly.

```
Algorithm 24.2: Persistent MCMC-SGD for fitting an EBM
1 Initialize parameters \(\boldsymbol{\theta}\) randomly
2 Initialize chains \(\tilde{\mathbf{x}}_{1:S}\) randomly
3 Initialize learning rate \(\eta\)
4 for \(t = 1, 2, \dots\) do
5   for \(\mathbf{x}_b\) in minibatch of size \(B\) do
6     \(\mathbf{g}_b = \nabla_{\boldsymbol{\theta}}\mathcal{E}_{\boldsymbol{\theta}}(\mathbf{x}_b)\)
7   for sample \(s = 1 : S\) do
8     Sample \(\tilde{\mathbf{x}}_s \sim\) MCMC(target \(= p(\cdot|\boldsymbol{\theta})\), init \(= \tilde{\mathbf{x}}_s\), nsteps \(= N\))
9     \(\tilde{\mathbf{g}}_s = \nabla_{\boldsymbol{\theta}}\mathcal{E}_{\boldsymbol{\theta}}(\tilde{\mathbf{x}}_s)\)
10  \(\mathbf{g}_t = -(\frac{1}{B}\sum_{b=1}^B \mathbf{g}_b) - (\frac{1}{S}\sum_{s=1}^S \tilde{\mathbf{g}}_s)\)
11  \(\boldsymbol{\theta} := \boldsymbol{\theta} + \eta\mathbf{g}_t\)
12  Decrease step size \(\eta\)
```

A theoretical justification for this was given in [You89], who showed that we can start the MCMC chain at its previous value, and just take a few steps, because \(p(\mathbf{x}|\boldsymbol{\theta}_t)\) is likely to be close to \(p(\mathbf{x}|\boldsymbol{\theta}_{t-1})\), since we only changed the parameters by a small amount in the intervening SGD step.

# 24.2.2.3 Other methods

PCD can be further improved by keeping multiple historical states of the MCMC chain in a replay buffer and initialize new MCMC chains by randomly sampling from it [DM19b]. Other variants of CD include mean field CD [WH02], and multi-grid CD [Gao+18].

EBMs trained with CD may not capture the data distribution faithfully, since truncated MCMC can lead to biased gradient updates that hurt the learning dynamics [SMB10; FI10; Nij+19]. There are several methods that focus on removing this bias for improved MCMC training. For example, one line of work proposes unbiased estimators of the gradient through coupled MCMC [JOA17; QZW19]; and Du et al. [Du+20] propose to reduce the bias by differentiating through the MCMC sampling algorithm and estimating an entropy correction term.