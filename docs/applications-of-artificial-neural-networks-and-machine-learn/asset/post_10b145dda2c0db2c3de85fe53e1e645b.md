
![](img/4048998719320644ee88964326fd7995_416_0.png)

Fig. 20.7 The histograms of discrepancy ratio between measured and predicted maximum bond strength by different models

![](img/4048998719320644ee88964326fd7995_416_1.png)

Fig. 20.8 The variations of DR values of different models as a function of axial rigidity ($E_p t_p$)

## 20.5.2 Sensitivity Analysis

One of the main advantages of MARS model is its ability to evaluate whether input parameters are making an important contribution to generate final model or they just marginally improve the accuracy of the developed model. The Analysis of Variances (ANOVA) decomposition of the developed MARS models based on both with piece-wise linear and cubic segments is presented in Table 20.5. The first column lists the number of ANOVA function. The second column gives the standard deviation of the corresponding ANOVA functions. This gives one indication of the relative contribution of each function to the overall model performance. The third column provides another indication of the importance of the corresponding ANOVA function, by listing the GCV score for a model with the whole basis functions compared to a model in which that particular ANOVA function is removed. This can be used to judge whether this ANOVA function makes an important contribution to the model performance, or whether it slightly improves the global GCV score. The last column gives the particular predictor variables associated with that ANOVA function [34]. This ability of MARS can be applied to determine the most important parameters in prediction of bond strength of EBR FRP systems.

In Fig. 20.9, the relative importance of the input parameters for the developed MARS models based on ANOVA analysis is depicted. The relative importance of each input parameter was determined based on the increase of GCV value that caused by removing the considered variables from the developed MARS model. For example, according to Table 20.5, the ANOVA functions with parameters of $b_p$ and $b_p/b_m$ remarkably improved the amount of GCV values. Therefore, it can be expected that these parameters have remarkable contribution in developing prediction models for bond strength. As graphically shown in Fig. 20.9, $b_p/b_m$ and $b_p$ were the most important parameters in the developed MARS models and $L_b$, $f_{mt}$, and $E_p t_p$ were the other important parameters, respectively.

| Func. | STD Linear | STD Cubic | GCV Linear | GCV Cubic | Variable(s) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 2812.925 | 49.643 | 11,572,307.35 | 3607.591 | $b_p/b_m$ |
| 2 | 1.242 | 2.122 | 12.99 | 33.324 | $f_{mt}$ |
| 3 | 0.759 | 0.961 | 5.415 | 8.992 | $E_p t_p$ |
| 4 | 5.647 | 5.213 | 105.579 | 87.188 | $b_p$ |
| 5 | 4.032 | 3.169 | 32.75 | 29.965 | $L_b$ |
| 6 | 2817.19 | 52.778 | 11,038,785.57 | 3922.107 | $b_p/b_m, b_p$ |
| 7 | 1.904 | 1.454 | 9.351 | 14.589 | $b_p/b_m, L_b$ |
| 8 | 1.111 | 1.505 | 6.018 | 10.967 | $f_{mt}, b_p$ |
| 9 | 4.832 | 4.555 | 47.506 | 54.292 | $f_{mt}, L_b$ |
| 10 | 2.038 | 1.848 | 10.11 | 12.049 | $f_{mt}, b_p/b_m, L_b$ |
| 11 | 1.35 | 0.384 | 6.929 | 7.618 | $f_{mt}, b_p/b_m, L_b, E_p t_p$ |

![](img/4048998719320644ee88964326fd7995_418_0.png)

Fig. 20.9 The relative importance of the input variables in developing the MARS models

## 20.5.3 Safety Analysis

A reliable prediction of maximum bond strength between FRP reinforcements and masonry units is vital for engineers to have a safe, technically correct and economical design. In this study, the box plot of discrepancy ratio between measured and predicted maximum bond strength (DR) is used to assess the reliability and uncertainty of the empirical and proposed models. Box plot is a convenient graphical way to illustrate data points through their quartiles. It displays the variation in samples of a statistical population without making any assumptions of the underlying distribution. The spreading between the different parts of the box indicates the degree of dispersion (spread) or skewness in the database. According to statistical analysis of previous sections, it can be expected that the developed M5' and MARS models are more reliable than existing equations. However, it is impossible to identify the uncertainty/safety factor of different models. Therefore, the exact degree of uncertainty in the mentioned models cannot be determined. To overcome this limitation, a safety factor based on the acceptable level of risk for each model can be considered.

Figure 20.10 illustrates the box plots of different models including the proposed ones and the most accurate empirical equations according to the previous results. It is clear that Yang et al. [18] and Khalifa et al. [15] equations generally overestimate the bond strength while Tanaka [12] and Neubauer and Rostasy [14] equations underestimate the maximum bond strength. Among mentioned equations, the Khalifa et al. [15] formula is more conservative and has the highest uncertainty (wider box plot). The Tanaka [12] formula has the lowest uncertainty among existing empirical equations. Figure 20.10 also shows that the box plots of M5' and MARS models developed in this study are narrower than those of others, which is an indicator

![](img/4048998719320644ee88964326fd7995_419_0.png)

Fig. 20.10 Box plot of different equations

of a higher level of confidence. Furthermore, the error distribution of DR values for a precise and accurate formula should be symmetrical around its mean value and close to 1. As it is shown, the error distributions of developed M5' and MARS models are nearly symmetrical and their averages are very close to 1. In addition, the safety factors of M5' and MARS models are generally smaller than other equations. For example, according to Fig. 20.10, if 10% risk is acceptable than the prediction of MARS and M5' models should be divided by 1.40 and 1.45, respectively, while these factors for Tanaka [12], Yang et al. [18], Neubauer and Rostasy [14], Khalifa et al. [15] equations are 1.8, 2.7, 2.1 and 3.1, respectively.

To quantitatively evaluate the safety of proposed models and existing design equations, a new scale has been employed in this study. Collins [62] introduced a new scale to evaluate and classify the reliability of design codes. This scale is known as Demerit Points Classification (DPC), which consider the safety, accuracy and scattering of design codes as a function of the ratio between the ultimate resistances in experimental tests and the estimated theoretically load capacity. In this study, the measured maximum bond strength ($P_{max,exp}$) and predicted bond strength by existing formulae and proposed models ($P_{max,predicted}$) are the ultimate resistances in experimental tests and the estimated theoretically load capacity, respectively. Table 20.6 presents an adaption made in the present study to the original values proposed by Collins [62]. According to the bond strength predicted by each formula, a demerit point to each prediction for 230 data points is attributed to that formula based on Table 20.6. Then, the general value of demerit of each formula is calculated by the sum of the products of the number of specimens in each interval and their corresponding demerit penalty. The lower the value of total sum, the more reliable the formula considered.

Table 20.7 presents the evaluation of M5', MARS and some existing equations as a function of the adapted criteria from Collins [62]. According to this criteria,

| $P_{max,exp}/P_{max,predicted}$ | Classification | Demerit points |
|---|---|---|
| <0.50 | Extremely dangerous | 10 |
| [0.50–0.85) | Dangerous | 5 |
| [0.85–1.15) | Appropriate and safe | 0 |
| [1.15–2.00) | Conservative | 1 |
| ≥2.00 | Extremely conservative | 2 |

Tanaka [12] model presents a higher total demerit points (844 total points) than other models, with 58% of the values in the first and second classification ranges (smaller than 0.85), which is unfavorable in terms of safety. Khalifa et al. [15] model presents the lowest total demerit points amongst the other design equations. However, 57% of its prediction values are in the fourth and fifth classification ranges (larger than 1.15), which are classified as conservative and extremely conservative in terms of safety. In general, the existing equations usually suffer from either having limited accuracy or being too conservative or both of problems. However, the M5' and MARS developed in this study with lowest total demerit points (281 and 282, respectively) and having 60% and 59% of their predictions in the range of the third classification (appropriate and safe) had the best performance amongst the other equations in terms of safety.

| Models | DR < 0.5 | 0.5 < DR < 0.85 | 0.85 < DR < 1.15 | 1.15 < DR < 2 | DR > 2 | Total |
|---|---|---|---|---|---|---|
| Tanaka [12] | 20 | 115 | 41 | 39 | 15 | 844 |
| | 20 × 10 | 115 × 5 | 41 × 0 | 39 × 1 | 15 × 2 | |
| Yang et al. [18] | 4 | 46 | 81 | 57 | 42 | 411 |
| | 4 × 10 | 46 × 5 | 81 × 0 | 57 × 1 | 42 × 2 | |
| Neubauer and Rostasy [14] | 19 | 102 | 44 | 50 | 16 | 782 |
| | 19 × 10 | 102 × 5 | 44 × 0 | 50 × 1 | 16 × 2 | |
| Khalifa et al. [15] | 1 | 24 | 74 | 77 | 54 | 315 |
| | 1 × 10 | 24 × 5 | 74 × 0 | 77 × 1 | 54 × 2 | |
| MARS (present study) | – | 47 | 136 | 47 | – | 282 |
| | – | 47 × 5 | 136 × 0 | 47 × 1 | – | |
| M5' (present study) | – | 47 | 136 | 45 | 2 | 284 |
| | – | 47 × 5 | 136 × 0 | 45 × 1 | 2 × 2 | |
