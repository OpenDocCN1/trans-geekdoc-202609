

若 `p` 和 `n` 均非常大，则在每次迭代步骤中计算 Hessian 矩阵 `X^T R(k) X` 的逆矩阵将变得非常耗时。假设初始种子 `β(0)` 已经非常接近所要寻找的最大点，我们可以用一个近似值来替代 `X^T R(k) X`，例如，将 `H(β(k)) = X^T R(k) X` 简单地替换为 `H(β(m)) = X^T R(m) X`，其中 `m << k`，这意味着我们仅在经过相当多的步骤后才更新一次 Hessian 矩阵。这种捷径方法是 *quasi‐Newton method*（拟牛顿法）的一个特例（参见 [\[17\]](#c10.xhtml#c10-bib-0017））。该方法虽有用，但可能导致一些局限性，即随着迭代的进行，某些 `π_i(k)` 会迅速趋近于 0 或 1，由于计算机程序使用的浮点数位数有限，它们的值可能被错误地记录为 0 或 1。此时，Hessian 矩阵 `H(β(k))` 将变得奇异，迭代过程 ([10.26](#c10.xhtml#c10-disp-0076)) 将变得病态；另请参见 [Figure 10.14](#c10.xhtml#c10-fig-0014)。

## REFERENCES

1.  1 Akaike, H. (1974). A new look at the statistical model identification. IEEE Transactions on Automatic Control, 19(6), 716–723.

2.  2 Atkinson, K.E. (2008). An Introduction to Numerical Analysis. Wiley.

3.  3 Chinchor, N. (1992). MUC‐4 evaluation metrics. *Proceedings of the Fourth Message Understanding Conference*, pp. 22–29.

4.  4 Fama, E., and French, K. (1992). The cross‐section of expected stock returns. The Journal of Finance, 47(2), 427–465.

5.  5 Fama, E.F., and French, K.R. (1993). Common risk factors in the returns on stocks and bonds. Journal of Financial Economics, 33(1), 3–56.

6.  6 Fisher, R.A. (1936). The use of multiple measurements in taxonomic problems. Annals of Eugenics, 7(2), 179–188.

7.  7 Galton, F. (1885). Presidential address, section H, anthropology. British Association Reports, 55, 1206–1214.

8.  8 Gauss, C.F. (1809). Theoria Motus Corporum Coelestium in Sectionibus Conicis Solem Ambientium Auctore Carolo Friderico Gauss. Sumtibus Frid. Perthes et IH Besser.

9.  9 Harrison Jr, D., and Rubinfeld, D.L. (1978). Hedonic housing prices and the demand for clean air. Journal of Environmental Economics and Management, 5(1), 81–102.

10.  10 Horn, R.A., and Johnson, C.R. (2012). Matrix Analysis. Cambridge University Press.

11.  11 Jensen, M.C. (1968). The performance of mutual funds in the period 1945–1964. The Journal of Finance, 23(2), 389–416.

12.  12 Johnson, R.A., and Wichern, D.W. (2007). Applied Multivariate Statistical Analysis (6th ed.). Prentice Hall.

13.  13 Karimireddy, S.P., Stich, S.U., and Jaggi, M. (2018). Global linear convergence of Newton's method without strong‐convexity or Lipschitz gradients. *ArXiv preprint* arXiv:1806.00413.

14.  14 Krzanowski, W.J., and Hand, D.J. (2009). ROC Curves for Continuous Data. CRC Press.

15.  15 Lee, Y., Nelder, J.A., and Pawitan, Y. (2018). Generalized Linear Models with Random Effects: Unified Analysis via H‐Likelihood. CRC Press.

16.  16 Markowitz, H. (1952). Portfolio selection. The Journal of Finance, 7(1), 77–99.

17.  17 Nocedal, J., and Wright, S. (2006). Numerical Optimization. Springer.

18.  18 Pearson, K. (1903). The law of ancestral heredity. Biometrika, 2(2), 211–228.

19.  19 Schwarz, G. (1978). Estimating the dimension of a model. The Annals of Statistics, 6(2), 461–464.

20.  20 Stehman, S.V. (1997). Selecting and interpreting measures of thematic classification accuracy. Remote Sensing of Environment, 62(1), 77–89.

## NOTES

