# APPENDIX: LOCALITY DEFEATS THE CURSE OF DIMENSIONALITY

![](bbox=[0.283, 0.068, 0.818, 0.452])

Figure 36: Learning curves for uniformly distributed on the unit sphere $S^{d-1}$, with $d=10$ if not specified otherwise. The teacher and student filter sizes are denoted with $t$ and $s$ respectively. Solid lines are the results of numerical experiments averaged over 128 realizations and the shaded areas represent the empirical standard deviations.

**LOCAL TEACHER** In Figure 35 we report the empirical learning curves for a local teacher kernel and data uniformly sampled in the hypercube $[0,1]^d$. In panels I and J, also the student is a local kernel and the same discussion of Section 2.5 applies. In panel K, the student is a convolutional kernel and the generalization error does not decrease by increasing the size of the training set. Indeed, a local shift-invariant function is not on the span of the eigenfunctions of a convolutional kernel, and therefore the student is not able to learn the target.

**EMPIRICAL DATA** In Figure 36 we report the empirical learning curves for convolutional and convolutional (left panels) and local (right panels) student kernels. Data are restricted to the unit sphere $S^{d-1}$. Panels L–O are the analogous of panels A–D of Figure 1. Notice that when the filter size of the student coincides with $d$ (panels P, Q), the learning curves decay with exponent $eta=1/(d-1)$ (instead of $eta=1/d$). Indeed, for data normalized on $S^{d-1}$, the spectrum of the