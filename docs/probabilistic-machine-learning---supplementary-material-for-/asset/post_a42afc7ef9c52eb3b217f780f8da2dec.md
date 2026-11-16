
![](img/c73db5a1f734ebb7c0655f19e5bc9daa_165_0.png)

Figure 31.6: The two most probable DAGs learned from the Sewell-Shah data. From [HMC97]. Used with kind permission of David Heckerman

### 31.2.3.5 Marginal likelihood for non-tabular CPDs

If all CPDs are linear Gaussian, we can replace the Dirichlet-multinomial model with the normal-gamma model, and thus derive a different exact expression for the marginal likelihood. See [GH94] for the details. In fact, we can easily combine discrete nodes and Gaussian nodes, as long as the discrete nodes always have discrete parents; this is called a conditional Gaussian DAG. Again, we can compute the marginal likelihood in closed form. See [BD03] for the details.

In the general case (i.e., everything except Gaussians and CPTs), we need to approximate the marginal likelihood. The simplest approach is to use the BIC approximation, which has the form

$$
\sum_t \log p(\mathcal{D}_t | \hat{\theta}_t) - \frac{K_t C_t}{2} \log N \quad (31.28)
$$

## 31.2.4 Bayesian model selection: algorithms

In this section, we discuss some algorithms for approximately computing the mode of (or samples from) the posterior p(G|D).

### 31.2.4.1 The K2 algorithm for known node orderings

Suppose we know a total ordering of the nodes. Then we can compute the distribution over parents for each node independently, without the risk of introducing any directed cycles: we simply enumerate over all possible subsets of ancestors and compute their marginal likelihoods. If we just return the best set of parents for each node, we get the K2 algorithm [CH92]. In this case, we can find the best set of parents for each node using l1-regularization, as shown in [SNMM07].

### 31.2.4.2 Dynamic programming algorithms

In general, the ordering of the nodes is not known, so the posterior does not decompose. Nevertheless, we can use dynamic programming to find the globally optimal MAP DAG (up to Markov equivalence), as shown in [KS04; SM06].

If our goal is knowledge discovery, the MAP DAG can be misleading, for reasons we discussed in ??. A better approach is to compute the marginal probability that each edge is present, p(G_st = 1|D). We can also compute these quantities using dynamic programming, as shown in [Koi06; PK11].

Unfortunately, all of these methods take V2^V time in the general case, making them intractable for graphs with more than about 16 nodes.

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_166_0.png)

Figure 31.7: A locally optimal DAG learned from the 20-Newsgroup data. From Figure 4.10 of [Sch10a]. Used with kind permission of Mark Schmidt.

### 31.2.4.3 Scaling up to larger graphs

The main challenge in computing the posterior over DAGs is that there are so many possible graphs. More precisely, [Rob73] showed that the number of DAGs on D nodes satisfies the following recurrence:

$$
f(D) = \sum_{i=1}^D (-1)^{i+1} \binom{D}{i} 2^{i(D-i)} f(D-i) \quad (31.29)
$$

for D > 2. The base case is f(1) = 1. Solving this recurrence yields the following sequence: 1, 3, 25, 543, 29281, 3781503, etc.1

1 A longer list of values can be found at http://www.research.att.com/~njas/sequences/A003024. Interestingly, the number of DAGs is equal to the number of (0,1) matrices all of whose eigenvalues are positive real numbers [McK+04].

Indeed, the general problem of finding the globally optimal MAP DAG is provably NP-complete [Chi96]. In view of the enormous size of the hypothesis space, we are generally forced to use approximate methods, some of which we review below.

### 31.2.4.4 Hill climbing methods for approximating the mode

A common way to find an approximate MAP graph structure is to use a greedy hill climbing method. At each step, the algorithm proposes small changes to the current graph, such as adding, deleting or reversing a single edge; it then moves to the neighboring graph which most increases the posterior. The method stops when it reaches a local maximum. It is important that the method only proposes local changes to the graph, since this enables the change in marginal likelihood (and hence the posterior) to be computed in constant time (assuming we cache the sufficient statistics). This is because all but one or two of the terms in Equation (31.23) will cancel out when computing the log Bayes factor $\delta(G \rightarrow G') = \log p(G'|D) - \log p(G|D)$.

We can initialize the search from the best tree, which can be found using exact methods discussed in Section 31.1.2. For speed, we can restrict the search so it only adds edges which are part of the Markov blankets estimated from a dependency network [Sch10a]. Figure 31.7 gives an example of a DAG learned in this way from the 20-newsgroup data. For binary data, it is possible to use techniques from frequent itemset mining to find good Markov blanket candidates, as described in [GM04].

We can use techniques such as multiple random restarts to increase the chance of finding a good local maximum. We can also use more sophisticated local search methods, such as genetic algorithms or simulated annealing, for structure learning. (See also Section 31.2.6 for gradient based techniques based on continuous relaxations.)

It is also possible to perform the greedy search in the space of PDAGs instead of in the space of DAGs; this is known as the **greedy equivalence search** method [Chi02]. Although each step is somewhat more complicated, the advantage is that the search space is smaller.

### 31.2.4.5 Sampling methods

If our goal is knowledge discovery, the MAP DAG can be misleading, for reasons we discussed in **??**. A better approach is to compute the probability that each edge is present, \(p(G_{st}=1|\mathcal{D})\). We can do this exactly using dynamic programming [Koi06; PK11], although this can be expensive. An approximate method is to sample DAGs from the posterior, and then to compute the fraction of times there is an \(s \rightarrow t\) edge or path for each \((s,t)\) pair. The standard way to draw samples is to use the Metropolis Hastings algorithm (**??**), where we use the same local proposal as we did in greedy search [MR94].

A faster-mixing method is to use a collapsed MH sampler, as suggested in [FK03]. This exploits the fact that, if a total ordering of the nodes is known, we can select the parents for each node independently, without worrying about cycles, as discussed in Section 31.2.4.1. By summing over all possible choice of parents, we can marginalize out this part of the problem, and just sample total orders. [EW08] also use order-space (collapsed) MCMC, but this time with a parallel tempering MCMC algorithm.

## 31.2.5 Constraint-based approach

We now present an approach to learning a DAG structure — up to Markov equivalence (the output of the method is a PDAG) — that uses local conditional independence tests, rather than scoring models globally with a likelihood. The CI tests are combined together to infer the global graph structure, so this approach is called **constraint-based**. The advantage of CI testing is that it is more local and does not require specifying a complete model. (However, the form of the CI test implicitly relies on assumptions, see e.g., [SP18].)

### 31.2.5.1 IC algorithm

The original algorithm, due to Verma and Pearl [VP90], was called the **IC algorithm**, which stands for “inductive causation”. The method is as follows [Pea09, p50]:

- 1. For each pair of variables \(a\) and \(b\), search for a set \(S_{ab}\) such that \(a \perp b | S_{ab}\). Construct an undirected graph such that \(a\) and \(b\) are connected iff no such set \(S_{ab}\) can be found (i.e., they cannot be made conditionally independent).

- 2. Orient the edges involved in v-structures as follows: for each pair of nonadjacent nodes \(a\) and \(b\) with a common neighbor \(c\), check if \(c \in S_{ab}\); if it is, the corresponding DAG must be \(a \rightarrow c \leftarrow b\), \(a \leftarrow c \rightarrow b\) or \(a \leftarrow c \leftarrow b\), so we cannot determine the direction; if it is not, the DAG must be \(a \rightarrow c \leftarrow b\), so add these arrows to the graph.

- 3. In the partially directed graph that results, orient as many of the undirected edges as possible, subject to two conditions: (1) the orientation should not create a new v-structure (since that would have been detected already if it existed), and (2) the orientation should not create a directed cycle. More precisely, follow the rules shown in Figure 31.8. In the first case, if \(X \rightarrow Y\) has a known orientation, but \(Y - Z\) is unknown, then we must have \(Y \rightarrow Z\), otherwise we would have created a new v-structure \(X \rightarrow Y \leftarrow Z\), which is not allowed. The other two cases follow similar reasoning.
