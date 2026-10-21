
where there are only good funds and zero-alpha funds. We vary the true fraction π_g and the good alpha parameter α_g, and keep track of which funds in the simulation actually have good or zero alphas. We record the discovery rates for each method as a function of the parameter values, averaging the number of true and false discoveries across 1000 simulation trials. Like in the previous section we bootstrap from the hedge fund data, but now we form a mixture of the two known distributions and we run a two-group version of our model on each draw of the mixture, treating each draw as if it was the original data. (The equations for the two-group model are given in the Internet Appendix.)

We compare the discovery rates of three approaches. The first is a naïve application of the simple t-ratio. Setting the size of the one-tailed test to 10%, an empirical critical value of the t-ratio is found by simulating each fund separately under the null hypothesis that its alpha is zero. The funds whose alpha t-ratios exceed their critical values are discovered to have positive alphas. The calculation is naïve in that it takes no account of the multiple comparisons.

The second approach is the classical false discovery rate (FDR) method. Here, the critical value of the t-ratio is adjusted to obtain a desired false discovery rate in the cross-section of funds. We search for a size of the test, γ, so that γ(π0,C)/Fg = 0.10, where π0,C is the classical estimator of the fraction of zero-alpha funds and Fg is the fraction of funds where the null hypothesis is rejected. We select FDR = 10%, following BSW who find (Table V) their best results at this FDR value. Both π0,C and Fg depend on the size of the tests. Simulation under the null hypothesis at the optimal test size determines a critical value for the alpha t-ratio, and all funds with alpha t-ratios in excess of this single critical value are discovered to have positive alphas. Note that since there is no confusion parameter in the two-group model, the classical FDR cannot be biased by confusion in this example.

The third approach is our method as described in equations (108.4) and (108.5). For each draw from the mixture of distributions we implement our simulation method, treating that draw like we do the original data. We use a two-group model with a test size of γ = 10%. Using the estimated model parameters, a fund is discovered to have a positive alpha if the posterior probability given its alpha estimate, αp, satisfies P(α > 0|αp) > P(α = 0|αp), so that a positive alpha is more likely than a zero-alpha.

Table 108.3 summarizes the results of our analysis of the discovery rates. We present results for two choices of the true alpha values. The first, 0.252% per month, is the value from Table 108.5 below, estimated on the hedge funds when the test size is 10%. The second value, 0.861% is the cutoff for

## Table 108.3: Analysis of discovery rates.

| Fraction |  | Simple *t*-test |  | FDR Method |  |  | CF Method |  |  |
|---|---|---|---|---|---|---|---|---|---|
| Good α<sub>g</sub> | Good, π<sub>g</sub> | Correct | False | π<sub>g,C</sub> | Correct | False | π<sub>g,CF</sub> | Correct | False |
| 0.252 | 0.00 | 0.000 | 0.108 | 0.008 | 0.000 | 0.108 | 0.078 | 0.000 | 0.042 |
| 0.252 | 0.10 | 0.032 | 0.097 | 0.031 | 0.031 | 0.095 | 0.131 | 0.013 | 0.059 |
| 0.252 | 0.20 | 0.069 | 0.085 | 0.059 | 0.067 | 0.082 | 0.218 | 0.045 | 0.095 |
| 0.252 | 0.30 | 0.107 | 0.074 | 0.090 | 0.103 | 0.070 | 0.325 | 0.109 | 0.139 |
| 0.252 | 0.40 | 0.132 | 0.065 | 0.106 | 0.126 | 0.061 | 0.385 | 0.166 | 0.155 |
| 0.252 | 0.50 | 0.159 | 0.054 | 0.126 | 0.154 | 0.051 | 0.457 | 0.243 | 0.174 |
| 0.252 | 0.60 | 0.198 | 0.044 | 0.158 | 0.191 | 0.041 | 0.569 | 0.377 | 0.196 |
| 0.252 | 0.70 | 0.231 | 0.031 | 0.181 | 0.224 | 0.028 | 0.649 | 0.513 | 0.175 |
| 0.252 | 0.80 | 0.271 | 0.020 | 0.213 | 0.262 | 0.019 | 0.743 | 0.659 | 0.135 |
| 0.252 | 0.90 | 0.301 | 0.011 | 0.236 | 0.291 | 0.011 | 0.801 | 0.798 | 0.078 |
| 0.252 | 1.00 | 0.333 | 0.000 | 0.260 | 0.324 | 0.000 | 0.851 | 0.907 | 0.000 |
| 0.861 | 0.00 | 0.000 | 0.109 | 0.009 | 0.000 | 0.110 | 0.031 | 0.000 | 0.013 |
| 0.861 | 0.10 | 0.069 | 0.096 | 0.078 | 0.073 | 0.088 | 0.106 | 0.042 | 0.031 |
| 0.861 | 0.20 | 0.138 | 0.087 | 0.148 | 0.143 | 0.078 | 0.202 | 0.117 | 0.046 |
| 0.861 | 0.30 | 0.205 | 0.077 | 0.233 | 0.210 | 0.070 | 0.291 | 0.192 | 0.056 |
| 0.861 | 0.40 | 0.287 | 0.062 | 0.284 | 0.298 | 0.055 | 0.404 | 0.298 | 0.065 |
| 0.861 | 0.50 | 0.335 | 0.053 | 0.363 | 0.366 | 0.048 | 0.493 | 0.389 | 0.075 |
| 0.861 | 0.60 | 0.420 | 0.044 | 0.429 | 0.426 | 0.041 | 0.589 | 0.483 | 0.079 |
| 0.861 | 0.70 | 0.492 | 0.032 | 0.500 | 0.521 | 0.033 | 0.687 | 0.597 | 0.083 |
| 0.861 | 0.80 | 0.576 | 0.020 | 0.587 | 0.617 | 0.022 | 0.806 | 0.742 | 0.086 |
| 0.861 | 0.90 | 0.635 | 0.011 | 0.645 | 0.680 | 0.012 | 0.884 | 0.856 | 0.070 |
| 0.861 | 1.00 | 0.709 | 0.000 | 0.719 | 0.758 | 0.000 | 0.971 | 0.990 | 0.000 |

*Notes:* This table presents simulated discovery rates for three methods. The values of the good alpha, α<sub>g</sub>, in the simulated populations are shown in the first column and the fractions of good funds, π<sub>g</sub>, are shown in the second column. The discovery rates are the fractions of funds in the simulated sample that a test finds to be a positive-alpha fund, averaged over the 1000 simulation trials. The total fraction discovered to be good is the sum of the False discoveries and the Correct discoveries. The three methods are the simple *t*-test, the classical false discovery rate method (FDR Method) and our approach (CF Method). The symbol π<sub>g,C</sub> denotes the classical FDR estimate of the fraction of positive-alpha funds averaged across simulation trials. The symbol π<sub>g,CF</sub> denotes our average estimate. The simulations are based on a parametric bootstrap from a sample of 3620 hedge funds during January 1994–March 2012.

the upper 10% tail of the alphas in the original hedge fund sample, as shown in Table 108.1.

The rows in Table 108.3 vary the true fraction of good funds between 0.0 and 100%. Consider the results in the first ten rows. In the first row, when the true fraction of good funds is zero, there are no correct discoveries to be had. The number of false discoveries by both the classical *t*-ratio and the FDR method are close to the desired 10%. In row ten, when all of the funds are good, there are no false discoveries to be had. As the fractions of good funds is increased across the rows, the FDR method delivers the smallest number of false discoveries among the three methods, but the classical t-ratio is very close behind. The FDR method is based on the biased classical estimator, which finds too many zero-alpha funds, so it tends to over-correct for false discoveries. For example, when the true fraction of good funds exceeds 50%, the FDR method delivers 5% or fewer false discoveries, even though it is calibrated to a 10% false discovery rate. The FDR method also posts the smallest number of correct discoveries among the methods, topping out at only 32.4% when the true fraction is 100%. The correct discovery rates of the classical t-ratio are slightly better. Interpreting the discovery rates as size and power, this says that both the naïve t-ratio and the FDR method using the classical estimator are undersized: when the desired false discovery rate is 10% the actual false discovery rate is lower than 10%.

Our “CF” method turns in the highest rate of correct discoveries. The estimates of the π_g fractions are considerably more accurate, and the total discovery rates are usually much closer to the actual fractions of good funds than with the other methods. Our method excels in correct detection, especially when the fraction of good funds reaches and exceeds 50% (55% is the value that we estimate using the two-group model for hedge funds in Table 108.5). The correct discovery rates of the CF method top out at 90.7% when the true fraction is 100%, where the other two methods deliver 33% or less.

The cost of the improved power of our CF method is more false discoveries than either the classical t-ratio or the FDR method. When the true fraction of good funds is in the 30–80% range, our method posts false discovery rates in the 14–20% range. It would be possible in future research, to assign utility costs to the different cases of potential misclassification, and our method could then make a different tradeoff between correct and false discoveries. In this example, once the investor has incurred the costs of engaging in active fund selection, the utility cost of falsely discovering a zero alpha fund to be a good fund is likely to be very low, given that the investor’s alternative decision is to invest in a zero alpha fund. The improved ability of our method to correctly detect positive-alpha funds is the important result of this example.

The last ten rows of Table 108.3 represent a world in which the good alpha is the value that defines the top 10% in our hedge fund sample. The classical estimates of π_g are less biased in this example. This illustrates that while the classical estimator does not refer to the locations of the nonzero
