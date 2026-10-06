# 10.3 Deep generative models

# 10.3 Deep generative models

Key to the generative paradigm is that we model x as a random variable, and it requires making some assumptions regarding its distribution. In the GMM discussed above we used a Gaussian to model the (class-conditional) distribution of x. It is important to note that this assumption does not mean we truly believe the data is Gaussian, but rather that it is close to being Gaussian so that we can obtain a useful model (whether it is for clustering or classification). That being said, however, in many situations the generative assumption is oversimplifying, which can limit the performance of the resulting model.

One way to relax the assumption is to manually design some alternative distribution that is believed to better correspond to the properties of the data. However, in many situations it is very challenging to come up with a stable distribution “by hand”, not least when x is high-dimensional and with complex dependencies between the individual coordinates. In this section we will consider another approach, which is to view x as a transformation of some simple random variable z. With a high degree of flexibility in the transformation, we can model very complex distributions over x in this way. Specifically, we discuss how deep neural networks (Chapter 6) can be used in this task, namely deep generative models.

Since the key challenge in developing flexible non-Gaussian generative model is to construct the distribution over x, which we will throughout this section (and for the remainder of the chapter) drop class, or label y from the model. From that, we will try to learn the distribution p(x) in an unsupervised way, assuming that there are any clusters in the data (or put differently, there is only a single class). The purpose of this is first, learning generative models for high-dimensional data can be even in the absence of distinct clusters. Second, it simplifies the notation in the presentation below. If we do expect that the data contains clusters, the methods presented below can be easily generalized to model the class-conditional distribution p(x|y) indent.

The problem that we are concerned with this section can thus be formulated as: given a training data set {x_i}_{i=1}^n of n samples from some distribution p(x), learn a parametric model of this distribution.

# Invertible non-Gaussian models and normalizing flows

To lay the foundation for the non-Gaussian generative model, let us use with a simple Gaussian model for the time being:

```
$p(x) = N(x|\mu, \Sigma)$
```

The parameters of this model are the mean vector and the covariance matrix, $\theta = {\mu, \Sigma\}$, which can be learned from the training data $\{x_i\}_{i=1}^n$ by maximum likelihood. As we discussed above, this leads us to estimating $\mu$ by the sample mean, and $\Sigma$ by the sample covariance (analogously to 10.3), but with a single class.

Since a linear transformation of a Gaussian random vector is also Gaussian, an equivalent representation of (10.19) is to introduce a random variable z of the sample p as x, following a generative distribution,

```
$p_z(z) = N(z|0, I)$
```

and then expressing x by a linear change of variables,

```
$x = \mu + Lz.$
```

Here L is any matrix such that $LL^T = \Sigma$. Note that, in this representation, the distribution $p_z(x) = N(z|0, I)$ takes a very simple and generic form, which is independent of the model parameters. indent,

> ^7 We use a subscript on p_z(z) to emphasize that this is the distribution of z, and to distinguish this pdf from p(x).
8 For a positive definite matrix $\Sigma$, such factorization always exists. For instance, we can take L to be the lower triangular matrix from a Cholesky decomposition of $\Sigma$. For our purposes, it is not important how the matrix L is obtained, just that it exists.

This will be published by Cambridge University Press. This pre-publication version is free to view and download for personal use only. Not for re-distribution, re-use or de use in media.
© Andreas Lindholm, Niklas Wahlström, Fredrik Lindson, and Thomas B. Schön. 2021