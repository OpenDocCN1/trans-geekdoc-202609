

The GMDH algorithm returned the following selective polynomials for prediction of concrete shear capacity of HSC slender beams as:

Layer 1:

\( L_1 = -1.7 + 1.3\rho + 1.1\left(\frac{a}{d}\right) + 0.02d + 0.27\left(\frac{a}{d}\right)\rho - 0.004d\rho - 0.009d\left(\frac{a}{d}\right) \
- 0.18\rho^2 - 0.18\left(\frac{a}{d}\right)^2 - 1.5 \times 10^{-5}d^2 - 0.00041d\left(\frac{a}{d}\right)\rho - 0.026\left(\frac{a}{d}\right)\rho^2 \
- 0.016\left(\frac{a}{d}\right)^2\rho + 0.00059d\rho^2 + 0.0014d\left(\frac{a}{d}\right)^2 + 2.9 \times 10^{-6}d^2\rho \
+ 2 \times 10^{-6}d^2\left(\frac{a}{d}\right) + 0.0067\rho^3 - 0.0094\left(\frac{a}{d}\right)^3 + 4.3 \times 10^{-9}d^3 \) (22.20a)

Layer 2:

\( v_u(kN) = 2.5 - 1.4L_1 - 0.03f'_c - 25\left(\frac{a_g}{d}\right) + 0.0017f'_cL_1 + 42\left(\frac{a_g}{d}\right)L_1 + 0.7\left(\frac{a_g}{d}\right)f'_c \
+ 0.42L_1^2 + 7.9 \times 10^{-5}f'_c^2 - 4.1 \times 10^2\left(\frac{a_g}{d}\right)^2 - 0.3\left(\frac{a_g}{d}\right)f'_cL_1 \
+ 0.0095f'_cL_1^2 - 6.7 \times 10^{-5}f'_c^2L_1 - 7.1\left(\frac{a_g}{d}\right)L_1^2 - 0.0039\left(\frac{a_g}{d}\right)f_c'^2 \
+ 6\left(\frac{a_g}{d}\right)^2L_1 + 2.6\left(\frac{a_g}{d}\right)^2f'_c - 0.092L_1^3 + 1.2 \times 10^{-6}f_c'^3 + 7200\left(\frac{a_g}{d}\right)^3 \) (22.20b)

To further evaluate the proposed MARS and GMDH model against the most common regression approaches, a new regression equation was developed using MNLR as:

\( v_u = 14.50d^{-0.39}\left(\frac{a}{d}\right)^{-0.62}f_c'^{0.12}\rho^{0.45} \) (22.21)

To analytically evaluate the performances of the developed models, the following statistical error parameters were applied: mean absolute error (MAE), root mean square error (RMSE), correlation coefficient (R) and coefficient of determination (\(R^2\)).

\( MAE = \frac{\sum_{i=1}^N |P_i - O_i|}{N} \) (22.22)

\( RMSE = \sqrt{\frac{1}{N}\sum_{i=1}^N (P_i - O_i)^2} \) (22.23)

\( R = \frac{\sum_{i=1}^N (P_i - P_m)(O_i - O_m)}{\sqrt{(P_i - P_m)^2}\sqrt{(O_i - O_m)^2}} \) (22.24)

\( R^2 = 1 - \frac{\sum_{i=1}^N (O_i - P_i)^2}{\sum_{i=1}^N (O_i - O_m)^2} \) (22.25)

where \( O_i \) is the measured value, \( P_i \) stands for prediction values; \( N \) is the number of data points, \( O_m \) is the mean value for observation and \( P_m \) is the mean value of prediction. The correlation coefficient (\( R \)) is a measure of the relative correlation between the predicted and measured values. The \( R \) values ranged between \( -1 \) and \( 1 \). If the \( R \) value is close to \( 1 \), it indicates that there is direct linear relationship between measured and predicted values. However, \( R \) does not necessarily indicate the goodness of the model performance, particularly when data range is very wide and the data points distributed about their mean. Therefore, the coefficient of determination, \( R^2 \), can be used as an unbiased estimate and can be a better measure for evaluating model performance. The \( MAE \) and \( RMSE \) measure the difference between predicted and measured values and values near to zero indicate a close match.

## 22.5 Results and Discussion

The results of developed models and the most common design equations for prediction of shear strength of HSC slender beams without web reinforcement are compared in this section. Moreover, the influences of important parameters on shear strength have been investigated through parametric and sensitivity analyses. The most important predictive parameters were determined through sensitivity analysis in prediction of shear strength. Finally, safety analysis was done by using demerit point's classifications of Collins.

### 22.5.1 Performance Analysis

The number of data used to develop a new predictor model based on machine learning approaches plays a crucial role in modeling process. For developing a reliable model based on data mining approaches, Frank and Todeschini [37] suggested that the minimum ratio between the number of data used and the number of involved variables should be 3. A safer value of 5 can be more conservative. In the present study, this ratio is remarkably more and is equal to 250/6 = 41.66. The performances of developed MARS and GMDH models shown in Fig. 22.2a, b demonstrate that there are a little scatter around optimal line between measured and predicted shear strength by developed models for both training and testing data sets. For further verification of developed models, analytical analysis of statistical error parameters for training and testing data sets are presented in Table 22.4. Also the results of the developed MNLR method in this study were compared with those of the other proposed ones.

### Table 22.4 Performance of GMDH and regression models in predicting shear strength for training and testing datasets

| Subset | Model | MAE | RMSE | R | R² |
|---|---|---|---|---|---|
| Training | MARS | 0.1405 | 0.1849 | 0.9715 | 0.9438 |
| Training | GMDH | 0.2223 | 0.2983 | 0.9241 | 0.8537 |
| Training | MNLR | 0.2741 | 0.3626 | 0.8866 | 0.7839 |
| Testing | MARS | 0.1395 | 0.1902 | 0.9630 | 0.9253 |
| Testing | GMDH | 0.2592 | 0.3670 | 0.8519 | 0.7217 |
| Testing | MNLR | 0.2684 | 0.3831 | 0.8414 | 0.6966 |
| Total | MARS | 0.1403 | 0.1860 | 0.9699 | 0.9408 |
| Total | GMDH | 0.2297 | 0.3132 | 0.9122 | 0.8321 |
| Total | MNLR | 0.2729 | 0.3668 | 0.8789 | 0.7697 |

Smith [38] suggested that if |R| > 0.8, it can be expected that there is a strong correlation between observed and predicted values. It should be recognized that even if R is close to 1, the predicted and observed values may not match each other; they only tend to vary similarly. To compensate this limitation, coefficient of determination R² can be used. To have precise results, R² values should be close to 1. In all cases, the RMSE and MAE should be close to zero. As shown in Table 22.4, the MARS model outperformed the GMDH and MNLR models in term of accuracy for both training and testing data sets. For example, the MARS model decreased the RMSE value by 40.6% and 49.2% and increased R² values by 13% and 22.2% in respect to GMDH and MNLR models, respectively. It should be noted that the performances of developed GMDH and MNLR models are also acceptable and GMDH outperformed the MNLR model. Lower accuracy of MNLR can be attributed to its limitations in predicting the phenomenon with a highly nonlinear relationship or with multiple criteria.

The results of developed models are also compared with those obtained from the most available design codes and standards including ACI 318-11 [27], CSA A23.3-04 [28], fib Model Code [29], Eurocode-2 [30], CEB-FIP [31] Model Code, AS 3600-2009 [32], JSCE [33] Guidelines, and Cladera and Mari [34] in Table 22.5. In general, the accuracy of design codes is remarkably limited for predicting shear strength of HSC slender beams without web reinforcement, especially ACI 318-11, CSA A23.3-04, fib model Code, and JSCE guidelines. In fact, these design codes except CEB-FIP models were not exclusively suggested for HSC slender beams without web reinforcement and had limitations on the maximum value of f’<sub>c</sub> (ACI 318-11 [27], CSA A23.3-04 [28], fib Model Code [29], Eurocode-2 [30], CEB-FIP [31] Model Code, AS 3600-2009 [32], JSCE [33] Guidelines, and Cladera and Mari [34]) or on the percentage of tension steel (Eurocode-2 [30], and Cladera and Mari [34]). Therefore, most of these equations cannot correctly be employed to predict shear strength of HSC slender beams. However, AS 3600-2009 [32] model had the best performance amongst the other design codes, which had an R² of 0.50 (highest) and the RMSE of 0.54 Mpa (lowest), yet this model is significantly behind the three developed GMDH, MARS and MNLR models. For example, MARS model improved the RMSE and R2 respectively by 65.5% and 88% in comparison with the best design code. Thus, the developed models can predict the target values of the shear strength of HSC slender beams without web reinforcement with acceptable accuracy and less error than the available design codes over a wide range of input variables.

To have a deeper understanding of the errors in design codes, the discrepancy (DR) between measured and predicted shear strength as an error indicator was plotted against the most effective parameters including longitudinal steel ratio (\(\rho\)), \(f'_c\), \(d\) and \(a/d\) for testing data set in Fig. 22.3. The results of Eurocode-2 [30], CEB-FIP [31] and AS 3600-2009 [32], which had more acceptable accuracy, were compared with those of GMDH and MARS models in this aspect. The best linear regression is also fitted to prediction values of mentioned models. Errors of an appropriate model should be independent or less sensitive to the variation of the input parameters involved in that phenomenon. Otherwise, it can be interpreted that those input parameters either aren’t correctly incorporated or should be included in that model [39]. As shown in Fig. 22.3, the errors of these design codes are sensitive to change of \(\rho\) as if their prediction varied from overestimation status to underestimation status as \(\rho\) increases. It can be interpreted that this parameter is not correctly involved in their equations. On the other hand, the errors of GMDH and MARS models are completely independent of this parameter.

According to this figure, the errors of all models are almost independent of \(f'_c\) and \(d\) parameters. Thus, it can be expected that these parameters probably well-defined in the mentioned models. It should be noted that the errors of Eurocode-2 [30] to variation of \(d\) parameter is more than other models. Also the error sensitivity of GMDH and MARS models to variations of \(d\) and \(f'_c\) is less than the three design codes. Figure 22.3 also demonstrates the errors of mentioned models as a function of \(a/d\) parameter. It can be seen that the predictions of design codes varied from underestimation status to overestimation status as \(a/d\) increases and this inclination in CEB-FIP [31] model is less than the other two equations. As a result, these figures

![](img/4048998719320644ee88964326fd7995_471_0.png)

![](img/4048998719320644ee88964326fd7995_471_1.png)

Fig. 22.2 Comparison between measured and predicted shear strength (V(kN)) by a MARS, b GMDH model for training and testing dataset

### Table 22.5 Performance of existing equations for prediction of shear strength of slender HSC beams

| Model | MAE | RMSE | R | R² |
|---|---|---|---|---|
| ACI 318-11 | 0.5891 | 0.7939 | 0.6676 | -0.0787 |
| CSA A23.3-04 | 0.6976 | 0.9358 | 0.5289 | -0.4988 |
| Fib | 0.6895 | 0.9254 | 0.5252 | -0.4656 |
| Eurocode 2 | 0.4341 | 0.6161 | 0.7311 | 0.3503 |
| CEB-FIP | 0.4273 | 0.6059 | 0.8498 | 0.3718 |
| AS 3600-2009 | 0.3758 | 0.5402 | 0.8241 | 0.5005 |
| JSCE | 0.5430 | 0.7525 | 0.8188 | 0.0307 |
| Cladera and Mari | 0.4540 | 0.6399 | 0.8104 | 0.2992 |

