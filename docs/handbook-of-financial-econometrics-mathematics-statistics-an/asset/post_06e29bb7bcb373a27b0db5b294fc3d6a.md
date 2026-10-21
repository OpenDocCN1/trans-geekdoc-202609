
Next, we multiply equation (12.33) by η^l, where η^l = 1/γ^l and then take an average over all investors, where the weights are the investors’ relative wealth.⁷

$$E_t r_{i,t+1} - r_{f,t+1} = -\frac{V_{ii}}{2} + \frac{1}{\eta^m}V_{im}^l + \left(\frac{1}{\eta^m} - 1\right)\sum_l \omega^l V_{ih}^l$$ $$\quad + \left(1 - \frac{1}{\eta^m}\right)\sum_l \omega^l V_{i\pi}^l + \left(1 - \frac{1}{\eta^m}\right)\sum_l \omega^l V_{ih\pi}^l,\tag{12.34}$$

where,

$$\eta^m = \left(\sum_l W^l \eta^l\right)/\left(\sum_l W^l\right)\quad\text{and}\quad \omega^l = \frac{(1 - \gamma^l)W^l}{\sum_l (1 - \gamma^l)W^l}.$$

The drawback is that the third, fourth, and fifth terms of equation (12.34) are unobservable. In the international setting, they contain the covariances of security i with the heterogeneous investors’ rate of market return forecasting, rate of inflation, and inflation forecasting. They are weighted by their wealth and by one minus their relative risk aversion. Because it is impossible to measure each individual’s relative risk aversion, we cannot use the wealth and relative risk aversion weighted average rate of market return forecasting, rate of inflation, or inflation forecasting. But if all the individuals of the same country who use the same deflator and use the national wealth weighted average relative risk aversion instead of the individual ones, we have a sum of one term per each country.

Several interesting and intuitive results emerge. First, the international asset risk premium adjusted for one-half its own variance is related to its covariances with: (a) the market portfolio, (b) the aggregate of innovation in discounted expected future market returns from different investors across countries, (c) the aggregate of inflation from different countries, and (d) the aggregate of innovation in inflation of different investors, discounted using values for expected future inflation across different countries. The weights are 1/η^m, 1/η^m − 1, 1 − 1/η^m, 1 − 1/η^m, respectively that sum to one.⁸

Second, the international asset is priced without referring to its covariance with consumption growth. Third, because consumption has been substituted

⁷We follow Adler and Dumas (1983) to deal with the intrinsic problem of aggregation in international asset pricing.
⁸The market hedging risk is a weighted average of the market portfolio for investors from different countries. This is different from the domestic counterpart of Campbell (1993).

out, the coefficient of risk tolerance, η^m, is the only preference parameter that enters the asset pricing model — equation (12.34).

If we are willing to make further simplifying assumptions, we can obtain a more compact result. Specifically, if investors use identical current and future market portfolio returns, we can take an average over all investors, where the weights are their relative wealth, and thus obtain a simple version of the intertemporal international asset pricing model:

$$E_t r_{i,t+1} - r_{f,t+1} = -\frac{V_{ii}}{2} + \gamma^m V_{im} + (\gamma^m - 1)V_{ih} + (1 - \gamma^m)\sum_l \omega^l V_{i\pi}^l + (1 - \gamma^m)\sum_l \omega^l V_{ih\pi}^l$$ (12.35)

where

$$\gamma^m = \left(\sum_l W^l \gamma^l\right)/\left(\sum_l W^l\right)\quad\text{and}\quad \omega^l = \frac{(1 - \gamma^l)W^l}{\sum_l (1 - \gamma^l)W^l}.$$

In our model, inflation rate measured in currency of country L+1 contains inflation rate in domestic and exchange rate between domestic currency and the currency of country L + 1. Therefore, we should separate our inflation rate measured in currency of country L + 1 to country l's inflation rate and percentage change in exchange rate. We assume that π^{L+1} is country l's price level measured in currency of country L + 1, π^l is country l's price level measured in currency of country l, and S is currency L + 1 price of currency l, S $(L + 1)/$(l).

$$\frac{\pi_{t+1}^{L+1}}{\pi_t^{L+1}} = \frac{\pi_{t+1}^l}{\pi_t^l} * \frac{S_{t+1}}{S_t},$$

$$\Delta \ln(\pi_{t+1}^{L+1}) = \Delta \ln(\pi_{t+1}^l) + \Delta \ln(S_{t+1}),$$

$$r_{\pi^{L+1},t+1} = r_{\pi^l,t+1} + r_{e,t+1},$$

$$V_{i,\pi^{L+1}}^l = V_{i,\pi^l}^l + V_{i,e}^l.$$

Therefore, inflation risk includes inflation risk measured in domestic currency and exchange rate risk. If domestic inflation is a stable variable, the only random component in π is the relative change in the exchange rate between the numeraire currency and the investor's home currency. Then, V_{iπ}^l is a pure measure of the exposure of asset i to the exchange rate risk and V_{ihπ}^l is a measure of the exposure of asset i to hedge against the exchange rate risk of the country in which investor l resides.

Equation (12.35) also states that the exchange rate risk is different from the hedging risk. Indeed, if V_{ih} and V_{iπ}^l are significantly large, then their contribution to expected return depends on whether γ^m is different from one. This may be the reason why Dumas and Solnik (1995) argue that exchange rate risk premium may be equivalent to intertemporal risk premium. Their conjecture is, however, based on an empirical “horse race” test between an international model and an intertemporal model.

## 12.3.3 Empirical methodology

### 12.3.3.1 A vector autoregressive model

We adopt the vector autoregressive (VAR) approach of Campbell (1991) and construct a state variable system to estimate the market hedging portfolio and the currency hedging portfolio. We assume that the market index return, r_m, is the 1st element of a K-element state variable vector z_t and the currency deposit return, r_{e,t}^l, is the l + 1st element, l = 1, 2, …, L. The other elements of z_t are known to the market at the end of period t and are related to the forecasting of future market returns and currency deposit returns. In addition, we assume that all the variables z_t are demeaned and that the vector z_t follows a first-order VAR.

$$z_{t+1} = \Psi z_t + u_{t+1}, \tag{12.36}$$

where Ψ is a K × K companion matrix of the VAR. The representation of the VAR as a first-order is not restrictive because a higher-order VAR can always be stacked into first-order companion form as discussed by Schwarz (1978). Then we can use the first order VAR to generate simple multi-period forecasts of future returns as

$$E_t z_{t+1+i} = \Psi^{i+1} z_t. \tag{12.37}$$

Define a K-element constant vector e1 whose 1st element is one and the other elements are all zero. Then, r_{m,t} = e1' z_t and r_{m,t+1} - E_t r_{m,t+1} = e1' u_{t+1}. Define another K-element constant vector e_l whose l + 1st element is one and other elements are all zero. Then, r_{e,t}^l = e_l' z_t and r_{e,t+1}^l - E_t r_{e,t+1}^l = e_l' u_{t+1}.

It follows that the discounted sum of forecast revisions in market returns is

$$\begin{aligned}
(E_{t+1} - E_t) \sum_{j=1}^{\infty} \rho^j r_{m,t+1+j} &= e1' \sum_{j=1}^{\infty} \rho^j \Psi^j u_{t+1} \\
&= e1' \rho \Psi (\mathbf{I} - \rho \Psi)^{-1} u_{t+1} \\
&= \theta_h' u_{t+1},
\end{aligned} \tag{12.38}$$

where \(\theta'_h\) is defined as \(e1'\rho\Psi(\mathbf{I}-\rho\Psi)^{-1}\) which measures the importance of each state variable in forecasting future returns on the market.

Similarly, the discounted sum of forecast revisions in currency deposit returns is

\[
\begin{aligned}
(E_{t+1}-E_t)\sum_{j=1}^{\infty}\rho^j r^l_{e,t+1+j}
&=e_l'\sum_{j=1}^{\infty}\rho^j\Psi^j u_{t+1}\\
&=e_l'\rho\Psi(\mathbf{I}-\rho\Psi)^{-1}u_{t+1}\\
&=\theta'_e u_{t+1}.
\end{aligned}
\tag{12.39}
\]

where \(\theta'_e\) is defined as \(e_l'\rho\Psi(\mathbf{I}-\rho\Psi)^{-1}\) which measures the importance of each state variable in forecasting future returns on the currency deposit.

Thus, equation (12.34) can now be written as

\[
\begin{aligned}
E_t r_{i,t+1}-r_{f,t+1}
={}&-\frac{V_{ii}}{2}+\gamma V_{im}+(1-\gamma)\sum_{l=1}^{L}\omega^l V^l_{ie}\\
&+\sum_{k=1}^{K}\left[(\gamma-1)\theta_{h,k}+(1-\gamma)\sum_{l=1}^{L}\omega^l\theta^l_{e,k}\right]V_{ik}.
\end{aligned}
\tag{12.40}
\]

We define \(V_{ik}\equiv\operatorname{var}(r_{i,t+1},u_{k,t+1})\), where \(u_{k,t+1}\) is the \(k\)th element of \(u_{t+1}\). Equation (12.40) implies that the expected log excess return on asset \(i\), adjusted for the effect of Jensen’s inequality, is linear in the covariance of the return with the \(K\) factors. The set of restrictions on the risk prices of the factor is the most important contribution of the intertemporal optimization problem in the international asset pricing model.

### 12.3.3.2 Econometric specification

Equation (12.35) appears to be the natural relation to use in an empirical investigation of the intertemporal IAPM because it takes into account the investor’s use of newly acquired information in creating a portfolio, thus taking into account his hedging strategy. The model requires equation (12.35) to hold for every asset including the market portfolio, market hedging portfolio, currency portfolio and currency hedging portfolio. Therefore, we assume
