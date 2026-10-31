
## 3.2 Data Preprocessing

### 3.2.1 Data Scaling
The dataset displays a significant variance in the scales of different input attributes within the original database. The presence of significant differences in the scales of features might have a notable negative impact on the accuracy and performance of the model. Therefore, it is essential and non-negotiable to include the data scaling process as a crucial stage in the analysis. Data scaling is indispensable due to the magnitude differences observed in input features. By applying the Z-score technique for data scaling and effectively normalizing the range of the dataset across features, mitigating the impact of these magnitude disparities. This vital preprocessing step ensures that each feature contributes equitably to the model’s performance, ultimately enhancing its accuracy, robustness, and interpretability.

### 3.2.2 Outliers and Z-Score
Outliers can significantly affect values. Hence, datasets containing a significant number of outliers may likewise produce imprecise results. The Z-score approach was employed to eliminate outliers. The Z-score, or standard score, is a statistical technique used to detect outliers in a dataset by quantifying the extent to which each data point deviates from the mean in terms of standard deviations. The standardized measure quantifies the degree of extremity or uniqueness exhibited by a specific data point in relation to the overall distribution of the dataset. The Z-score can be calculated using Eq. 1.

Z = (X - μ) / σ
(1)

In the above equation, Z denotes the Z-score associated with the given data point. The variable X represents the numerical value of a certain data point that is being evaluated. The symbol μ represents the arithmetic mean, often known as the average, of the given dataset. The symbol σ represents the standard deviation of the dataset.

The Z-score quantifies how many standard deviations a data point is away from the mean. However, one of the limitations of the Z-score is that it may provide inaccurate results for smaller datasets. Nevertheless, the sample size is unlikely to pose a concern in our specific scenario, as a sample size exceeding 30 is generally considered adequate for ensuring precise Z-score computations [69]. Z-score threshold of 3 was used to identify outliers as Z-scores with an absolute value exceeding 3 are typically regarded as outliers [70].

After the removal of the outliers, the dataset was reduced to 43 data points for noncircular and 91 data points for circular specimens.

### 3.2.3 Hyperparameters
Hyperparameters play a crucial role in determining the effectiveness of ML algorithms, especially in the context of supervised learning. As stated by the study [71], the accurate determination of hyperparameter values has great importance due to its substantial impact on the model’s performance. The selection of suitable values for these hyperparameters can significantly enhance the performance of the model. Likewise, it has been emphasized that in the context of supervised learning, the attainment of optimal algorithmic performance is greatly contingent upon the appropriate selection and tuning of hyperparameters [72].

### 3.2.4 Grid Search
In this study, the grid search method was employed to determine the optimal configuration for a model for increasing the performance of ML models. The grid search method is a fundamental and influential methodology in the domain of ML, serving as a crucial tool for increasing the performance of models through hyperparameter modification [73]. By conducting a thorough investigation of various combinations of hyperparameters, grid search facilitates the determination of the optimal configuration for a model, hence exerting a substantial influence on the performance of ML models [74]. Furthermore, grid search is particularly useful in situations when the precise values of hyperparameters are unknown. It provides a systematic method for exploring different parameter configurations while employing cross-validation to determine the optimal set of hyperparameters [75].

When compared to alternative hyperparameter tuning methods such as Random Search, Bayesian Optimization, Gradient-based optimization, and Evolutionary algorithms, grid search excels in its comprehensive examination of all possible combinations [76]. This comprehensive approach has the potential to achieve higher accuracy, provided that time constraints are not the primary consideration. Despite the possible computing requirements, grid search is considered a powerful method for accomplishing model optimization in machine learning applications [77].

### 3.2.5 SHAP Feature Selection
Feature selection is a crucial step in machine learning model development. Feature selection aids in the reduction of the dimension of the feature space [78–80]. This is advantageous because high-dimensional data can result in a model that performs well on training data but unfavorably on unobserved data, a condition known as overfitting [80]. By minimizing the number of features, the computational complexity of the model is decreased, thereby allowing the learning algorithm to run faster. Features that are irrelevant or only partially relevant can have a negative effect on a model's performance [79]. Feature selection improves the predictive precision of a classification algorithm. When the dimensionality of the feature space is decreased, the outcomes of the learning process are easier to interpret [80].

of features on predictions for each data point. It encapsulates intricate feature interactions and dependencies, transcending the limitations of traditional correlation-based techniques [85].

Figure 3 shows that feature εco and volume had the least influence in circular specimens, similarly the feature εco and area as well as volume had the least influence in noncircular specimens. So, these features were dropped. The statistical summaries of the data after the preprocessing for the circular and noncircular specimens are shown in Tables 2 and 3, respectively.

The SHAP methodology, as described by Lundberg and Lee [81], is an interpretable technique that draws upon game theory and the concept of Shapley value [82]. The Tree-SHAP method was introduced as a means of elucidating the inner workings of tree-based machine learning models, namely those employing gradient-boosting methods [83]. The Shapley value φj(i) denotes the incremental contribution of individual input features toward the projected value. The establishment of the weighted linear regression model is as follows:

y'i = ybase + Σ_{j=1}^M φ_j^{(i)}  (2)

## 4 ML Models and Performance Evaluation

### 4.1 ML Models

### 4.1.1 Extreme Gradient Boosting (XGBoost)
The term "ybase" in the context of the model refers to the baseline, which often corresponds to the average values of all anticipated values. The calculation of the global significance of each input characteristic may be determined using the following method [84]:

XGBoost was first introduced by Chen and Guestrin [86] in 2016. Since its introduction, it has been widely acknowledged as a highly effective estimator, demonstrating outstanding performance in both classification and regression tasks.

I_j = 1/n Σ_{i=1}^n |φ_j^{(i)}|  (3)

XGBoost is a powerful gradient boosting library that improves the gradient-boosting decision method, offering efficiency, versatility, and scalability [87–89]. This approach improves upon conventional gradient boosting algorithms by integrating multiple enhancements and regularization techniques to mitigate the issue of overfitting. The XGBoost loss function incorporates a loss term, Ψ(*), to quantify the discrepancy between predicted and actual labels, and a regularization term, Ω(f), that discourages complex models by penalizing the number of leaves and the output of each leaf node. The regularization term Ω(f) is defined in Eq. 5:

Additionally, SHAP feature dependency serves as an appropriate alternate to partial dependence and overall local impacts. This approach encompasses the following key aspects [84]:

Ω(f) = γ T + 1/2 λ ||ω||^2  (5)

{ (x_j^{(i)}, φ_j^{(i)}) }_{i=1}^n  (4)

where γ, T, λ and ||ω||^2 represent the complexity control of leaves, the number of leaves, the penalty parameter, and the output of each leaf node, respectively. XGBoost differs from traditional gradient boosting by utilizing a second-order Taylor series to approximate the objective function. This approach transforms the objective function into a quadratic minimization problem.

In this study, SHAP was used for both feature selection as well as feature dependency analysis. In the realm of feature selection, conventional methods typically involve a comparison between feature sets and target variables, followed by the computation of correlation coefficients, such as the Pearson correlation coefficient. These coefficients are employed to gauge the significance of specific feature categories. In stark contrast, the SHAP method takes a distinct approach to feature importance assessment. It delineates the significance of various feature classes by averaging the absolute magnitudes of individual feature importance across each sample. This alternative methodology provides a comprehensive perspective on feature importance, emphasizing the collective impact

The objective function is represented by Eq. 6 where gi and hi denote the first and second order gradient statistics on the loss function for the i-th sample.

L_K ≃ Σ_{i=1}^n [ g_i f_k(x_i) + 1/2 h_i f_k^2(x_i) ] + Ω(f_k)  (6)
