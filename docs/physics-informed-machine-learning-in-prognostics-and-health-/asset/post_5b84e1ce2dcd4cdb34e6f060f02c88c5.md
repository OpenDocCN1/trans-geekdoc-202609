
![](img/3ec5662c0c5150f5b95af65046cb9cd4_6_0.png)

Fig. 8. Overview on applications of PIML in PHM.

research focuses on solving the PHM tasks in the presence of sparse (26%) or noisy data (38%). This remark highlights the relevance of the PIML over the purely data-driven models when it comes to such data quality issues. Table 2 lists the metrics used in the literature to train and evaluate the performance of PIML methods. It also shows the specific PHM tasks to which these metrics correspond, as well as the types of monitoring measurements.

From Table 2, we can derive the following remarks:

- 1. This table summarizes the training and testing metrics used in various PHM tasks for evaluating PIML models. Metrics such as Mean Square Error (MSE), Mean Absolute Error (MAE), Precision, Recall, F1-score, and others are employed to assess the performance of these models in condition monitoring, fault diagnostics, Remaining Useful Life (RUL) prediction, and degradation prediction tasks. MSE, MAE and RMSE are the most commonly used training metrics in the collected literature, accounting for 35.7%, 20.0% and 10% respectively.
- 2. In paper [76], the metric (binary cross-entropy), commonly employed for classification, is used for degradation prediction. This is because the prediction of degradation states is transformed into a classification of degradation levels.
- 3. One important aspect worth discussing is the embedding knowledge related to PIML models. In most studies, the choice of which type of knowledge to embed tends to be more based on subjective intentions. In practice, the knowledge embedded is strongly related to the monitoring signals used, e.g., the relationship between strain signals and deformation and damage growth, the relationship between temperature and fatigue, the relationship between vibration and modalities, so collecting knowledge in this area from the available monitoring signals for use in informed machine learning would be a good place to start.
- 4. Table 2 also outlines the specific information about the corresponding monitoring signals utilized in each task, such as displacement, voltage, vibration, temperature, stress, current, and more. The vast majority of studies (94.3%) focuses on processing time-series or one-dimensional monitoring signals, with only 5.7% of studies involving two-dimensional image signals.
- 5. The applications of PIML are mainly in the field of structures. The majority of processed signals in these applications are derived from vibration (25.7%) and stress (27.1%). In addition, certain non-destructive detection measurement methods, such as guided wave or acoustic emissions, are also utilized. Upon examining Table 2, one can see that a wide array of metrics and monitoring signals are employed across various PIML studies. This diversity reflects the intricate and multidimensional nature of PHM tasks, highlighting the necessity for tailored approaches that align with specific applications and system characteristics. Gaining an

![](img/3ec5662c0c5150f5b95af65046cb9cd4_6_1.png)

Fig. 9. Statistical results of relevant research on data quality problem.

## Table 2 Summary of the training, testing metrics and monitoring signals for PIML according to PHM tasks.

| Ref. | Train metric | Test metric | PHM tasks | Signals |
| :--- | :--- | :--- | :--- | :--- |
| [161] | MSE | MSE | Condition monitoring | Displacement and voltage |
| [124,131] | MSE | MSE | Condition monitoring | Vibration |
| [165] | MSE | MSE | Condition monitoring | Currents, voltages and time measurements |
| [106] | MAE, MSE, RMSE | Precision, recall, F1-score | Condition monitoring & Fault diagnostic | Vibration, acoustic, image, temperature |
| [53,74,151] | MSE | MSE | Condition monitoring & Fault diagnostic | Stress |
| [126,132,166] | MAE, Cross-entropy loss | Precision, recall, f-k value, accuracy, macro F1, and G-mean | Condition monitoring & Fault diagnostic | Power, voltages, current |
| [13] | Customized design loss | RMSE | Condition monitoring & Fault diagnostic | Temperature, pressure, vibration, and air flow |
| [167,168] | Cross-entropy | Relative percentage error | Condition monitoring & Fault diagnostic | Vibration |
| [169] | MAE | Confusion matrix | Fault diagnostic | Temperature |
| [170] | Maximum cross entropy | MAE | Fault diagnostic | Vibration |
| [171,172] | Binary cross-entropy | Categorical cross-entropy | Fault diagnostic | Vibration |
| [173] | MAE, similarity distance | Precision, recall, f-measure, confusion matrix | Fault diagnostic | Temperature, pressure, and fuel coefficient |
| [14] | Customized design metrics | Test false positive rate, MAE. | Fault diagnostic | Vibration, acoustic signal, and temperature |
| [6] | MAE | Confusion matrix, recall, precision | Fault diagnostic | Vibration |
| [50] | MSE | MSE, Pearson correlation coefficients test | Fault diagnostic | Vibration |
| [112,146] | Cross-entropy loss | Confusion matrix | Fault diagnostic | Vibration, strain, torque, acoustic emission |
| [130] | MSE | MAE | Fault diagnostic | Magnetic flux leakage image, stress |
| [117] | Customized loss | Confusion matrix | Fault diagnostic | Far-field loads, stress ratio and a corrosivity index |
| [129,133] | MSE | MAE | Fault diagnostic | Stress |
| [81] | MSE, Kernel norm | Relative percentage error | Fault diagnostic | Ultrasonic signal |
| [27] | MSE | MSE | Fault diagnostic | Stress, temperature |
| [143] | Cross-entropy loss | MAE | Fault diagnostic | Vibration |
| [150] | Customized loss | Customized metric | Fault diagnostic | Wave data |
| [174] | Cross-entropy | Confusion matrix | Fault diagnostic | Stress |
| [175] | Softmax loss test | Relative percentage error, | Fault diagnostic | Guided wave signal |
| [37] | MSE | MSE, Pearson correlation coefficients test | Fault diagnostic | Acoustic signal |
| [84] | Cross-entropy, MSE, Softmax loss | MAE | Fault diagnostic | Mode shapes signal |
| [154] | Customized loss | F1 score | Fault diagnostic | Proposed access location, error locations |
| [176] | MAE | Relative percentage rate | Fault diagnostic | Stress |
| [70] | Cross-entropy loss function | MAE | Fault diagnostic & RUL prediction | Phase field images |
| [36] | MAE | α_λ distribution accuracy | RUL prediction | Vibration |
| [51] | MAE | One σ tolerance interval | RUL prediction | Voltage and current |
| [16,54,155,177,178] | RMSE | RMSE | RUL prediction | Temperature, pressure, flow |
| [55,110] | Relative error rate | Relative error rate | RUL prediction | Stress or strain |
| [113,179] | MSE | RMSE | RUL prediction | Current, voltage, temperature |
| [180] | F.norm | RMSE | RUL prediction | Capacities and voltage |
| [123] | MSE | RMSE | RUL prediction | Vibration |
| [181] | MSE | MSE, MAE, R2 | RUL prediction | Vibration |
| [182] | Similarity distance | Prognostic horizon, α_λ distribution, CRA, convergence, normalized RMSE | RUL prediction & Degradation prediction | Stress, crack length, pressure |
| [78,123] | MAE, MSE | MAE, RMSE | Degradation prediction | Forces, vibrations and acoustic signal |
| [183] | RMSE | MAE | Degradation prediction | Vibration |
| [184] | MSE | RMSE | Degradation prediction | Stress |
| [77,114] | MAE | MSE, test point-wise errors, relative error | Degradation prediction | Stress |
| [76] | Binary cross-entropy | F1-score | Degradation prediction | Cutting speed, temperature |
| [115,118,185] | MSE | MAPE | Degradation prediction | Stress or image |
| [116] | MSE | RMSE | Degradation prediction | Stress, viscosity, wind speed, and temperature |
| [43] | NMSE | NMAE | Degradation prediction | Spindle motor current |
| [186] | MSE | MSE | Degradation prediction | Far-field stress |
| [187] | Discretization error | MAE | Degradation prediction | Stress |
| [188] | RMSE | MRSE | Degradation prediction | Rise time, displacement |
| [93] | Negative log likelihood | Sensitivity analysis, MAE, and absolute error variance | Degradation prediction | Stress, temperature |

understanding of the different combinations of physics knowledge, metrics, and signals utilized can serve as a valuable guide for researchers and practitioners when selecting appropriate evaluation measures and sensor inputs for their respective PHM applications.

## 3. Synthetic review of PIML studies in PHM

The physics involved in research subjects in the field of PHM are often diverse and can be expressed in different forms such as algebraic equations, differential equations, simulation results, logic rules, and probabilistic relations along with limited monitoring

| Authors | Topics of interest | Main Challenges | Taxonomy |
| :--- | :--- | :--- | :--- |
| Rai, Rahul, and Chandan K. Sahu. [72] | • Cyber-physical system's dynamic behavior modeling | • Discretization approximation of the continuous system behavior in a chaotic environment.<br>• Scenario-oriented PIML hybrid framework.<br>• Efficient extraction of causal and model parameter relationships in big data. | • Physics-based data pre-processing.<br>• Physics-guided ML algorithm structure design.<br>• Physics-based ML regularization item. |
| Willard, J., Jia, X., Xu, S., Steinbach, M. [32] | • Engineering and environmental systems modeling.<br>• Model solving methods. | • Embedding incomplete physics knowledge.<br>• Keeping physical consistency in data mining.<br>• Sparse data and uncertainty quantitative information.<br>• Designing prior informed deep learning framework.<br>• ML training data scarcity.<br>• Keeping physical consistency.<br>• ML black-box nature explanation.<br>• Training data scarcity.<br>• Keeping physical consistency. | • Physics-based regularization item in ML algorithm.<br>• Physics-guided ML initialization.<br>• Physics-informed ML algorithm architecture design.<br>• Physics-informed Feature engineering.<br>• Physics-informed NN structure.<br>• Physics-informed loss function.<br>• Parallel/Series physics-ML combination structure.<br>• Physics-based regularization item in ML objective function.<br>• Physics-based data pre-processing.<br>• Physics-guided ML algorithm architecture design.<br>• Physics-based regularization item in ML algorithm. |
| Kim, S. W., Kim, I., Lee, J., Lee, S. [189] | • Physics-informed deep learning in dynamical systems behavior modeling.<br>• PHM is mentioned | | |
| Jan Hagendorfer, Elias. [190] | Condition monitoring | | |
| Finegan, D. P., Zhu, J., Feng, et al. [71] | Battery cell state prediction. | Keeping physical consistency. | • Physics-based data pre-processing.<br>• Physics-guided ML algorithm architecture design.<br>• Physics-based regularization item in ML algorithm. |
| Jianjing Zhang, Robert X. Gao. [191] | • Data curation and model interpretation for smart manufacturing.<br>• PHM is mentioned. | • Non-interpretable prediction logic in deep learning.<br>• Error or imbalance training data.<br>• Data and data labels scarcity. | • Physical model bias compensation and unknown parameters estimation via deep learning.<br>• Involving Physics-constraints into deep learning training.<br>• Physics-informed architecture<br>• Physics-informed loss function |
| Xu, Yanwen and Kohtz, et al. [29] | • Reliability analysis and risk assessment.<br>• Uncertainty quantification.<br>• PHM is mentioned. | • Scenario-oriented PIML hybrid framework and its computational efficiency.<br>• Incompleteness of physics knowledge and limited representatives of the training dataset.<br>• The need for accurate and reliable data to create an accurate digital twin model.<br>• Integrating data from different sources and formats.<br>• Selecting the appropriate modeling technique for a given physical system.<br>• Scaling up the digital twin model to larger and more complex systems.<br>• Validating the digital twin model against the physical system it represents. | • Modifying the loss function.<br>• Generating synthetic data.<br>• Pre-training on physics-based data.<br>• Correcting models with unmodeled physics.<br>• Correcting models with prediction residuals.<br>• Learning to predict inputs. |
| Thelen Adam, Zhang Xiaoge and Fink Olga, et al., [192,193] | • Physical system modeling | | |
