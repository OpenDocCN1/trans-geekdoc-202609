previous vector: \(\vec{v}_k \rightarrow \vec{v}_{k-1} \rightarrow \dots \dots \rightarrow \vec{v}_1\). Different choices of \(f(\cdot)\) yield different sequences for the same \(\vec{v}_k\). We call the sequence \(\{\vec{v}_1, ..., \vec{v}_k\}\) a *generated RWT*.

A generated RWT will only be realistic for special choices of \(\vec{v}_k\). In particular, we want \(\vec{v}_k\) to be the ending vector for some graph from the same family as the graphs in \(\mathcal{G}\). Formally, we want \(\vec{v}_k = \bar{L}^k \vec{v}_1\), where \(\bar{L}\) is the smoothed normalized adjacency of such a graph. But we do not know \(\vec{v}_1\) or \(\bar{L}\). The following theorem shows how to select \(\vec{v}_k\).

**Theorem 1.** Consider an *n*-node graph with degrees \(\{d_i\}\), smoothed degrees \(\{d'_i\}\), starting vector \(\boldsymbol{v} \in \mathbb{R}^n_+\) built using a function \(f(d_i)\), and smoothed normalized adjacency *L*, as in Definition 1. Let \(\boldsymbol{w}\) be a vector with entries

```
\(\boldsymbol{w}_i := \gamma \cdot \sqrt{d'_i}\)
```

```
\(\text{where } \gamma = \frac{n \left( \sum_j f(d_j) \sqrt{d'_j} \right)}{\left( \sum_j f(d_j) \right) \left( \sum_j d'_j \right)}.\)
```

Then, we have:

```
\(\lim_{k \to \infty} \| L^k \boldsymbol{v} - \boldsymbol{w} \| = 0.\)
```

*Proof.* From Lemma 1 in the Appendix, the largest eigenvalue of *L* is 1 with eigenvector \(\boldsymbol{u}_1\) having components \(u_{1;i} = \sqrt{d'_i} / (\sum_j d'_j)\). The matrix *L* is irreducible (since the graph is connected) and aperiodic (since \(\alpha > 0\) induces self-loops). Hence, no other eigenvalue has absolute value 1. Next, we observe that \(\boldsymbol{v}^T \boldsymbol{u}_1 > 0\), since both \(\boldsymbol{v}\) and \(\boldsymbol{u}_1\) are in the positive orthant. Hence, \(L^k \boldsymbol{v}\) tends to the vector \((\boldsymbol{v}^T \boldsymbol{u}_1) \boldsymbol{u}_1\), which is seen to be the vector \(\boldsymbol{w}\).

Theorem 1 shows that a realistic ending vector \(\bar{\boldsymbol{v}}_k\) must be close to \(\boldsymbol{w}\), and \(\boldsymbol{w}\) only depends on the degrees \(\{d_i\}\). So, to construct \(\bar{\boldsymbol{v}}_k\), we must generate a realistic degree distribution that matches the family \(\mathcal{G}\). One approach is to sample a graph \(G \in \mathcal{G}\) and perturb its degree distribution. Another option is to fit a model to the degree distributions of the graphs in \(\mathcal{G}\). For example, we can fit a power law or a lognormal since they are widely observed in real-world data. Then, we can sample a new degree distribution from this fitted model. Either way, we get a realistic degree distribution \(\{d_i\}\).

Now, we generate an RWT as follows. Using \(\{d_i\}\) and a choice of \(f \in \mathcal{F}\), we construct the ending vector \(\bar{\boldsymbol{v}}_k\) (Theorem 1). Next, we use the reverse predictor *P* from Sect. 2.1 to predict \(\bar{\boldsymbol{v}}_{k-1} := P(\bar{\boldsymbol{v}}_k)\), \(\bar{\boldsymbol{v}}_{k-2} := P(\bar{\boldsymbol{v}}_{k-1})\), and so on. Proceeding this way, we construct all the vectors \(\{\bar{\boldsymbol{v}}_1, ..., \bar{\boldsymbol{v}}_k\}\). This sequence of vectors is the *generated RWT*.

By repeating these steps with the same \(\bar{\boldsymbol{v}}_k\) but different \(f \in \mathcal{F}\), we can generate several RWTs. We must now construct the sparse graph corresponding to the generated RWTs. The following section shows how.