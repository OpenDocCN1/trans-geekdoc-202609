
represents the regularization strength. The larger value specifies stronger regularization, which was skilled in dealing with the problem of multi-collinearity and reduces the variance of the estimates (Ikeuchi, 2021). While in LR and ENR models, ‘alpha’ represents the constant that multiplies the penalty terms. When ‘alpha’ equal to 0, the modeling algorithm was equivalent to an ordinary least square (Januaviani et al., 2019; Meier et al., 2008). In SVR models, the kernel function and the regularization parameter (‘C’) were the important hyper-parameters usually need to be tuned (Pan et al., 2022). In this paper, ‘linear’, ‘poly’, ‘rbf’ were selected as the candidates of kernel function. The parameter of ‘C’ was inversely proportional to regularization strength. In addition, the algorithms of DT and the three advanced GBM were all tree-based ML techniques. And the parameters were related to the ‘model tree’ which were listed in Table 1 (Hong, 2020; Hosseinzadeh et al., 2022; Ke et al., 2017). The hyper-parameters and the tuned optimal value were summarized in Fig. 4 and Table 1.

## 3.4. Prediction performance of regularization algorithms

All the HCP-Models were established with the optimum hyper-parameters (Table 1), and the statistical results of the nine models were shown in Tables 2 and 3. RR, LR, and ENR models were approximately equal to each other with the test R² of ~0.80 and RMSE of ~0.48%, which were nearly consistent with our previous study (Gao, Shu, et al., 2022). The predicted values from the regularization algorithms vs. measured values in datasets were plotted in Fig. 5. It should be mentioned that the previous models built by regularization algorithms lacks the step of tuning hyper-parameters. It was expected that the models should present higher predictive accuracy than the previous ones with the help of the additional tuning step. Nevertheless, it only displays marginally better results of RMSE in test set since the tuning process was monitored based on the value of RMSE. Therefore, it suggests that the tuning step is slightly helpful to improve the quality of models built by regularization algorithms in this study. It still leaves room for improvement for better algorithms.

## 3.5. Prediction performance of classical machine learning algorithms

In order to obtain models with higher precision, three types of classical ML algorithms were adopted to execute the task, and the results were listed in Tables 2 and 3. The predictive performance was listed in Fig. 6. In HCP-Models built by SVR, DT, and RF, the statistical results of

**Table 1**
The optimized hyper-parameters of algorithms.

| Algorithm | Hyper-parameter | Ranges | Optimized value |
|---|---|---|---|
| RR | alpha | 0~7 | 0.46 |
| LR | alpha | 0~2 | 0.005 |
| ENR | alpha | 0~2 | 0.007 |
| SVR | kernel | linear, rbf, poly | Linear |
| | C | 0~6 | 0.4 |
| DT | max_depth | 1~10 | 9 |
| | min_samples_leaf | 1~6 | 3 |
| | min_samples_split | 1~9 | 7 |
| RF | n_estimators | 100~480 | 280 |
| | max_depth | 1~9 | 6 |
| LightGBM | learning_rate | 0~1 | 0.09 |
| | max_depth | 2~11 | 3 |
| | num_leaves | 3~20 | 9 |
| | min_data_in_leaf | 1~10 | 1 |
| CatBoost | learning_rate | 0~1 | 0.64 |
| iterations:100 | l2_leaf_reg | 2~16 | 13 |
| | depth | 2~10 | 3 |
| XGBoost | learning_rate | 0~1 | 0.15 |
| | n_estimators | 20~180 | 120 |
| | gamma | 0~0.1 | 0.03 |
| | max_depth | 2~11 | 2 |

Note: other unlisted hyperparameters were kept at default values.

test R² were ≥0.81, the test RMSE were ≤0.47%, the test MAE were ≤0.40%, and the test MAPE were ≤0.49%. Those three classical ML algorithms were proved to be qualified to build HCP-Model. Among the three classical ML algorithms, RF performed best predictive accuracy with a test R² of 0.85, an RMSE of 0.40%, an MAE of 0.31%, and an MAPE of 0.38%, showing a competitive advantage. And the predictive accuracy of HCP-Models developed by classical ML algorithms was higher than those built by regularization algorithms because of the higher R², lower RMSE, MAE, and MAPE.

It is generally accepted that the classical ML algorithms are capable of dealing with complicated features of the input data, such as multiple-dimensions and multi-collinearity. The input variables of HCP-Models were the features extracted from Raman spectra, which were all related to holocellulose, which may lead to the correlation among predictor variables. For verify the multi-collinearity, the variance inflation factor (VIF) was calculated. The value of VIF was 17.22, greater than 10, indicating that the data were suffered from multi-collinearity. The characteristic of multi-collinearity brings greater challenge for model development, which may partially unsolved by introducing the penalty item in regularization models. SVR is a widely used algorithm in regression and classification tasks. In SVM system, the result was determined by a few support vectors. The key information was utilized efficiently and the redundant information was eliminated, which is helpful to improve the robustness of SVR model. Both DT and RF are tree-based models. In DT model, the number of splitting nodes are adjusted to cater to the complexity of input values. By doing so, the essential information of input values can be extracted as much as possible when the redundant ones were hindered from intervening the models. Meanwhile, the deeper the model tree, the higher accuracy the training set, but the more possibility of overfitting. So, the tree-depth of the DT is controlled in model development, which can effectively avoid overfitting. Even DT and RF are both tree-based models, it may be difficult to train a reliable model with high predictive accuracy from multitudinous or complicated data because of the restrictions of memory, time complexity and data complexity (Mu et al., 2018). These deficiencies of DT can be partially compensated by RF which was an ensemble of many decision trees. In RF models, each decision tree was used as parallel estimators and the result of the model was based on majority vote of the results received from each decision tree. Consequently, the predictive accuracy of RF model was higher than that of DT. Comparing the classical ML models with the regularization models, it can be found that the prediction accuracy of the classical ML models was higher than that of the regularization model. It may demonstrate that the classical ML algorithms are more suitable than the regularization algorithms in dealing with the multiple-dimensions and multi-collinearity input values in this study. Furthermore, the RF model was superior to others five models. It is also coherent to the findings in building the lignin predictive models (Gao, Zhou, Liu, et al., 2022). Consequently, comparing with the result in this study with the findings of lignin predictive models in our previous work, it is suggested that the selection of optimum model from different classical ML algorithms did not change with the different data matrix of extracted features from Raman spectra.

## 3.6. Prediction performance of advanced GBM algorithms

As shown in Tables 2 and 3, models developed by LightGBM, CatBoost, and XGBoost all performed well in predicting holocellulose content. In these three models, all the test R² were ≥ 0.90, the test RMSE were ≤ 0.34%, the test MAE were ≤ 0.25%, and the test MAPE were ≤ 0.30%, indicating the high predictive accuracy in the task of predicting holocellulose content based on Raman features. Significantly, in HCP-Models built by CatBoost and XGBoost, the test R² was 0.93, and the RMSE were 0.28% and 0.27%, respectively. By comparing with related published literature (Gao, Shu, et al., 2022), the result could be the heretofore best precision of predictive model of holocellulose based on
![](img/e15c3a13b491ae6ef05b67702b1cf3da_5_0.png)

Fig. 4. The optimum hyper-parameters tuned by GridSearchCV.

**Table 2**
The statistical results of the nine models in training set.

| Modeling algorithms | R² | RMSE(%) | NRMSE | MAE(%) | MAPE(%) |
|---|---|---|---|---|---|
| RR | 0.85 | 0.46 | 0.0057 | 0.39 | 0.48 |
| LR | 0.85 | 0.46 | 0.0057 | 0.39 | 0.48 |
| ENR | 0.85 | 0.46 | 0.0057 | 0.39 | 0.48 |
| SVR | 0.84 | 0.47 | 0.0057 | 0.39 | 0.48 |
| DT | 0.88 | 0.41 | 0.0050 | 0.29 | 0.36 |
| RF | 0.91 | 0.35 | 0.0043 | 0.28 | 0.34 |
| LightGBM | 0.98 | 0.17 | 0.0021 | 0.13 | 0.16 |
| CatBoost | 0.99 | 0.13 | 0.0016 | 0.10 | 0.13 |
| XGBoost | 0.97 | 0.20 | 0.0025 | 0.16 | 0.19 |

**Table 3**
The statistical results of the nine models in test set.

| Modeling algorithms | R² | RMSE(%) | NRMSE | MAE(%) | MAPE(%) |
|---|---|---|---|---|---|
| RR | 0.80 | 0.47 | 0.0058 | 0.42 | 0.51 |
| LR | 0.80 | 0.48 | 0.0058 | 0.42 | 0.52 |
| ENR | 0.80 | 0.47 | 0.0058 | 0.42 | 0.51 |
| SVR | 0.82 | 0.45 | 0.0055 | 0.40 | 0.49 |
| DT | 0.81 | 0.47 | 0.0057 | 0.34 | 0.42 |
| RF | 0.85 | 0.40 | 0.0049 | 0.31 | 0.38 |
| LightGBM | 0.90 | 0.33 | 0.0041 | 0.25 | 0.30 |
| CatBoost | 0.93 | 0.28 | 0.0035 | 0.20 | 0.24 |
| XGBoost | 0.93 | 0.27 | 0.0033 | 0.24 | 0.29 |

Raman spectroscopy so far for our knowledge. The predicted values vs. measured values from the advanced GBM models were plotted in Fig. 7. It is gratifying to find that almost all the predicted and measured values were centered around the y = x straight line, indicating the satisfactory predictive accuracy (Zhang et al., 2021).

After comparing the results of advanced GBM algorithms with those classical ML algorithms, it is obviously found that the HCP-Models built by the advanced GBM algorithms performed higher predictive accuracy than those built by the classical ones. RF model bagging many decision trees by using the bootstrapping method. Different with RF, advanced GBM using gradient boosting to create a model in a stepwise manner by optimizing an objective function, and the residual of each tree constructed was smaller than that of the previous predictor, which bring a gradient descent of residuals of predictors in GBM (Dorogush et al., 2018; Hong, 2020; Ke et al., 2017). So HCP-Models built by advanced GBM algorithms may bring higher predictive accuracy than RF in the task of regression. Furthermore, CatBoost, and XGBoost models obtained higher predictive accuracy than LightGBM, with the higher test R², lower test RMSE, MAE and MAPE. But, marginally higher predictive accuracy of XGBoost than CatBoost and LightGBM was found in prediction of lignin content (Gao, Zhou, Liu, et al., 2022). It means the comparative result of advanced GBM algorithms is discrepant between the prediction of lignin and holocellulose.

XGBoost models consistently performed higher predictive performance and the lightGBM displayed relative poor result both in prediction of lignin and holocellulose content. In the XGBoost system, greedy algorithm for single machine setting and approximate algorithm with both local and global proposal methods were settled down in order to find the optimal split node. Simultaneously, in the LightGBM system, the histogram-based algorithm was applied to build feature histograms for
