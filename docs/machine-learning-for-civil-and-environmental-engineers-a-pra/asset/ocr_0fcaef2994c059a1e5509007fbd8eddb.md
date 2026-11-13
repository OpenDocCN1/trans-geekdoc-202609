Now, here is an illustration.

Suppose we clustered two fire-exposed RC columns with similar features into a pair. If both columns have spalled (or not spalled) under fire, then a third synthetic column can be generated with features equal to the averaged features of the parents. In other words, if the parent columns have spalled, then the synthetic column is also likely to spill since it has averaged features to its parents.17 In contrast, if one of the columns spalled while the other did not spill, then the third (synthetic column) is assumed to spill. Table 9.1 lists the statistical properties of the running example of fire-exposed RC columns.18 As you can see, the statistical insights from synthetic and real data match well.

# Table 9.1 Comparison between real and synthetic data as obtained from the fire-exposed RC columns dataset.

| | Statistic | Width (mm) | Steel ratio (%) | Compressive strength of concrete (MPa) | Concrete cover (mm) | Loading (kN) |
|---|---|---|---|---|---|---|
| Real observations | Minimum | 152.0 | 0.3 | 15.0 | 13.0 | 0.0 |
| | Maximum | 514.0 | 11.7 | 126.5 | 64.0 | 5373.0 |
| | Average | 326.1 | 2.3 | 42.1 | 33.5 | 1342.0 |
| | Standard deviation | 71.8 | 1.6 | 24.3 | 7.7 | 1001.3 |
| | Skewness | 0.8 | 2.5 | 1.9 | –0.4 | 1.6 |
| Synthetic observations | Minimum | 152.0 | 0.5 | 16.1 | 13.0 | 84.5 |
| | Maximum | 511.0 | 10.8 | 119.7 | 51.0 | 4970.0 |
| | Average | 325.6 | 2.3 | 42.0 | 33.5 | 1338.4 |
| | Standard deviation | 66.0 | 1.3 | 23.1 | 7.3 | 911.8 |
| | Skewness | 0.8 | 2.5 | 1.9 | –0.7 | 1.6 |
| All observations | Minimum | 152.0 | 0.7 | 16.0 | 25.0 | 0.0 |
| | Maximum | 514.0 | 4.9 | 126.5 | 64.0 | 5373.0 |
| | Average | 325.3 | 2.5 | 54.3 | 37.6 | 1556.9 |
| | Standard deviation | 69.4 | 0.8 | 27.9 | 4.4 | 1109.1 |
| | Skewness | 0.7 | 1.0 | 1.1 | 0.6 | 1.4 |

# 9.1.3 Synthetic Minority Over-sampling Technique (SMOTE)

The synthetic minority over-sampling technique (SMOTE), together with its derives, creates new observations by examining how the nearest two observations of the smaller class are joined by a form of distance (i.e., straight line) and then multiplies such distance by a random number between zero and unity, and places the newly generated synthetic observation at this new distance from one of the real observations belonging to the smaller class used for distance calculation. Figure 9.2 illustrates the basic idea behind SMOTE.

# 9.1.4 Generative Adversarial Networks (GANs) and Triplet-based Variational Autoencoder (TVAE)

As we learned before, GANs is a deep learning technique [4]. If you think about it, since GANs follow an unsupervised approach, then they could be used to learn the structure of the patterns in our limited data. Thus, GANs can also be used to generate synthetic data that could have been possibly drawn from the space of our dataset19 These generated synthetic data are statistically indistinguishable from actual data [4]. A good library to use GANs, as well as other advanced techniques (such as Triplet-based Variational Autoencoder (TVAE)) is the Synthetic Data Vault (SDV) [5].

Allow me now to go over the following short example. I will extend one of the running examples we have covered earlier on RC columns exposed to fire since having limited data is a prime problem within the structural fire engineering area. As you might