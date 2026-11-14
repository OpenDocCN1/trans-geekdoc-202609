```
K_{RBF} = \exp - \gamma d\left(x, x^T\right)
```

where according to Schölkopf and Smola (2018) is a smoothing parameter and the polynomial kernel's order. For the distance to be a metric and the kernel to be definitively positive and so a Mercer kernel, it must meet the following requirements to guarantee that the problem of optimization is convex.

+   **Symmetry:** \( d\left(x, x^T\right) = d\left(x^T, x\right) \)

+   **Separation:** \( d\left(x, y\right) = 0 \Rightarrow x = y \)

+   **Positivity:** \( d\left(x, y\right) > 0 \)

The triangular inequality: \(\forall x,y,z,d(x,y)\le d(x,y)+d(x,y)\).

“For any given metric, the linear, polynomial, and RBF DS kernels guarantee the presence of a domain A to where the data X has been projected from the starting point by \(\phi: X\rightarrow A, x\rightarrow\phi(x)\). The similarities in A are computed with the kernel trick without going through the projection: \(K(x,x^T)\le\phi(x)\times\phi(xT)\). The new objective function that replaces the one in equation (1.2) is given in equation (1.6) as;

```
\(\min \sum_{i,j}^N \alpha_i \alpha_j DSk\left(S^i, S^j\right), \quad (1.6)\)
```

where S is the collection of training sub-sequences and DSK is a DS kernel. Therefore, convexity may be guaranteed with a DS kernel using any metric dissimilarity” (Melakhssou et al., 2023).

Figure 1 depicts RBF and Linear Kernels in a One-Class SVM. This diagram shows the decision boundaries produced by the RBF and linear basis function (RBF) kernels used in the One-Class SVM. A straight line is used to depict the decision boundary of the linear kernel, which divides conventional data points from possible aberrations (Schölkopf et al., 2001). On the other hand, Yang et al. (2021) state that the RBF kernel generates a non-linear decision limit that facilitates a more complex distinction between normal and outlier data points. For datasets with complicated interrelationships between variables or non-linear patterns, this non-linear border is especially appropriate (Jiang et al., 2018). All things considered, these graphs show how various One-Class SVM algorithm kernels affect the decision bounds and, in turn, the model's ability to identify data anomalies.

# Application to Hourly Thermal Electricity Generation

The data used in this chapter includes 41,616 hourly observations of ESKOM’s heat and electricity production spanning the period 1 April 2019 to 30 December 2023. The time series' variance instability is fixed via a log transformation. Next, the data is split into two distinct sets: a training set and a test set. Figure 2 displays the results of a univariate examination of the data, which has as its focus the variable of interest, the hourly thermal electricity output in South Africa. This graphic depicts a time series, a box-and-whisker plot, a normal Q-Q plot, and a normal kernel density histogram. Notably, the hourly