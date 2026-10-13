
# Example 6.1

The goal of this example is to demonstrate the comparative performance, with respect to the convergence rates of the `RLS`, `NLMS`, and `APA` algorithms, which have been discussed in Chapter [5](#Chp005_177-248_B9780443292385000111.xhtml). To this end, we generate data according to the regression model

*y*[*n*] = **θ**[*o*]^(*T*)**x**[*n*] + *η*[*n*]

where **θ**[*o*] ∈ ℝ^(200). Its elements are generated randomly according to the normalized Gaussian. The noise samples are i.i.d. generated via the zero mean Gaussian with variance equal to *σ*[*η*]² = 0.01. The elements of the input vector are also i.i.d. generated via the normalized Gaussian. Using the generated samples (*y*[*n*], **x**[*n*]), *n* = 0, 1, …, as the training sequence for all three previously stated algorithms, the convergence curves of [Fig. 6.8](#Chp006_249-291_B9780443292385000123.xhtml#f0055) are obtained. The curves show the squared error in dBs (10log[10](*e*[*n*]²)), averaged over 100 different realizations of the experiments, as a function of the time index *n*. The following parameters were used for the involved algorithms:

(a) For the `NLMS`, we used *μ* = 1.2 and *δ* = 0.001;
(b) for the `APA`, we used *μ* = 0.2, *δ* = 0.001, and *q* = 30;
(c) for the `RLS`, we used *β* = 1 and *λ* = 0.1.

The parameters for the `NLMS` algorithm and the `APA` were chosen so that both algorithms converge to the same error floor. The improved performance of the `APA` concerning the convergence rate compared to the `NLMS` is readily seen. However, both algorithms fall short when compared to the `RLS`. Note that the `RLS` converges to lower error floor, because no forgetting factor was used. To be consistent, a forgetting factor *β* < 1 should have been used in order for this algorithm to settle at the same error floor as the other two algorithms; this would have a beneficial effect on the convergence rate. However, having chosen *β* = 1, it is demonstrated that the `RLS` can converge really fast, even to lower error floors. On the other hand, this improved performance is obtained at substantial higher complexity. In case the input vector is part of a random process, and the special time shift structure can be exploited, as discussed in Section [6.10](#Chp006_249-291_B9780443292385000123.xhtml#s0105), the lower-complexity versions are at the disposal of the designer. A further comparative performance example, including another family of online algorithms, will be given in Chapter [8](#Chp008_343-416_B9780443292385000147.xhtml).

![Figure 6.8 MSE curves as a function of the number of iterations for NLMS, APA, and RLS. The RLS converges faster and at lower error floor.](images/B9780443292385000123/gr008.jpg)

[Figure 6.8](#Chp006_249-291_B9780443292385000123.xhtml#cf0640) MSE curves as a function of the number of iterations for `NLMS`, `APA`, and `RLS`. The `RLS` converges faster and at lower error floor.

However, it has to be stressed that this notable advantage (between `RLS`- and `LMS`-type schemes) in convergence speed from the initial conditions to steady state may not be the case concerning the tracking performance, when the algorithms have to track time-varying environments. This is demonstrated next.

# Example 6.2

This example focuses on the comparative tracking performance of the `RLS` and `NLMS`. Our goal is to demonstrate some cases where the `RLS` fails to do as well as the `NLMS`. Of course, it must be kept in mind that according to the theory, the comparative performance is very much dependent on the specific application.

For the needs of our example, let us mobilize the time-varying model of the parameters given in Eq. [(6.55)](#Chp006_249-291_B9780443292385000123.xhtml#deq110) in a more practical version and generate the data according to the following linear system:
