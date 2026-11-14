
Since \(g_3(z_3) \propto \log f_3(z_3)\) we get

\(\mathbf{L}_3(q_3) = \sum_{z_3} q_3(z_3) [\log f_3(z_3) - \log q_3(z_3)] + \text{const} = -D_{KL}(q_3 \| f_3) + \text{const}\) (10.83)

Since \(D_{KL}(q_3 \| f_3)\) achieves its minimal value of 0 when \(q_3(z_3) = f_3(z_3)\) for all \(z_3\), we see that \(q_3^*(z_3) = f_3(z_3)\).

Now suppose that the joint distribution is defined by a Markov chain, where \(z_1 \to z_2 \to z_3\), so \(z_1 \perp z_3 | z_2\). Hence \(\log \tilde{p}(z_1, z_2, z_3) = \log \tilde{p}(z_2, z_3 | z_1) + \log \tilde{p}(z_1)\), where the latter term is independent of \(q_3(z_3)\). Thus the ELBO simplifies to

\(\mathbf{L}_3(q_3) = \sum_{z_3} q_3(z_3) \left[ \sum_{z_2} q_2(z_2) \log \tilde{p}(z_2, z_3) \right] + \mathbb{H}(q_3) + \text{const}\) (10.84)
\(= \sum_{z_3} q_3(z_3) [\log f_3(z_3) - \log q_3(z_3)] + \text{const}\) (10.85)

where

\(f_3(z_3) \propto \exp \left[ \sum_{z_2} q_2(z_2) \log \tilde{p}(z_2, z_3) \right] = \exp [\mathbb{E}_{z_{mb_3}} [\log \tilde{p}(z_2, z_3)]]\) (10.86)

where \(z_{mb_3} = z_2\) is the Markov blanket (Section 4.2.4.3) of \(z_3\). As before, the optimal variational distribution is given by \(q_3(z_3) = f_3(z_3)\).

In general, when we have \(J\) groups of variables, the optimal variational distribution for the \(j\)’th group is given by
\(q_j(z_j) \propto \exp \left[ \mathbb{E}_{z_{mb_j}} [\log \tilde{p}(z_j, z_{mb_j})] \right]\) (10.87)

(Compare to the equation for Gibbs sampling in Equation (12.19).) The CAVI method simply computes \(q_j\) for each dimension \(j\) in turn, in an iterative fashion (see Algorithm 10.4). Convergence is guaranteed since the bound is convex wrt each of the factors \(q_i\) [Bis06, p. 466].

```
**Algorithm 10.4:** Coordinate ascent variational inference (CAVI).
1 Initialize \(q_j(z_j)\) for \(j=1:J\)
2 foreach \(t=1:T\) do
3   foreach \(j=1:J\) do
4     Compute \(q_j(z_j) = \mathbb{E}_{z_{mb_j}} [\log \tilde{p}(z_j, z_{mb_j})]\)
5     Compute \(q_j(z_j) \propto \exp(q_j(z_j))\)
```

Note that the functional form of the \(q_i\) distributions does not need to be specified in advance, but will be determined by the form of the log joint. This is therefore called **free-form VI**, as opposed to fixed-form, where we explicitly choose a convenient distributional type for \(q\) (we discuss fixed-form VI in Section 10.2). We give some examples below that will make this clearer.

![](img/ca72c1626f4850f058a9edc138c1ac73_483_0.png)

Figure 10.8: A grid-structured MRF with hidden nodes \(z_i\) and local evidence nodes \(x_i\). The prior \(p(\mathbf{z})\) is an undirected Ising model, and the likelihood \(p(\mathbf{x}|\mathbf{z}) = \prod_i p(x_i|z_i)\) is a directed fully factored model.

### 10.3.2 Example: CAVI for the Ising model

In this section, we apply CAVI to perform mean field inference in an Ising model (Section 4.3.2.1), which is a kind of Markov random field defined on binary random variables, \(z_i \in \{-1, +1\}\), arranged in a 2d grid.

Originally Ising models were developed as models of atomic spins for magnetic materials, although we will apply them to an image denoising problem. Specifically, let \(z_i\) be the hidden value of pixel \(i\), and \(x_i \in \mathbb{R}\) be the observed noisy value. See Figure 10.8 for the graphical model.

Let \(L_i(z_i) \triangleq \log p(x_i|z_i)\) be the log likelihood for the \(i\)’th pixel (aka the **local evidence** for node \(i\) in the graphical model). The overall likelihood has the form

\(p(\mathbf{x}|\mathbf{z}) = \prod_i p(x_i|z_i) = \exp(\sum_i L_i(z_i))\) (10.88)

Our goal is to approximate the posterior \(p(\mathbf{z}|\mathbf{x})\). We will use an Ising model for the prior:

\(p(\mathbf{z}) = \frac{1}{Z_0} \exp(-\mathcal{E}_0(\mathbf{z}))\) (10.89)

\(\mathcal{E}_0(\mathbf{z}) = - \sum_{i \sim j} W_{ij} z_i z_j\) (10.90)

where we sum over each \(i - j\) edge. Therefore the posterior has the form

\(p(\mathbf{z}|\mathbf{x}) = \frac{1}{Z(\mathbf{x})} \exp(-\mathcal{E}(\mathbf{z}))\) (10.91)

\(\mathcal{E}(\mathbf{z}) = \mathcal{E}_0(\mathbf{z}) - \sum_i L_i(z_i)\) (10.92)

We will now make the following fully factored approximation:

\(q(\mathbf{z}) = \prod_i q_i(z_i) = \prod_i \text{Ber}(z_i|\mu_i)\) (10.93)

where \(\mu_i = \mathbb{E}_{q_i}[z_i]\) is the mean value of node \(i\). To derive the update for the variational parameter \(\mu_i\), we first compute the unnormalized log joint, \(\log \tilde{p}(\mathbf{z}) = -\mathcal{E}(\mathbf{z})\), dropping terms that do not involve $z_i$:

$$ \log \tilde{p}(\boldsymbol{z}) = z_i \sum_{j \in \text{nbr}_i} W_{ij} z_j + L_i(z_i) + \text{const} $$

This only depends on the states of the neighboring nodes. Hence

$$ q_i(z_i) \propto \exp(\mathbb{E}_{q_{-i}(\boldsymbol{z})} [\log \tilde{p}(\boldsymbol{z})]) = \exp \left( z_i \sum_{j \in \text{nbr}_i} W_{ij} \mu_j + L_i(z_i) \right) $$

where $q_{-i}(\boldsymbol{z}) = \prod_{j \neq i} q(z_j)$. Thus we replace the states of the neighbors by their average values. (Note that this replaces binary variables with continuous ones.)

We now simplify this expression. Let $m_i = \sum_{j \in \text{nbr}_i} W_{ij} \mu_j$ be the mean field influence on node $i$. Also, let $L_i^+ \triangleq L_i(+1)$ and $L_i^- \triangleq L_i(-1)$. The approximate marginal posterior is given by

$$ q_i(z_i = 1) = \frac{e^{m_i+L_i^+}}{e^{m_i+L_i^+} + e^{-m_i+L_i^-}} = \frac{1}{1+e^{-2m_i+L_i^- - L_i^+}} = \sigma(2a_i) $$

$$ a_i \triangleq m_i + 0.5(L_i^+ - L_i^-) $$

Similarly, we have $q_i(z_i = -1) = \sigma(-2a_i)$. From this we can compute the new mean for site $i$:

$$ \mu_i = \mathbb{E}_{q_i} [z_i] = q_i(z_i = +1) \cdot (+1) + q_i(z_i = -1) \cdot (-1) $$

$$ = \frac{1}{1+e^{-2a_i}} - \frac{1}{1+e^{2a_i}} = \frac{e^{a_i} - e^{-a_i}}{e^{a_i} + e^{-a_i}} = \tanh(a_i) $$

We can turn the above equations into a fixed point algorithm by writing

$$ \mu_i^t = \tanh \left( \sum_{j \in \text{nbr}_i} W_{ij} \mu_j^{t-1} + 0.5(L_i^+ - L_i^-) \right) $$

Following [MWJ99], we can use **damped updates** of the following form to improve convergence:

$$ \mu_i^t = (1-\lambda)\mu_i^{t-1} + \lambda \tanh \left( \sum_{j \in \text{nbr}_i} W_{ij} \mu_j^{t-1} + 0.5(L_i^+ - L_i^-) \right) $$

for $0 < \lambda < 1$. We can update all the nodes in parallel, or update them asynchronously.

Figure 10.9 shows the method in action, applied to a 2d Ising model with homogeneous attractive potentials, $W_{ij} = 1$. We use parallel updates with a damping factor of $\lambda = 0.5$. (If we don't use damping, we tend to get "checkerboard" artifacts.)

### 10.3.3 Variational Bayes

In Bayesian modeling, we treat the parameters $\boldsymbol{\theta}$ as latent variables. Thus our goal is to approximate the parameter posterior $p(\boldsymbol{\theta}|\mathcal{D}) \propto p(\boldsymbol{\theta})p(\mathcal{D}|\boldsymbol{\theta})$. Applying VI to this problem is called **variational Bayes** [Att00].

![](img/ca72c1626f4850f058a9edc138c1ac73_485_0.png)

Figure 10.9: Example of image denoising using mean field (with parallel updates and a damping factor of 0.5). We use an Ising prior with $W_{ij} = 1$ and a Gaussian noise model with $\sigma = 2$. We show the results after 1, 3 and 15 iterations across the image. Compare to Figure 12.3, which shows the results of using Gibbs sampling. Generated by *ising\_image\_denoise\_demo.ipynb*.

In this section, we assume there are no latent variables except for the shared global parameters, so the model has the form

\(p(\boldsymbol{\theta}, \mathcal{D}) = p(\boldsymbol{\theta}) \prod_{n=1}^N p(\mathcal{D}_n | \boldsymbol{\theta})\) (10.102)

These conditional independencies are illustrated in Figure 10.5a.

We will fit the variational posterior by maximizing the ELBO

\(\mathbf{L}(\boldsymbol{\psi}_{\boldsymbol{\theta}} | \mathcal{D}) = \mathbb{E}_{q(\boldsymbol{\theta} | \boldsymbol{\psi}_{\boldsymbol{\theta}})} [\log p(\boldsymbol{\theta}, \mathcal{D})] + \mathbb{H}(q(\boldsymbol{\theta} | \boldsymbol{\psi}_{\boldsymbol{\theta}}))\) (10.103)

We will assume the variational posterior factorizes over the parameters:

\(q(\boldsymbol{\theta} | \boldsymbol{\psi}_{\boldsymbol{\theta}}) = \prod_j q(\boldsymbol{\theta}_j | \boldsymbol{\psi}_{\theta_j})\) (10.104)

We can then update each \(\boldsymbol{\psi}_{\theta_j}\) using CAVI (Section 10.3.1).

### 10.3.4 Example: VB for a univariate Gaussian

Consider inferring the parameters of a 1d Gaussian. The likelihood is given by \(p(\mathcal{D} | \boldsymbol{\theta}) = \prod_{n=1}^N \mathcal{N}(x_n | \mu, \lambda^{-1})\), where \(\mu\) is the mean and \(\lambda\) is the precision. Suppose we use a conjugate prior of the form

\(p(\mu, \lambda) = \mathcal{N}(\mu | \mu_0, (\kappa_0 \lambda)^{-1}) \text{Ga}(\lambda | a_0, b_0)\) (10.105)

It is possible to derive the posterior \(p(\mu, \lambda | \mathcal{D})\) for this model exactly, as shown in Section 3.4.3.3.

However, here we use the VB method with the following factored approximate posterior:

\(q(\mu, \lambda) = q(\mu | \psi_\mu) q(\lambda | \psi_\lambda)\) (10.106)

We do not need to specify the forms for the distributions \(q(\mu | \psi_\mu)\) and \(q(\lambda | \psi_\lambda)\); the optimal forms will “fall out” automatically during the derivation (and conveniently, they turn out to be Gaussian and gamma respectively). Our presentation follows [Mac03, p. 429].
