methods find only prototypes, but no criticisms. This chapter presents MMD-critic by Kim et al. (2016)$^{27}$, an approach that combines prototypes and criticisms in a single framework.

MMD-critic compares the distribution of the data and the distribution of the selected prototypes. MMD-critic selects prototypes that minimize the discrepancy between the two distributions. Data points in areas with high density are good prototypes, especially when points are selected from different “clusters”. Data points from regions that are not well explained by the prototypes are selected as criticisms.

Let us deeper into the theory.

# 7.7.1 Theory

The MMD-critic procedure on a high-level can be summarized briefly:

+   1. Select the number of prototypes and criticisms you want to find.
2. Find prototypes with greedy search. Prototypes are selected so that the distribution of prototypes is close to the data distribution.
3. Find criticisms with greedy search. Points are selected as criticisms where the distribution of prototypes differs from the distribution of the data.

We need a couple of ingredients to find prototypes and criticisms for a dataset with MMDcritic. The most basic ingredient, we need a kernel function to estimate the data densities. A kernel is a function that weighs two data points according to their proximity. Based on density estimates, we measure a density distribution tells us how different two distributions are so that we can determine whether the distribution of the we select is close to the data distribution. This is solved by measuring the maximum discrepancy (MMD). Also based on the kernel function, we need the witness function to tell us how different two distributions are at a particular point. With the witness function, we can select criticisms, i.e data points at which distribution of prototypes diverges and the witness function takes on large absolute values. The last ingredient is a search strategy for good prototypes and criticisms, which is solved with a simple greedy search.

Let us start with the maximum discrepancy (MMD), which measures the discrepancy between two distributions. The selection of prototypes creates a distribution of prototypes. We want to evaluate whether the prototypes distribution differs from the data distribution. We estimate both with kernel density functions. The maximum discrepancy measures the difference between two distributions, which is the supremum over a function space of differences between the expectations according to the two distributions. All clear? Personally, I understand these concepts much better when I see something calculated with data. The following formula shows how to calculate the squared MMD measure (MMD2)

> $27}$Kim, Rajiv Khanna, and Oluwasanni O. Koyejo. “Examples are not enough, learn to criticize! Criticism for interpretability.” Advances in Neural Information Processing Systems (2016).