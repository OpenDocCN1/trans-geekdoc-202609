
where **μ**[1] = [0, 0]^T, **μ**[2] = [5, 5]^T, *Σ*[1] = *Σ*[2] = diag{0.25, 2}, and the proposal distribution is 𝒩(**x**|**μ**, *I*), where **μ** = [2.5, 2.5]^T. [Fig. 14.11](#Chp014_717-754_B9780443292385000202.xhtml#f0060) shows the paths traveled by the drawn and accepted points over three different runs. In [Figs. 14.11](#Chp014_717-754_B9780443292385000202.xhtml#f0060)A and B after 400 iterations the points drawn cover only one of the two mixtures. Both mixtures are visited in the run corresponding to [Fig. 14.11](#Chp014_717-754_B9780443292385000202.xhtml#f0060)C.

![Figure 14.11 The desired distribution comprises the mixture of two Gaussians. In each figure, a different initialization point is selected. In all cases, 400 points have been generated. Note that in two of the cases, the process seems to be trapped in either one of the two Gaussians.](images/B9780443292385000202/gr011.jpg)

Figure 14.11 The desired distribution comprises the mixture of two Gaussians. In each figure, a different initialization point is selected. In all cases, 400 points have been generated. Note that in two of the cases, the process seems to be trapped in either one of the two Gaussians.

## 14.9 Gibbs sampling

*Gibbs sampling* is among the most popular and widely used sampling methods. It is also known as the *heat bath* algorithm. Although Gibbs sampling was already known and used in statistical physics, two papers [9,10] were catalytic for its widespread use in the Bayesian and machine learning communities.

Josiah Willard Gibbs (1839–1903) was an American scientist whose work on thermodynamics laid the foundations of physical chemistry. Together with James Clark Maxwell (1831–1879) and Ludwig Eduard Boltzmann (1844–1906), Gibbs pioneered the field of statistical mechanics. He is also the father, together with Oliver Heaviside (1850–1925), of what is today known as vector calculus.

Gibbs sampling is appropriate for drawing samples from multidimensional distributions, and it can be considered a special instance of the more general Metropolis method.

Let the random vector in the Markov chain at time *n* be given as

**x**[*n*] = [*x*[*n*](1), …, *x*[*n*](*l*)]^T.

The basic assumption underlying Gibbs sampling is that the *conditional* distributions of each one of the variables, *x*[*n*](*d*), *d* = 1, 2, …, *l*, given the rest, that is,

*p*(*x*[*n*](*d*)|{*x*[*n*](*i*): *i*≠*d*}), (14.51)

are known and they can be easily sampled. At each iteration, a sample is drawn for only one of the variables, based on Eq. [(14.51)](#Chp014_717-754_B9780443292385000202.xhtml#deq104), by freezing the values of the rest to those already available from the previous iteration. The scheme is summarized next.

Algorithm 14.4

**Gibbs sampler**

*   • Initialize, *x*[0](1), …, *x*[0](*l*), arbitrarily.
