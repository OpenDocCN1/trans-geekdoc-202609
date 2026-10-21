
The Laplace transform of the option price with respect to \(T\) is given by

$$\int_{0}^{\infty} e^{-\beta T} V(S_{0}, T) dT = \frac{1}{\beta} E_{x}\left[e^{-(r+\beta)\tau}\right] = \frac{1}{\beta} \prod_{k=1}^{m+1} \rho_{k}\left\{\sum_{h=1}^{m+1}\left[\frac{1}{\rho_{h}\prod_{l=1, l\neq h}^{m+1}(-\rho_{h}+\rho_{l})}\prod_{i=1}^{m}\frac{\rho_{h}+\eta_{i}}{\eta_{i}}\right]\left(\frac{S_{0}}{H}\right)^{\rho_{h}}\right\}.\tag{41.62}$$

### Remark 41.4.8

It is worth noting that the time zero value of debt in Example 41.3.9 is of the form \(A\int_{0}^{\infty} m e^{-mT} B(V, L, T) dT\), where \(B(V, L, T)\) is the time zero value of a bond issued at zero with face value 1 and maturity \(T\). The price formula (41.29) follows by similar arguments as in Example 41.4.7.

## 41.5 Concluding Remarks

The expected discounted penalty is a generalized notion of the ruin probability in the insurance literature. It has been widely studied and generalized since Gerber and Shiu (1998). On the other hand, this function has been a major concern in the pricing of perpetual financial securities and the Laplace transforms of securities with finite maturity, and examples include option theory and credit risk modeling.

While empirical studies have been indicating the failure of diffusion models, the seminal paper of Merton (1976) has received more attention in recent years. However, unlike the diffusion case in which many functions are available, this is no longer the case for jump-diffusion processes, especially in the first-passage models, this is where the difficulty in the pricing of securities under a jump-diffusion process arises.

In this chapter, we consider the jump-diffusion process as in Asmussen et al. (2004). In the case where the jump distribution is a two-sided phase-type one, by a Fourier transform argument, we transform the integro-differential equation of the expected discounted penalty into a homogeneous ordinary differential equation. The present method could possibly be extended to transform more integro-differential equations into ordinary differential equations, and hence give an alternative approach to compute prices in jump-diffusion models.

Next, by ODE theory, we know that the solution for the expected discounted penalty is a linear combination of some known exponential functions. Moreover, by using the limit behavior of the expected discounted penalty and the integro-differential equation, we can determine these coefficients (under some conditions). All these distinguish not only our approach from that of Asmussen et al. (2004) but also itself from the classical method to solve differential equations in which the knowledge of boundary values is required. This could be applied to solve other functionals once we have transformed their integro-differential equation into an ordinary differential equation.

Our results in fact provide explicit solutions to a large amount of existing pricing problems in finance. Using our closed-form solutions, especially Theorem 41.4.3, the Laplace transforms of securities with finite maturities have explicit solutions as mentioned in Example 41.4.7, and we show an example by considering a touch-and-out option. In addition, the pricing problems of perpetual securities in jump-diffusion models have improved answers. For example, both the value of shareholders and the optimal bankrupt level (by using the smooth-pasting condition) in the optimal capital structure problem have exact solution. We worked out these in Example 41.3.9 under the setup of Hilberink and Rogers (2002), which is an extension of Leland and Toft (1996). Moreover, in Example 41.4.6, we obtained a closed-form solution even in a two-sided jump case. By using our closed-form solution as criterion, many structural firm models in credit risk can be reconsidered and modified to see whether more phenomena in empirical studies can be captured by a jump-diffusion model.

## Acknowledgment

We thank two anonymous referees for their comments on an early draft of this chapter. We are also grateful to the editor for his useful comments.

## Bibliography

- Asmussen, S. (2000). Ruin Probabilities. World Scientific, Singapore.
- Asmussen, S., Avram, F. and Pistorius, M. R. (2004). Russian and American put Options Under Exponential Phase-Type Lévy Models. Stoch. Process. Appl. 109, 79-111.
- Bertoin, J. (1996). Lévy Processes. Cambridge Tracts in Mathematics, vol. 121. Cambridge University Press, Cambridge.
- Boyarchenko, S. I. (2000). Endogenous default under Lévy processes. Working paper, University of Texas, Austin.
- Boyarchenko, S. I. and Levendorskiĭ, S. (2002a). Perpetual American Options Under Lévy Processes. SIAM J. Control Optim. 40, 1663-1696.
- Boyarchenko, S. I. and Levendorskiĭ, S. (2002b). Barrier Options and Touch-and-Out Options Under Regular Lévy Processes of Exponential Type. Ann. Appl. Probab. 12, 1261–1298.
- Cai, J. and Yang, H. (2005). Ruin in the Perturbed Compound Poisson Risk Process Under Interest Rate. Adv. Appl. Prob. 37, 819-835.
- Chan, T. (1999). Pricing Contingent Claims on Stocks Driven by Lévy Processes. Ann. Appl. Probab. 9, 504-528.
- Chan, T. (2005). Pricing Perpetual American Options Driven by Spectrally One-Sided Lévy Processes. In Exotic Option Pricing and Advanced Lévy Models, Kyprianou, A. ed. Wiley, New York: pp. 195-216.
- Chen, Y. T., Lee, C. F. and Sheu, Y. C. (2006). On the expected discounted penalty at ruin in two-sided jump-diffusion model, submitted. National Chiao Tung University.
- Dufresne, F. and Gerber, H. U. (1989). Three Methods to Calculate the Probability of Ruin. ASTIN Bull. 19, 71-90.
- Dufresne, F. and Gerber, H. U. (1991). Risk Theory for the Compound Poisson Process that is Perturbed by Diffusion. Insur. Math. Econ. 10, 51-59.
- Friedberg, S. H., Insel, A. J. and Spence, L. E. (1997). Linear Algebra, 3rd edn. New Jersey: Prentice Hall.
- Gerber, H. U. (1970). An Extension of the Renewal Equation and Its Application in the Collective Theory of Risk. Scand. Actuar. J. 205-210.
- Gerber, H. U. and Landry, B. (1998). On the Discounted Penalty at Ruin in a Jump-Diffusion and The Perpetual Put Option. Insur. Math. Econ. 22, 263-276.
- Gerber, H. U. and Shiu, E. S. W. (1998). On the Time Value of Ruin. North Am. Actuar. J. 2, 48-78.
- Hilberink, B. and Rogers, L. C. G. (2002). Optimal Capital Structure and Endogenous Default. Finance Stoch. 6, 237-263.
- Kallenberg, O. (2002). Foundations of Modern Probability, 2nd edn. Berlin: Springer.
- Kou, S. G. and Wang, H. (2003). First Passage Times of a Jump-Diffusion Process. Adv. Appl. Probab. 35, 504-531.
- Kyprianou, A. and Surya, A. (2007). Principles of Smooth and Continuous Fit in the Determination of Endogenous Bankruptcy Levels. Finance Stoch. 11, 131-152.
- Leland, H. E. (1994). Corporate Debt Value, Bond Covenants, and Optimal Capital Structure. J. Finance 49, 1213-1252.
- Leland, H. E. and Toft, K. (1996). Optimal Capital Structure, Endogenous Bankruptcy, and the Term Structure of Credit Spreads. J. Finance 51, 987-1019.
- Merton, R. (1976). Option Pricing When Underlying Stock Returns are Discontinuous. J. Financ. Econ. 3, 125-144.
- Mordecki, E. (2002). Optimal Stopping and Perpetual Options for Lévy Processes. Finance Stoch. 6, 473-493.
- Rolski, T., Schmidli, H., Schmidt, V. and Teugels, J. (1999). Stochastic Processes for Insurance and Finance. New York: Wiley.
- Sato, K. I. (1999). Lévy Processes and Infinitely Divisible Distributions. Studies in Advanced Mathematics, Vol. 68. Cambridge: Cambridge University Press.
- Stein, E. M. and Shakarchi, R. (2005). Real Analysis. Princeton: Princeton University Press.
- Tenenbaum, M. and Pollard, H. (1985). Ordinary Differential Equations. New York: Dover.
- Tsai, C. C.-L. and Willmot, G. E. (2002). A Generalized Defective Renewal Equation for the Surplus Process Perturbed by Diffusion. Insur. Math. Econ. 30, 51-66.

## Appendix 41.A

Let \(\epsilon > 0\) and find \(M > x\) such that

\[
\int_{(-\infty, x-M-1]\cup[x+M-1,\infty)} dF(z) < \epsilon.
\]

Then, for all \(y > 0\) such that \(|x - y| \le 1/2\),

\[
\left| \int \Phi(y - z)dF(z) - \int \Phi(x - z)dF(z) \right| \le 2\|g\|_{\infty}\epsilon + \left| \int_y^{y+M} g(y - z)dF(z) - \int_x^{x+M} g(x - z)dF(z) \right| + \left| \int_{y-M}^y \Phi(y - z)dF(z) - \int_{x-M}^x \Phi(x - z)dF(z) \right| \le 2\|g\|_{\infty}\epsilon + \left| \int_{-M}^0 g(z)[f(y - z) - f(x - z)]dz \right| + \left| \int_0^M \Phi(z)[f(y - z) - f(x - z)]dz \right|,
\]

where \(f\) is the density function for \(F\). Since \(g\) and \(\Phi\) are bounded and \(f\) is continuous on \(R \setminus \{0\}\), by dominated convergence, we have

\[
\limsup_{y\to x} \left| \int \Phi(y - z)dF(z) - \int \Phi(x - z)dF(z) \right| \le 2\|g\|_{\infty}\epsilon.
\]

Since \(\epsilon > 0\) is arbitrary, the proof is completed.

To prove (41.10), we need the following lemmas and Dynkin's formula.

### Lemma 41.A.1

For every bounded Borel-measurable function \(g\) on \(R_-\), there exists a sequence of uniformly bounded functions \((g_n)\) in \(C^2_0(R_-)\) such that \(g_n \to g\) Lebesgue-a.e. on \(R_-\) and \(g_n(0) = g(0)\) for all \(n\).

**Proof.** Write \(dm\) for Lebesgue measure on \(R\). Let \(h\) be a normal density, and set \(dG(y) = h(y)dm\). Then, by the strict positivity of \(h\), \(dG\), and \(dm\) are equivalent.

Fix \(\epsilon > 0\), by dominated convergence, we can find \(N\) large enough such that \(\int_{-\infty}^0 |1_{[-N,0]} g - g| dG < \epsilon\). Also, since \(g1_{[-N,0]}\) is bounded and in \(L_1(R, dm)\), a modification of the proof of Theorem 2.4 in (Stein and Shakarchi (2005), Chapter 2), shows that we can find a sequence of uniformly bounded \(C^2_0(R_-)\)-functions \((g'_n)\) such that \(g'_n \to g1_{[-N,0]}\) \(dm\)-a.e. Since \(dG\) and \(dm\) are equivalent, \(g'_n \to g1_{[-N,0]}\) \(dG\)-a.e. Hence, by dominated convergence, we can pick \(n\) large such that \(\int |g'_n - g1_{[-N,0]}| dG < \epsilon\). We have obtained that \(\int_{-\infty}^0 |g'_n - g| dG < 2\epsilon\). And this implies that there exists a sequence of \(C^2_0(R_-)\)-functions \((g_n)\) such that \(g_n \to g\) \(dm\)-a.e. on \(R_-\). In addition, it is clear that we can pick \((g_n)\) to be uniformly bounded.
