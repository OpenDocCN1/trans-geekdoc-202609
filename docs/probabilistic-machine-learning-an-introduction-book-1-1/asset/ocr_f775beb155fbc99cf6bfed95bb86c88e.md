shape to the Gaussian cdf (see Sec. **3.3.1**) \(\Phi(a)\). In particular we have \(\sigma(a) \approx \Phi(\lambda a)\), where \(\lambda^2 = \pi/8\) ensures the two functions have the same slope at the origin. This is useful since we can integrate a Gaussian cdf wrt a Gaussian pdf exactly:

\[\int \Phi(\lambda a)\mathcal{N}(a\mid m,v)\,da = \Phi\left(\frac{m}{(\lambda^{-2}+v)^{1/2}}\right) = \Phi\left(\frac{\lambda m}{(1+\lambda^2v)^{1/2}}\right) \approx \sigma(\kappa(v)m) \tag{10.115}\]

where we have defined

\[\kappa(v) \triangleq (1+\pi v/8)^{-1/2} \tag{10.116}\]

Thus if we define \(a = \mathbf{x}^{\mathsf T}\mathbf{w}\), we have

\[p(y=1\mid\mathbf{x},\mathcal{D}) \approx \sigma(\kappa(v)m) \tag{10.117}\]

\[m = \mathbb{E}[a] = \mathbf{x}^{\mathsf T}\boldsymbol{\mu} \tag{10.118}\]

\[v = \mathbb{V}[a] = \mathbb{V}[\mathbf{x}^{\mathsf T}\mathbf{w}] = \mathbf{x}^{\mathsf T}\boldsymbol{\Sigma}\mathbf{x} \tag{10.119}\]

where we used Eq. **(D.68)** in the last line. Since \(\Phi^{-1}\) is known as the probit function, we will call this the **probit approximation**.

Using Eq. **(10.117)** results in predictions that are less extreme (in terms of their confidence) than the plug-in estimate. To see this, note that \(0 < \kappa(v) < 1\) and hence \(\kappa(v)m < m\), so \(\sigma(\kappa(v)m)\) is closer to 0.5 than \(\sigma(m)\) is. However, the decision boundary itself will not be affected. To see this, note that the decision boundary is the set of points \(\mathbf{x}\) for which \(p(y=1\mid\mathbf{x},\mathcal{D}) = 0.5\). This implies \(\kappa(v)m = 0\), which implies \(m = \bar{\mathbf{w}}^{\mathsf T}\mathbf{x} = 0\); but this is the same as the decision boundary from the plug-in estimate. Thus “being Bayesian” doesn’t change the misclassification rate (in this case), but it does change the confidence estimates of the model, which can be important, as we illustrate in Sec. **10.6.2**.

In the multiclass case, [Nab01, p353] suggests the following extension of the Spiegelhalter method of Sec. **10.6.1.2**:

\[p(y=c\mid\mathbf{x},\mathcal{D}) \approx \frac{\exp(\kappa(v_c)m_c)}{\sum_{c'}\exp(\kappa(v_{c'})m_{c'})} \tag{10.120}\]

\[m_c = \mathbf{m}_c^{\mathsf T}\mathbf{x} \tag{10.121}\]

\[v_c = \mathbf{x}^{\mathsf T}\mathbf{V}_{c,c}\mathbf{x} \tag{10.122}\]

where \(\kappa\) is defined in Eq. **(10.116)**. Unlike the binary case, taking into account posterior covariance gives different predictions than the plug-in approach (see Exercise 3.10.3 of [RW06]).

# 10.6.2  Laplace approximation

As we discuss in Sec. **7.7.2**, the Laplace approximation approximates the posterior using a Gaussian. The mean of the Gaussian is equal to the MAP estimate \(\hat{\mathbf{w}}\), and the covariance is equal to the inverse Hessian \(\mathbf{H}\) computed at the MAP estimate, i.e., \(p(\mathbf{w}\mid\mathcal{D}) \approx \mathcal{N}(\mathbf{w}\mid\hat{\mathbf{w}},\mathbf{H})\). We can find the mode using a standard optimization method (see Sec. **10.2.7**), and we can use the results from Sec. **10.2.3.4** to compute the Hessian at the mode.