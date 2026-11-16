![](bbox=[0.225, 0.095, 0.43, 0.255])

![](bbox=[0.49, 0.08, 0.77, 0.255])

Figure 9.2: (a) Illustration of pairwise UGM on binary nodes, together with a set of pseudo marginals that are not globally consistent. (b) A slice of the marginal polytope illustrating the set of feasible edge marginals, assuming the node marginals are clamped at \(\mu_1 = \mu_2 = \mu_3 = 0.5\). From Figure 4.1 of [WJ08]. Used with kind permission of Martin Wainwright.

We call the terms \(\tau_s, \tau_{st} \in \mathbb{L}(G)\) **pseudo marginals**, since they may not correspond to marginals of any valid probability distribution. As an example of this, consider Figure 9.2(a). The picture shows a set of pseudo node and edge marginals, which satisfy the local consistency requirements. However, they are not globally consistent. To see why, note that \(\tau_{12}\) implies \(p(X_1 = X_2) = 0.8\), \(\tau_{23}\) implies \(p(X_2 = X_3) = 0.8\), but \(\tau_{13}\) implies \(p(X_1 = X_3) = 0.2\), which is not possible (see [WJ08, p81] for a formal proof). Indeed, Figure 9.2(b) shows that \(\mathbb{L}(G)\) contains points that are not in \(\mathbb{M}(G)\).

We claim that \(\mathbb{M}(G) \subseteq \mathbb{L}(G)\), with equality iff \(G\) is a tree. To see this, first consider an element \(\boldsymbol{\mu} \in \mathbb{M}(G)\). Any such vector must satisfy the normalization and marginalization constraints, hence \(\mathbb{M}(G) \subseteq \mathbb{L}(G)\). Now consider the converse. Suppose \(T\) is a tree, and let \(\boldsymbol{\mu} \in \mathbb{L}(T)\). By definition, this satisfies the normalization and marginalization constraints. However, any tree can be represented in the form

```
$$
p_\mu(\boldsymbol{x}) = \prod_{s \in V} \mu_s(x_s) \prod_{(s,t) \in E} \frac{\mu_{st}(x_s, x_t)}{\mu_s(x_s)\mu_t(x_t)}
$$ (9.17)
```

Hence satisfying normalization and local consistency is enough to define a valid distribution for any tree. Hence \(\boldsymbol{\mu} \in \mathbb{M}(T)\) as well. In contrast, if the graph has loops, we have that \(\mathbb{M}(G) \neq \mathbb{L}(G)\). See Figure 9.2(b) for an example of this fact. The importance of this observation will become clear in Section 10.1.3.

# 9.1.3.2 Algorithms

Our task is to solve Equation (9.13), which requires maximizing a linear function over a simple convex polytope. For this, we could use a generic linear programming package. However, this is often very slow.

Fortunately, one can show that a simple algorithm, that sends messages between nodes in the graph, can be used to compute \(\boldsymbol{\tau}^*\). In particular, the **tree reweighted belief propagation** algorithm can be used; see Section 10.1.5.3 for details.

# 9.1.3.3 Application to stereo depth estimation

Belief propagation is often applied to low-level computer vision problems (see e.g., [Sze10; BKR11; Pri12]). For example, Figure 9.3 illustrates its application to the problem of **stereo depth estimation** given a pair of monocular images (only one is shown). The value \(x_i\) is the distance of pixel \(i\) from the camera (quantized to a certain number of values). The goal is to infer these values from noisy measurements. We quantize the state space, rather than using a Gaussian model, in order to avoid oversmoothing at discontinuities, which