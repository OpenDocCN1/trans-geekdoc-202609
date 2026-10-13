
**y**[*n*] = *H*[*n*]**x**[*n*] + **v**[*n*],

where **η**[*n*] and **v**[*n*] are zero mean, mutually independent noise disturbances modeled by Gaussian distributions. This is the celebrated Kalman filter, which we have already discussed in Chapter [4](#Chp004_119-175_B978044329238500010X.xhtml) and it will also be considered, from a probabilistic perspective, in Chapter [17](#Chp017_855-884_B9780443292385000238.xhtml). The probabilistic counterparts of Eqs. [(16.28)](#Chp016_805-853_B9780443292385000226.xhtml#deq57) and [(16.29)](#Chp016_805-853_B9780443292385000226.xhtml#deq58) are

*p*(**x**[*n*]|**x**[*n* − 1]) = 𝒩(**x**[*n*]|*F*[*n*]**x**[*n* − 1], *Q*[*n*]),

*p*(**y**[*n*]|**x**[*n*]) = 𝒩(**y**[*n*]|*H*[*n*]**x**[*n*], *R*[*n*]),

where *Q*[*n*] and *R*[*n*] are the covariance matrices of **η**[*n*] and **v**[*n*], respectively.

![Figure 16.15 The Bayesian network corresponding to a Markov model. If the unobserved variables, x, are of a discrete nature, this corresponds to an HMM. If both observed, y, and unobserved variables are continuous and follow a Gaussian distribution, this corresponds to a linear dynamic system (LDS). Note that the observed variables comprise the leaves of the graph.](images/B9780443292385000226/gr015.jpg)

Figure 16.15 The Bayesian network corresponding to a Markov model. If the unobserved variables, **x**, are of a discrete nature, this corresponds to an HMM. If both observed, **y**, and unobserved variables are continuous and follow a Gaussian distribution, this corresponds to a linear dynamic system (LDS). Note that the observed variables comprise the leaves of the graph.

## 16.5 Hidden Markov models

Hidden Markov models are represented by the graphical model in [Fig. 16.15](#Chp016_805-853_B9780443292385000226.xhtml#f0080) and Eqs. [(16.26)](#Chp016_805-853_B9780443292385000226.xhtml#deq55) and [(16.27)](#Chp016_805-853_B9780443292385000226.xhtml#deq56). The latent variables are discrete; hence, we write the *transition* probability as *P*(**x**[*n*]|**x**[*n* − 1]) and this corresponds to a table of probabilities. Observation variables can either be discrete or continuous. Basically, an HMM is used to model a *quasistationary* process that undergoes *sudden* changes among a number of, say, *K* subprocesses. Each one of these subprocesses is described by different statistical properties. One could alternatively view it as a combined system comprising a number of subsystems; each one of these subsystems generates data/observations according to a different statistical model; for example, one may follow a Gaussian and the other one a Student's *t* distribution. Observations are emitted by these subsystems; however, once an observation is received, we do not know which subsystem this was emitted from. This reminds us of the mixture modeling task of a PDF; however, in mixture modeling, we did not care about the sequence in which observations occur.
