![](bbox=[0.1, 0.08, 0.88, 0.26])

(a) Results on a subset of datasets used for experiments in [20].

![](bbox=[0.1, 0.3, 0.88, 0.46])

(b) Results on synthetic datasets, identified by their edge size.

Fig. 2. Empirical distributions of the number of 3-cycles in 33 samples. The observed value is omitted when far from both empirical distributions.

On synthetic datasets with higher density, and therefore degeneracy, the distributions are more distinct. On all but the least dense synthetic dataset, the observed number of 3-cycles is found to be significant under the degeneracy-allowed null model, and non-significant under our null model. Results for directed 2-cycles are similar (see the supplementary materials).

In all cases the distributions over the two null models are different, so there exist critical thresholds for which a hypothesis would be rejected under one null model but not under the other. This fact stresses the profound difference between our null models and that of Preti et al. [20], emphasizing the importance of choosing the appropriate null model when testing hypotheses.

# 6.2 Convergence

The perturbation score [22] is a popular measure for the empirical mixing time of MCMC algorithms that sample from null models over dyadic graphs and binary matrices. Given two binary matrices, it is defined as the fraction of entries with value 1 in one matrix that have value 0 in the other. We extend the perturbation score between two dihypergraphs \(\dot{G}\) and \(G\) as the average of the perturbation