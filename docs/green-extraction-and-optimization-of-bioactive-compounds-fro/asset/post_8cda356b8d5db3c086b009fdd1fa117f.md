
# Table 3 (continued)

| S. No | Independent parameters | Experimental Responses | RSM Predicted Responses | ANFIS Predicted Responses | ML Algorithm Predicted Responses |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | | X1 | X2 | X3 | Y1 | Y2 | Y3 | Y1 | Y2 | Y3 | Y4 | Y1 | Y2 | Y3 | Y4 | Y1 | Y2 | Y3 | Y4 | Y5 |
| 42 | 60 | 55 | 37.5 | 8.1 | 472.34 | 227.69 | 35.7 | 43.66 | 55.22 | 522.17 | 270.52 | 43.37 | 50.23 | 59.82 | 474 | 228 | 35.7 | 55.2 | 481.14 | 244.47 | 36.48 | 43.36 | 54.10 |
| 43 | 60 | 55 | 37.5 | 20 | 513.38 | 276.92 | 40.11 | 47.11 | 52.43 | 465.10 | 263.99 | 66.61 | 71.80 | 74.17 | 474 | 268 | 37.1 | 52.2 | 475.56 | 267.85 | 37.17 | 42.31 | 51.81 |
| 44 | 65 | 50 | 30 | 15 | 570.98 | 440 | 65.53 | 71.66 | 75.76 | 789.33 | 467.19 | 66.61 | 71.80 | 74.17 | 771 | 440 | 65.5 | 71.7 | 757.73 | 455.05 | 67.56 | 73.15 | 75.72 |
| 45 | 60 | 55 | 37.5 | 31.9 | 683.01 | 406.14 | 62.14 | 67.85 | 74.12 | 597.31 | 344.48 | 49.53 | 56.79 | 66.83 | 608 | 406 | 61.2 | 67.8 | 596.50 | 365.80 | 52.89 | 53.99 | 65.19 |
| 46 | 60 | 55 | 37.5 | 20 | 471.23 | 276.92 | 32.11 | 38.11 | 39.55 | 465.10 | 263.99 | 36.20 | 41.09 | 51.75 | 474 | 268 | 31.7 | 42 | 472.56 | 267.85 | 37.17 | 42.1 | 51.81 |
| 47 | 65 | 50 | 30 | 15 | 648.45 | 315.15 | 35.1 | 43.15 | 46.15 | 528.33 | 320.28 | 38.13 | 43.13 | 51.75 | 671 | 315 | 37.1 | 44.1 | 715.20 | 317.58 | 37.17 | 40.84 | 56.45 |
| 48 | 65 | 50 | 25 | 15 | 808.87 | 483.08 | 71.66 | 74.11 | 75.35 | 868.99 | 505.83 | 75.02 | 78.33 | 80.32 | 809 | 483 | 71.7 | 74.1 | 802.88 | 474.26 | 71.49 | 75.42 | 76.75 |
| 49 | 55 | 50 | 45 | 15 | 808.37 | 293.85 | 30.56 | 35.22 | 44.21 | 492.26 | 315.08 | 39.34 | 41.01 | 51.81 | 489 | 294 | 30.6 | 35.2 | 442.14 | 290.87 | 33.64 | 37.58 | 48.27 |
| 50 | 55 | 50 | 30 | 15 | 1550.08 | 310.77 | 33.43 | 46.66 | 451.82 | 247.63 | 34.12 | 39.23 | 49.18 | 489 | 550 | 33.1 | 36.7 | 481.36 | 278.83 | 34.86 | 38.68 | 49.78 |

* All experiments were repeated three times.

![](img/e46bd6ed00fca11057503aecbc84a_7_0.png)

Fig. 1. The input and output data in this study's set. $Y_3, Y_4,$ and $Y_5$ are used as output units. The dataset first imported is the experimental values in order to produce the predictions, and it is then preprocessed to determine whether the dataset has missing or noisy data.

## 2.15 Validation experiments
In order to ensure that the experiment worked, the validity of the optimization result was investigated. The mean experimental results were compared to evaluate the model's efficiency. In the case, the triplet experiment was conducted on a variety of responses with changing parameters.

## 2.16 GC-MS and LC-MS analysis
Gas chromatography-mass spectrometry (GC-MS) analysis was performed using a nonpolar 60 m RTX95 column and the Shimadzu Q-2010 GC-MS system with helium as the carrier gas, containing 15 psi as constant pressure. The bioactive compounds in the optimized extract were identified and described accordingly. By comparing the results of chromatographic peaks using a Quadrupole detector and the National Institute of Standards and Technology (2014) library to retrieve identity, the chemical compounds from extraction of *S. swrv* were determined. 62,509 patterns were identified from the acquired mass spectrum. The fraction's unidentified components were compared to the reference spectra of recognized components in the NIST library. Liquid chromatography-mass spectrometry (LC-MS) analysis was performed using the 1290 UHPLC HPLC with Chorus and 6500 Ion Q-TOF (Agilent Technologies, USA) in accordance with the previously described protocol (Chowdhury et al., 2018).

## 2.17 Statistical analysis
All investigations were conducted based on BCC of RSM and were repeated three times. Using design experiment software (version 8.0.7.1, Stat-Ease, Inc., 227 Hennepin Ave, Suite 480, Minneapolis, MN 55413, USA), all the experimental data collected from extraction process were processed. One-way analysis of variance (ANOVA) and Duncan's test were used to evaluate the analytical strength. All collected data were mentioned as mean $\pm$ standard deviation. The contour plots and three-dimensional (3D) surface plots were used to identify the extraction conditions. Microsoft Excel 2010 was used for statistical analysis, together with the Adaptive Neuro-Fuzzy Logic Toolbox in the MATLAB v2013a.

## 3. Result and conclusion

### 3.1 Fitting model
The experimental parameters were successfully optimized using BCC with RSM. This experimental design based on the condition of linear, interaction, and quadratic factors of ultrasound-assisted extraction parameters to achieve the highest yield of bioactive compounds from *S. swrv*. Table 3 predicted the experimental $DPPH\%$, $ABTS\%$ and $H_2O_2$ scavenging activities of *S. swrv*. Extraction from ultrasound-assisted solvent extraction showed that the predicted values of polyphenolic compounds, total carotene content, flavonoid showed that the optimized values were achieved at 65% of medium, 60 $cm^{-2}$ ultrasound intensity, 45 °C, 15 minutes, and 0.5 mm particle size. The optimization condition, the optimal yield of $Y_p$ and antioxidant activities were found to be 83.66 mg/mL, 53.38 mg/mL, 77.52 $DPPH\%$, 81.12 $ABTS\%$, 85.02 $H_2O_2\%$, respectively. The results are consistent with earlier research work which demonstrated most amount of bioactive compounds from *Garcinia indica* (Kanjappan et al., 2020), and *Azolla mylla* (Selvaraj et al., 2014). By examining the effects of multiple determination and performing analyses of variety, the experimental data fitted to describe

### 3.2 Investigation of surfaces
The experimental values and results for total polyphenolic compounds using ultrasound-aided solvent extraction are presented in Table 3. Analysis of variance (ANOVA) was performed to estimate the significance of regression model. From data of Table 4 and Equation (7), it clearly showed that the methanol concentration (X1) and particle size (X2) are significant while the effect of ultrasound intensity (X3) and time (X4) are not. Furthermore, the regression coefficient of model of ultrasound-aided extraction of total polyphenols showed a lack of fit ($R = 0.2704; R^2 = 0.0137$, and $R^2 = 0.008$). The empirical model for the highest yield of total polyphenols with content parameter is given in the following equation:

$Y_3 = 46.5 + 30.181X_1 + 8.221X_2 + 1.457X_3 + 11.593X_4 + 6.815X_5 + 19.941X_6 - 51.22X_7 - 6.74X_4 \text{ (note: duplicate in OCR)} + 9.955X_5 + 14.214X_6 - 15.615X_7 - 13.5X_8 + 27.2X_9 + 11.852X_{10} + 72.538X_{11}$

The data were further examined in order to determine the difference between experimental values and the value predicted by the model. Residuals were calculated and the distribution of residuals of $X_1, X_2, X_3$ and $X_4$ are shown in Fig. (2a) as a normal probability plot. There are no deviations from the normal distribution. Fig. (2b) shows the residuals versus predicted values, which indicates that the model is fit the data. The effect of methanol concentration (X1) and ultrasound intensity (X3) on the extent of maximum content of total polyphenolic compounds were further illustrated by 3D response surface and contour plot in Fig. (2c) and (2d), which show the effect of the three variables-(X3), time (X4) and particle size (X2) were well-held (constant) at 37°C, 20 min, and 3 mm, respectively. Table 3 shows that the total phenolic concentrations ranging from 314.737 to 830.667 mg/G. At 65% methanol concentration, 60 cm⁻² ultrasound intensity, 45°C, 15 min, and 5 mm particle size, the highest yield of total polyphenolic was obtained.

### 3.2.2 Total flavonoids
The linear term of particle size (X_2), interaction term $X_2X_3$ and quadratic term $X_2^2$ are significant (at $\alpha=0.05$) for determining the maximum yield of total flavonoids and is presented in the second-order polynomial equation (8). The experimental model successfully fits the data, as evidenced by the response surface analysis of the total content of the flavonoids, which had a high regression coefficient of $R^2 =0.7119$ and a lack of fit of 0.001. The second-order polynomial equation for the total content of flavonoids in coded variables is provided by the following equation (8):

$Y_2 = 26.939 + 16.296X_1 + 6.91X_2 + 3.113X_3 + 17.4X_4 - 17.16X_5 - 5.84X_6 - 5.00X_7 - 8.46X_8 - 2.693X_9 - 2.212X_{10} + 0.814X_{11} + 8.444X_{12} - 6.828X_{13} - 3.36X_{14} + 6.78X_{15} + 19.18X_{16} - 13.5X_{17} + 7.62X_{18} + 5.05X_{19}$

Fig. (2c) displays the distributed residuals for $X_1, X_2, X_3$ and $X_4$. They have a normal distribution and no deviation. The high regression coefficient values ($R^2 = 0.711$) which as a good fit, are shown in Fig. (3a). The 3D response surface and contour plot in Fig. (3b) and (3d) demonstrate how methanol concentration (X1) and particle size (X2) affect the S. torruf extract. The greatest level of total flavonoids. From 200.73 to 535.38 mg/unit (RE/s) of flavonoids were found in Table 2. 65% methanol (v/v), 60 cm v² of ultrasound intensity, 45 temperature, 15 min, and 5 mm of particle size produced the highest yield,

### 3.3 Antioxidant capacity (%DPPH%, %ABTS% and %H2O2%)
Based on the statistical analysis of the RSM design in Table 3 and Equations (9)-(11), the linear terms of methanol concentration (X1), particle size (X3), interaction term X1X3, quadratic term X1² have significant effects on all three antioxidant
