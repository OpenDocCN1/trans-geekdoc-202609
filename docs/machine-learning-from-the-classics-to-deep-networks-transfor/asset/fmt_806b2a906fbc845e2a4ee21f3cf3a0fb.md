
where, once more, the Markov property (i.e., Eq. [(17.14)](#Chp017_855-884_B9780443292385000238.xhtml#deq20)) has been used.

![Figure 17.2 Graphical model corresponding to the state-space modeling for Kalman and particle filters.](images/B9780443292385000238/gr002.jpg)

**Figure 17.2** Graphical model corresponding to the state-space modeling for Kalman and particle filters.

Eqs. [(17.18)](#Chp017_855-884_B9780443292385000238.xhtml#deq24)–[(17.20)](#Chp017_855-884_B9780443292385000238.xhtml#deq26) comprise the set of recursions which lead to the update

*p*(**x**[*n* − 1]|**y**[1 : *n* − 1]) → *p*(**x**[*n*]|**y**[1 : *n*])

starting from the initial (prior) *p*(**x**[0]|**y**[0]) :  = *p*(**x**[0]). If *p*(**x**[0]) is chosen to be Gaussian, then all the involved PDFs turn out to be Gaussians due to Eqs. [(17.16)](#Chp017_855-884_B9780443292385000238.xhtml#deq22) and [(17.17)](#Chp017_855-884_B9780443292385000238.xhtml#deq23) and the linearity of Eqs. [(17.14)](#Chp017_855-884_B9780443292385000238.xhtml#deq20) and [(17.15)](#Chp017_855-884_B9780443292385000238.xhtml#deq21); this makes the computation of the integrals a trivial task following the recipe rules in the Appendix of Chapter [12](#Chp012_583-634_B9780443292385000184.xhtml).

Before we proceed further, note that the recursions in Eqs. [(17.18)](#Chp017_855-884_B9780443292385000238.xhtml#deq24) and [(17.20)](#Chp017_855-884_B9780443292385000238.xhtml#deq26) are an instance of the sum-product algorithm for graphical models. Indeed, to put our current discussion in this context, let us compactly write the previous recursions as

![Equation](images/B9780443292385000238/fx004.jpg) (17.21)

Note that this is of exactly the same form, within the normalizing factor, as Eq. [(16.43)](#Chp016_805-853_B9780443292385000226.xhtml) of Chapter [16](#Chp016_805-853_B9780443292385000226.xhtml); just replace summation with integration. One can rederive Eq. [(17.21)](#Chp017_855-884_B9780443292385000238.xhtml#deq28) using the sum-product rule, following similar steps as for Eq. [(16.43)](#Chp016_805-853_B9780443292385000226.xhtml). The only difference is that the normalizing constant has to be involved in all respective definitions and we replace summations with integrations. Because all the involved PDFs are Gaussians, the computation of the involved normalizing constants is trivially done; moreover, it suffices to derive recursions only for the respective mean values and covariances.

In Eq. [(17.20)](#Chp017_855-884_B9780443292385000238.xhtml#deq26), we have

*p*(**x**[*n*]|**x**[*n* − 1]) = 𝒩(**x**[*n*]|*F*[*n*]**x**[*n* − 1], *Q*[*n*]).

Let, also, *p*(**x**[*n* − 1]|**y**[1 : *n* − 1]) be Gaussian with mean and covariance matrix

**μ**[*n* − 1|*n* − 1], *P*[*n* − 1|*n* − 1].
