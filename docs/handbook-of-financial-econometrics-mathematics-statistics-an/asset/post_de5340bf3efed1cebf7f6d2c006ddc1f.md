
firm, again with a strike price equal to the face value of debt and a time-to-maturity of T.

Symbolically, the Merton model stipulates that the equity value of a firm satisfies

$$E = V N(d_1) - e^{-rT} F N(d_2), \tag{126C.2}$$

where $E$ is the market value of the firm’s equity, $F$ is the face value of the firm’s debt, $r$ is the instantaneous risk-free rate, $N(\cdot)$ is the cumulative standard normal distribution function, $d_1$ is given by

$$d_1 = \frac{\ln\left(\frac{V}{F}\right) + \left(r + 0.5\sigma_V^2\right)T}{\sigma_V\sqrt{T}}, \tag{126C.3}$$

and $d_2$ is just $d_1 - \sigma_V\sqrt{T}$.

The Merton DD model makes use of two important equations. The first is the Black–Scholes–Merton equation (126C.2), expressing the value of a firm’s equity as a function of the value of the firm. The second relates the volatility of the firm’s value to the volatility of its equity. Under Merton’s assumptions the value of equity is a function of the value of the firm and time, so it follows directly from Ito’s lemma that

$$\sigma_E = \left(\frac{V}{E}\right)\frac{\partial E}{\partial V}\sigma_V. \tag{126C.4}$$

In the Black–Scholes–Merton model, it can be shown that $\frac{\partial E}{\partial V}=N(d_1)$, so that under the Merton model’s assumptions, the volatilities of the firm and its equity are related by

$$\sigma_E = \left(\frac{V}{E}\right)N(d_1)\sigma_V, \tag{126C.5}$$

where $d_1$ is defined in equation (126C.3).

The Merton DD model basically uses these two nonlinear equations (126C.2) and (126C.5), to translate the value and volatility of a firm’s equity into an implied probability of default. In most applications, the Black–Scholes–Merton model describes the unobserved value of an option as a function of four variables that are easily observed (strike price, time-to-maturity, underlying asset price, and the risk-free rate) and one variable that can be estimated (volatility). In the Merton DD model, however, the value of the option is observed as the total value of the firm’s equity, while the value of the underlying asset (the total value of the firm) is not directly observable. Thus, while $V$ must be inferred, $E$ is easy to observe in the marketplace by multiplying the firm’s shares outstanding by its current stock price. Similarly,

in the Merton DD model, the volatility of equity, $\sigma_E$, can be estimated but the volatility of the underlying firm, $\sigma_V$, must be inferred.

The first step in implementing the Merton DD model is to estimate $\sigma_E$ from either historical stock returns data or from option-implied volatility data. The second step is to choose a forecasting horizon and a measure of the face value of the firm’s debt. For example, it is common to use historical returns data to estimate $\sigma_E$, assume a forecasting horizon of 1 year ($T = 1$), and take the book value of the firm’s total liabilities to be the face value of the firm’s debt.

The third step is to collect values of the risk-free rate and the market equity of the firm. After performing these three steps, we have values for each of the variables in equations (126C.2) and (126C.5) except for $V$ and $\sigma_V$, the total value of the firm and the volatility of firm value, respectively.

The fourth, and perhaps most significant, step in implementing the model is to solve equation (126C.2) numerically for values of $V$ and $\sigma_V$. Once this numerical solution is obtained, the distance to default can be calculated as

$$\text{DD} = \frac{\ln\left(\frac{V}{F}\right) + (\mu - 0.5\sigma_V^2)T}{\sigma_V\sqrt{T}}, \qquad (126C.6)$$

where $\mu$ is an estimate of the expected annual return of the firm’s assets. The corresponding implied probability of default, sometimes called the expected default frequency (or EDF), is

$$\pi_{\text{Merton}} = N\left(-\left(\frac{\ln\left(\frac{V}{F}\right) + (\mu - 0.5\sigma_V^2)T}{\sigma_V\sqrt{T}}\right)\right) = N(-\text{DD}). \qquad (126C.7)$$

If the assumptions of the Merton model really hold, the Merton DD model should give very accurate default forecasts. In fact, if the Merton model holds completely, the implied probability of default defined above, $\pi_{\text{Merton}}$, should be a sufficient statistic for default forecasts.

Simultaneously solving equations (126C.2) and (126C.5) is reasonably straightforward. However, Crosbie and Bohn (2003) explain that “In practice the market leverage moves around far too much for [equation (126C.5)] to provide reasonable results.” To resolve this problem, we follow Crosbie and Bohn (2003) and Vassalou and Xing (2004) by implementing a complicated iterative procedure. First, we propose an initial value of $\sigma_V = \sigma_E[E/(E+F)]$ and we use this value of $\sigma_V$ and equation (126C.2) to infer the market value of each firm’s assets every day for the previous year. We then calculate the

implied log return on assets each day and use that returns series to generate new estimates of $\sigma_V$ and $\mu$. We iterate on $\sigma_V$ in this manner until it converges (so the absolute difference in adjacent $\sigma_V$s is less than $10^{-3}$). Unless specified otherwise, in the rest of the paper values of $\pi_{\text{Merton}}$ are calculated by following this iterative procedure and calculating the corresponding implied default probability using equation (126C.7).

## Chapter 127

## Predicting Credit Card Delinquencies: An Application of Deep Neural Networks*

Ting Sun and Miklos A. Vasarhelyi

## Contents

- 127.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4350
- 127.2 Literature Review . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4352
- 127.2.1 Statistical modeling . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4352
- 127.2.2 Machine learning . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4353
- 127.2.3 Artificial neural networks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4354
- 127.2.4 Deep neural networks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4356
- 127.3 Deep Learning Approach . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4357
- 127.3.1 The basic idea of deep learning . . . . . . . . . . . . . . . . . . . . . . . . . 4357
- 127.3.2 The differences between deep learning and conventional machine learning approaches . . . . . 4358
- 127.4 Data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4359
- 127.5 Experimental Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4361
- 127.5.1 Splitting the data . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4362
- 127.5.2 Tuning the hyperparameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4362
- 127.5.3 Techniques handling data imbalance . . . . . . . . . . . . . . . . . . . . . 4365
- 127.6 Results . . . . . . . . . . . . . . . . . . . . . . . . . . 4365
- 127.6.1 The predictor importance . . . . . . . . . . . . . . . 4365
- 127.6.2 The predictive result for cross validation . . . . 4367
- 127.6.3 Z-Test . . . . . . . . . . . . . . . . . . . . . . . . . . . 4370
- 127.6.4 Prediction on test set . . . . . . . . . . . . . . . . . 4370
- 127.7 Conclusion and Limitations . . . . . . . . . . . . . . . . 4373
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4374
- Appendix 127A Variable Definition . . . . . . . . . . . . . . . 4377
- Appendix 127B Summary Statistics . . . . . . . . . . . . . . . 4379
- Appendix 127C Differences of the Mean for Important Variables between Groups . . . . . . . . . . . . . . . . . . . . . . . . . . 4380

## Abstract

The objective of this paper is 2-fold. First, it develops a prediction system to help the credit card issuer model the credit card delinquency risk. Second, it seeks to explore the potential of deep learning (also called deep neural network), an emerging artificial intelligence technology, in credit risk domain. With a real-life credit card data linked to 711,397 credit card holders from a large bank in Brazil, this study develops a deep neural network to evaluate the risk of credit card delinquency based on the client’s personal characteristics and the spending behaviors. Compared to machine learning algorithms of logistic regression, naïve Bayes, traditional artificial neural network, and decision tree, deep neural network has a better overall predictive performance with the highest F scores and AUC. The successful application of deep learning implies that artificial intelligence has great potential to support and automate credit risk assessment for financial institutions and credit bureaus.

## Keywords

Credit card delinquency • Deep neural network • Artificial intelligence • Risk assessment • Machine learning.

### 127.1 Introduction

Credit card debt is climbing rapidly. For example, the total amount of outstanding revolving credit debt in the US has reached more than $1 trillion in 2017, according to a report of the Federal Reserve.¹ This is the highest level of credit card debt since January 2009 (Porche, 2017). In the UK, the annual rate of credit card lending in September 2017 expanded by 9.2% on the same month a year earlier (Chu, 2017). This trend serves as an alarm for a high risk of credit card delinquencies. S&P/Experian Bankcard Default Index shows that the credit card delinquency rate in the US in March 2017 has reached
