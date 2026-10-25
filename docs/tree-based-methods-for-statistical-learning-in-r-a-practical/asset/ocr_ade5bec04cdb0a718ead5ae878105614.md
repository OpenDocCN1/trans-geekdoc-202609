general pruning technique that can be helpful in screening out pure noise variables.

![](bbox=[0.165, 0.156, 0.835, 0.439])

FIGURE 2.11: A decision tree fit to a copy of the air quality data set that includes ten completely random categorical features, each with cardinality 26.

In some cases, it's possible to reduce the number of potential categories to something more manageable—like lumping rare categories together, or combining categories into a smaller set of meaningful subgroups (e.g., combining zip or area codes into a smaller set of larger geographic areas).

The partitioning algorithms discussed in Chapters 3–4 address the split selection bias issue more directly by separating the exhaustive search over all possible splits for each feature into two sequential steps, where the optimal split point is found only after a splitting variable has been selected.

# 2.4.3 To encode, or not to encode?

When dealing with categorical data, we are often concerned with how to encode such features. In linear models, for example, we often employ dummy encoding or effect encoding, depending on the task at hand. Similarly, one-hot-encoding (OHE), closely related to dummy encoding, is often used in general machine learning problems outside of (generalized) linear models. And there are plenty of other ways to encode categorical variables, depending on the algorithm and task at hand.