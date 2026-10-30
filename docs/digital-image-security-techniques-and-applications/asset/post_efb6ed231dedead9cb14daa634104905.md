
and thus analytically tractable [36]. NIG PDF has been implemented in the modeling of the sub-band wavelet coefficients and results in effective feature extraction. The density function of NIG PDF is defined as:

$$P(C)=\left(\alpha\delta e^{\alpha\delta}K_1\left(\alpha\sqrt{\delta^2+C^2}\right)\right)/\left(\pi\sqrt{\delta^2+C^2}\right)$$ (11.6)

Where C denotes the random variable, K_1 denotes modified Bessel function with order =1. Tail heaviness of the distribution is defined by α and can control the steepness of the distribution. The scale parameter is denoted by δ. The shape of the distribution is controlled by α and δ. α → ∞ and δ → ∞ yields Gaussian distribution, and α → 0 yields Cauchy distribution [37]. Distribution parameters are estimated by fitting NIG PDF in all sub-bands (LL, LH, HL). Next, the variance information σ̂_c² of the sub-bands is calculated using the following equation:

$$\hat{\sigma}_c^2 = \int_{-\infty}^{+\infty} C^2 P(C) dc - \left(\int_{-\infty}^{+\infty} c P(C) dc\right)^2$$ (11.7)

A total of 18 features F₁ – F₉ are calculated correspond to variance values, and F₁₀ – F₁₈ correspond to α values across the sub-bands.

### 11.2.3 Noise variance in diagonal sub-band

Diagonal sub-band in wavelet decomposition contains all the noisy data and gives important information regarding the noise present in the medical image. This concept motivates to extract image features F₁₉ – F₂₁ correspond to noise variance in HH sub-band in all scales. Orthogonal property of wavelet decomposition says that sub-band diagonal coefficient fits well by zero mean Gaussian PDF. By fitting the empirical wavelet distribution using Gaussian PDF, median is calculated from the distribution parameter, and next, a median estimator is applied to find the noise variance of the medical image. Noise variance (σ̂_n²), calculated using a median estimator, is given by [38]:

$$\hat{\sigma}_n^2 = \left(\frac{\text{Median}(HH)}{0.6745}\right)^2$$ (11.8)

### 11.2.4 Spatial correlation feature extractor

Medical images modify their structure in the presence of distortion. The smoothness of the image varies over the distance. The correlation between spatial structures of the sub-bands can be utilized to evaluate the quality factor. The following steps are implemented to find the correlation between the spatial structures.

**Step 1:** Calculation of joint empirical distribution $f_{x,y}(X,Y)$ between the coefficients at $(l,k)$ and $N_8(l,k)$.
$N_8(i,j)$ is the distance $d \in \{1,2,......25\}$

**Step 2:** Calculation of correlation between the variables $X$, $Y$ using the following equation (11.9).

$\rho_d = \frac{E_{xy}(X,Y)[X - E_x(X)]^T (Y - E_y(Y))}{\sigma_X \sigma_Y}$  (11.9)

Where $E$ is the expectation operator and $\sigma_X$, $\sigma_Y$ are the variances of X and Y vector, respectively.

**Step 3:** Parameterize the correlation $\rho_d$ by fitting a $3^{rd}$ order polynomial and calculation of coefficient of the polynomial.

Finally, the empirical value of correlation coefficient, fit error, and coefficient of the polynomial form the features $F_{22} - F_{51}$.

### 11.2.5 NSS feature extraction in the wavelet domain

Wavelet transform includes properties like multiresolution, locality, Gaussianity, and persistency. Self-similarity property of the scene is one of the most important properties of wavelet transform. The NSS feature in the wavelet domain changes irregularly with artifacts [24]. Magnitude of the wavelet coefficients exponentially decay across scale. This feature is utilized in this chapter for implementing quality detection. NSS feature is extracted from the image in wavelet domain. Sparse representation is implemented in this chapter to extract NSS features. Magnitude, variance, and entropy are calculated for the horizontal and vertical sub-bands for each scale as shown below:

$magnitude_s = \frac{1}{N_s \times M_s} \sum_{k=1}^{N_s} \sum_{l=1}^{M_s} \log_2 |C_s(l,k)|$  (11.10)

$variance_s = \frac{1}{N_s \times M_s} \sum_{k=1}^{N_s} \sum_{l=1}^{M_s} \log_2 |C_s(l,k) - magnitude_s|$  (11.11)

$entropy_s = \sum_{j=1}^{N_s} \sum_{i=1}^{M_s} P(C_s(i,j)) \ln P(C_s(i,j))$  (11.12)

Where $N_s$ and $M_s$ are length and width of $s^{th}$ sub-band, $C_s(k, l)$ is the $(k, l)$ coefficients of the $s^{th}$ sub-band, and $P(.)$ = Probability density function of the sub-band.

These features are averaged in the same sub-band and in the same scale and combined into a vector. For six sub-bands in three scales, the vector is defined as below.

$$f = \begin{bmatrix} m_{LH1}, m_{HL1}, m_{LH2}, m_{HL2}, m_{LH3}, m_{HL3}, \\ \vartheta_{LH1}, \vartheta_{HL1}, \vartheta_{LH2}, \vartheta_{HL2}, \vartheta_{LH3}, \vartheta_{HL3}, \\ e_{LH1}, e_{HL1}, e_{LH2}, e_{HL2}, e_{LH3}, e_{HL3} \end{bmatrix}^T$$ (11.13)

Where $m_{xy}$ is the magnitude of x sub-band at scale y, $\vartheta_{xy}$ is the variance of x sub-band at scale y, and $e_{xy}$ is the entropy of x sub-band at scale y. A total of 18 features $F_{52} - F_{69}$ are calculated that correspond to magnitude, variance, and entropy values in sub-bands.

### 11.2.6 SVM regression and parameter selection

In our work, a standard regression is considered that works under general setting for predictive learning [39]. This method estimates a real value function as:

$$y = r(f) + \delta$$ (11.14)

Where $\delta$ is the hyper parameter and $f$ is a multi-valued input and $y$ is the scalar output. Parameter selection is based on the finite number of features $f$ and $y$ values.

Let the features and their corresponding selection parameters are distributed jointly and defined by PDF as $P_{f,y}(F, Y)$. It can be written as:

$$P_{f,y}(F, Y) = P_f(F) P_{f,y}(Y | F)$$ (11.15)

From equation (11.14) and (11.15) we can write the regression function as:

$$r(f) = \int y P_{f,y}(Y | F) dy$$ (11.16)

The prime aim of the estimation procedure is to find the best model $f(f, \omega_0)$ from a sequence of models $f(f, \omega)$ for $\omega$. The best model can be created by minimizing prediction risk as:

$$R(\omega) = \int \big(L(y, f(f, \omega))\big) P(f, y) df dy$$ (11.17)

Where $L(y,f(f,\omega))=(y-f(f,\omega))^2$ defines the loss function (11.18)

Applying equation (11.18) in equation (11.17) results:

$R(\omega)=\int (y-f(f,\omega))^2 P(f,y) df dy$ (11.19)

In SVM regression method, a mapping scheme is used to map the input features to a multidimensional feature space. Next, a linear model in the feature space is created and can be written as:

$f(f,\omega)=\sum_{i=1}^{n}\omega_i g_i(f)+b$ (11.20)

Where $b$ is the bias term, $g_i$ is the non-linear transform function, and $n$ are the training samples. SVM regression is a linear regression in the high dimensional feature space consider the insensitive loss $\varepsilon$, and also reduces the complexity of the model $||\omega||^2$. The modified loss function can be written as:

$L_{\varepsilon}(y,f(f,\omega))=\begin{cases}0,\text{if }y-f(f,\omega)\le\varepsilon\\|y-f(f,\omega)|-\varepsilon\text{ otherwise}\end{cases}$ (11.21)

The Risk function considering the insensitive loss is given by:

$R_{\varepsilon}(\omega)=\frac{1}{n}\sum_{i=1}^{n}L_{\varepsilon}(y,f(f,\omega))$ (11.22)

Thus, SVM regression minimizes the function $\frac{1}{2}||\omega||^2 + c\sum_{i=1}^{n}\epsilon_i + \epsilon_i^*$

With constraints $\begin{cases}y-f(f,\omega)-b\le\epsilon_i+\epsilon_i^*\\f(f,\omega)+b-y\le\epsilon_i+\epsilon_i^*\\\epsilon_i\epsilon_i^*\ge0\end{cases}$ (11.23)

Where $c$ is a positive constant, $\epsilon_i,\epsilon_i^*$ are the slack variables, and $n$ are the training samples.

## 11.3 EXPERIMENTAL RESULTS

This section discusses the performance results of the proposed method. The objective assessment is compared with human valuation. The proposed method is tested on National Institutes of Health (NIH) database [40] and simulated in MATLAB environment. All images are converted to 400×400 size for simulation. The proposed method requires approximately 50 seconds to produce the quality score. Compared to prediction time, SVR training time is negligible. The NIH database for different medical images such as Bone marrow Smear image liver, Brain MRI, Chest X-Ray, CT Scan of Brain, and Brain MRI images are shown in Figure 11.5. The proposed algorithm is compared with state-of-the-art methods including FR-IQA- and NR-IQA-based methods. Full reference methods include PSNR, SSIM [8], and IFC [9]. No reference methods include BRISQUE [15], CORNIA [19], DIIVINE [20], and WLBP [32]. The performance of the proposed algorithm

![](img/6e4271af21d9a195003ab8711aa79d27_252_0.png)

![](img/6e4271af21d9a195003ab8711aa79d27_252_1.png)

![](img/6e4271af21d9a195003ab8711aa79d27_252_2.png)

![](img/6e4271af21d9a195003ab8711aa79d27_252_3.png)

![](img/6e4271af21d9a195003ab8711aa79d27_252_4.png)

![](img/6e4271af21d9a195003ab8711aa79d27_252_5.png)

Figure 11.5 Medical images (a) Bone marrow smear (b) liver (c) Brain MRI (d) Chest X-Ray (e) CT Scan of Brain (f) Brain MRI.
