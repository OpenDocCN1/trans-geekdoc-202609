# 5.2 Variable Order Structure

have

```
$A \prec_{s,K} B \Longleftrightarrow \max \left\{ \sup_{b\in B\ a\in A} \psi(a-b, a), \sup_{a\in A\ b\in B} \psi(a-b, b) \right\ \leq 0$
```

if the arising terms exist.

It is obvious that these terms exist if the linear space $Y$ is normed, the sets $A$ and $B$ are weakly compact, and the functional $\psi$ is weakly lower semicontinuous (compare [72, Theorem 2.3]).

We investigate set optimization problems with a variable order structure. Based on the set less variable order relation in a real linear space $Y$, we consider a family $\mathcal{F}$ of nonempty subsets of $Y$, and we investigate minimal sets of $\mathcal{F}$ in a similar way as in Definition 5.2.

**Definition 5.4** Assumption 2.2 let $\mathcal{F}$ be a family of nonempty subsets of $Y$. A set $\tilde{A} \in \mathcal{F}$ is called a *minimal set* of $\mathcal{F}$ iff

```
$A \prec_{s,K} \tilde{A}, \\tilde{A} \in \mathcal{F} \Longimplies \tildetilde{A} \prec_{s,K} A$.
```

Minimal sets can be characterized using the equivalence in Proposition 5.6.

**Theorem 5.1** [[74, Theorem 5.1]] Let Assumption 2.2 be satisfied, and let $\psi$ be a $-K$convex representing functional. Then we have

$\tilde{A} \in \mathcal{F}$ is a minimal set of $\mathcal{F}$

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\ \ \leq 0 \\text{or}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\ \ > 0$
```

(5.5)

if the arising terms exist.

# **Proof**

+   (a) Let $\tilde{A} \in \mathcal{F}$ be a minimal set of $\mathcal{F}$, and let $A \in \mathcal{F}$ be arbitrarily chosen. Then we consider two cases:

+   (i) If $A \prec_{s,K} \tilde{A}$, then we obtain $\tilde{A} \prec_{s,K} A$, i.e., with Proposition 5.6

```
$$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\	ilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(\	ilde{a}-a, \tilde{a}) \right\ \ \leq 0$.
```