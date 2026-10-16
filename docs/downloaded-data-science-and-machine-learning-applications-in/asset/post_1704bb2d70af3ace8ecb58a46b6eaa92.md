
Extra-Trees exhibit low variance, and their prediction accuracy improves with an increasing number of trees (Ernst et al., 2006).

## 4. Data Collection and Description

The Volve field, located in the Norwegian part of the North Sea, is a sandstone oil-bearing reservoir interval. The Volve field formation predominantly consists of near-shore, shallow, to marginal marine deposits. As a result of the extensive core sampling, it was discovered that six distinct facies associations represent the Heather Formation; coastal plain, shoreface, fluvio-tidal channel-fill, bay-fill, mouth bar, and offshore open marine (Folkestad and Satur, 2008; Otchere et al., 2022b, 2021a; Sneider et al., 1995). The data used has 12 dimensions compiled from three wells, Well 15_9-F-1_A (Well A), 15_9-F-1_B (Well B) and 15_9-F-15_D (Well C). However, well A and B were combined, making up 4,000 data points (2,125 for Well A and 1,875 for Well B), to train and test the model. A wireline plot of Wells A and B showing the shear (DTS) and compressional (DT) logs is illustrated in Figs. 4.2 and 4.3. The model was then deployed to estimate DTS and DT for Well C, which had a total data point of 11,935 without Vp and Vs logs. One of the main advantages of applying data analytics to data is to find patterns and hidden information in high dimensional data. As such, the primary input features for this research are summarised and justified in Table 4.4. Table 4.5 shows the descriptive statistics of the features for the combined Well A and Well B.

Table 4.4. Justification for log selection as input variables.

| Log | Purpose | Reason |
|---|---|---|
| Gamma ray (GR) | Lithology determinant | Lithologies exhibit different Vs and Vp wave velocities (Otchere et al., 2021c). |
| Neutron (NPHI) | Lithology and porosity determinant | Lithologies and porosity influences Vs and Vp differently (Otchere et al., 2021c). |
| Density (RHOB) | Lithology and porosity determinant | Lithologies and porosity influences Vs and Vp differently (Otchere et al., 2021c). |
| Photoelectric factor (PEF) | Determination of minerals for lithology interpretation | The response of Vs and Vp varies with different mineral types or compositions (Castagna et al., 1985). |
| Porosity (PHIF) | Lithology determinant | Vs velocity is more sensitive than Vp to porosity (Hamada and Joseph, 2020). |
| Water saturation (SW) | Fluid determinant | Different formation fluids affect Vp and Vs responses differently (Castagna et al., 1985). |
| Resistivity {true (RT), shallow (RACELM), medium (RACEHM), and deep (RPCELM)} | Lithology and hydrocarbon detection logs | Different fluids have different effects on Vs and Vp (Otchere et al., 2021c). |
| Caliper (CALI) | Detection of permeable zones hence relates to formation types | Different permeabilities affect Vs and Vp differently (Hamada and Joseph, 2020). |

![](img/80b94770dd572ad559c67fa9921bb887_87_0.png)

Fig. 4.2. Wireline plot of Well A showing the input logs and the shear (DTS) and compressional (DT) logs.

![](img/80b94770dd572ad559c67fa9921bb887_88_0.png)

Fig. 4.3. Wireline plot of Well B showing the input logs and the shear (DTS) and compressional (DT) logs.

Table 4.5. Descriptive statistics of the outputs and input variables for the combined Wells A and B.

| | CALI | DT | DTS | GR | NPHI | PEF | RACEHM | RACELM | RHOB | RPCELM | RT | PHIF |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| count | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 | 4000 |
| mean | 8.66 | 75.98 | 129.96 | 48.75 | 0.16 | 6.07 | 4.25 | 3.40 | 2.47 | 3.02 | 3.96 | 0.11 |
| std | 0.04 | 6.80 | 13.56 | 20.18 | 0.05 | 0.75 | 87.41 | 50.11 | 0.13 | 7.85 | 11.99 | 0.06 |
| min | 8.47 | 58.63 | 96.90 | 8.00 | 0.05 | 4.30 | 0.20 | 0.23 | 2.15 | 0.14 | 0.19 | 0.02 |
| 25% | 8.63 | 71.68 | 122.19 | 36.88 | 0.13 | 5.62 | 1.04 | 1.03 | 2.40 | 1.06 | 1.08 | 0.06 |
| 50% | 8.67 | 75.14 | 130.42 | 46.23 | 0.16 | 6.05 | 1.44 | 1.38 | 2.48 | 1.50 | 1.58 | 0.10 |
| 75% | 8.70 | 80.93 | 136.00 | 56.55 | 0.19 | 6.37 | 2.53 | 2.42 | 2.56 | 2.64 | 3.03 | 0.15 |
| max | 8.87 | 96.22 | 186.09 | 127.06 | 0.41 | 10.99 | 5464.37 | 2189.60 | 3.05 | 96.43 | 134.70 | 0.27 |

## 5. Methodology

### 5.1 Data Analysis and Visualisation

The data for this study were analysed and visualised to help understand how the input variables correlate to both targets. The Kendall correlation covariance heatmap was used to calculate the degree of correlation between the inputs and the targets. The NPHI, RHOB, and PHIF were the parameters that strongly correlated to both targets. The nonlinear distribution between the input and the targets is also illustrated in the pair plot in Fig. 4.4. Based on the nonlinear distribution, it is clear that none of the input parameters had a linear relationship to both targets, hence advising on the selection of nonlinear models for this study.

### 5.2 Machine Learning Model Application

As part of the machine learning process, the models are trained on data which were randomly sampled from the total dataset using the holdout cross-validation technique. This technique is used to assess the performance of models and prevents selection bias and overfitting by predicting the targets using unseen data (Otchere et al., 2022a; Tarafder et al., 2021). The holdout approach divided the data into a 90:10 split, making up 3,600 training and 400 testing data points. The selection of the split is to ensure that the majority of the data are used to train the model due to the heterogeneity of the subsurface but to ensure a suitable number unknown to the models is kept for testing. Different multi-output models were utilised in this study to determine which model accurately predicts the Vs and Vp accurately. This study utilised the same out-of-sample data to guarantee that all the models were predicted on equivalent data points. The performance of the models was assessed, in order of ranking, using the mean absolute error (MAE), root mean squared error (RMSE), mean absolute per cent error (MAPE) and R². The models were also compared using the Akaike Information Criterion (AIC), a frequentist probability framework that scores models based on the maximum likelihood of fitting unknown data. Upon selecting the best model based on these criteria (BO), hyperparameter tuning, a sequential model-based optimisation procedure, was used to enhance the model’s prediction accuracy. The BO technique is a convenient and dynamic paradigm that uses the Bayes Theorem to give a reasonable mechanism for guiding the search of a global optimisation problem to the extrema of objective functions (Otchere et al., 2022b). The technique operates by training a Bayesian approximation probabilistic model of the objective function repeatedly based on previous result estimation. Before choosing acceptable samples for evaluation on the real objective function, the probabilistic model is evaluated using an acquisition function. The process of adjusting the model’s parameters to improve the learning algorithm’s efficiency and optimise model performance by reaching a sufficiently reduced cost function is known as hyperparameter tuning (Otchere et al., 2022b). The optimised model is then deployed on a new well from the same field to predict Vs and Vp from the wireline logs. The predicted Vs and Vp log will be compared to that obtained from empirical correlations. Figure 4.5 shows the research workflow.

![](img/80b94770dd572ad559c67fa9921bb887_90_0.png)

Fig. 4.4. Pair plot distribution of all input features colour-coded using sand flag.

![](img/80b94770dd572ad559c67fa9921bb887_91_0.png)

Fig. 4.5. Schematic workflow of the methods used in this study.

## 6. Results and Discussion

### 6.1 Evaluation of Model Performance

The models employed in this study were assessed using AIC to identify the model with the highest likelihood of fitting out-of-sample data. The procedure in using this metric to evaluate the models suggests that the lower the AIC values, the greater the possibility of fitting new data. The following considerations were taken for this study when comparing and selecting the best model. There are four levels of significance when it comes to differences in AIC results between models: negligible (< 20), moderate (21–50), substantial (51–100) and extremely strong (> 100). The Extra-Trees model resulted in the highest probability of fit for Vp and Vs predictions by recording the lowest AIC value. When the Extra-Trees model was compared to the Random Forest model, representing the two models with the lowest AIC, there was a difference of 180 AIC. The result is illustrated in Fig. 4.6. Based on this outcome, the Extra-Trees model showed extreme differences and an enhanced chance of fit. AIC determines the model’s convergence to actual data. However, over- or underfitting may persist. As such, further model assessment is required using other error metrics.

Out-of-sample data results were used to evaluate the models’ performance. Since the models were trained using the training dataset, any attempt to duplicate the data will be highly accurate. As a result, the models are expected to have a high training accuracy score. However, a high level of training accuracy might lead to an unrepresentative model due to overfitting the data by matching inherent noise in the data. The proportion of accurate predictions generated by the models on the test data is used to assess the model performance on data that has not yet been observed. A high test accuracy is highly desired in the prediction of Vp and Vs to confirm model accuracy and robustness on new data since inaccurate measurements will have long-term defects in many operations. In this study, R² greater than 0.9 was regarded as an acceptable compromise between bias and variance. As can be seen in Fig. 4.7, the Extra-Trees model performed the best in terms of estimating Vp and Vs during testing.

![](img/80b94770dd572ad559c67fa9921bb887_92_0.png)

Fig. 4.6. AIC results comparing all the models on the test data.
