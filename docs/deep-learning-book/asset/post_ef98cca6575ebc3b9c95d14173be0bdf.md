
In general, to model $n$ discrete variables each having $k$ values, the cost of the single table approach scales like $O(k^n)$, as we have observed before. Now suppose we build a directed graphical model over these variables. If $m$ is the maximum number of variables appearing (on either side of the conditioning bar) in a single conditional probability distribution, then the cost of the tables for the directed model scales like $O(k^m)$. As long as we can design a model such that $m \ll n$, we get very dramatic savings.

In other words, as long as each variable has few parents in the graph, the distribution can be represented with very few parameters. Some restrictions on the graph structure, such as requiring it to be a tree, can also guarantee that operations like computing marginal or conditional distributions over subsets of variables are efficient.

It is important to realize what kinds of information can and cannot be encoded in the graph. The graph encodes only simplifying assumptions about which variables are conditionally independent from each other. It is also possible to make other kinds of simplifying assumptions. For example, suppose we assume Bob always runs the same regardless of how Alice performs. (In reality, Alice’s performance probably influences Bob’s performance—depending on Bob’s personality, if Alice runs especially fast in a given race, this might encourage Bob to push hard and match her exceptional performance, or it might make him overconfident and lazy). Then the only effect Alice has on Bob’s finishing time is that we must add Alice’s finishing time to the total amount of time we think Bob needs to run. This observation allows us to define a model with $O(k)$ parameters instead of $O(k^2)$. However, note that $t_0$ and $t_1$ are still directly dependent with this assumption, because $t_1$ represents the absolute time at which Bob finishes, not the total time he spends running. This means our graph must still contain an arrow from $t_0$ to $t_1$. The assumption that Bob’s personal running time is independent from all other factors cannot be encoded in a graph over $t_0$, $t_1$, and $t_2$. Instead, we encode this information in the definition of the conditional distribution itself. The conditional distribution is no longer a $k \times k - 1$ element table indexed by $t_0$ and $t_1$ but is now a slightly more complicated formula using only $k - 1$ parameters. The directed graphical model syntax does not place any constraint on how we define our conditional distributions. It only defines which variables they are allowed to take in as arguments.

## 16.2.2 Undirected Models

Directed graphical models give us one language for describing structured probabilistic models. Another popular language is that of **undirected models**, otherwise

![](img/e7937519e1e39a29aca97c7de303ca30_580_0.png)

Figure 16.3: An undirected graph representing how your roommate's health h_r, your health h_y, and your work colleague's health h_c affect each other. You and your roommate might infect each other with a cold, and you and your work colleague might do the same, but assuming that your roommate and your colleague do not know each other, they can only infect each other indirectly via you.

defined on an undirected graph G. For each clique C in the graph,3 a factor φ(C) (also called a clique potential) measures the affinity of the variables in that clique for being in each of their possible joint states. The factors are constrained to be nonnegative. Together they define an unnormalized probability distribution

tilde{p}(x) = Π_{C∈G} φ(C). (16.3)

The unnormalized probability distribution is efficient to work with so long as all the cliques are small. It encodes the idea that states with higher affinity are more likely. However, unlike in a Bayesian network, there is little structure to the definition of the cliques, so there is nothing to guarantee that multiplying them together will yield a valid probability distribution. See figure 16.4 for an example of reading factorization information from an undirected graph.

Our example of the cold spreading between you, your roommate, and your colleague contains two cliques. One clique contains h_y and h_c. The factor for this clique can be defined by a table and might have values resembling these:

| | h_y = 0 | h_y = 1 |
|---|---|---|
| h_c = 0 | 2 | 1 |
| h_c = 1 | 1 | 10 |

A state of 1 indicates good health, while a state of 0 indicates poor health (having been infected with a cold). Both of you are usually healthy, so the corresponding state has the highest affinity. The state where only one of you is sick has the lowest affinity, because this is a rare state. The state where both of you are sick (because one of you has infected the other) is a higher affinity state, though still not as common as the state where both are healthy.

3 A clique of the graph is a subset of nodes that are all connected to each other by an edge of the graph.

![](img/e7937519e1e39a29aca97c7de303ca30_581_0.png)

Figure 16.4: This graph implies that $p(a, b, c, d, e, f)$ can be written as $\frac{1}{Z} \phi_{a,b}(a,b) \phi_{b,c}(b,c) \phi_{a,d}(a,d) \phi_{b,e}(b,e) \phi_{e,f}(e,f)$ for an appropriate choice of the $\phi$ functions.

To complete the model, we would need to also define a similar factor for the clique containing $h_y$ and $h_r$.

## 16.2.3 The Partition Function

While the unnormalized probability distribution is guaranteed to be nonnegative everywhere, it is not guaranteed to sum or integrate to 1. To obtain a valid probability distribution, we must use the corresponding normalized probability distribution⁴

$$p(\mathbf{x}) = \frac{1}{Z} \tilde{p}(\mathbf{x}), \tag{16.4}$$

where $Z$ is the value that results in the probability distribution summing or integrating to 1:

$$Z = \int \tilde{p}(\mathbf{x}) d\mathbf{x}. \tag{16.5}$$

You can think of $Z$ as a constant when the $\phi$ functions are held constant. Note that if the $\phi$ functions have parameters, then $Z$ is a function of those parameters. It is common in the literature to write $Z$ with its arguments omitted to save space. The normalizing constant $Z$ is known as the **partition function**, a term borrowed from statistical physics.

Since $Z$ is an integral or sum over all possible joint assignments of the state $\mathbf{x}$, it is often intractable to compute. To be able to obtain the normalized probability distribution of an undirected model, the model structure and the definitions of the $\phi$ functions must be conducive to computing $Z$ efficiently. In the context of deep learning, $Z$ is usually intractable. Because of the intractability of computing $Z$

⁴ A distribution defined by normalizing a product of clique potentials is also called a **Gibbs distribution**.

exactly, we must resort to approximations. Such approximate algorithms are the topic of chapter 18.

One important consideration to keep in mind when designing undirected models is that it is possible to specify the factors in such a way that Z does not exist. This happens if some of the variables in the model are continuous and the integral of \tilde{p} over their domain diverges. For example, suppose we want to model a single scalar variable x ∈ ℝ with a single clique potential φ(x) = x². In this case,

Z = ∫ x² dx. (16.6)

Since this integral diverges, there is no probability distribution corresponding to this choice of φ(x). Sometimes the choice of some parameter of the φ functions determines whether the probability distribution is defined. For example, for φ(x; β) = exp(−βx²), the β parameter determines whether Z exists. Positive β results in a Gaussian distribution over x, but all other values of β make φ impossible to normalize.

One key difference between directed modeling and undirected modeling is that directed models are defined directly in terms of probability distributions from the start, while undirected models are defined more loosely by φ functions that are then converted into probability distributions. This changes the intuitions one must develop to work with these models. One key idea to keep in mind while working with undirected models is that the domain of each of the variables has dramatic effect on the kind of probability distribution that a given set of φ functions corresponds to. For example, consider an n-dimensional vector valued random variable x and an undirected model parametrized by a vector of biases b. Suppose we have one clique for each element of x, φ⁽ⁱ⁾(xᵢ) = exp(bᵢxᵢ). What kind of probability distribution does this result in? The answer is that we do not have enough information, because we have not yet specified the domain of x. If x ∈ ℝⁿ, then the integral defining Z diverges, and no probability distribution exists. If x ∈ {0,1}ⁿ, then p(x) factorizes into n independent distributions, with p(xᵢ = 1) = sigmoid(bᵢ). If the domain of x is the set of elementary basis vectors ({[1,0,…,0], [0,1,…,0],…,[0,0,…,1]}), then p(x) = softmax(b), so a large value of bᵢ actually reduces p(xⱼ = 1) for j ≠ i. Often, it is possible to leverage the effect of a carefully chosen domain of a variable to obtain complicated behavior from a relatively simple set of φ functions. We explore a practical application of this idea in section 20.6.
