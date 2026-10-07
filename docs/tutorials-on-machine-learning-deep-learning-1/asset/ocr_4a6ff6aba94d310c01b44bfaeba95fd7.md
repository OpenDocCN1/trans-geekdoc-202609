# An Introduction to Restricted Boltzmann Machines 23

Gibbs sampler to the stationary distribution of the MRF is bounded by the following inequality (see for [6]):

```
$|\mu^K - \pi| \leq \frac{1}{2}|\mu - \pi(1 - e^{-N\Delta})|^k, \quad (19)$
```

where $\Delta = \sup_{v \in V} \delta_v$ and $\delta_i = \sup|\delta(x) - y|; x_i = y_i; v \in V$ with $i \neq l$. Here $\mu$ is an arbitrary starting distribution and $\frac{1}{2}|\mu - \pi|$ is the distance in variation defined in (15).

# 4 Restricted Boltzmann Machines

A RBM (also denoted as Harmonium) is an MRF associated with a bipartite undirected graph as shown in Fig. 1. It consists of $m$ visible units $\mathbf{V} = (v_1, ..., v_m)$ to represent observable data and $n$ hidden units $\mathbf{H} = (h_1, ..., h_n)$ to capture dependencies between observed variables. In binary RBMs, in this tutorial, the variables $(\mathbf{V}, \mathbf{H})$ take values in $\{0,1\}^{m+n}$ and the joint probability distribution over the model is given by the Gibbs distribution $p(\mathbf{v}, \mathbf{h}) \propto e^{-E(\mathbf{v, h)}}$ with the energy function

```
$E(\mathbf{v}, \mathbf{h}) = -\sum_{i=1}^m\sum_{j=1}^n w_{ij}v_ih_j - \sum_{j=1}^m b_jv_j - \sum_{i=1}^n c_ih_i. \quad (20)$
```

For all $i \in \{1,...,n\}$ and $j \in \{1,...,m\}$, $w_{ij}$ is a real valued weight associated with the edge between units $v_j$ and $h_i$, and $b_j$ and $c_i$ are real valued bias terms associated with the $j$th visible variable and the $i$th hidden variable, respectively.

![](bbox=[0.335, 0.563, 0.663, 0.703])

Fig. 1. The undirected graph of an RBM with $n$ hidden and $m$ visible variables

The graph of an RBM has only connections between the layer of hidden and visible variables but not between two variables of the same. In terms of probability this means that the hidden variables are independent given the state of the visible variables and vice versa: