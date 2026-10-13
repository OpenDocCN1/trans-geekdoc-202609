
where `f(x)` is a *random process*. From Chapter [2](#Chp002_19-64_B9780443292385000081.xhtml), we know that a random process is a random entity whose realization (the outcome of an experiment) is a function, `f(x)`, instead of a single value. The idea that spans this section is to work directly on `f(x)` instead of the indirect approach of modeling it via the set of parameters, `θ`. This is not the first time we have adopted such a path. We silently did it in Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml) while searching for functions in RKHSs. As a matter of fact, this section can be considered a bridge between the current chapter and Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml).

Recall from Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml) that instead of expanding an unknown function in a parameterized form in terms of a number of *preselected* basis functions as in Eq. [(13.136)](#Chp013_635-716_B9780443292385000196.xhtml#deq210), we preferred to search directly for functions that reside in an RKHS; the optimization was carried out with respect to the function itself (not with respect to a preselected set of parameters). In the context of the squared error loss function, the optimization was cast as

```
\min_{f \in \mathbb{H}}\sum_{n = 1}^{N}\left( y_{n} - f(\mathbf{x}_{n}) \right)^{2} + C{\| f\|}^{2},
```

where `∥ ⋅ ∥` denotes the norm in `ℍ`. The goal in this section is to state the “Bayesian counterpart” to this approach. To this end, we will focus on a specific family of processes, known as Gaussian processes, proposed in [57].

### Definition 13.1

A random process, `f(x)`, is called a *Gaussian process* if and only if for *any* finite number of points, `x(1), …, x(N)`, the respective joint probability density function, `p(f(x(1)),…,f(x(N)))`, is Gaussian.

We know that a set of jointly Gaussian distributed random variables is fully described by the respective mean value and the covariance matrix. In a similar spirit, a Gaussian process is fully determined by its mean value and its *covariance function*, that is,
