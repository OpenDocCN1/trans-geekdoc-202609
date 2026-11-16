the coefficients. Choosing $\gamma$ can be done through cross-validation. In Fig. 3.4, the dashed vertical line shows $\gamma_{se}$, which is the largest value of $\gamma$ such that the squared error is within one standard error of the minimum. At this point, three predictors remain in the model out of the initial 17 that were included in the fit.

To employ variable selection techniques for fault isolation, the multiple linear regression model is reframed so that the mean vector is being monitored and those variables whose mean is unchanged are filtered out. Several variations of the penalties presented here have also been employed, and a few specific methods will be presented in the following subsections.

# 3.2.3.1 Phase I variable selection

One of the primary goals of a Phase I analysis is to test whether a set of observations could reasonably be expected to come from an IC process. As such, data used in a Phase I analysis could be contaminated by multiple faults simultaneously. A secondary goal may be to retrospectively analyze a fault or multiple faults that occurred so that operators may begin to diagnosis them. We present an example of each type of analysis in this section.

Example method 1, mphase1. Capizzi and Masarotto [8] developed a distribution-free retrospective change point detection method designed to test for multiple change-points over a given period of time, called mphase1. Their approach is designed to first test whether the period of time under consideration is IC; if not, then the shifted variables can be identified, along with their shift sizes and directions. Their method assumes that the observations are iid when the process is IC. It also allows for sub grouped data, in which multiple realizations of the process are present at a single time points. This allows the user to detect outlying observations at a single isolated time point in addition to detecting step shifts. For simplicity, we ignore the potential presence of sub grouped observations in our description of the method.

A user-friendly R package called dfphase1 contains code to implement mphase1 [8]. It is not assumed that data from an IC period exists. The following steps are performed:

+   1. Standardization. The data are standardized and transformed to the multivariate signed ranks using a robust estimate of the center and spread. For the location estimate, $\ell$, the transformation–retransformation spatial median is applied to subgroup means [39]. For the spread, a robust scatter matrix, $\mathbf{S}_r$, is constructed as

![](bbox=[0.3, 0.81, 0.72, 0.86])

Then, they use $\ell$ and $\mathbf{S}_r$ to standardize the data, $\mathbf{z}_i = \mathbf{S}_r^{-1/2} (\mathbf{x}_i - \ell)$, and compute the multivariate signed ranks $\mathbf{u}_i$ as follows: