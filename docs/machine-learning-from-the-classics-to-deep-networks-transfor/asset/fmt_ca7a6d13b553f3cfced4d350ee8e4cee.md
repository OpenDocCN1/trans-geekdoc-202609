
# State-Space Models for Sequential Data

A very popular and effective framework to model sequential data is via the so-called *state-observation* or *state-space* models. Each set of random variables, **y**[*n*] ∈ ℝ<sup>l</sup>, which are observed at time *n*, is associated with a corresponding unobserved (latent) random vector **x**[*n*] (not necessarily of the same dimensionality as that of the observations). The system dynamics are modeled via the latent variables and observations are considered to be the output of a measuring *noisy* sensing device. The so-called hidden Markov models are built around the following two independence assumptions:

(1) **x**[*n* + 1] ⊥ (**x**[1], …, **x**[*n* − 1]) | **x**[*n*], (16.24)

(2) **y**[*n*] ⊥ (**x**[1], …, **x**[*n* − 1], **x**[*n* + 1], …, **x**[*N*]) | **x**[*n*], (16.25)

where *N* is the total number of observations. The first condition defines the system dynamics via the transition model

*p*(**x**[*n* + 1] | **x**[1], …, **x**[*n*]) = *p*(**x**[*n* + 1] | **x**[*n*]), (16.26)

and the second one via the observation model

*p*(**y**[*n*] | **x**[1], …, **x**[*N*]) = *p*(**y**[*n*] | **x**[*n*]). (16.27)

In words, *the future is independent of the past given the present, and the observations are independent of the future and past given the present*.

The previously stated independencies are graphically represented via the graph of [Fig. 16.15](#Chp016_805-853_B9780443292385000226.xhtml#f0080). If the latent variables are of a discrete nature, the resulting model is known as a hidden Markov model. If, on the other hand, both latent and observed variables are of a continuous nature, the resulting model gets rather involved to deal with. However, analytically tractable tools can be and have been developed for some special cases. In the so-called *linear dynamic systems* (LDSs), the system dynamics and the generation of the observations are modeled as

**x**[*n*] = *F*[*n*]**x**[*n* − 1] + **η**[*n*], (16.28)
