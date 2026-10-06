# 7.3 PROOF FOR MVT

Lemma 6 can be easily derived based on Theorem 22 by considering $y$ as a fixed prompt.

THEOREM 23. Assume that the above assumptions holds, as $n ightarrow \infty$, when achieving the largest prediction probability of $z$ given prompt under concept $\phi^*$, the corresponding class description $y$ follows the same $y$ obtained from the prompt distribution:

```
$$\arg_y p(z|S_n, x_q, y, \phi^*) \rightarrow \arg_y p_{prompt}(z|x_q, y)$ $$ (7.56)
```

PROOF. Since we already have Theorem 22, if we can prove that

```
$$\arg_y p(y|S_n, x_q, \phi^*) = \arg_y p(z|S_n, x_q, y, \phi^*)$ $$ (7.57)
```

```
$$\arg_y p_{prompt}(y|x_q) = \arg_y p_{prompt}(z|x_q, y)$ $$ (7.58)
```

then we can complete the justification.

```
$$\p(z|S_n, x_q, \phi^*) = \sum_{h^{start} \in \mathcal{H}} p(z|h_q^{start})p(h^{start}|S_n, x_q, y, \phi^*)$ $$ (7.59)
```

By expanding the last term, we have:

where ($h^{start}$) is considered as a constant. Moreover, based on Assumption 21, the joint distribution $p(x_q, y)$ is predefined by the pretraining distribution, which does not affect the marginal distribution of $z$, thus we can have

```
$$\p(x_q, y|h_q^{start}, S_n, \phi^*) = \frac{p(y|S_n, x_q, h_q^{start}, \phi^*)p(x_q|h_q^{start})}{p(x_q, y)}$ $$ (7.62)
```