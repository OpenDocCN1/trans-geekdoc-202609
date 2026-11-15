By using this positive-rule Saleh-type R-estimator, a LASSO-type of penalty is applied to the unrestricted R-estimates in a manner similar to how LASSO operates on LS estimates.

The ridge R-estimator of the location parameter can be obtained using

\(\hat{\theta}_n^{\text{ridgeR}} = \text{argmin}_{\theta \in \mathbb{R}} \{D_n(\theta) + \frac{\lambda}{2}\theta^2\}\) (3.3.9)

or in terms of the unrestricted estimate, we define the ridge-type R-estimator as

\(\hat{\theta}_n^{\text{ridgeR}}(\lambda) = \frac{1}{1 + \lambda} \hat{\theta}_n^{\text{UR}}\).

Its trace is illustrated in the bottom-left plot of Figure 3.1. You can observe the decay characteristic that was detailed in Chapter 2.

Finally, the nEnet R-estimator is as follows:

\(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha) = \text{argmin}_{\theta \in \mathbb{R}} \{D_n(\theta) + \alpha\lambda|\theta| + \frac{\lambda(1 - \alpha)}{2}\theta^2\}.\) (3.3.10)

In this case, we have two tuning parameters1, \(\lambda\) and \(\alpha\). In the bottom right figure, we show six cases corresponding to \(\alpha = 0, 0.2, 0.4, 0.6, 0.8, 1.0\). The case for \(\alpha = 1.0\) is the same as the LASSO R-estimator, and \(\alpha = 0.0\) is the same as the ridge R-estimator. Other values of \(\alpha\) produce curves that lie between the two, as one would expect.

The corresponding nEnet-type R-estimator is given by

\(\hat{\theta}_n^{\text{nEnetR}}(\lambda, \alpha) = \frac{\hat{\theta}_n^{\text{UR}}}{1 + \lambda(1 - \alpha)}\left(1 - \frac{\lambda\alpha}{\sqrt{\mathcal{L}_n}}\right)I(\mathcal{L}_n > \lambda^2\alpha^2).\) (3.3.11)

While not shown in the figure, it would have similar characteristics as the bottom-right plot.

This completes the first pass through all the estimators. In the sections to follow, we will carry out detailed analysis of each estimator. For this purpose, Figure 3.1 can be very useful as a quick reference guide to give context and meaning for the analysis in each section.