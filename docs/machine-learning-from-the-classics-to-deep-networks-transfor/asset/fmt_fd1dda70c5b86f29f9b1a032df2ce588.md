
In Chapters [12](#Chp012_583-634_B9780443292385000184.xhtml) and [13](#Chp013_635-716_B9780443292385000196.xhtml), the Bayesian inference task was considered. A large part of the latter chapter was dedicated to dealing with approximation techniques, which offered escape routes when the involved PDFs were complex enough to render integral computations intractable. All these techniques were of a deterministic nature; that is, the goal was to approximate the mathematical expression of the corresponding PDF by another one that could ease the associated calculations. Such methods include the Laplacian approximation, as well as the variational methods based on the mean field theory or the convex duality concept. Deterministic approximation methods will also be used for approximate inference in Chapter [15](#Chp015_755-803_B9780443292385000214.xhtml), to deal with graphical models.

In this chapter, we turn our attention to approximation methods with a much stronger statistical flavor, which are based on randomly generating samples using numerical techniques; these samples are typical of an underlying distribution, which may be of either continuous or discrete nature. This is an old field, with origins tracing back to the late 1940s and early 1950s in the pioneering work of Stanislav Ulam, John Von-Neumann, and Nicholas Metropolis in Los Alamos, when the term `Monte Carlo` was coined as an umbrella name of such techniques, inspired by the famous casino in Monaco (see, e.g., [28] for a historical note). The first application of such techniques, which coincided with the development of the first computers, was in the context of the Manhattan project for developing the hydrogen bomb; soon after, Monte Carlo methods were embraced by almost every scientific area where statistical computations are involved.

As is often the case with pioneering ideas, when they are looked at a posteriori, that is, once they have been stated, the basic idea seems simple. Our current task of interest is the computation of an integral, which involves a PDF; this can alternatively be interpreted as the computation of an "expectation." Such a view provides the permit to approximate the integral as the sample mean of the involved quantities, given a sufficient number of samples and exploiting the law of large numbers.

To condense a field with a history of a number of decades in a single chapter is obviously impossible. Our goal is to present the basic concepts, definitions, and directions, with the aim of serving the needs associated with typical machine learning tasks rather than looking at it as an entity on its own.

We start with the more classical methods using transformations and then move on to the rejection and importance sampling techniques. In the sequel, the more powerful methods based on arguments from the theory of Markov chains are reviewed. The Metropolis–Hastings and Gibbs sampling methods are presented and discussed. Finally, a case study concerning the change-point detection task is considered.

## 14.2 Monte Carlo methods: the main concept

Our starting point is the evaluation of integrals of the form

𝔼[*f*(**x**)] :  = ∫[ − ∞]^∞*f*(**x**)*p*(**x**) *d***x** (14.1)

where **x** ∈ ℝ^(*l*) is a random vector and *p*(**x**) is the corresponding distribution.^([^(106)](#fn106))

Coming back to Eq. [(14.1)](#Chp014_717-754_B9780443292385000202.xhtml#deq1), assume that one has at her/his disposal a number of i.i.d. samples, **x**[1], …, **x**[*N*], drawn from *p*(**x**). Then the approximation

```
𝔼[f(x)] ≈ (1/N) ∑_{i=1}^N f(x_i) = Ē_{f,N}
```
(14.2)
