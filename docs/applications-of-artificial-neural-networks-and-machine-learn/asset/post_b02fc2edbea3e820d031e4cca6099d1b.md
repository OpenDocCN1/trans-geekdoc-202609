
![](img/4048998719320644ee88964326fd7995_412_0.png)

Fig. 20.5 The variations of $F_{max}$ with input variables for different classes

## 20.4.4 The MARS Model

As stated in Sect. 20.3, the segments (splines) of the MARS algorithm can be either piecewise linear or cubic segments. In this study, both segments are used to develop model; but the developed model based on piecewise linear segment, which had better performance, is only presented. After presenting training data set to MARS algorithm, the following equation for maximum bond strength is derived:

$$
\begin{aligned}
F_{max}(kN) = {} & 17 - 0.71 \times BF_1 - 1.2 \times BF_2 + 0.25 \times BF_3 - 0.076 \times BF_4 \\
& + 3.8 \times 10^3 \times BF_5 - 0.019 \times BF_6 - 0.94 \times BF_7 + 0.118 \times BF_8 + 0.067 \times BF_9 \\
& - 7.5 \times 10^4 BF_{10} + 3.7 \times 10^3 BF_{11} - 3.8 \times 10^3 BF_{12} - 3 BF_{13}
\end{aligned}
\tag{20.19}
$$

The basis functions (BFs) and their corresponding equations are listed in Table 20.2. It should be noted that, from Table 20.2, of the 14 BFs, 12 BFs with interaction terms are integrated in this model, indicating that the model is not simply additive and that interaction terms play a significantly important role. The final model of MARS (Eqs. 20.18a–20.18d) is achieved via GCV obtained from forward selection and backward deletion process. As observed, one of the advantages of MARS algorithm is that not only captures complex relationships between independent and dependent variables but also does not require additional effort to verify a prior assumption about the relationship between the set of independent variables and the dependent response variable. The latter feature becomes more important as the dimension of the problem increases.

| Basis function number | Equation |
|---|---|
| BF1 | max(0, 60 - bp) |
| BF2 | max(0, 3.3 - fmt) |
| BF3 | max(0, 160 - Lb) |
| BF4 | max(0, 38 - Epfp) |
| BF5 | BF1 x max(0, 0.36 - bp/bm) |
| BF6 | BF3 x max(0, bp - 35) |
| BF7 | max(0, bp - 60) x max(0, 0.4 - fmt) |
| BF8 | max(0, Lb - 160) x max(0, fmt - 1.9) x max(0, bp/bm - 0.45) |
| BF9 | max(0, Lb - 160) x max(0, fmt - 1.9) x max(0, 0.45 - bp/bm) x max(0, Epfp - 21) |
| BF10 | max(0, 0.36 - bp/bm) |
| BF11 | BF10 x max(0, bp - 40) |
| BF12 | BF10 x max(0, 40 - bp) |
| BF13 | BF3 x max(0, 0.27 - bp/bm) |
| BF14 | max(0, 1.1 - fmt) x max(0, bp - 50) |

## 20.5 Results and Discussions

### 20.5.1 Performance Analysis

The number of data used to develop a reliable model based on data mining approaches plays a crucial role in modeling process. Frank and Todeschini [59] suggested that the minimum ratio between the number of data used and the number of involved variables should be 3. A safer value of 5 can be more conservative. In the present study, this ratio is remarkably more and is equal to 230/7 = 32.85. For evaluation of the developed models, the scatter diagrams between measured and predicted maximum bond strength based on M5′ and MARS algorithms for testing and training data points are shown in Fig. 20.6. As seen, there are little scatters between predicted and measured values of bond strength around the optimal line in both training and testing sets; and data points mostly concentrated around this line. For further verification of developed models, analytical analysis of statistical error parameters for training and testing data sets are presented in Table 20.3.

Smith [60] suggested that if |R| > 0.8, it can be expected that there is a strong correlation between observed and predicted values. It should be recognized that even if R is close to 1, the predicted and observed values may not match each other; they only tend to vary similarly. To compensate this limitation, coefficient of determination R2 can be used. To have precise results, R2 values should be close to 1. In all cases, the RMSE and MAE should be close to zero. As shown in Table 20.3, the MARS model constructed based on piecewise linear basis segments outperformed the models of

![](img/4048998719320644ee88964326fd7995_414_0.png)

Fig. 20.6 Comparisons of measured and predicted values of Pmax (kN). a M5′ and b MARS

| Model | Dataset | MAE | RMSE | SI (%) | R | R² |
|---|---|---|---|---|---|---|
| M5′ | Training | 1.8191 | 3.0476 | 31.4 | 0.8606 | 0.7094 |
| M5′ | Testing | 1.3317 | 1.9082 | 32.76 | 0.8524 | 0.7137 |
| M5′ | Total | 1.6749 | 2.7458 | 31.79 | 0.8536 | 0.7133 |
| MARS Linear | Training | 1.2510 | 1.7449 | 19.70 | 0.9455 | 0.8934 |
| MARS Linear | Testing | 1.3658 | 1.8632 | 22.94 | 0.9157 | 0.8315 |
| MARS Linear | Total | 1.2854 | 1.7812 | 20.62 | 0.9377 | 0.8793 |
| MARS Cubic | Training | 1.4040 | 1.9887 | 22.45 | 0.9283 | 0.8616 |
| MARS Cubic | Testing | 1.3389 | 1.9722 | 24.28 | 0.9017 | 0.8112 |
| MARS Cubic | Total | 1.3845 | 1.9837 | 22.97 | 0.9221 | 0.8503 |

MARS with cubic segments and M5′ in terms of accuracy for both training and testing data sets. For example, it decreases the RMSE value by 11% and 35%, respectively, and increases the R² values by 3.4% and 23.2% in respect to MARS model with cubic segment and M5′ model, respectively. It should be noted that the performances of developed MARS with cubic segments and M5′ models are also acceptable and MARS with cubic segments also outperforms the M5′ model.

The performances of the developed MARS (with linear segments) and M5′ models are also compared with the most common existing equations including Tanaka [12], Sato (from [21]), Iso (from [21]), Yang et al. [18], Neubauer and Rostasy [14], Willis et al. [20], Kashyap et al. [22], Maeda et al. [13], Khalifa et al. [15], and De Lorenzis et al. [16]. The statistical error parameters related to these equations are presented in Table 20.4. As shown, the accuracy of these equations is remarkably limited. However, Yang model has the best performance among other existing design equations. The proposed M5′ and MARS models outperform Yang equation by improving the R² value by 129% and 183%, respectively and the RMSE value by

35% and 58%, respectively. Therefore, the proposed models can predict the target values of the maximum bond strength with an acceptable level of accuracy and are remarkably more accurate than the available empirical models over a wide range of input parameters.

The histograms of discrepancy ratio between measured and predicted maximum bond strength ($DR = F_{max,meas}/F_{max,pre}$) by equations of Tanaka [12], Yang et al. [18], Neubauer and Rostasy [14], Khalifa et al. [15], and the proposed ones (M5’ and MARS) are illustrated in Fig. 20.7. The errors of a good predictive equation should be close to one and also be symmetrical around their mean values. A wider distribution generally leads to more uncertainty. As can be seen from Fig. 20.7, the distribution errors of mentioned empirical equations are remarkably wide and their predictions generally underestimate the values of maximum bond strength. On the contrary, the distribution errors of proposed M5’ and MARS models concentrate around 1 and these just slightly underestimate the bond strength.

The variations of DR values of different empirical equations and the proposed ones as a function of axial rigidity ($E_pt_p$) are shown in Fig. 20.8. A good model has errors that are independent of the input parameters [61]. Tanaka [12], Yang et al. [18], Neubauer and Rostasy [14], and Khalifa et al. [15] formulas are very sensitive to change of $E_pt_p$. However, according to Fig. 20.8, the model trees had a better performance than the others in this aspect. In addition, this figure shows that $E_pt_p$ is included in a better way in the developed models. A similar process has also been observed (not shown) for other input parameters, such as bond length, the width of reinforcement, the ratio between the width of reinforcement and support, and the tensile strength.

| Model | MAE | RMSE | SI (%) | R | R² |
|---|---|---|---|---|---|
| Tanaka [12] | 3.6059 | 4.428 | 51.27 | 0.5301 | 0.2543 |
| Sato [21] | 13.3588 | 17.9796 | 208.17 | 0.4977 | −11.2937 |
| Iso [21] | 21.8221 | 27.6588 | 320.24 | 0.7932 | −28.0931 |
| Yang et al. [18] | 2.9149 | 4.2581 | 49.3 | 0.692 | 0.3105 |
| Neubauer and Rostasy [14] | 3.5678 | 4.6007 | 53.27 | 0.6735 | 0.1951 |
| Willis et al. [20] | 5.2918 | 6.8515 | 79.33 | 0.5799 | −0.7852 |
| Kashyap et al. [22] | 8.0432 | 12.7069 | 147.12 | 0.3824 | −5.1405 |
| Maeda et al. [13] | 5.894 | 6.9859 | 80.88 | 0.5127 | −0.8559 |
| Khalifa et al. [15] | 3.1023 | 4.5276 | 0.5242 | 0.6633 | 0.2204 |
| De Lorenzis et al. [16] | 10.6634 | 12.4054 | 143.63 | 0.4797 | −4.8526 |
| M5′ (present study) | 1.6749 | 2.7458 | 31.79 | 0.8536 | 0.7133 |
| MARS (present study) | 1.2854 | 1.7812 | 20.62 | 0.9377 | 0.8793 |
