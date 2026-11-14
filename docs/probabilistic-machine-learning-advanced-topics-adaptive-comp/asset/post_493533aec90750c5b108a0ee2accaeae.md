
## 24.5.1 Minimizing Differences/Derivatives of KL Divergences

The overarching strategy for learning probabilistic models from data is to minimize the KL divergence between data and model distributions. However, because the normalizing constants of EBMs are typically intractable, it is hard to directly evaluate the KL divergence when the model is an EBM (see the discussion in Section 24.2.1). One generic idea that has frequently circumvented this difficulty is to consider differences/derivatives of KL divergences. It turns out that the unknown partition functions of EBMs are often cancelled out after taking the difference of two closely related KL divergences, or computing the derivatives.

Typical examples of this strategy include minimum velocity learning [Mov08; Wan+20d], minimum probability flow [SBDB11], and minimum KL contraction [Lyu11], to name a few. In minimum velocity learning and minimum probability flow, a Markov chain is designed such that it starts from the data distribution p_D(x) and converges to the EBM distribution p_θ(x) = e^{-E_θ(x)} / Z_θ. Specifically, the Markov chain satisfies p_0(x) ≡ p_D(x) and p_∞(x) ≡ p_θ(x), where we denote by p_t(x) the state distribution at time t >= 0.

This Markov chain will evolve towards p_θ(x) unless p_D(x) ≡ p_θ(x). Therefore, we can fit the EBM distribution p_θ(x) to p_D(x) by minimizing the modulus of the "velocity" of this evolution, defined by

```
\frac{d}{dt} D_{KL}(p_t(\mathbf{x}) \| p_\theta(\mathbf{x})) \Big|_{t=0} \quad \text{or} \quad \frac{d}{dt} D_{KL}(p_D(\mathbf{x}) \| p_t(\mathbf{x})) \Big|_{t=0}
```

in minimum velocity learning and minimum probability flow respectively. These objectives typically do not require computing the normalizing constant Z_θ.

In minimum KL contraction [Lyu11], a distribution transformation Φ is chosen such that

```
D_{KL}(p(\mathbf{x}) \| q(\mathbf{x})) \ge D_{KL}(\Phi\{p(\mathbf{x})\} \| \Phi\{q(\mathbf{x})\})
```

with equality if and only if p(x) = q(x). We can leverage this Φ to train an EBM, by minimizing

```
D_{KL}(p_D(\mathbf{x}) \| p_\theta(\mathbf{x})) - D_{KL}(\Phi\{p_D(\mathbf{x})\} \| \Phi\{p_\theta(\mathbf{x})\})
```

This objective does not require computing the partition function Z_θ whenever Φ is linear.

Minimum velocity learning, minimum probability flow, and minimum KL contraction can all be viewed as generalizations to score matching and noise contrastive estimation [Mov08; SBDB11; Lyu11].

## 24.5.2 Minimizing the Stein discrepancy

We can train EBMs by minimizing the Stein discrepancy, defined by

```
D_{Stein}(p_D(\mathbf{x}) \| p_\theta(\mathbf{x})) := \sup_{\mathbf{f} \in \mathcal{F}} \mathbb{E}_{p_D(\mathbf{x})} [\nabla_\mathbf{x} \log p_\theta(\mathbf{x})^\mathsf{T} \mathbf{f}(\mathbf{x}) + \text{trace}(\nabla_\mathbf{x} \mathbf{f}(\mathbf{x}))]
```

where F is a family of vector-valued functions, and ∇_x f(x) denotes the Jacobian of f(x). With some regularity conditions [GM15; LLJ16], we have D_S(p_D(x) || p_θ(x)) >= 0, where the equality holds if and only if p_D(x) ≡ p_θ(x). Similar to score matching (Equation (24.30)), the objective Equation (24.62) only involves the score function of p_θ(x), and does not require computing the EBM's partition function. Still, the trace term in Equation (24.62) may demand expensive computation, and does not scale well to high dimensional data.

There are two common methods that sidestep this difficulty. Gorham and Mackey [GM15] and Liu, Lee, and Jordan [LLJ16] discovered that when \(\mathcal{F}\) is a unit ball in a reproducing kernel Hilbert space (RKHS) with a fixed kernel, the Stein discrepancy becomes kernelized Stein discrepancy, where the trace term is a constant and does not affect optimization. Otherwise, trace(\(\nabla_x \mathbf{f}(\mathbf{x})\)) can be approximated with the Skilling-Hutchinson trace estimator [Ski89; Hut89; Gra+20c].

## 24.5.3 Adversarial training

Recall from Section 24.2.1 that when training EBMs with maximum likelihood estimation (MLE), we need to sample from the EBM per training iteration. However, sampling using multiple MCMC steps is expensive and requires careful tuning of the Markov chain. One way to avoid this difficulty is to use non-MLE methods that do not need sampling, such as score matching and noise contrastive estimation. Here we introduce another family of methods that sidestep costly MCMC sampling by learning an auxiliary model through adversarial training, which allows fast sampling.

Using the definition of EBMs, we can rewrite the maximum likelihood objective by introducing a variational distribution \(q_\phi(\mathbf{x})\) parameterized by \(\phi\):

```
\(\mathbb{E}_{p_D(\mathbf{x})}[\log p_\theta(\mathbf{x})] = \mathbb{E}_{p_D(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - \log Z_\theta\)
\(= \mathbb{E}_{p_D(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - \log \int e^{-\mathcal{E}_\theta(\mathbf{x})} \mathrm{d}\mathbf{x}\)
\(= \mathbb{E}_{p_D(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - \log \int q_\phi(\mathbf{x}) \frac{e^{-\mathcal{E}_\theta(\mathbf{x})}}{q_\phi(\mathbf{x})} \mathrm{d}\mathbf{x}\)
\(\overset{(i)}{\le} \mathbb{E}_{p_D(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - \int q_\phi(\mathbf{x}) \log \frac{e^{-\mathcal{E}_\theta(\mathbf{x})}}{q_\phi(\mathbf{x})} \mathrm{d}\mathbf{x}\)
\(= \mathbb{E}_{p_D(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - \mathbb{E}_{q_\phi(\mathbf{x})}[-\mathcal{E}_\theta(\mathbf{x})] - H(q_\phi(\mathbf{x})),\) (24.63)
```

where \(H(q_\phi(\mathbf{x}))\) denotes the entropy of \(q_\phi(\mathbf{x})\). Step (i) is due to Jensen's inequality. Equation (24.63) provides an upper bound to the expected log-likelihood. For EBM training, we can first minimize the upper bound Equation (24.63) with respect to \(q_\phi(\mathbf{x})\) so that it is closer to the likelihood objective, and then maximize Equation (24.63) with respect to \(\mathcal{E}_\theta(\mathbf{x})\) as a surrogate for maximizing likelihood.

This amounts to using the following minimax objective

```
\(\max_\theta \min_\phi \mathbb{E}_{q_\phi(\mathbf{x})}[\mathcal{E}_\theta(\mathbf{x})] - \mathbb{E}_{p_D(\mathbf{x})}[\mathcal{E}_\theta(\mathbf{x})] - H(q_\phi(\mathbf{x})).\) (24.64)
```

Optimizing the above objective is similar to training GANs (Chapter 26), and can be achieved by adversarial training. The variational distribution \(q_\phi(\mathbf{x})\) should allow both fast sampling and efficient entropy evaluation to make Equation (24.64) tractable. This limits the model family of \(q_\phi(\mathbf{x})\), and usually restricts our choice to invertible probabilistic models, such as inverse autoregressive flow (Section 23.2.4.3). See Dai et al. [Dai+19b] for an example on designing \(q_\phi(\mathbf{x})\) and training EBMs with Equation (24.64).

Kim and Bengio [KB16] and Zhai et al. [Zha+16] propose to represent \(q_\phi(\mathbf{x})\) with neural samplers, like the generator of GANs. A neural sampler is a deterministic mapping \(g_\phi\) that maps a random Gaussian noise \(\mathbf{z} \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\) directly to a sample \(\mathbf{x} = g_\phi(\mathbf{z})\). When using a neural sampler as \(q_\phi(\mathbf{x})\), it is efficient to draw samples through the deterministic mapping, but \(H(q_\phi(\mathbf{x}))\) is intractable since the density of \(q_\phi(\mathbf{x})\) is unknown. Kim and Bengio [KB16] and Zhai et al. [Zha+16] propose several heuristics to approximate this entropy function. Kumar et al. [Kum+19c] propose to estimate the entropy through its connection to mutual information: \(H(q_\phi(\mathbf{z})) = I(g_\phi(\mathbf{z}), \mathbf{z})\), which can be estimated from samples with variational lower bounds [NWJ10b; NCT16b]. Dai et al. [Dai+19a] noticed that when defining \(p_\theta(\mathbf{x}) = p_0(\mathbf{x})e^{-\varepsilon_\theta(\mathbf{x})/Z_\theta}\), with \(p_0(\mathbf{x})\) being a fixed base distribution, the entropy term \(-H(q_\phi(\mathbf{x}))\) in Equation (24.64) can be replaced by \(\mathrm{D}_{\mathrm{KL}}(q_\phi(\mathbf{x}) \| p_0(\mathbf{x}))\), which can also be approximated with variational lower bounds using samples from \(q_\phi(\mathbf{x})\) and \(p_0(\mathbf{x})\), without requiring the density of \(q_\phi(\mathbf{x})\).

Grathwohl et al. [Gra+20a] represent \(q_\phi(\mathbf{x})\) as a noisy neural sampler, where samples are obtained via \(g_\phi(\mathbf{z}) + \sigma \boldsymbol{\epsilon}\), assuming \(\mathbf{z}, \boldsymbol{\epsilon} \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\). With a noisy neural sampler, \(\nabla_\phi H(q_\phi(\mathbf{x}))\) becomes particularly easy to estimate, which allows gradient-based optimization for the minimax objective in Equation (24.63). A related approach is proposed in Xie et al. [Xie+18], where authors train a noisy neural sampler with samples obtained from MCMC, and initialize new MCMC chains with samples generated from the neural sampler. This cooperative sampling scheme improves the convergence of MCMC, but may still require multiple MCMC steps for sample generation. It does not optimize the objective in Equation (24.63).

When using both adversarial training and MCMC sampling, Yu et al. [Yu+20] noticed that EBMs can be trained with an arbitrary \(f\)-divergence, including KL, reverse KL, total variation, Hellinger, etc. The method proposed by Yu et al. [Yu+20] allows us to explore the trade-offs and inductive bias of different statistical divergences for more flexible EBM training.
