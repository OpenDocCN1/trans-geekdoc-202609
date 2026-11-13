Equation (3.1). The first obvious difference is the introduction of the nonlinear function \(g\): indeed, there is no reason (beyond simplicity and interpretability) why we should restrict the model to linear relationships. One early reference for nonlinearities in asset pricing kernels is Bansal and Viswanathan (1993).

More importantly, the second difference between (3.7) and (3.1) is the shift in the time index. Indeed, from an investor's perspective, the interest is to be able to *predict* some information about the structure of the cross-section of assets. Explaining asset returns with synchronous factors is not useful because the realization of factor values is not known in advance. Hence, if one seeks to extract value from the model, there needs to be a time interval between the observation of the state space (which we call \(\mathbf{x}_{t,n}\)) and the occurrence of the returns. Once the model \(\hat{g}\) is estimated, the time-\(t\) (measurable) value \(g(\mathbf{x}_{t,n})\) will give a forecast for the (average) future returns. These predictions can then serve as signals in the crafting of portfolio weights (see Chapter 12 for more on that topic).

While most studies do work with returns on the l.h.s. of (3.7), there is no reason why other indicators should not be used. Returns are straightforward and simple to compute, but they could very well be replaced by more sophisticated metrics, like the Sharpe ratio, for instance. The firms' features would then be used to predict a risk-adjusted performance rather than simple returns.

Beyond the explicit form of Equation (3.7), several other ML-related tools can also be used to estimate asset pricing models. This can be achieved in several ways, some of which we list below.

First, one mainstream problem in asset pricing is to characterize the stochastic discount factor (SDF) \(M_t\), which satisfies \(\mathbb{E}_t[M_{t+1}(r_{t+1,n}-r_{t+1,f})]=0\) for any asset \(n\) (see Cochrane (2009)). This equation is a natural playing field for the generalized method of moment (Hansen (1982)): \(M_t\) must be such that

\(\mathbb{E}[M_{t+1}R_{t+1,n}g(V_t)] = 0, \quad (3.8)\)

where the instrumental variables \(V_t\) are \(\mathcal{F}_t\)-measurable (i.e., are known at time \(t\)) and the capital \(R_{t+1,n}\) denotes the excess return of asset \(n\). In order to reduce and simplify the estimation problem, it is customary to define the SDF as a portfolio of assets (see chapter 3 in Back (2010)). In Chen et al. (2020), the authors use a generative adversarial network (GAN, see Section 7.6.1) to estimate the weights of the portfolios that are the closest to satisfy (3.8) under a strongly penalizing form.

A second approach is to try to model asset returns as linear combinations of factors, just as in (3.1). We write in compact notation

\(r_{t,n} = \alpha_n + \beta'_{t,n}\mathbf{f}_t + \epsilon_{t,n},\)

and we allow the loadings \(\beta_{t,n}\) to be time-dependent. The trick is then to introduce the firm characteristics in the above equation. Traditionally, the characteristics are present in the definition of factors (as in the seminal definition of Fama and French (1993)). The decomposition of the return is made according to the exposition of the firm's return to these factors constructed according to market size, accounting ratios, past performance, etc. Given the exposures, the performance of the stock is attributed to particular style profiles (e.g., small stock, or value stock, etc.).

Habitually, the factors are heuristic portfolios constructed from simple rules like thresholding. For instance, firms below the 1/3 quantile in book-to-market are growth firms and those above the 2/3 quantile are the value firms. A value factor can then be defined by the