
in which $N$ is the number of data and $C(B)$ is a complexity penalty that increases with the number of basis function (BF) in the model. It is defined as

$C(B) = (B + 1) + dB$ (22.12)

where $d$ is a penalty for each BF included into the model and $B$ is number of basis functions [24].

### 22.3.2 GMDH

GMDH is a learning machine based on the polynomial theory of complex systems [22]. From this network, the most significant input parameters, number of layers, the number of neurons in middle layers, and optimal topology design of the network are defined automatically. Therefore, the GMDH network is included those of active neurons known as a self-organized model. The structure of the GMDH network is configured through the training stage with polynomial model which produces the minimum error between the predicted value and observed output. The formal definition of the system identification problem is to find an approximate function \(\hat{f}\) that can be used to predict the actual output \(\hat{y}\) or a given input vector \(X = (x_1, x_2, ..., x_n)\) as close as possible to actual output y. Therefore, \(n\) observations of multi-input-single-output data pairs are considered as:

$y_i = f(x_{i1}, x_{i2}, x_{i3}, ... x_{in})(i = 1, 2, ...., M)$ (22.13)

The general relationship between input and output variables can be expressed by a complicated discrete form of the Volterra function, a series in the form of

$y = w_0 + \sum_{i=1}^n w_i x_i + \sum_{i=1}^n \sum_{j=1}^n w_{ij} x_i x_j + \sum_{i=1}^n \sum_{j=1}^n \sum_{k=1}^n w_{ijk} x_i x_j x_k + \cdots$ (22.14)

which is known as the Kolmogorov-Gabor polynomial [36]. In the present study, a quadratic polynomial of the GMDH network is used that is written as:

Quadratic: \(\hat{y} = w_0 + w_1 x_i + w_2 x_j + w_3 x_i x_j + w_4 x_i^2 + w_5 x_j^2\) (22.15)

The weighting coefficients of Eq. (22.14) are calculated using regression techniques such that the difference between actual output, \(y\), and the calculated value, \(\hat{y}\), for each pair of \(x_i\) and \(x_j\) as input variables is minimized. In this way, the weighting coefficients of the quadratic function \(G_i\) are obtained to optimally fit the output to the whole set of input–output data pairs, which is defined as:

$E = \frac{\sum_{i=1}^{M} \left[y_i - G_i(0)\right]^2}{M} \rightarrow \min \quad \text{(22.16)}$

In this study, the GMDH network is improved using a back propagation algorithm. This method includes two main steps: (1) the weighting coefficients of the quadratic polynomial are determined using the least squares method from the input layer to output layer in the form of a forward path; and (2) the weighting coefficients were updated using a back-propagation algorithm in a backward path. This procedure may be continued until the error of the training network \( E \) is minimized.

### 22.3.3 MNLR

Assume that \( y \) is a dependent variable and have a nonlinear relation with \( n \) independent variables as \( x_1, x_2, ..., x_n \). The nonlinear relation between them can be expressed as:

\( y = a_0 x_1^{a_1} x_2^{a_2} ... x_n^{a_n} \quad \text{(22.17)} \)

By applying logarithmic transformation, the following equation can be obtained as:

\(\log y = \log a_0 + a_1 \log x_1 + a_2 \log x_2 + \cdots + a_n \log x_n \quad \text{(22.18)}\)

where the coefficients \( a_0, a_1, ..., \text{and } a_n \) can be determined by applying least squares method in similar to multi linear regression (MLR) method.

## 22.4 Model Development

### 22.4.1 Model Inputs and Outputs

Five variables were presented to the MARS, GMDH and MNLR as model inputs including the effective depth (\( d \)), the shear span-to-depth ratio (\( a/d \)), the compressive strength of concrete (\( f'_c \)), the aggregate size-to-depth ratio (\( a_g/d \)), and the longitudinal steel ratio (\( \rho \)). The single model output is concrete shear capacity, \( v_u \).

### 22.4.2 Data Division and Pre-processing

The data used to calibrate and validate the MARS, GMDH, and MNLR models were obtained from the literature and include a series of 250 concrete shear capacity tests, which were compiled by Elsanadedy et al. [12] from 33 experimental studies performed between 1957 and 2013. All selected beams are without stirrups and were longitudinally reinforced with non-prestressed steel rebars. Only slender beams with a/d ≥ 2.5 that their failures primarily occur due to shear were considered. The specimens are monotonically loaded using either one or two concentrated loads till failure. Details of data used can be found in [12].

The available data were randomly divided into two sets: a training set for model calibration and an independent validation set for model verification. The validation dataset was used to specify the generalization capability of the models to new data they had not been trained with. In other words, the testing data were applied to measure the performance of the models obtained by proposed algorithms when applied to dataset which played no role in building the models. The statistics of the data used in the training and validation sets are given in Table 22.2, which include the mean, standard deviation, minimum, and maximum. For more visualization, matrix-plot of input and output parameters is represented in Fig. 22.1. This plot presents all possible scatter plots of input and output parameters one by one. The plots in the diagonal of this matrix are the histograms of input and output parameters for whole data points. As shown, most of data points are concentrated in the ranges: d ≤ 400 mm, f′c ≤ 100 MPa and ρ ≤ 4 (%). It should be noted that the derived model can be more reliable in these ranges.

Table 22.2 Ranges of input and output parameters for training and testing sets

| Variable | Subset | Min | Max | Mean | STD |
|---|---|---|---|---|---|
| d (mm) | Training | 133 | 925 | 284.88 | 158.94 |
| | Testing | 135 | 718 | 255.98 | 96.99 |
| a/d | Training | 2.46 | 6.1 | 3.59 | 0.86 |
| | Testing | 2.47 | 6.1 | 3.66 | 0.89 |
| a_g/d | Training | 0.01 | 0.17 | 0.06 | 0.02 |
| | Testing | 0.02 | 0.17 | 0.06 | 0.02 |
| f'_c (MPa) | Training | 42.5 | 183 | 65.40 | 21.44 |
| | Testing | 45.3 | 155 | 64.56 | 20.75 |
| ρ (%) | Training | 0.33 | 6.64 | 2.17 | 1.31 |
| | Testing | 0.33 | 6.64 | 2.29 | 1.26 |
| v_u (kN) | Training | 0.48 | 4.08 | 1.72 | 0.78 |
| | Testing | 0.57 | 3.85 | 1.8 | 0.70 |

![](img/4048998719320644ee88964326fd7995_466_0.png)

Fig. 22.1 Matrix plot of input and output parameters

Out of the 250 tests, 200 data vectors (80%) were taken for the training process. The remaining 50 data vectors (20%) were used for the testing of the models. It should be noted that, like other empirical models, the proposed MARS, GMDH, and MNLR models are only valid for the ranges they trained and their performance is more acceptable in ranges which the density of data is more concentrated.

### 22.4.3 Derived Models

Following data division, training data set was presented to the GMDH, MARS, and MNLR algorithms for model training. The MARS model returned the following equation for concrete shear capacity:

```
v_u(kN) = 5.4 - 3.5 x BF_1 + 22 x BF_2 + 41 x BF_3 - 0.079 x BF_4 + 0.078 x BF_5
- 0.049 x BF_6 + 0.054 x BF_7 - 0.54 x BF_8 + 38 x BF_9 + 0.096 x BF_10
- 0.47 x BF_11 - 3.6 x BF_12 + 31 x BF_13 + 700 x BF_14 - 4100 x BF_15
- 16 x BF_16 - 15 x BF_17 + 1.7 x BF_18 + 4.3 x BF_19 - 0.09 x BF_20
- 0.79 x BF_21 - 23 x BF_22 - 0.15 x BF_23 + 0.48 x BF_24 + 17 x BF_25
+ 0.093 x BF_26 + 6.8 x 10^-5 x BF_27 + 2.4 x BF_28
```

Table 22.3 lists the BFs and their corresponding equations. It should be noted that, from Table 22.3, that of 28 BFs, 19 BFs with interaction terms are integrated in this model, indicating that the model is not simply additive and that interaction terms play a significantly important role. The final model of MARS (Eq. (22.19)) is achieved via GCV obtained from forward selection and backward deletion process. As observed, one of advantages of MARS algorithm is that not only captures complex relationships between independent and dependent variables but also does not require additional effort to verify a priori assumption about the relationship between the set of independent variables and dependent response variable. The latter feature becomes more important as the dimension of the problem increases.

Table 22.3 Basis functions of the developed MARS model

| Basis functions | Equations |
|---|---|
| BF1 | max(0, ρ-3.2) |
| BF2 | max(0, 3.2-ρ) |
| BF3 | max(0, 2.5-a/d) |
| BF4 | max(0, d-190) |
| BF5 | max(0, d-230) |
| BF6 | max(0, 230-d) |
| BF7 | max(0, 170-d) |
| BF8 | max(0, a/d-2.5) × max(0, 1.4-ρ) |
| BF9 | max(0, 230-d) × max(0, 0.061-a_g/d) × max(0, 3.9-a/d) |
| BF10 | max(0, 360-d) × max(0, 0.077-a_g/d) |
| BF11 | BF10 × max(0, ρ-4) |
| BF12 | BF9 × max(0, 60-f'_c) |
| BF13 | max(0, 230-d) × max(0, 0.061-a_g/d) × max(0, a/d-3) |
| BF14 | max(0, 230-d) × max(0, 0.061-a_g/d) × max(0, 3-a/d) |
| BF15 | max(0, 230-d) × max(0, 0.061-a_g/d) × max(0, ρ-3.2) |
| BF16 | max(0, 230-d) × max(0, 0.061-a_g/d) × max(0, 3.2-ρ) |
| BF17 | max(0, 230-d) × max(0, ρ-1.4) × max(0, 0.063-x_3) |
| BF18 | BF5 × max(0, a_g/d-0.068) |
| BF19 | max(0, ρ-3.4) |
| BF20 | max(0, 310-d) × max(0, 0.076-a_g/d) × max(0, 6-a/d) |
| BF21 | max(0, d-170) × max(0, a_g/d-0.071) |
| BF22 | max(0, 3.2-ρ) |
| BF23 | max(0, a/d-2.5) × max(0, ρ-1) |
| BF24 | max(0, a/d-2.5) × max(0, 1-ρ) |
| BF25 | max(0, 230-d) × max(0, a_g/d-0.061) × max(0, ρ-3.2) × max(0, 3-a/d) × max(0, f'_c-64) |
| BF26 | max(0, d-170) × max(0, 0.071-a_g/d) × max(0, ρ-3.3) |
| BF27 | max(0, 360-d) × max(0, f'_c-70) |
| BF28 | BF3 × max(0, f'_c-54) |
