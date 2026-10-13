
## 2. Unknown Vector Estimation Algorithms

For the unknown vector estimation, employ the following algorithms:

- Combine-then-adapt diffusion APSM ([Algorithm 8.3](#Chp008_343-416_B9780443292385000147.xhtml#enun0150))
- Adapt-then-combine LMS ([Algorithm 5.7](#Chp005_177-248_B9780443292385000111.xhtml))
- Combine-then-adapt LMS ([Algorithm 5.8](#Chp005_177-248_B9780443292385000111.xhtml))
- Noncooperative LMS ([Algorithm 5.1](#Chp005_177-248_B9780443292385000111.xhtml))

### Combine-then-adapt APSM Parameters
Set the parameters as follows:
- `\mu[n] = 0.5 \times M[n]`
- `\epsilon_k = \sqrt{2}\sigma_k`
- `q = 20`

### LMS Algorithms Parameters
For the adapt-then-combine, combine-then-adapt, and noncooperative LMS, set the step size equal to `0.03`.

### Combination Weights
Finally, choose the combination weights `a[mk]` with respect to the Metropolis rule ([Remarks 5.4](#Chp005_177-248_B9780443292385000111.xhtml)).

## 3. Simulation Setup

Run 100 independent experiments and plot the average MSD per iteration in dBs:

```
MSD(n) = 10\log_{10}\left( \frac{1}{K}\sum_{k=1}^{K}{\|\mathbf{\theta}_k(n) - \mathbf{\theta}_o\|}^2 \right)
```

## 4. Tasks

1.  Compare the performance of the combine-then-adapt APSM with the performance of the LMS-based algorithms.
2.  Keep playing with different values of the parameters for the involved algorithms and observe their influence on the obtained performance.

## 5. Exercise 8.40

Download the `banknote authentication` data set.^([^(60)](#fn60))

## References

*   [1] A. Agarwal, P. Bartlett, P. Ravikumar, M.J. Wainwright, Information-theoretic lower bounds on the oracle complexity of convex optimization, *IEEE Trans. Inf. Theory* 2012;58(5):3235–3249.
*   [2] A.E. Albert, L.A. Gardner, *Stochastic Approximation and Nonlinear Regression*. MIT Press; 1967.
*   [3] S. Amari, Natural gradient works efficiently in learning, *Neural Comput.* 1998;10(2):251–276.
*   [4] F. Bach, E. Moulines, Non-strongly-convex smooth stochastic approximation with convergence rate `O(1/n)`, [arXiv:1306.2119v1 [cs.LG]](http://www.arxiv.org/abs/1306.2119v1); 2013.
*   [5] F. Bach, Adaptivity of averaged stochastic gradient descent to local strong convexity for logistic regression, *J. Mach. Learn. Res.* 2014;15:595–627.
*   [6] H.H. Bauschke, J.M. Borwein, On projection algorithms for solving convex feasibility problems, *SIAM Rev.* 1996;38(3):367–426.
*   [7] H.H. Bauschke, P.L. Combettes, *Convex Analysis and Monotone Operator Theory in Hilbert Spaces*. Springer; 2011.
*   [8] A. Beck, M. Teboulle, Gradient-based algorithms with applications to signal recovery problems, D. Palomar, Y. Eldar, eds. *Convex Optimization in Signal Processing and Communications*. Cambridge University Press; 2010:42–88.
*   [9] A. Beck, M. Teboulle, Mirror descent and nonlinear projected subgradient methods for convex optimization, *Oper. Res. Lett.* 2003;31:167–175.
*   [10] D.P. Bertsekas, *Nonlinear Programming*. second ed. Athena Scientific; 1999.
*   [11] D.P. Bertsekas, A. Nedic, A.E. Ozdaglar, *Convex Analysis and Optimization*. Athena Scientific; 2003.
*   [12] L. Bottou, Y. Le Cun, Large scale online learning, *Advances in Neural Information Processing Systems*. *NIPS*. MIT Press; 2003:2004–2011.
*   [13] L. Bottou, O. Bousquet, The tradeoffs of large scale learning, *Adv. Neural Inf. Process. Syst.* 2007;20:161–168.
*   [14] L. Bottou, Large-scale machine learning with stochastic gradient descent, Y. Lechevallier, G. Saporta, eds. *Proceedings 19th Intl. Conference on Computational Statistics*. *COMPSTAT 2010, Paris, France*. Springer; 2010.
*   [15] S. Boyd, L. Vandenberghe, *Convex Optimization*. Cambridge University Press; 2004.
*   [16] S. Boyd, N. Parikh, E. Chu, P. Peleato, J. Eckstein, Distributed optimization and statistical learning via the alternating direction method of multipliers, *Found. Trends Mach. Learn.* 2011;3(1):1–122.
*   [17] L.M. Bregman, The method of successive projections for finding a common point of convex sets, *Sov. Math. Dokl.* 1965;6:688–692.
*   [18] R. Bruck, An iterative solution of a variational inequality for certain monotone operator in a Hilbert space, *Bull. Am. Math. Soc.* 1975;81(5):890–892.
*   [19] N. Cesa-Bianchi, A. Conconi, C. Gentile, On the generalization ability of on-line learning algorithms, *IEEE Trans. Inf. Theory* 2004;50(9):2050–2057.
*   [20] R.L.G. Cavalcante, I. Yamada, B. Mulgrew, An adaptive projected subgradient approach to learning in diffusion networks, *IEEE Trans. Signal Process.* 2009;57(7):2762–2774.
*   [21] N. Cesa-Bianchi, G. Lugosi, *Prediction, Learning, and Games*. Cambridge University Press; 2006.
*   [22] S. Chouvardas, K. Slavakis, S. Theodoridis, Adaptive robust distributed learning in diffusion sensor networks, *IEEE Trans. Signal Process.* 2011;59(10):4692–4707.
*   [23] S. Chouvardas, K. Slavakis, S. Theodoridis, I. Yamada, Stochastic analysis of hyperslab-based adaptive projected subgradient method under bounded noise, *IEEE Signal Process. Lett.* 2013;20(7):729–732.
*   [24] P.L. Combettes, The foundations of set theoretic estimation, *Proc. IEEE* 1993;81(2):182–208.
