
We have seen a number of definitions and theorems referring to the notion of conditional independence in graphs and probability distributions. Before we proceed further, it will be instructive to summarize what has been said and provide some definitions that will dress up our findings in a more formal language. This will prove useful for subsequent generalizations.

We have seen that a BN is a DAG that encodes a number of conditional independencies. Some of them are local ones, defined by the parent–child links, and some of them are of a more global nature and are the result of `d`-separations. Given a DAG, `G`, we denote as `I(G)` the set of all independencies that correspond to `d`-separations. Also, let `p` be a probability distribution over a set of random variables, `x[1], …, x[l]`. We denote as `I(p)` the set of all independence assertions of the type `x[i] ⊥ x[j] | Z` that hold true for the distribution `p`.

Let `G` be a DAG and `p` a distribution that factorizes over `G`; in other words, it satisfies the local independencies as suggested by `G`. Then we have seen (Theorem 15.3) that

```
I(G) ⊆ I(p).
```

We say that `G` is an `I-map` (independence map) for `p`. This property is sometimes referred to as *soundness*.

### Definition 15.6

A distribution `p` is *faithful* to a graph `G` if *any* independence in `p` is reflected in the `d`-separation properties of the graph.

In other words, the graph can represent all (and only) the conditional independence properties of the distribution. In such a case we write `I(p) = I(G)`. If equality is valid, we say that the graph `G` is a *perfect* map for `p`. If this were true for any `p`, the graph would be called *complete*. Unfortunately, this is *not* valid for any distribution, `p`, that factorizes over `G`. However, for most practical purposes, `I(G) = I(P)`, which is true for *almost all* distributions that factorize over `G`.

Although `I(p) = I(G)` is not valid for all distributions that factorize over `G`, the following two properties are always valid for any BN structure (e.g., [25]):

*   If `x ⊥ y | Z` for *all* distributions `p` that factorize over `G`, then `x` and `y` are `d`-separated given `Z`.
*   If `x` and `y` are `d`-connected given `Z`, then there will be some distribution that factorizes over `G` where `x` and `y` are *dependent*.

A final definition concerns minimality.

### Definition 15.7

A graph `G` is said to be a *minimal* I-map for a set of independencies if the removal of any of its edges renders it *not* to be an I-map.

Note that a minimal I-map is not necessarily a perfect map. In the same way that there exist algorithms to find the set of `d`-separations, there exist algorithms to find perfect and minimal I-maps for a distribution (e.g., [25]).

## 15.4 Undirected graphical models
