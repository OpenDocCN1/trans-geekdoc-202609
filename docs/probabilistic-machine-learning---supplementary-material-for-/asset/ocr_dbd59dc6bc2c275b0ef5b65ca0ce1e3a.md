![](bbox=[0.206, 0.086, 0.792, 0.413])

Figure 31.7: A locally optimal DAG learned from the 20-Newsgroup data. From Figure 4.10 of [Sch10a]. Used with kind permission of Mark Schmidt.

# 31.2.4.3 Scaling up to larger graphs

The main challenge in computing the posterior over DAGs is that there are so many possible graphs. More precisely, [Rob73] showed that the number of DAGs on D nodes satisfies the following recurrence:

```
$$f(D) = \sum_{i=1}^D (-1)^{i+1} \binom{D}{i} 2^{i(D-i)} f(D-i) \quad (31.29)$$
```

for D > 2. The base case is f(1) = 1. Solving this recurrence yields the following sequence: 1, 3, 25, 543, 29281, 3781503, etc.1

Indeed, the general problem of finding the globally optimal MAP DAG is provably NP-complete [Chi96]. In view of the enormous size of the hypothesis space, we are generally forced to use approximate methods, some of which we review below.

# 31.2.4.4 Hill climbing methods for approximating the mode

A common way to find an approximate MAP graph structure is to use a greedy hill climbing method. At each step, the algorithm proposes small changes to the current graph, such as adding, deleting or reversing a single edge; it then moves to the neighboring graph which most increases the posterior. The method stops when it reaches a local maximum. It is important that the method only proposes local changes to the graph, since this enables the change in marginal likelihood (and hence the posterior) to be computed in constant time (assuming we cache the sufficient statistics). This is because all but one or two of the terms in Equation (31.23) will cancel out when computing the log Bayes factor $\delta(G \rightarrow G') = \log p(G'|D) - \log p(G|D)$.

We can initialize the search from the best tree, which can be found using exact methods discussed in Section 31.1.2. For speed, we can restrict the search so it only adds edges which are part of the Markov

1 A longer list of values can be found at http://www.research.att.com/~njas/sequences/A003024. Interestingly, the number of DAGs is equal to the number of (0,1) matrices all of whose eigenvalues are positive real numbers [McK+04].