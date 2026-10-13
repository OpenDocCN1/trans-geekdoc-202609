
### 多项分布的统计特性

𝔼[**x**] = *n***P**, *σ*[*x*[*k*]]² = *n**P*[*k*](1 − *P*[*k*]), *k* = 1, 2, …, *K*, cov(*x*[*i*], *x*[*j*]) = −*n**P*[*i*]*P*[*j*], *i* ≠ *j*.

The special case of the multinomial, where only one experiment, *n* = 1, is performed, is known as the *categorical* distribution. The latter can be considered as the generalization of the Bernoulli distribution.

### 2.3.2 Continuous variables

#### The uniform distribution

A random variable x is said to follow a *uniform* distribution in an interval [*a*, *b*], and we write *x* ∼ 𝒰(*a*, *b*), with *a* > −∞ and *b* < +∞, if

```
f(x) = 1/(b-a) for a ≤ x ≤ b, 0 otherwise
```
(2.60)

[Fig. 2.3](#Chp002_19-64_B9780443292385000081.xhtml#f0020) shows the respective graph. The mean value is equal to

𝔼[ x ] = (a + b)/2,
(2.61)

and the variance is given by (Problem [2.2](#Chp002_19-64_B9780443292385000081.xhtml#o0015))

*σ*ₓ² = (1/12)(b - a)².
(2.62)

![Figure 2.3 The PDF of a uniform distribution 𝒰(a,b)](images/B9780443292385000081/gr003.jpg)

[Figure 2.3](#Chp002_19-64_B9780443292385000081.xhtml#cf0380) The PDF of a uniform distribution 𝒰(*a*, *b*).

#### The Gaussian distribution

The Gaussian or normal distribution is one among the most widely used distributions in all scientific disciplines. We say that a random variable x is *Gaussian* or *normal* with parameters *μ* and *σ*², and we write *x* ∼ 𝒩(*μ*, *σ*²) or 𝒩(*x*|*μ*, *σ*²), if
