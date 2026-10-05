# A.5 ASYMPOTIC LEARNING CURVES WITH A LOCAL TEACHER

the estimates of Equation 168 and Equation 170 extend to kernels with nonoverlapping patches after substituting the degeneracy d/s with |P| = d.

# A-5 ASYMPOTIC LEARNING CURVES WITH A LOCAL TEACHER

**Theorem A.5.1.** Let K_t be a d-dimensional local kernel with a translationally-invariant d constituent and leading nonanalyticity at the origin controlled by the exponent a_t > 0. Let K_s be a d-dimensional local kernel with a translationally-invariant s-dimensional constituent, and with a nonanalicity at the origin controlled by the exponent a_s > 0. Assume, in addition, if the kernels have overlapping patches s > t; whereas if the kernels have nonoverlapping patches s is an integer multiple of t; that are uniformly distributed on a d-dimensional torus. Then the following asymptotic equivalence holds in the limit P → ∞,

```
B(P) ~ P^{-\beta}, \\beta = a_t/s. (174)
```

Proof. The proof is analogous to that of Section A.4, the only difference being that eigenfunctions and eigenvalues are indexed by k and the patch index i. This results in an additional factor of d/s in the RHS of Equation 161. The discussion between Equation 162 and Equation 167 can be repeated by attaching the additional patch index i to all coefficients. Equation 168 for B(P) is then corrected with an additional sum over patches. The extra sum, however, does not influence the asymptotic scaling with P.

# A.6 PROOF OF THEOREM 2.6.1

**Theorem A.6.1** In the main text). Let us consider a positive-definite kernel K with eigenvalues \lambda. \sum \lambda_p < \infty, and eigenfunctions f_p learning a random target function f* in kernel ridge regression (Equation 21) with ridge \lambda from P observations f*_i = f*(x_i), with x_i \in R^d drawn from a certain probability distribution. Let us denote by D_T(\lambda) the reduced density of kernel values with respect to the target and E(\lambda, P) generalization error and also any

+   i) For any P-tuple of indices p_1, . . . p_P, the vector (\Phi_{p_1}(x_1), . . . \Phi_{p_P}(x_P)) is a Gaussian random vector;

+   ii) The target function can be written in the kernel basis with coefficients c_p and c^2(\lambda) = E[|c_p|^2], with D_T(\lambda) ~ \lambda^{-(1+r)}, c^2(\lambda) ~ asymptotically for small \lambda and r > 0, r < q < r + 2;