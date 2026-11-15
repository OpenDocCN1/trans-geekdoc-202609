# 5.5 Generalizing the algorithm design

In this section, we examine the effectiveness of Algorithm 1 under conditions of limited transmission delays.

# 5.5.1 Bounded communication delays

Consider that nodes in the network may encounter communication delays which are arbitrary but uniformly bounded during the reception of information sent by its in-neighbors. To elaborate, let us denote \(\vartheta_{ij}, (j, i) \in \mathcal{E}\), as a previously unknown delay incurred when information is relayed from node \(j\) to node \(i\). Subsequently, we postulate the following assumptions concerning these communication delays.

**Assumption 5.3.** The delays in communication, denoted as \(\vartheta_{ij}\), are consistently limited across all pairs \((j, i)\) belonging to the set \(\mathcal{E}\). This means that there exists a positive integer \(\vartheta\) such that

```
0 \leq \vartheta_{ij} \leq \vartheta, \forall (j, i) \in \mathcal{E} .
```

Furthermore, every node has its own variable without any delay, implying that \(\vartheta_{ii}\) equals zero for all \(i\) belonging to the set \(\mathcal{V}\).

**Remark 5.7.** Actually, it is not an unrealistic presumption, as supported by references [50,51], to postulate that the communication delays encountered in every connection are not fixed constants but are consistently limited. Moreover, to accommodate varying (yet bounded) delays in the connection at different times, we can utilize time stamping to store information up to the maximum constant delay in the worst-case scenario (that is, transforming fluctuating delays into constants for easier processing), as outlined in [52]. This simplifies the analytical process.

It is important to observe that the updates of \(y_{i,k}\) and \(z_{i,k}\) in Algorithm 1 depend on data from the incoming neighbors of each node \(i\) belonging to the set \(\mathcal{V}\). Conversely, the updates of \(x_{i,k}\) do not necessitate any additional information exchange and are executed solely within the local environment. Therefore in the presence of communication delays, the updates of \(y_{i,k}\) and \(z_{i,k}\) in Algorithm 1 undergo

```
\(z_{i,k+1} = \sum_{j=1}^n A_{ij} \bar{z}_{j,k-\vartheta_{ij}} + \frac{g_{i,k}}{y_{i,k}},\)

\(y_{i,k+1} = \sum_{j=1}^n A_{ij} y_{j,k-\vartheta_{ij}}.\) (5.38)
```

The simplified representation of Algorithm 1, incorporating communication delays, is presented in Algorithm 2.