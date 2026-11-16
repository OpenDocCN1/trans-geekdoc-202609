
![](img/c73db5a1f734ebb7c0655f19e5bc9daa_89_0.png)

Figure 10.1: (a) A graph. (b-d) Some of its spanning trees. From Figure 7.1 of [WJ08]. Used with kind permission of Martin Wainwright.

This is a concave objective being maximized over a convex set, and hence has a unique optimum. Furthermore, the result is always an upper bound on log Z, because the entropy is an upper bound, and we are optimizing over a larger set than the marginal polytope.

It remains to specify the set of tractable submodels, F, and the distribution ρ. We discuss some options below.

### 10.1.5 Tree-reweighted belief propagation

In this section, we discuss tree reweighted BP [WJW05b; Kol06], which is a form of convex BP which uses spanning trees as the set of tractable models F, as we describe below.

### 10.1.5.1 Spanning tree polytope

It remains to specify the set of tractable submodels, F, and the distribution ρ. We will consider the case where F is all spanning trees of a graph. For any given tree, the entropy is given by Equation 10.12. To compute the upper bound, obtained by averaging over all trees, note that the terms \(\sum_F \rho(F)H(\mu(F)_s)\) for single nodes will just be H_s, since node s appears in every tree, and \(\sum_F \rho(F) = 1\). But the mutual information term I_st receives weight \(\rho_{st} = E_\rho [ I((s,t) \in E(T))]\), known as the **edge appearance probability**. Hence we have the following upper bound on the entropy:

```
\mathbb{H}(\boldsymbol{\mu}) \le \sum_{s \in V} H_s(\mu_s) - \sum_{(s,t) \in E} \rho_{st} I_{st}(\mu_{st}) \triangleq \mathbb{H}_{\text{TRBP}}(\boldsymbol{\mu}) \quad (10.34)
```

This is called the **tree reweighted BP** approximation [WJW05b; Kol06]. This is similar to the Bethe approximation to the entropy except for the crucial \(\rho_{st}\) weights. So long as \(\rho_{st} > 0\) for all edges (s,t), this gives a valid concave upper bound on the exact entropy.

The edge appearance probabilities live in a space called the **spanning tree polytope**. This is because they are constrained to arise from a distribution over trees. Figure 10.1 gives an example of a graph and three of its spanning trees. Suppose each tree has equal weight under \(\rho\). The edge f occurs in 1 of the 3 trees, so \(\rho_f = 1/3\). The edge e occurs in 2 of the 3 trees, so \(\rho_e = 2/3\). The edge b appears in all of the trees, so \(\rho_b = 1\). And so on. Ideally we can find a distribution \(\rho\), or equivalently edge probabilities in the spanning tree polytope, that make the above bound as tight as possible. An algorithm to do this is described in [WJW05a]. A simpler approach is to use all single edges with weight \(\rho_e = 1/E\).

What about the set we are optimizing over? We require \(\boldsymbol{\mu}(T) \in \mathbb{M}(T)\) for each tree T, which means enforcing normalization and local consistency. Since we have to do this for every tree, we are enforcing normalization and local consistency on every edge. Thus we are effectively optimizing in the pseudo-marginal polytope \(\mathbb{L}(G)\). So our final optimization problem as follows:

```
\max_{\boldsymbol{\tau} \in \mathbb{L}(G)} \boldsymbol{\tau}^T \boldsymbol{\theta} + \mathbb{H}_{\text{TRBP}}(\boldsymbol{\tau}) \ge \log Z \quad (10.35)
```

### 10.1.5.2 Message passing implementation

The simplest way to minimize Equation (10.35) is a modification of belief propagation known as **tree reweighted belief propagation**. The message from \(t\) to \(s\) is now a function of all messages sent from other neighbors \(v\) to \(t\), as before, but now it is also a function of the message sent from \(s\) to \(t\). Specifically, we have the following [WJ08, Sec 7.2.1]:

\(m_{t \to s}(x_s) \propto \sum_{x_t} \exp \left( \frac{1}{\rho_{st}} \theta_{st}(x_s, x_t) + \theta_t(x_t) \right) \frac{\prod_{v \in \text{nbr}(t) \setminus s} [m_{v \to t}(x_t)]^{\rho_{vt}}}{[m_{s \to t}(x_t)]^{1 - \rho_{st}}}\)

At convergence, the node and edge pseudo marginals are given by

\(\tau_s(x_s) \propto \exp(\theta_s(x_s)) \prod_{v \in \text{nbr}(s)} [m_{v \to s}(x_s)]^{\rho_{vs}}\)

\(\tau_{st}(x_s, x_t) \propto \varphi_{st}(x_s, x_t) \frac{\prod_{v \in \text{nbr}(s) \setminus t} [m_{v \to s}(x_s)]^{\rho_{vs}}}{[m_{t \to s}(x_s)]^{1 - \rho_{st}}} \frac{\prod_{v \in \text{nbr}(t) \setminus s} [m_{v \to t}(x_t)]^{\rho_{vt}}}{[m_{s \to t}(x_t)]^{1 - \rho_{st}}}\)

\(\varphi_{st}(x_s, x_t) \triangleq \exp \left( \frac{1}{\rho_{st}} \theta_{st}(x_s, x_t) + \theta_s(x_s) + \theta_t(x_t) \right)\)

If \(\rho_{st} = 1\) for all edges \((s, t) \in E\), the algorithm reduces to the standard LBP algorithm. However, the condition \(\rho_{st} = 1\) implies every edge is present in every spanning tree with probability 1, which is only possible if the original graph is a tree. Hence the method is only equivalent to standard LBP on trees, when the method is of course exact.

In general, this message passing scheme is not guaranteed to converge to the unique global optimum. One can devise double-loop methods that are guaranteed to converge [HS08], but in practice, using damped updates as in Equation ?? is often sufficient to ensure convergence.

### 10.1.5.3 Max-product version

We can modify TRBP to solve the MAP estimation problem (as opposed to estimating posterior marginals) by replacing sums with products in Equation (10.36) (see [WJ08, Sec 8.4.3] for details). This is guaranteed to converge to the LP relaxation discussed in Section 9.1.3 under a suitable scheduling known as **sequential tree-reweighted message passing** [Kol06].

### 10.1.6 Other tractable versions of convex BP

It is possible to upper bound the entropy using convex combinations of other kinds of tractable models besides trees. One example is a **planar MRF** (one where the graph has no edges that cross), with binary nodes and no external field, i.e., the model has the form \(p(\mathbf{x}) \propto \exp(\sum_{(s,t) \in E} \theta_{st} x_s x_t)\). It turns out that it is possible to perform exact inference in this model. Hence one can use convex combinations of such graphs which can sometimes yield more accurate results than TRBP, albeit at higher computational cost. See [GJ07] for details, and [Sch10b] for a related *exact* method for planar Ising models.

## Chapter 11

## Monte Carlo Inference

## Chapter 12

## Markov Chain Monte Carlo (MCMC) inference

## Chapter 13

## Sequential Monte Carlo (SMC) inference

## Part III

## Prediction

## Chapter 14

## Discriminative models: an overview

## Chapter 15

## Generalized linear models

### 15.1 Variational inference for logistic regression

In this section we discuss a variational approach to Bayesian inference for logistic regression models based on local bounds to the likelihood. We will use a Gaussian prior, \( p(w) = \mathcal{N}(w|\mu_0, V_0) \). We will create a “Gaussian-like” lower bound to the likelihood, which becomes conjugate to this prior. We then iteratively improve this lower bound.

### 15.1.1 Binary logistic regression

In this section, we discuss VI for binary logistic regression. Our presentation follows [Bis06, Sec 10.6].

Let us first rewrite the likelihood for a single observation as follows:

```
\(\begin{aligned} p(y_n|x_n, w) &= \sigma(\eta_n)^{y_n}(1 - \sigma(\eta_n))^{1-y_n} \tag{15.1} \\ &= \left( \frac{1}{1+e^{-\eta_n}} \right)^{y_n} \left( 1 - \frac{1}{1+e^{-\eta_n}} \right)^{1-y_n} \tag{15.2} \\ &= e^{-\eta_n y_n} \frac{e^{-\eta_n}}{1 + e^{-\eta_n}} = e^{-\eta_n y_n} \sigma(-\eta_n) \tag{15.3} \end{aligned}\)
```

where \(\eta_n = w^T x_n\) are the logits. This is not conjugate to the Gaussian prior. So we will use the following “Gaussian-like” variational lower bound to the sigmoid function, proposed in [JJ96; JJ00]:

```
\(\sigma(\eta_n) \ge \sigma(\psi_n) \exp [(\eta_n - \psi_n)/2 - \lambda(\psi_n)(\eta_n^2 - \psi_n^2)] \tag{15.4}\)
```

where \(\psi_n\) is the variational parameter for datapoint \(n\), and

```
\(\lambda(\psi) \triangleq \frac{1}{4\psi} \tanh(\psi/2) = \frac{1}{2\psi} \left[ \sigma(\psi) - \frac{1}{2} \right] \tag{15.5}\)
```

We shall refer to this as the JJ bound, after its inventors, Jaakkola and Jordan. See Figure 15.1(a) for a plot, and see Section 6.5.4.2 for a derivation.

Using this bound, we can write

```
\(p(y_n|x_n, w) = e^{-\eta_n y_n} \sigma(-\eta_n) \ge e^{-\eta_n y_n} \sigma(\psi_n) \exp [(-\eta_n + \psi_n)/2 - \lambda(\psi_n)(\eta_n^2 - \psi_n^2)] \tag{15.6}\)
```

We can now lower bound the log joint as follows:

```
\(\begin{aligned} \log p(y|X, w) + \log p(w) \ge {} &-\frac{1}{2}(w - \mu_0)^T V_0^{-1}(w - \mu_0) \tag{15.7} \\ &+ \sum_{n=1}^N [\eta_n(y_n - 1/2) - \lambda(\psi_n)w^T(x_n x_n^T)w] \tag{15.8} \end{aligned}\)
