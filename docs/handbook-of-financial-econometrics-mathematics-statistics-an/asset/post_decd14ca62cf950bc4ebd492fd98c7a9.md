
![](img/31ee7e6fa5107b22bbf7960ec96106a1_1614_0.png)

**Figure 39.5:** Wing model calibration to implied volatility of TXO data.

As mentioned in Section 39.2, under the Matlab experimental environment, time series data of futures and option’s prices have to be relocated to GPUarray.⁷ Since the typical Matlab solver `blsimpv.m` for implied volatility calculation is not a GPU-enabled function, the bisection⁸ method is introduced to calculate implied volatilities. As for the wing model calibration to implied volatility curves, if the number of updated implied volatility is less than 6, we use the previously estimated parameters⁹ of the wing model.

Two implied volatility curves with their fitted wing models are shown in Figure 39.5. These are results calibrated at two different time points, i.e., 11:10:26 and 11:10:57, respectively.

In our dataset on 8/25/2015, there are more than 120,000 call TXO option prices in total. Our task is to fit the wing model every second, so it is about 18,000 times per trading day in TAIFEX. Table 39.2 is the table of GPU parallel computation time before and after acceleration.

From Table 39.2, it is observed that on average for each wing model calibration, 49 ms (0.049 s = 875.34/18,000 times) and merely 20 ms (0.02 s = 352.82/18,000 times) are needed on traditional CPU computing and GPU computing frameworks, respectively. The effect of GPU parallel acceleration for fitting implied volatility curve by using the wing model is significant. It reduces about 60% computing time. Since the performance of Matlab on GPU is less than CUDA, we can expect to gain more efficiency if CUDA is implemented.

⁷Stock = gpuArray(stock); call_data = gpuArray(call_data).

⁸If we use Newton’s method instead, we will gain more significant effect of acceleration. However, the bisection method is more stable.

⁹The function polyfit in Matlab can fit the data in quadratic form and it is also GPU-enabled function which can directly be used by GPU to accelerate.

Table 39.2: Comparisons of execution time, numerical results, and hardware configuration of CPU and GPU computing on implied volatility calculation and the wing model calibration.

|  | CPU time | GPU time | Time reduction |
|---|---|---|---|
| Implied Vol Calculation | 14.78 s in total (0.123 ms per option price) | 0.53 s in total (0.004 ms per option price) | 96.06% |
| Wing Model Calibration | 875.34 s in total (49 ms each calibration) | 352.82 s in total (20 ms each calibration) | 60.35% |
| Hardware model | CPU: Intel®Core(TM) i5-6300HQ | GPU: NVIDIA GeForceGTX950M (Total number of cores: 640) |  |
| Software | Matlab | Matlab |  |

## 39.5 Conclusion

Engineers, scientists, and financial quants have been successfully employing GPU technology for their domain applications. However, GPU’s programming language CUDA is low-level and it requires technical knowledge about hardware device. With minimal effort, Matlab users can take advantage of the promising power of GPUs by using gpuArrays and GPU-enabled functions to speed up MATLAB operations. We illustrate several typical examples from computational finance and find that Matlab GPU computing can be beneficial. Hands on codes for Matlab CPU and GPU are provided for comparisons. Moreover, a fast calibration of the wing model to implied volatilities in high frequency is provided. It can play a crucial role on establishing a price stability system for option trading exchanges.

## Bibliography

Carr, P. and Madan, D. (1999). Option Evaluation Using the Fast Fourier Transform. Journal of Computational Finance, 24, 61–73.
Fouque, J. P. and Han, C. H. (2007). A Martingale Control Variate Method for Option Pricing with Stochastic Volatility. ESAIM Probability & Statistics, 11, 40-54.
Han, C. H. (2017). Research on Instantaneous Pricing Models of Equity Futures and Options in High Frequency. Technical Report (in Chinese), TAIFEX.
Han, C. H. and Lin, Y.-T. (2014). Accelerated Variance Reduction Methods on GPU. *Proceedings of the 20th IEEE International Conference on Parallel and Distributed Systems.*
Hull, J. (2011). *Options, Futures, and other Derivatives*, 8th ed. Pearson/Prentice Hall.
Kienitz, J. and Wetterau, D. (2012). *Financial Modeling: Theory, Implementation and Practice with Matlab Source.* Wiley Finance.
Lambertson, D. and Lapeyre, B. (2007). *Introduction to Stochastic Calculus Applied to Finance.* 2nd ed. Chapman Hall/CRC.

## Chapter 40

## Does VIX Truly Measure Return Volatility?

K. Victor Chow, Wanjun Jiang and Jingrui Li

## Contents

- 40.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . 1534
- 40.2 Related Literature . . . . . . . . . . . . . . . . . . . . . . 1536
- 40.3 Ex ante Moment-Combination and Option Prices . . . . . 1537
- 40.4 The VIX and GVIX Indexes . . . . . . . . . . . . . . . . . . 1540
- 40.5 Empirical Investigation . . . . . . . . . . . . . . . . . . . 1546
- 40.6 Conclusion . . . . . . . . . . . . . . . . . . . . . . . . . . 1557
- Acknowledgment . . . . . . . . . . . . . . . . . . . . . . . . . . 1558
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . 1558

## Abstract

This chapter demonstrates theoretically that without imposing any structure on the underlying forcing process, the model-free CBOE volatility index (VIX) does not measure market expectation of volatility but that of a linear moment-combination. Particularly, VIX undervalues (overvalues) volatility when market return is expected to be negatively (positively) skewed. Alternatively, we develop a model-free generalized volatility index (GVIX). With no diffusion assumption, GVIX is formulated directly from the definition of log-return variance, and VIX is a special case of the GVIX. Empirically, VIX generally understates the true volatility, and the estimation errors considerably enlarge during volatile markets. The spread between GVIX and VIX follows a mean-reverting process.

K. Victor Chow
West Virginia University
e-mail: Victor.Chow@mail.wvu.edu

Wanjun Jiang
Peking University
e-mail: jiangwj@gsm.pku.edu.cn

Jingrui Li
Tulane University
e-mail: jli61@tulane.edu

**Keywords**
Implied volatility • VIX • *Ex ante* moments.

### 40.1 Introduction

One of the most frequently used devices to estimate expectation of market volatility is the Chicago Board of Option Exchanges (CBOE) Volatility Index (VIX). The index, designed to capture the market’s aggregate expectation of future volatility over the next 30 days, was originally introduced in 1993 and based on the implied volatility of at-the-money option prices on the S&P100 index. Since the calculation of implied volatility relied heavily on assumptions of option pricing models, in 2003, CBOE made a significant change in the volatility estimating methodology to avoid the problem of modeling specification. The 2003 VIX formulation has intuitive appeal in that option premiums and the underlying asset (S&P 500 index) prices reflect the same information, and the *ex ante* volatility of asset’s returns can thus be directly extracted from option market data without employing any option pricing model. Simply, a volatility forecast does not require a specific model, only current option prices. Coined with Demeterfi *et al.* (1999), this concept of model-free implied volatility has been formalized by Britten-Jones and Neuberger (2000) and further extended by Jiang and Tian (2005, 2007).

Specifically, under diffusion assumptions of the return generating process, the arbitrage-free argument implies that the fair value of expected volatility is extractable from the market price of a portfolio composited by all possible out-of-the-money (OTM) call/put options of the underlying index with weight inversely proportional to square value of the strike price. As demonstrated by Jiang and Tian (2005), this model-free implied volatility provides a more efficient forecast for future realized volatility and is more efficient than the historical variance even if the underlying asset price process has jumps. Because of the superiority of the model-free approach to its predecessor, CBOE has recently applied its formulation to a wide range of indices including ones for Nasdaq 100, Dow Jones Industry Average, Russell 2000, interest rate, crude oil, gold/silver, energy, currency (Euro), as well as individual stocks such as Amazon, Apple, Goldman Sachs, Google and IBM.

This chapter argues that the expression of the CBOE volatility index (VIX) is in fact not model-free because its estimates are dependent on
