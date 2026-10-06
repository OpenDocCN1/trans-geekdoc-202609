
# 9 The Bayesian approach and Gaussian processes

## 9.4 Practical aspects of the Gaussian process

$\ln p(y)$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_0.png)

$\ln p(y) = -7.18$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_1.png)

$\ln p(y) = -8.52$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_2.png)

$\ln p(y) = -8.59$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_3.png)

$\ln p(y) = -7.38$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_4.png)

$\ln p(y) = -49.36$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_196_5.png)

**Figure 9.12.** To choose hyperparameters $\eta=(\ell, \sigma^2)$ for the Gaussian process kernel, the marginal likelihood $p_{\eta}(y)$ can be maximized. For a given dataset of five points (black dots) and the squared exponential kernel, the landscape of the logarithm of the likelihood (as a function of the hyperparameters $\ell$ and noise variance $\sigma^2$) is shown as a contour plot in the upper left panel. Each point in that corresponds to a selection of the hyperparameters $\ell, \sigma^2$. For five points (gray, purple, green, and orange dots) the corresponding Gaussian process is shown in separate panels with the same color. Note that the orange dot is located at the maximum of $p_{\eta}(y)$. The orange upper right plot therefore corresponds to a Gaussian process where the hyperparameters have been maximized using marginal likelihood. It is clear that optimizing $p_{\eta}(y)$ does *not mean* selecting hyperparameters such that the Gaussian process follows the data as close as possible (as the blue one).

This material will be published by Cambridge University Press. This pre-publication version is free to view and for personal use only. Not for re-distribution, re-sale or use in derivative works.
© Andreas Lindholm, Nikolai Wahlström, Fredrik Lindsten, and Thomas B. Schön 2021.

$\ln p(\mathbf{y})$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_197_0.png)

$\ln p(\mathbf{y}) = -8.06$

$\ln p(\mathbf{y}) = -8.13$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_197_1.png)

**Figure 9.13:** The landscape of $p(y)$ may have several local maxima. In this case there is one local maximum at the blue dot, with relatively large noise variance and length scale. There is another local maximum, which is also the global one, at the green dot, with much less noise variance and a shorter timescale. There is also a third local maximum in between (not shown). It is not uncommon that the different maxima provide different “interpretations” of the data. As a machine learning engineer it is important to be aware that this can happen; the green one does indeed optimize the marginal likelihood, but the blue one can also be practically useful.

We conclude this part about the Gaussian process by applying it to the car stopping distance problem in Example 9.3.

Draft (April 30, 2021) – A First Course for Engineers and Scientists. http://smlbook.org
© Andreas Lindholm, Niklas Wahlström, Fredrik Lindqvist, and Thomas B. Schön. 2021.

## 9.4 Practical aspects of the Gaussian process

### Example 9.3: Car stopping distances

We consider the car stopping distance problem from Example 2.2. We have already discussed the application of kernel ridge regression and support vector regression in Examples 8.2 and 8.3, respectively, both in the previous examples looked reasonable, we use the same kernel and hyperparameters again, meaning that we have

$$\hat{k}(x,x') = \exp\left(-\frac{|x-x'|^2}{2\ell^2}\right) + \sigma^2$$

with $\ell=3$ and $\sigma^2=1$ (with $\lambda=0.1$ and $n=6$ data points). However, we also have the option to introduce another parameter $\zeta$ as $\hat{\zeta}(x,x')$. In the top part of Figure 9.14 we use $\zeta=2$ and $n=4$ to illustrate the functional impact that $\zeta$ has on the posterior predictive. Note that only the variance, and the mean, is not affected by $\zeta$. This can be confirmed by the fact that $\zeta$ cancels algebraically in (9.2a) but not in (9.2b).

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_198_0.png)

$\zeta = 2$

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_198_1.png)

To select $\zeta$ we therefore maximize the marginal likelihood with respect to it, which gives us $\zeta=2$, as shown in the bottom of Figure 9.14. It indeed seems to have a very reasonable variance ("uncertainty") in the posterior predictive distribution.

This material will be published by Cambridge University Press. This pre-publication version is free to view and for personal use only. Not for re-distribution, re-sale or use in derivative works.
© Andreas Lindholm, Nils Wahlström, Fredrik Lindsten, and Thomas B. Schön 2021.

## 9.5 Other Bayesian methods in machine learning

Unlike the Bayesian approach in general, this chapter contains the Bayesian treatment of linear regression (Bayesian linear regression, Section 9.2) and kernel ridge regression (Gaussian processes, Section 9.3-9.4). The Bayesian approach is, however, applicable to all methods that learn a model from data. The reason for the selection of methods in this chapter is firstly that Bayesian linear regression and Gaussian process regression are the few supervised methods where the posterior and/or the posterior predictive are easy to compute.

Most often the Bayesian approach requires numerical integration routines as methods for representing the posterior distribution (the posterior does not have to be a Gaussian or any other standard distribution) when applied to various models. There are two major families of such methods: variational inference and Monte Carlo methods respectively. The development of variational inference is to approximate probability distributions in such a way that the problem becomes tractable whereas Monte Carlo methods represent distributions using random samples from them.

The Gaussian process model is an example of a method belonging to the family of Bayesian methods. Another method in that family is the Dirichlet process, which can be used for the unsupervised clustering problem (see Chapter 10) with no need to specify the number of clusters.

Another direction is the Bayesian approach applied to deep learning, often referred to as Bayesian deep learning. In short, Bayesian deep learning amounts to computing the posterior $p(\theta|y)$, instead of only parameter values $\theta$. So stochastic gradient descent has to be replaced with either some version of variational inference or some Monte Carlo method. Due to the massive number of parameters used in deep learning, this is a computationally challenging problem.

## 9.6 Further reading

The Bayesian approach has a long history within statistics. The name originates from Thomas Bayes and his 1763 posthumously published work "Essay towards solving a Problem in the Doctrine of Chances", also Pierre-Simon Laplace made significant contributions to the idea in the late 18th and early 19th century. For an overview of its use in statistics and its historical contours, we refer to Efron and Hastie (2016, Part I).

A relatively short review of modern Bayesian machine learning with many suggestions for further reading is Ghmani (2015). There are also several textbooks on the use of the Bayesian approach in machine learning, including Barber (2012), Gelman et al. (2014) and Rohshaus and Girolami (2017), and to some also Bishop (2016) and Murphy (2012).

Gaussian processes are covered in the textbook Rasmussen and Williams (2006). Other Bayesian nonparametric models in general and the Dirichlet process are introduced by Hershman and Blei (2012), Ghahmani (2013), and Hjort et al. (2010).

As mentioned above, the Bayesian approach often requires advanced computational methods not discussed in this chapter. For further studies of variational inference we refer to Bishop (2006, Chapter 10) and Blei et al. (2017). Introduction to Monte Carlo methods are found in Owen (2013), Robert and Casella (2004) and Gelman et al. (2014, Part III).

Although a very recent topic, the idea of Bayesian learning of neural networks was laid out already in the 90's (R. M. Neal 1996). Some more recent contributions include Blundell et al. (2015), Dusenberry et al. (2020), Fort et al. (2019), and R. Zhang et al. (2020).
