
$$
\sum_{k=1}^{K} P_k = 1 \quad \text{and} \quad \sum_{i=1}^{K} P_{ij} = 1, \quad j = 1,2,\ldots K.
$$

![Equation](images/B9780443292385000226/si296.png)

The resulting reestimation formulas are (Problem [16.18](#Chp016_805-853_B9780443292385000226.xhtml#o0130)):

![](images/B9780443292385000226/fx010.jpg)

The reestimation of **θ**[*k*] depends on the form of the corresponding distribution *p*(**y**[*n*]|*k*; **θ**[*k*]). For example, in the Gaussian scenario, the parameters are the mean values and the elements of the covariance matrix. In this case, we obtain exactly the same iterations as those resulting for the problem of Gaussian mixtures (see Eqs. [(12.60)](#Chp012_583-634_B9780443292385000184.xhtml) and [(12.61)](#Chp012_583-634_B9780443292385000184.xhtml)), if in place of the posterior we use *γ*.

In summary, training an HMM comprises the following steps:

1.  Initialize the parameters in `Θ`.
2.  Run the sum-product algorithm to obtain `γ(·)` and `ξ(·, ·)`, using the current set of parameter estimates.
3.  Update the parameters as in Eqs. (16.56) and (16.57).

Iterations in steps 2 and 3 continue until a convergence criterion is met, such as in EM. This iterative scheme is also known as the *Baum–Welch* or *forward-backward* algorithm. Besides the forward-backward algorithm for training HMMs, the literature is rich in a number of alternatives with the goal of either simplifying computations or improving performance. For example, a simpler training algorithm can be derived tailored to the Viterbi scheme for computing the optimum path (e.g., [63,72]). Also, to further simplify the training algorithm, we can assume that our state observation variables, **y**[*n*], are discretized (quantized) and can take values from a finite set of *L* possible ones, {1, 2, …, *L*}. This is often the case in practice. Furthermore, assume that the first state is also known. This is, for example, the case for left-to-right models like the one shown in [Fig. 16.17](#Chp016_805-853_B9780443292385000226.xhtml#f0090). In such a case, we need not compute estimates of the initial probabilities. Thus, the unknown parameters to be estimated are the transition probabilities and the probabilities *P*[**y**](*r*|*i*), *r* = 1, 2, …, *L*, *i* = 1, 2, …, *K*, that is, the probability of emitting symbol *r* from state *i*.

**Viterbi reestimation**: The goal of the algorithm is to obtain the best path and compute the associated cost, say, *D*, along the path. In the speech literature, the algorithm is also known as the *segmental k-means training* algorithm [63].

**Definitions**:

*   `n[i|j]` := number of transitions from state *j* to state *i*.
*   `n[·|j]` := number of transitions originated from state *j*.
*   `n[i|·]` := number of transitions terminated at state *i*.
*   `n(r|i)` := number of times observation *r* ∈ {1, 2, …, *L*} occurs jointly with state *i*.

**Iterations**:
