they require more computation than classification trees with constant fits, Loh [2009] empirically shows that their prediction accuracy is often relatively high.

# 4.3.3.1 Kernel-based and k-nearest neighbor fits

Kernel-based fits essentially select the class with the highest kernel density estimate in each node. For example, if the selected split variable x is ordered, then for each class in node t, a kernel density estimate $\hat{f}(x)$ is computed according to

```
$$\hat{f}(x) = \frac{1}{N_t h} \sum_{i=1}^{N_t} \phi \left( \frac{x - x_i}{h} \right),$$
```

where $\phi(\cdot)$ denotes the density function of a standard normal distribution, and

```
$$h = \begin{cases} 2.5 \min(s, 0.7413r) N_t^{-1/5} & \text{if } r > 0 \\ 2.5 s N_t^{-1/5} & \text{otherwise} \end{cases},$$
```

is the bandwidth; here, s and r denote the sample standard deviation and interquartile range (IQR) of the observed x values. Some motivation for using this bandwidth, which is more than twice as large as the usual bandwidth recommended for density estimation, is given in Ghosh et al. [2006].

A similar idea is used when applying k-nearest neighbor fits to each node. In particular, k is given by

```
$$k = \max(3, \lceil \log(N_t) \rceil),$$
```

where $\lceil x \rceil$ just means round x up to the nearest integer. The minimum number of neighbors (k) is three to avoid too much trouble in dealing with ties.

# 4.4 Pruning

The GUIDE algorithm continues to recursively perform splits until some stopping criteria are met (e.g., the minimum number of observations required for splitting has been reached in each node). Like CART, this will often lead to overfitting and an overly complex tree with too many splits. To circumvent