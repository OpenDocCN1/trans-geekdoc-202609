
ℱ(*p*(𝒳^(*l*)|𝒳; **ξ**^((*j*))), **ξ**) = 𝒬(**ξ**, **ξ**^((*j*))) − ∫ *p*(𝒳^(*l*)|𝒳; **ξ**^((*j*))) ln *p*(𝒳^(*l*)|𝒳; **ξ**^((*j*))) *d*𝒳^(*l*),

![Equation](images/B9780443292385000184/si285.png) (12.71)

where 𝒬(**ξ**, **ξ**^((*j*))) is the same as in Eq. [(12.40)](#Chp012_583-634_B9780443292385000184.xhtml#deq53) and the second term on the right-hand side is independent of **ξ**; this latter term is equal to the entropy associated with *q*^((*j* + 1))(𝒳^(*l*)). The rederivation of the EM via this path makes it clear that the quantity that is maximized is the log-likelihood, ln *p*(𝒳; **ξ**), and that its value is guaranteed not to decrease after each combined iteration step. [Fig. 12.10](#Chp012_583-634_B9780443292385000184.xhtml#f0070) illustrates schematically the two EM steps comprising the (*j* + 1)th iteration.

![Figure 12.10 The E-step adjusts q^{(j)}: = q^{(j)}(\\mathcal{X}^{l})Equation so that its KL divergence from p\_{\\cdot | \\cdot}^{(j)}: = p(\\mathcal{X}^{l}|\\mathcal{X};\\mathbf{\\xi}^{(j)})Equation becomes zero. The M-step maximizes with respect to ξ. We used pj to denote the evidence function.](images/B9780443292385000184/gr010.jpg)

[Figure 12.10](#Chp012_583-634_B9780443292385000184.xhtml#cf0925) The E-step adjusts *q*^((*j*)) := *q*^((*j*))(𝒳^(*l*)) so that its KL divergence from *p*[⋅|⋅]^((*j*)) := *p*(𝒳^(*l*)|𝒳; **ξ**^((*j*))) becomes zero. The M-step maximizes with respect to **ξ**. We used *p*^(*j*) to denote the evidence function.

Needless to say, the EM algorithm is not a panacea. We will soon seek variants to deal with cases where the posterior cannot be given in an analytic form. Moreover, there are still cases where the M-step can be computationally intractable. To this end, several variants have been proposed (see, for example, [31,34]).

### Remarks 12.5

*   **Online versions of EM**: We have already pointed out that in many cases of big data applications, online versions are the preferable choice in practice. The EM algorithm is no exception, and a number of related versions have been proposed. In [34], an online EM algorithm is proposed based on the lower bound interpretation. In [6], stochastic approximation arguments have been employed. In [25], a comparative study of different techniques is reported.
