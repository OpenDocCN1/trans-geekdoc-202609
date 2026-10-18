# SIDEBAR

# The mathematics for the multivariate case

The equations for updating the means and (co)variances are a little more complicated than those we encountered in the univariate case. If you’re interested though, here they are.

The mean of Gaussian \(k\) for variable \(a\) is:

$$\mu_{k,a}=\sum_{i=1}^{n}\left(\frac{p(k\mid x_i)}{n\times p(k)}\right)x_{i,a}$$

The centroid of the Gaussian is therefore just a vector where each element is the mean of a different variable.

The covariance between variables \(a\) and \(b\) for Gaussian \(k\) is:

$$(\Sigma_k)_{a,b}=\sum_{i=1}^{n}\left(\frac{p(k\mid x_i)}{n\times p(k)}\right)(x_{i,a}-\mu_{k,a})(x_{i,b}-\mu_{k,b})$$

where \(\Sigma_k\) is the covariance matrix for Gaussian \(k\).

Finally, in the multivariate case, the likelihood \(p(x_i\mid k)\) now needs to take into account the covariance, and so it now becomes:

$$p(x_i\mid k)=\frac{1}{\sqrt{2\pi}\,\Sigma_k}e^{-0.5(\vec{x_i}-\vec{\mu_k})^T\Sigma_k^{-1}(\vec{x_i}-\vec{\mu_k})}$$

Does this process seem familiar to you? Iteratively updating the position of the clusters based on how far away cases in the data are from them? We saw a similar procedure for the k-means algorithms in chapter 16. Gaussian mixture model clustering therefore extends k-means clustering to allow non-spherical clusters or different diameters (due to the covariance matrix) and soft clustering. In fact, if you were to constrain a Gaussian mixture model such that all clusters had the same variance, no covariance, and equal priors, you would get a very similar result as provided by Lloyd’s algorithm!