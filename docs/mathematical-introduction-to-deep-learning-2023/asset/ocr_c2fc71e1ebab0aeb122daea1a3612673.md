# # Chapter 4

# ## Multi-dimensional ANN approximation results

In this chapter we review basic deep ReLU ANN approximation results for possibly multi-dimensional target functions. We refer to the beginning of Chapter 3 for a small selection of ANN approximation results from the literature. The specific presentation of this chapter is strongly based on [25, Sections 2.2.6, 2.2.7, 2.2.8, and 3.1], [226, Sections 3 and 4.2], and [230, Section 3].

# ### 4.1 Approximations through supremal convolutions

**Definition 4.1.1 (Metric).** *We say that* $\delta$ *is a metric on* $E$ *if and only if it holds that* $\delta: E \times E \rightarrow [0, \infty)$ *is a function from* $E \times E$ *to* $[0, \infty)$ *which satisfies that*

+   (i) *it holds that*

$$ \{ (x, y) \in E^2: d(x, y) = 0\} = \bigcup_{x \in E} \{ (x, x) \} \quad \quad (4.1) $$

*(positive definiteness),*

+   (ii) *it holds for all* $x, y \in E$ *that*

$$ \delta(x, y) = \delta(y, x) \quad \quad (4.2) $$

*(symmetry), and*

+   (iii) *it holds for all* $x, y, z \in E$ *that*

$$ \delta(x, z) \leq \delta(x, y) + \delta(y, z) \quad \quad (4.3) $$

*(triangle inequality).*