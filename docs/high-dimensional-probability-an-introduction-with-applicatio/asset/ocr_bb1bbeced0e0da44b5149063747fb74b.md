using Lemma [7.5.5] and the definition of effective dimension $d(T)$ (see Definition [7.5.12]). So the takeaway is:

$$\operatorname{diam}(PT) \gtrsim \begin{cases} \sqrt{\frac{m}{n}}\,\operatorname{diam}(T), & \text{if } m \ge d(T) \\ w_s(T), & \text{if } m \le d(T). \end{cases}$$

(see Figure [7.5]). That is, as we decrease the dimension $m$ of the random projection, initially it shrinks $T$ roughly by $\sqrt{m/n}$ like in Johnson-Lindenstrauss ([7.20]). But once $m$ dips below the effective dimension $d(T)$, the shrinking stops and the diameter stays near the spherical width $w_s(T)$ as in ([7.21]). This is because $\operatorname{conv}(PT)$ looks like a ball of radius $w_s(T)$, as we will see in Section [9.7.2].

![](bbox=[0.355, 0.338, 0.711, 0.443])

**Figure 7.5** The diameter of a random $m$-dimensional projection of a set $T$ as a function of $m$.

With more tools, we will improve on Theorem [7.6.1] by dropping the constant in front of $\sqrt{m/n}$ in Section [9.2.2].

# 7.7 Notes

Slepian inequality (Theorem [7.2.2]) is originally due to D. Slepian [304, 305]; modern proofs can be found e.g. in [210, Corollary 3.12], [11, Section 2.2], [330, Section 6.1], [169], [180].

Sudakov-Fernique inequality (Theorem [7.2.8]) is attributed to V. N. Sudakov [309, 310] and X. Fernique [124]. Our presentation of the proofs of Slepian and Sudakov-Fernique inequalities in Section [7.2] is based on the approach of J.-P. Kahane [180] and a smoothing argument of S. Chatterjee (see [11, Section 2.2]), and it follows [330, Section 6.1].

The relevance of comparison inequalities to random matrix theory was noticed by S. Szarek. The applications in Section [7.3] can derived from the work of Y. Gordon [140]. Our presentation there follows the argument in [94, Section II.c], reproduced also in [340, Section 5.3.1].

Sudakov inequality (Theorem [7.4.1]) was originally proved by V. N. Sudakov. Our presentation follows [210, Theorem 3.18]; see [21, Section 4.2] for an alternative proof via duality.

Gaussian width, introduced in Section [7.5], originates in geometric functional analysis and asymptotic convex geometry [21, 246]. Starting from [290], the role of Gaussian width was recognized in applications to signal processing and high-dimensional statistics. Milman’s “hyperbolic sketch” of a high-dimensional convex body discussed in Remark [7.5.10] is from [241]; for more on this, see the preface of [21] and [23].

The effective dimension introduced in Section [7.5.3] has some variants in the literature, including the statistical dimension for convex cones [228, 18, 267].

Theorem [7.6.1] on the diameters of random projections of sets is due to V. Milman [245], see also [21, Proposition 5.7.1].

Talagrand contraction principle (Exercise [7.3]) can be found in [210, Corollary 3.17], where one can find a more general result (with a convex and increasing function of the supremum).