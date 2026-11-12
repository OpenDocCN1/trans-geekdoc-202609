The ease with which a CNF formula $\psi$ is understood decreases when variables are present in multiple clauses. Therefore, while considering the aggregated entropy for each clause $\mathcal{C}$ within $\psi$, we also consider the aggregate of its neighbouring clauses, i.e., the clauses $\mathcal{C}'$ with whom $\mathcal{C}$ shares variables.

# **Definition 3 (Aggregated entropy of a CNF).** The aggregated entropy $DL(\psi)$ of a CNF formula $\psi$ is

```
$$DL(\psi) = \sum_{C \in \psi} \left[ DL_{cl}(\mathcal{C}) + \sum_{C' \in \psi | e(\mathcal{C}, C') \in G_d(\psi)} DL_{cl}(C') \right], \tag{7}$$
```

with $e(\mathcal{C}, C') \in G_d(\psi)$ denoting the clause neighbour relationships through the dual graph defined in Sect. 2.

# **Example of Aggregated Entropy.** Given formula $\psi$ over categorical variables $\{A, B, X\}$ with $|A| = 5$, $|B| = 6$, and $|X| = 7$.

```
$$\psi = \underbrace{(a_1 \vee a_2 \vee a_3)}_{\mathcal{C}_1} \wedge \underbrace{(a_1 \vee b_1 \vee b_2)}_{\mathcal{C}_2} \wedge \underbrace{(x_1 \vee x_2 \vee x_3)}_{\mathcal{C}_3}$$
```

We compute $DL(\psi)$ using the following clause entropies:

```
$$\begin{aligned} DL_{cl}(\mathcal{C}_1) &= \phi(\frac{3}{5}) + \phi(\frac{2}{5}), \\ DL_{cl}(\mathcal{C}_2) &= \phi(\frac{1}{5}) + \phi(\frac{4}{5}) + \phi(\frac{2}{6}) + \phi(\frac{4}{6}) \\ DL_{cl}(\mathcal{C}_3) &= \phi(\frac{3}{7}) + \phi(\frac{4}{7}) \end{aligned}$$
```

with $\phi(\alpha) = -\alpha log_2(\alpha)$. Clauses $\mathcal{C}_1$ and $\mathcal{C}_2$ both mention categorical variable $A$, resulting in an edge $e(\mathcal{C}_1, \mathcal{C}_2)$ in the dual graph of $\psi$. This results in $DL(\psi) = \underbrace{DL_{cl}(\mathcal{C}_1) + DL_{cl}(\mathcal{C}_2) + DL_{cl}(\mathcal{C}_3)}_{\text{clause entropies}} + \underbrace{DL_{cl}(\mathcal{C}_2)}_{e(\mathcal{C}_1, \mathcal{C}_2)} + \underbrace{DL_{cl}(\mathcal{C}_1)}_{e(\mathcal{C}_2, \mathcal{C}_1)} \approx 6.21$

In the rest of this paper we minimise $DL(\psi)$ to obtain more preferred CNF formulas $\psi$.

# ## 4.3 User Study

To evaluate whether our newly proposed description length better captures human interpretability compared to using the number of literals, we conducted a user study. Participants (N = 46) were asked to answer 12 questions. In each question, they were given i) a playlist description in the form of a CNF formula, and ii) a set of songs, each represented as a list of categorical attributes, after which they were asked to select all songs that were covered by the playlist.

We posit that descriptions that are less interpretable, lead to a longer response time.

Furthermore, a description length should align with this, similarly assigning a higher length. Therefore, we compare the aggregated entropy and the classic