
13. Nualart, D., and Nualart, E. (2018). Introduction to Malliavin Calculus. Cambridge University Press.

14. Oosterlee, C.W., and Grzelak, L.A. (2020). Mathematical Modeling and Computation in Finance: With Exercises and Python and Matlab Computer Codes. World Scientific.

15. Robert, C.P., and Casella, G. (1999). Monte Carlo Statistical Methods. Springer.

16. Ross, M.R. (2022). Simulation (6th ed.). Academic Press.

17. Shreve, S.E. (2004). Stochastic Calculus for Finance II: Continuous-Time Models. Springer.

18. Steele, J.M. (2001). Stochastic Calculus and Financial Applications. Springer.

19. Walters, P. (2000). An Introduction to Ergodic Theory. Springer Science & Business Media.

20. Wilmott, P., Howison, S., and Dewynne, J. (1995). The Mathematics of Financial Derivatives: A Student Introduction. Cambridge University Press.

## NOTES

1. [1](#c05.xhtml#R_c05-note-0001) The explicit form of `σ_C_T^2` can be quite complicated. One may simply use the bootstrapped sample variance as an estimate for most practical considerations.

2. [2](#c05.xhtml#R_c05-note-0002) This curve, depicting the implied volatility against exercise price of a financial option, gets its name since it is usually convex and resembles a smile facing us.

# CHAPTER 6  

Approximation for Model Inference

The process of fitting models is often accomplished by minimizing the sum of squares (as in regression analysis) or minimizing cross-entropy (as in classification method). These are examples of the `maximum likelihood approach` to fitting. This chapter provides a comprehensive explanation of the maximum likelihood approach and introduces several methods of approximation for the purpose of model inference.

The examples provided in this chapter highlight the practical applications and importance of the algorithms to be introduced. For instance, by leveraging the maximum likelihood approach to fitting within numerical algorithms, it becomes possible to implement handwriting number recognition systems that accurately identify handwritten numbers commonly found on cheques and many business form filings. Estimating quantiles using numerical methods is essential for risk assessment and portfolio management, such as `Value-at-Risk` calibration (to be introduced in [Chapter 8](#c08.xhtml)). After providing a comprehensive and self-contained introduction to `Markov Chain theory`, we also introduce, with an illustrative example, the very useful `Markov Chain Monte Carlo` (MCMC) method for sampling from complex probability distributions.

## 6.1 EM ALGORITHM

The `Expectation–Maximization Algorithm` (or `EM Algorithm` for short) is a parametric learning method first introduced in `[5](#c06.xhtml#c06-bib-0005)` for tackling parametric estimations, especially with unobservable variates. Instead of looking for an explicit analytic solution, the EM algorithm finds a maximum point of a log-likelihood function via an iterative procedure that can easily be carried out by modern computers. An in-depth account of the general theory of the EM algorithm and its various extensions is given by the classical text `[22](#c06.xhtml#c06-bib-0022)`.
