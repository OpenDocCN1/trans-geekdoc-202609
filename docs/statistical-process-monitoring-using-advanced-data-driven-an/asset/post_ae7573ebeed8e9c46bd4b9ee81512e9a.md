
of data, outperforms the conventional Shewhart scheme for detecting faults in autocorrelated time-series data.

### 5.4.1.2 Effect of measurement noise on the conventional Shewhart chart

Here, the detection efficiency of the conventional Shewhart chart and its multiscale version are investigated when the data from the monitored process is noisy. To do so, we generate 500 random Gaussian data samples, which are being used to determine the control limits of the two schemes. The testing dataset consists of 500 data samples that are completely independent of the training data and contaminated with bias fault of amplitude equal to 2 introduced from samples 200 to 300 and from samples 400 to 450 of the testing data. This simulation is replicated 5000 times for different measurement noise levels taken from \(\sigma = 0.03\) to \(\sigma = 2\). Fig. 5.11 displays the average value for 5000 missed detection rates and false alarm rates as a function of the standard deviation of the measurement noise. In Fig. 5.11, we observe that the detection capacity decreases by increasing the missed detection rate when the noise level increases. This case study confirms the advantages of the multiscale Shewhart scheme over the single scale Shewhart scheme when applied to noisy data (Fig. 5.11). This is mainly due to the capacity of the multiscale representation to separate relevant and irrelevant features in the data. Thus, combining the advantages of a multiscale representation with those of a univariate monitoring Shewhart chart, it should be possible to obtain further improvements in fault detection.

| \(\sigma\) | Shewhart chart MD (%) | Multiscale Shewhart chart MD (%) | Shewhart Chart FA (%) | Multiscale Shewhart Chart FA (%) |
|---|---|---|---|---|
| 0.030 | 0 | 0 | 0.2873 | 0.9907 |
| 0.134 | 0 | 0 | 0.2904 | 0.9233 |
| 0.237 | 0 | 0 | 0.2758 | 1.062 |
| 0.341 | 0.2242 | 0.0604 | 0.2808 | 1.316 |
| 0.445 | 6.79 | 0.2802 | 0.2863 | 1.43 |
| 0.548 | 25.19 | 1.219 | 0.2871 | 1.391 |
| 0.652 | 42.25 | 4.116 | 0.2848 | 1.276 |
| 0.756 | 63.73 | 18.552 | 0.2841 | 1.255 |
| 0.859 | 74.7 | 30.23 | 0.2888 | 1.244 |
| 0.963 | 82.15 | 45.69 | 0.2833 | 1.158 |
| 1.067 | 86.18 | 53.1 | 0.2926 | 1.242 |
| 1.171 | 90.04 | 57.75 | 0.2852 | 1.254 |
| 1.274 | 92.22 | 61.6 | 0.2863 | 1.275 |
| 1.378 | 93.82 | 64.79 | 0.284 | 1.234 |
| 1.482 | 94.97 | 66.32 | 0.2805 | 1.222 |
| 1.585 | 95.8 | 69.48 | 0.2943 | 1.147 |
| 1.689 | 97.43 | 72.28 | 0.2808 | 1.051 |
| 1.793 | 96.95 | 73.14 | 0.286 | 1.077 |
| 1.896 | 97.36 | 74.93 | 0.2827 | 1.046 |
| 2 | 97.68 | 76.5 | 0.2808 | 1.037 |

FIGURE 5.11 Comparison of the performance of Shewhart and multiscale Shewhart monitoring charts for the case of noisy data.

### 5.4.1.3 Impact of the violation of normality assumption on the conventional Shewhart chart

In this case study, we investigate the ability of wavelet-based monitoring to deal with non-Gaussian data. Specifically, the detection performance of single and multiscale Shewhart schemes are compared when the normality assumption underlying the univariate monitoring charts is violated. In other words, we investigate the impact of violating the normality assumption on the conventional Shewhart monitoring chart. The statistical performance of the two schemes is investigated using the chi-square data, with different values of a fourth-order cumulant (or kurtosis). The kurtosis is used in this study to quantify the non-Gaussianity in the data. For univariate data x1, x2, ..., xN, the formula for kurtosis is computed as

Kurtosis = \frac{\sum_{i=1}^N (X_i - \mu)^4}{(N - 1)\sigma^4}, \quad (5.9)

where μ is the mean, σ is the standard deviation, and N is the number of data points. In fact, kurtosis quantifies the degree of peakedness of a distribution; it is 3 for a Gaussian distribution. Generally speaking, if it is greater than 3, the distribution is termed “super-Gaussian”, i.e., spikier than Gaussian, and if it is less than 3, such distribution is termed “sub-Gaussian”, i.e., flatter than Gaussian. To investigate the detection performance when the Gaussianity assumption is invalid, 1024 random fault-free data samples with a chi-square nonnormal distribution were generated. After computing detection limits of the two charts using the training data, another testing dataset of 1024 random samples with a chi-square distribution was generated. A step anomaly is then injected into the testing data between samples 201–250, 501–525, and 701–725. The magnitude of the considered step fault is 3σ. For different values of the kurtosis taken between 3 and 14, each simulation is repeated 5000 times to get more accurate results. The means of the 5000 missed detection rates and false alarm rates as functions of kurtosis are presented in Fig. 5.12. It shows that the missed detection rate significantly increased as the departure from Gaussianity increased (i.e., when we increased the kurtosis of data) while false alarm rate increased slightly when the kurtosis increased. Fig. 5.12, which shows the average of missed detection rate and false alarms rate as a function of kurtosis of these two charts, clearly illustrates the advantages of the multiscale Shewhart chart over the conventional chart. This case study shows that, in most instances, the performance of the multiscale Shewhart chart is superior to that of the conventional Shewhart chart in detecting process mean faults.

In essence, the wavelet-based univariate monitoring approaches offer several advantages compared to single scale monitoring schemes including: (i) decorrelating time-dependent data while keeping a Gaussian distribution; (ii) obtaining Gaussian wavelet coefficients at each scale even with non-Gaussian input data; (iii) separating noise from relevant features in the data; and (iv) compacting the deterministic features in a small number of coefficients.

| Kurtosis | Shewhart chart MD (%) | Multiscale Shewhart chart MD (%) | Shewhart Chart FA (%) | Multiscale Shewhart Chart FA (%) |
|---|---|---|---|---|
| 3.465 | 51.87 | 25.11 | 0.6113 | 0.3224 |
| 3.516 | 52.03 | 25.86 | 0.6437 | 0.3163 |
| 3.593 | 52.13 | 26.73 | 0.6869 | 0.3065 |
| 3.683 | 52.43 | 27.7 | 0.7282 | 0.2889 |
| 3.811 | 52.41 | 28.39 | 0.7976 | 0.2766 |
| 4.007 | 52.79 | 29.67 | 0.8827 | 0.2808 |
| 4.297 | 53.06 | 31.37 | 0.9921 | 0.2845 |
| 4.822 | 53.72 | 34.18 | 1.166 | 0.3013 |
| 6.171 | 54.8 | 38.5 | 1.482 | 0.3656 |
| 14.322 | 57.91 | 48.91 | 2.24 | 0.6721 |

FIGURE 5.12 Comparison of the performance of Shewhart and multiscale Shewhart monitoring charts for the case of non-Gaussian data.

## 5.5 Multiscale LVR modeling

### 5.5.1 Benefits of multiscale denoising in LVR modeling

Most of the real-world data are multiscale in nature; therefore, a model estimation using such data needs to consider the multiscale modeling methods that take into account multiscale filtering, using wavelets to increase the efficacy of the latent variable regression models. In this section, we highlight the major benefits of using multiscale filtering in LVR modeling [76].

- The presence of noise in the measured data degrades the model parameter estimation of the LVR models. The measured data are passed through low- and high-pass filters constructed from orthonormal basis functions, and subsequently reduce the noise embedded in the measurements and results, yielding a more precise prediction.
- Most of the measured data contain noise that is correlated in nature, because the source of noise is not independent and random, like the malfunctioning or error in sensor calibration, for example. Model parameter estimation becomes challenging with the presence of correlated data. Using wavelets for representing correlated data decorrelates it. This property is very helpful where measurement errors are not always random [24].

The model is developed by making use of the above advantages, which integrate the LVR model parameter estimation and multiscale filtering to improve model prediction.
