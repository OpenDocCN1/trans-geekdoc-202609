and let $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$ satisfy for all $\phi \in C(\mathbb{R}^d, \mathbb{R})$ that

```
$$\pmb{\mathfrak{L}}(\phi) = \frac{1}{M} \left[ \sum_{m=1}^{M} |\phi(\pmb{x}_m) - \pmb{y}_m|^2 \right].$$
```

As in the **introduction** we think of $M \in \mathbb{N}$ as the number of available known input-output data pairs, we think of $d \in \mathbb{N}$ as the dimension of the input data, we think of $\pmb{\mathfrak{L}}: \mathbb{R}^d \to \mathbb{R}$ as an unknown function which relates input and output data through **(5.1)**, we think of $\pmb{x}_1, \pmb{x}_2, \dots, \pmb{x}_{M+1} \in \mathbb{R}^d$ as the available known input data, we think of $\pmb{y}_1, \pmb{y}_2, \dots, \pmb{y}_M \in \mathbb{R}$ as the available known output data, and we have that the function $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$ in **(5.2)** is the objective function (the function we want to minimize) in the optimization problem associated to the considered learning problem (cf. **(3)** in the **introduction**). In particular, observe that

```
$$\pmb{\mathfrak{L}}(\pmb{\mathcal{E}}) = 0$$
```

and we are trying to approximate the function $\pmb{\mathcal{E}}$ by computing an approximate minimizer of the function $\pmb{\mathfrak{L}}: C(\mathbb{R}^d, \mathbb{R}) \to [0, \infty)$. In order to make this optimization problem amenable to numerical computations, we consider a spatially discretized version of the optimization problem associated to **(5.2)** by employing parametrizations of **ANNs** (cf. **(7)** in the **introduction**).

More formally, let $a: \mathbb{R} \to \mathbb{R}$ be differentiable, let $h \in \mathbb{N}$, $l_1, l_2, \dots, l_h, \mathfrak{d} \in \mathbb{N}$ satisfy $\mathfrak{d} = l_1(d+1) + \sum_{k=2}^h l_k(l_{k-1}+1) + l_h + 1$, and consider the parametrization function

```
$$\mathbb{R}^{\mathfrak{d}} \ni \theta \mapsto \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}} \in C(\mathbb{R}^d, \mathbb{R})$$
```

(cf. Definitions **1.1.3** and **1.2.1**). Note that $h$ is the number of hidden layers of the **ANNs** in **(5.4)**, note for every $i \in \{1, 2, \dots, h\}$ that $l_i \in \mathbb{N}$ is the number of neurons in the $i$-th hidden layer of the **ANNs** in **(5.4)**, and note that $\mathfrak{d}$ is the number of real parameters used to describe the **ANNs** in **(5.4)**. Observe that for every $\theta \in \mathbb{R}^{\mathfrak{d}}$ we have that the function

```
$$\mathbb{R}^d \ni \pmb{x} \mapsto \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}}(\pmb{x}) \in \mathbb{R}$$
```

in **(5.4)** is nothing else than the realization function associated to a *fully-connected feed-forward ANN* where before each hidden layer a multidimensional version of the activation function $a: \mathbb{R} \to \mathbb{R}$ is applied. We restrict ourselves in this section to a differentiable activation function as this differentiability property allows us to consider gradients (cf. **(5.7)**, **(5.8)**, and Section **5.3.2** below for details).

We now discretize the optimization problem in **(5.2)** as the problem of computing approximate minimizers of the function $\mathcal{L}: \mathbb{R}^{\mathfrak{d}} \to [0, \infty)$ which satisfies for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that

```
$$\mathcal{L}(\theta) = \frac{1}{M} \left[ \sum_{m=1}^{M} \left| \left( \mathcal{N}^{\pmb{a}, d}_{\pmb{m}_{a,l_1}, \pmb{m}_{a,l_2}, \dots, \pmb{m}_{a,l_h}, \mathrm{id}_{\mathbb{R}}} \right)(\pmb{x}_m) - \pmb{y}_m \right|^2 \right]$$
```