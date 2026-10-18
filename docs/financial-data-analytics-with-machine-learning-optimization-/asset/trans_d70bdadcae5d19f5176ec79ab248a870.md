

3. Chen, M.H., Shao, Q.M., and Ibrahim, J.G. (2012). Monte Carlo Methods in Bayesian Computation. Springer Science & Business Media.

4. De Pierro, A.R. (1993). On the relation between the ISRA and the EM algorithm for positron emission tomography. IEEE Transactions on Medical Imaging, 12(2), 328–333.

5. Dempster, A.P., Laird, N.M., and Rubin, D.B. (1977). Maximum likelihood from incomplete data via the EM algorithm. Journal of the Royal Statistical Society: Series B (Methodological), 39(1), 1–22.

6. Diaconis, P., and Freedman, D. (1997). On Markov chains with continuous state space. Annals of Probability, 27, 261–283.

7. Gamerman, D., and Lopes, H.F. (2006). Markov Chain Monte Carlo: Stochastic Simulation for Bayesian Inference (2nd ed.). Chapman & Hall/CRC.

8. Gilks, W.R., Richardson, S., and Spiegelhalter, D. (Eds.). (1995). Markov Chain Monte Carlo in Practice. CRC Press.

9. Grimmett, G., and Stirzaker, D. (2020). Probability and Random Processes (4th ed.). Oxford University Press.

10. Häggström, O. (2002). Finite Markov Chains and Algorithmic Applications. Cambridge University Press.

11. Hammersley, J.M., and Clifford, P. (1971). Markov fields on finite graphs and lattices. Unpublished manuscript. [`https://ora.ox.ac.uk/objects/uuid:4ea849da-1511-4578-bb88-6a8d02f457a6`](https://ora.ox.ac.uk/objects/uuid:4ea849da-1511-4578-bb88-6a8d02f457a6) (accessed 7 May 2024).

12. Hunter, D.R., and Lange, K. (2000). Quantile regression via an MM algorithm. Journal of Computational and Graphical Statistics, 9(1), 60–77.

13. Jacquier, E., Polson, N.G., and Rossi, P.E. (2002). Bayesian analysis of stochastic volatility models. Journal of Business & Economic Statistics, 20(1), 69–87.

14. Jacquier, E., Polson, N.G., and Rossi, P.E. (2004). Bayesian analysis of stochastic volatility models with fat-tails and correlated errors. Journal of Econometrics, 122(1), 185–212.

15. Kallenberg, O., and Kallenberg, O. (1997). Foundations of Modern Probability (Vol. 2). Springer.

16. Karlin, S., and Taylor, H.M. (1975). A First Course in Stochastic Processes (2nd ed.). Academic Press.

17. Kim, S., Shephard, N., and Chib, S. (1998). Stochastic volatility: likelihood inference and comparison with ARCH models. The Review of Economic Studies, 65(3), 361–393.

18. Lange, K. (2010). Numerical Analysis for Statisticians (2nd ed.). Springer.

19. Lange, K. (2013). Optimization (2nd ed.). Springer.

20. Lange, K. (2016). MM Optimization Algorithms. SIAM.

21. Levin, D.A., and Peres, Y. (2017). Markov Chains and Mixing Times (2nd ed.). American Mathematical Society.

22. McLachlan, G.J., and Krishnan, T. (2008). The EM Algorithm and Extensions (2nd ed.). Wiley.

23. Norris, J.R. (1998). Markov Chains. Cambridge University Press.

24. Persi, D., and Freedman, D. (1997). On Markov chains with continuous state space. Technical report.

25. Privault, N. (2013). Understanding Markov Chains. Springer.

26. Robert, C.P., and Casella, G. (2004). Monte Carlo Statistical Methods (2nd ed.). Springer.

27. Roberts, G., and Rosenthal, J. (2004). General state space Markov chains and MCMC algorithms. Probability Surveys, 1, 20–71.

28. Rudin, W. (1987). Real and Complex Analysis (3rd ed.). McGraw-Hill.

29. Tanner, M.A., and Wong, W.H. (1987). The calculation of posterior distributions by data augmentation. Journal of the American Statistical Association, 82(398), 528–540.

30. Taylor, S.J. (1982). Financial returns modelled by the product of two stochastic processes – a study of daily sugar prices 1961–79. In O.D. Anderson (Ed.), Time Series Analysis: Theory and Practice (Vol. 1, pp. 203–226). North-Holland.

31. Williams, D. (1991). Probability with Martingales. Cambridge University Press.

## NOTES

1. [1](#c06.xhtml#R_c06-note-0001) The `Modified National Institute of Standards and Technology` database, `MNIST` database for short, is revised (modified) from the original `National Institute of Standards and Technology` (`NIST`) database ([`https://www.nist.gov/srd/nist-special-database-19`](https://www.nist.gov/srd/nist-special-database-19)) by `Yann LeCun`. `MNIST` consists of 60,000 training images and 10,000 testing images of handwritten digits by high school students and employees of the `United States Census Bureau`, and is commonly used in training image processing systems. The database can be retrieved at [`http://yann.lecun.com/exdb/mnist/`](http://yann.lecun.com/exdb/mnist/).

2. [2](#c06.xhtml#R_c06-note-0002) Recall the aphorism added by `George Box` (see [`[2]`](#c06.xhtml#c06-bib-0002)): "`All models are wrong, but some of them are useful`."

3. [3](#c06.xhtml#R_c06-note-0003) According to the `Keras` website [`https://keras.io/about/`](https://keras.io/about/), the name `Keras` comes from the Greek word “horn”. It is a reference to a literary image from ancient Greek and Latin literature. In Python, `Keras` is a deep learning (e.g. `ANN`, `CNN`, `LSTM`) API (Application Programming Interface) running on top of the machine learning platform `TensorFlow`.

4. [4](#c06.xhtml#R_c06-note-0004) Each pixel of a grayscale image has a value ranging from 0 to 255, whose value represents the amount of light intensity.

5. [5](#c06.xhtml#R_c06-note-0005) This is actually the inverse distribution function introduced in [`Section 5.1`](#c05.xhtml#head-2-45) of [`Chapter 5`](#c05.xhtml), in which various simulation techniques are discussed.

6. [6](#c06.xhtml#R_c06-note-0006) According to the celebrated `Hammersley–Clifford Theorem` [`[11]`](#c06.xhtml#c06-bib-0011), the `positivity condition`, namely that for all `theta Subscript i`<math display="inline" overflow="scroll"><msub><mi>&#952;</mi><mi>i</mi></msub></math>, `i equals 1 comma ellipsis comma r`<math display="inline" overflow="scroll"><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>r</mi></math>, `pi Subscript i Baseline left-parenthesis theta Subscript i Baseline right-parenthesis greater-than 0`<math display="inline" overflow="scroll"><msub><mi>&#960;</mi><mi>i</mi></msub><mo stretchy="false">(</mo><msub><mi>&#952;</mi><mi>i</mi></msub><mo stretchy="false">)</mo><mo>&#62;</mo><mn>0</mn></math>, altogether implies that `pi left-parenthesis bold-italic theta bar bold-italic x 1 comma ellipsis comma bold-italic x Subscript n Baseline right-parenthesis greater-than 0`<math display="inline" overflow="scroll"><mi>&#960;</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">&#952;</mi><mo>&#8739;</mo><msub><mi mathvariant="bold-italic">x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi mathvariant="bold-italic">x</mi><mi>n</mi></msub><mo stretchy="false">)</mo><mo>&#62;</mo><mn>0</mn></math>, and this ensures the Markov chain to be irreducible and aperiodic.

