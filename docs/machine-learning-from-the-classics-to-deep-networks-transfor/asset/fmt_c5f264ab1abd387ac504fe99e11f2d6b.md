
$J(\mathbf{\theta}) = \sum\limits_{n = 1}^{N}\left\lbrack y_{n}\ln\sigma\left( \mathbf{\phi}^{T}(x_{n})\mathbf{\theta} \right) + (1 - y_{n})\ln\left( 1 - \sigma(\mathbf{\phi}^{T}(x_{n})\mathbf{\theta}) \right) \right\rbrack - \frac{1}{2}\mathbf{\theta}^{T}A\mathbf{\theta},$

![Equation](images/B9780443292385000196/si745.png)

1. where

$\sigma(z) = \frac{1}{1 + \exp( - z)}.$

![Equation](images/B9780443292385000196/si746.png)

1.  

2. **13.10** Show that the marginal of a Gaussian PDF with a gamma prior on the variance, after integrating out the variance, is the Student's *t* PDF, given by

${st}(x|\mu,\lambda,\nu) = \frac{\Gamma(\frac{\nu + 1}{2})}{\Gamma(\frac{\nu}{2})}\left( \frac{\lambda}{\pi\nu} \right)^{1/2}\frac{1}{\left( 1 + \frac{\lambda{(x - \mu)}^{2}}{\nu} \right)^{\frac{\nu + 1}{2}}}.$

![Equation](images/B9780443292385000196/si212.png)(13.152) 

1.  

2. **13.11** Derive the pair of recursions Eqs. (13.62)–(13.63).

3. **13.12** Consider a two-class classification task and assume that the feature vectors in each one of the two classes, $\omega_1, \omega_2$, are distributed according to the Gaussian PDF. Both classes share the same covariance matrix $\Sigma$, and the mean values are $\boldsymbol{\mu}_1$ and $\boldsymbol{\mu}_2$, respectively. Prove that, given an observed feature vector, $\mathbf{x} \in \mathbb{R}^{(l)}$, the posterior probability for deciding in favor of one of the classes is given by the logistic function, i.e.,
