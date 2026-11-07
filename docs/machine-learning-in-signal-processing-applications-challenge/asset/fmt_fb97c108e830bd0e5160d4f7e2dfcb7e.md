
In this work, we use six variants which, like their roots, are used to estimate the frequencies and amplitudes contained in the stator current signal of the machine. And apart from the `TLS` variant which takes as an argument a third parameter which is the window length, these variants take two essential parameters, the signal vector and the number of harmonics or the mode of estimation of the number of harmonics which is based on order selection models (`MOS`). These variants are: `ESPRIT_TLS`, `ESPRIT_ITCMP`, `ESPRIT_SVDSSA`, `ESPRIT_IRLBA`, `ESPRIT_SVD`, and `ESPRIT_ECON`.

The procedure for estimating the frequencies and amplitudes by these variants is given in [Figure 11.9](#ch11.xhtml#f11_9).

![FIGURE 11.9 Fault detection procedure with an HRM.](images/Fig11_09.jpg)

[**FIGURE 11.9**](#ch11.xhtml#f11_9b) Fault detection procedure with an HRM.

## 11.9 MOS (Order Selection Model)

When recording a stator signal coming from an electric induction machine prey to a fault and operating in a more or less noisy environment, we find ourselves with a signal in the frequency domain composed of several harmonics not all of which are not explanatory of the fault or do not translate the real number of harmonics constituting the signal [[16](#ch11.xhtml#r11_16),[17](#ch11.xhtml#r11_17)]. When we want to evaluate it, we use `MOS`.

`MOS` understood by model order selection is an important and fundamental problem in a variety of signal processing applications [[18](#ch11.xhtml#r11_18)]. For example, the determination of the number of coefficients in a linear regression model [[19](#ch11.xhtml#r11_19)], the selection of the order in the time series analysis [[20](#ch11.xhtml#r11_20)], the detection of the number of clusters in the `n`-way probabilistic classification [[20](#ch11.xhtml#r11_20)], the decision dimensionality for Principal Component Analysis (`PCA`) for the reduction of the dimension [[21](#ch11.xhtml#r11_21)], and the choice of the number of sources in a linear transformation model for separating the signal and noise subspaces [[22](#ch11.xhtml#r11_22)]. In general, the model order selection methods can be derived from the criteria of information theory [[16](#ch11.xhtml#r11_16)], Bayesian estimation [[21](#ch11.xhtml#r11_21)], and based on the deviation in an ordered sequence of parameters [[22](#ch11.xhtml#r11_22)].

### 11.9.1 Principle

They all estimate the number of harmonics in the signal using the eigenvalues of the signal covariance matrix. If `X` is the recorded signal of the electric induction machine affected by the fault, then its covariance matrix is:

$$R_{x} = \frac{\sum\limits_{n = 1}^{M}{X\left( n \right)X\left( n \right)^{T}}}{M}$$

(11.6)

where
1. `M` is the number of samples collected.

In this work, we compare five types of model order selector in order to validate the choice of the number of harmonics to be used for a rolling fault. We mention, however, that we use the formula:

`freq = |f[0] ± K × f[i,o]|`

(11.7)

where
1. `f[0]` is the power supply frequency,
2. `k` is an integer and `f[i,o]` is any internal or external frequency; to calculate the values of the harmonics. `k` will take the values 1, 2, 3, and 4 and `SNR` will take the values between 0 and 100 dB for a number of samples equal to 26.

### 11.9.2 Mathematical Expressions

Before giving the results obtained with these algorithms, we present their mathematical expressions:

* `MDL`: `MDL`, which stands for minimum description length, was developed by Rissanen in 1978. Its mathematical expression is:
`E[MDL](k) = − L(X/θ[k]) + 3 G(θ[k])`
(11.8)

* `AIC`: `AIC`, understood by Akaike’s information criteria, was developed by Akaike in 1974. Its mathematical expression is:
`E[AIC](k) = − 2 L(X/θ[k]) + 2 G(θ[k])`
(11.9)

* `KIC`: `KIC`, which stands for Kullback–Leibler Information Criteria, was developed by Cavanaugh in 1999. Its mathematical expression is:
`E[KIC](k) = − 2 L(X/θ[k]) + 3 G(θ[k])`
(11.10)

* `FPE`: `FPE` heard by final prediction error is expressed in terms of `AIC`. Its mathematical expression is:
$$\text{FPE}\left( k \right) = e^{\frac{\text{AIC}{(k)}}{T}}$$
(11.11)
with
$$L\left( {X/\theta_{k}} \right) = \frac{T}{2}\text{log}\left( \frac{MG}{MA} \right)^{m - k}$$
(11.12)
$$G\left( \theta_{k} \right) = 1 + mk - \frac{1}{2}k\left( {k - 1} \right)$$
(11.13)
where
$$MG = \prod\limits_{i = k + 1}^{m}\lambda_{i}{}^{\frac{1}{m - k}}$$
(11.14)
$$MA = \frac{1}{m - k}\sum\limits_{i = k + 1}^{m}\lambda_{i}$$
(11.15)
and where
1. `T` is the number of samples,
2. `L(X/θ[k])` is the maximum log-likelihood of the observation based on the model parameter as a function of `θ[k]` which is the `k`-th order and
3. `G(θ[k])` is the penalty for model complexity given by the total number of free parameters in `θ[k]`.

* `RAE`: The EAR heard by the adjacent eigenvalue report was presented by Liavas and Regalia (2001). It appears that the EAR has never been formally presented before. The EAR is expressed as:
$$RAE\,(p)\, = \,\frac{\lambda_{p}}{\lambda_{p + 1}},\, p\, = \, 1,\, 2,\,(m - 1)$$
(11.16)
Thus, we get `n` by:
`n = argmax(RAE(p))`, `p = 1, 2, …, (m−1)`
(11.17)

### 11.9.3 Results Obtained by Each of the MOS Algorithms

The red point is the coordinate of the minimum value of the cost functions. It is this value that we then compare in order to decide which `MOS` algorithm to use to obtain the number of harmonics that is important for the variants of the `ESPRIT` method.

* `MDL-AIC` : We can see that according to [Figure 11.10](#ch11.xhtml#f11_10) the minimum value for abscissa axis is `n=2` wich is the number of estimated harmonics. To know wich value of `SNR` and `k` correspond to, we plot the minimums of the values of the cost functions as shown in [Figure 11.11](#ch11.xhtml#f11_11).

* `KIC` : We can see that according to [Figure 11.12](#ch11.xhtml#f11_12) the minimum value for abscissa axis is `n = 2` wich is the number of estimated harmonics. To know wich value of `SNR` and `k` correspond to, we plot the minimums of the values of the cost functions as shown in [Figure 11.13](#ch11.xhtml#f11_13).
We realize that this corresponds to a value of `SNR` equal to 100 dB for a value of `k` = 1 and which should estimate the `n` to at most 2 ([Figure 11.12](#ch11.xhtml#f11_12)).

* `FPE`: We can see that according to [Figure 11.14](#ch11.xhtml#f11_14) the minimum value for abscissa axis is `n = 2` wich is the number of estimated harmonics. To know wich value of `SNR` and `k` correspond to, we plot the minimums of the values of the cost functions as shown in [Figure 11.15](#ch11.xhtml#f11_15).
We realize that this corresponds for a value of `SNR` equal to 100 dB for a value of `k` = 1 and which should estimate the `n` to at most 2 ([Figure 11.14](#ch11.xhtml#f11_14)).

* `RAE`: We can see that according to [Figure 11.16](#ch11.xhtml#f11_16) the minimum value for abscissa axis is `n = 2` wich is the number of estimated harmonics. To know wich value of `SNR` and `k` correspond to, we plot the minimums of the values of the cost functions as shown in [Figure 11.17](#ch11.xhtml#f11_17).
We realize that, this corresponds to a value of `SNR` equal to for a value of `k` = and which should estimate the `n` at most 2 ([Figure 11.16](#ch11.xhtml#f11_16)).

![FIGURE 11.10 Value of the MDL-AIC cost function as a function of n.](images/Fig11_10.jpg)

[**FIGURE 11.10**](#ch11.xhtml#f11_10b) Value of the MDL-AIC cost function as a function of `n`.
