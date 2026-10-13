
# Gibbs Distributions and Markov Random Fields

Following a path similar to that used for directed graphs, we will begin with the factorization properties of a distribution over an MRF and then move on to study conditional independencies. Let $x_1, \dots, x_l$ be a set of random variables that are grouped in $K$ groups, $\mathbf{x}_1, \dots, \mathbf{x}_K$; each random vector $\mathbf{x}_k, \quad k = 1, 2, \dots, K$ involves a subset of the random variables, $x_i, \quad i = 1, 2, \dots, l$.

## Definition 15.8

A distribution is called a **Gibbs** distribution if it can be factorized in terms of a set of potential functions $\psi_1, \dots, \psi_K$, such that

```
p(x_1, ..., x_l) = (1/Z) * ∏_{k=1}^K ψ_k(x_k)
```

The constant $Z$ is known as the **partition** function and it is the normalizing constant to guarantee that $p(x_1, ..., x_l)$ is a probability distribution. Hence,

```
Z = ∫ ... ∫ ∏_{k=1}^K ψ_k(x_k) dx_1, ..., dx_l
```

which becomes a summation for the case of probabilities.

Note that nobody can prohibit us from assigning conditional probability distributions as potential functions and making Eq. (15.20) look like Eq. (15.10); in this case, normalization is not explicitly required because each one of the conditional distributions is normalized. However, MRFs can deal with more general cases.

## Definition 15.9

We say that a Gibbs distribution $p$ factorizes over an MRF $H$ if **each** group of the variables $\mathbf{x}_k, \quad k = 1, 2, \dots, K$, involved in the $K$ factors of the distribution $p$ forms a **complete subgraph** of $H$. Every complete subgraph of an MRF is known as a **clique**, and the corresponding factors of the Gibbs distribution are known as **clique potentials**.
