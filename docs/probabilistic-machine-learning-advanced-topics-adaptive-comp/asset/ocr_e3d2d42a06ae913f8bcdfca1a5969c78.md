![](bbox=[0.1, 0.09, 0.85, 0.205])

Figure 18.12: Illustration of the graphical model for a GP on n observations, f_{1:n}, and one test case, f_*, with inducing variables u. The thick lines indicate that all variables are fully interconnected. The observations y_i (not shown) are locally connected to each f_i. (a) no approximations are made. (b) we assume f_* is conditionally independent of f_X given u. From Figure 1 of [QCR05]. Used with kind permission of Joaquin Quiñonero Candela.

(We write p(f_X, f_*) instead of p(f_X, f_* | X, X_*), since the inputs can be thought of as just indices into the random function f.) We will choose f_Z in such a way that it acts as a sufficient statistic for the data, so that we can predict f_* just using f_Z instead of f_X, i.e., we assume f_* \perp f_X | f_Z. Thus we approximate the prior as follows:

```
p(f_*, f_X, f_Z) = p(f_* | f_X, f_Z) p(f_X | f_Z) p(f_Z) \approx p(f_* | f_Z) p(f_X | f_Z) p(f_Z) (18.118)
```

See Figure 18.12 for an illustration of this assumption, and Section 18.5.3.4 for details on how to choose the inducing set Z. (Note that this method is often called a “sparse GP”, because it makes predictions for f_* using a subset of the training data, namely f_Z, instead of all of it, f_X.) From this, we can derive the following train and test conditionals

```
p(f_X | f_Z) = N(f_X | K_{X,Z} K_{Z,Z}^{-1} f_Z, K_{X,X} - Q_{X,X}) (18.119)
```

```
p(f_* | f_Z) = N(f_* | K_{*,Z} K_{Z,Z}^{-1} f_Z, K_{*,*} - Q_{*,*}) (18.120)
```

The above equations can be seen as exact inference on noise-free observations f_Z. To gain computational speedups, we will make further approximations to the terms Q_{X,X} = K_{X,X} - Q_{X,X} and Q_{*,*} = K_{*,*} - Q_{*,*}, as we discuss below. We can then derive the approximate prior q(f_X, f_*) = \int q(f_X | f_Z) q(f_* | f_Z) p(f_Z) df_Z, which we then condition on the observations in the usual way. All of the approximations we discuss below result in an initial training cost of O(M^3 + NM^2), and then take O(M) time for the predictive mean for each test case, and O(M^2) time for the predictive variance. (Compare this to O(N^3) training time and O(N) and O(N^2) testing time for exact inference.)

# 18.5.3.1 SOR/DIC

Suppose we assume Q_{X,X} = 0 and Q_{*,*} = 0, so the conditionals are deterministic. This is called the deterministic inducing conditional (DIC) approximation [QCR05], or the subset of regressors (SOR) approximation [Sil85; SB01]. The corresponding joint prior has the form

```
q_{SOR}(f_X, f_*) = N(0, ( K_{X,X}   Q_{X,*} ; Q_{*,X}   Q_{*,*} )) (18.121)
```