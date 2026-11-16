

| Research Work | ML Algorithm | Area of Focus/Work Done |
| :--- | :--- | :--- |
| Multiple Disease Prediction Using Different Machine Learning Algorithms Comparatively [Godse et al. 2019] | • Naive Bayes Algorithm<br>• K-Nearest Algorithm<br>• Decision Tree Algorithm<br>• Random Forest Algorithm<br>• SVM | • High accuracy achieved using weighted KNN<br>• Proposed system aimed at bridging the gap between doctors and patients<br>• Support prediction for multiple sickness prediction<br>• Builds doctor's recommendation system<br>• Web/android application deployed for user |
| A ML Model for Early Prediction of Multiple Diseases to Cure Lives [Kumar et al. 2021] | • Decision Tree<br>• Random Forest<br>• Naïve Bayes<br>• KNN algorithms | • Model build predicts the disease in compliance with symptoms entered by patients<br>• GUI based interaction system with users |

## 2 PROPOSED WORK

Methodology used in the paper involves several steps to predict diseases from symptoms using machine learning algorithms. The dataset contains features and corresponding disease labels. The aim is to predict diseases from symptoms using machine learning algorithms applied on the dataset based on two major specifications of binary classification, one on the basis of True Positives [TP] and the other False Negatives [FN].

### 2.1 Methodology

Methodology used in this paper is based on decision tree, random classifier and gradient boosting algorithm followed by several steps including data pre-processing, exploratory data analysis, model selection and evaluation, cross-validation, and model testing. The decision tree algorithm shown in Algorithm-1, correctly classify the dataset discussed in Table 2.

```
Algorithm 1:Decision-Tree with TP-FN
INPUT: Datasets including features, F {itching, skin-rash, nodal-eruption,
continuous_sneezing, ... , yellow_crust_ooze}
OUTPUT: Chosen Decision Tree D_TP-FN
if F is null then return (failure) end if
for all i = 1 to n do
set Fm = List of features (Fi ) in
DFS order set Fbm = { } , //
Selected Nodes
call update (F, Fm) set Fi = Fbm
end for choosing the tree procedure
for all i = 1 to n do
set D_Fm= ∑n D_Fm // compute the average distance to select the node.
Distance
Fm = argmin,D_Fm // choose the representative decision tree model D_TP-FN
Return Fm End Procedure
```

### Table 2. Classification report for selected features for the models

| Class | Decision Tree Precision | Decision Tree Recall | Decision Tree F1-Score | Random Forest Classifier Precision | Random Forest Classifier Recall | Random Forest Classifier F1-Score | Gradient Boosting Precision | Gradient Boosting Recall | Gradient Boosting F1-Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Paroxysmal Positional Vertigo | 1 | 0.95 | 0.97 | 1 | 0.89 | 0.94 | 1 | 0.95 | 0.97 |
| AIDS | 1 | 0.93 | 0.96 | 1 | 1 | 1 | 1 | 0.83 | 0.91 |
| Arthritis | 1 | 0.9 | 0.95 | 1 | 1 | 1 | 1 | 0.9 | 0.95 |
| Diabetes | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| Tuberculosis | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| hepatitis A | 1 | 0.02 | 0.04 | 0 | 0 | 0 | 1 | 1 | 1 |

From the Algorithm-1 first we choose the feature from the given dataset defined as ‘F’ and name that as ‘Fm’, which is a member based on DFS algorithm. If the selected feature is a member of the selected decision group, then make a separate function called ‘Fbm.’ Set ‘Fi’ to select the next feature from the given dataset. Finally compute the average distance of selected feature from the decision tree nodes and return the Fm. Furthermore, the number of unique diseases and their occurrences are calculated by using the below equation:

```
\( F_E = - \sum_{i=1}^{n} P_i * log P_i \) (1)
```

And the Selection of FBM is calculated by using the below equation:

```
\( F_{BM} = 1 - \sum_{i=1}^{n} P_i^2 \) (2)
```

Furthermore, for a better understanding of the data, Figure 2 shows the framework with a detailed step involved.

![](img/9eefc6d2972274efeb1680c6a31895e5_212_0.png)

### Figure 2. Proposed framework for multi-disease prediction.

In the above Figure 2, the first step is dataset acquisition, then selection of appropriate data features containing comprehensive symptom-based disease information is done. While doing this task the major considerations taken into the accounts are:

- Dataset readily available and accessible from reputable sources.
- Datasets include symptom information associated with various diseases.
- Dataset is sufficiently large having a sample size of 4920 samples and 133 characteristics to provide enough instances for each disease class.

### 2.2 Dataset description

Dataset¹ used has 4920 samples and 133 characteristics, including a wide spectrum of medical data involving 41 different classifications of diseases. Each sample is distinguished by 133 traits, making them a valuable source of data for disease prediction.

### 2.3 Data pre-processing

For data pre-processing techniques, missing data handling (imputation, removal, etc.), outlier detection & treatment, feature scaling & normalization and feature selection & dimensionality reduction is followed.

### 2.4 Training and model selection

For assessing the model performance, data is split into training and validation sets using the train test split () function. Models are trained using training set and evaluated on the validation set using metrics such as accuracy, confusion matrix, and classification report shown in Table 2.

## 3 RESULTS AND DISCUSSION

The paper conducts a thorough comparative analysis of three potential classifiers, including the decision tree, random forest classifier, and gradient boosting for the binary classification of True Positive (TP) and False Negative (FN) scenarios. Classifiers are evaluated based on their performance and outcome. Performance of the classifiers is thoroughly examined which contains confusion matrices, training and validation accuracy, and classification reports including precision, recall, F1-score, and support values for class of disease.

### 3.1 Performance analysis of decision tree model

Decision tree model performs admirably when it comes to disease prediction. The model adequately generalizes to new data without exhibiting over-fitting, as seen by the fact that both the training and validation accuracies are 78.57%. Notably, classes like “Diabetes” and “Tuberculosis” excel, scoring perfectly on F1-score tests for precision, memory, and performance. On the other hand, categories like “AIDS” and “Paroxysmal Positional Vertigo” also perform well, with good accuracy and recall. Some classifications like “hepatitis A” however display difficulties with a very low recall, indicating that the model may have trouble detecting these cases. Total weighted average F1-score for all classes comes in at about 0.77 and offers a thorough evaluation of the model’s performance. The values for the classification report that includes accuracy, recall, and F1-score for a few classes are listed in Table 1.

### 3.2 Performance analysis of random forest classifier

Random forest classifier performs well in the classification of diseases when the parameter values (criterion=’entropy’, max depth=10, and max features=’sqrt’) are implemented. Training and validation accuracy are both commendable and about 83.37%, showing that the model generalizes well with little or no over-fitting to the training set. When analyzing certain classes, the model excels at diagnosing diseases like “AIDS”, “Arthritis”, “Diabetes” and “Tuberculosis”, obtaining the highest possible accuracy, recall, and F1-score values. This displays the model’s incredible accuracy in identifying certain diseases. Model retains great precision and an adequate recall for classes like “Paroxysmal Positional Vertigo”, indicating its usefulness in a variety of disease circumstances. Weighted average F1-score taking into account the total model performance is almost 0.82 as shown in Figure 3. Random Forest model shows potential in disease prediction in terms of implications and suggestions, especially for diseases with high performance metrics.

### 3.3 Performance analysis of gradient boosting classifier

The Gradient Boosting Classifier, performs well in the classification of diseases when its parameters are set to (criterion='entropy', max depth=10, and max features='sqrt'). During training, the model shows a constant decrease in training loss. This demonstrates that the model successfully picks up complicated data patterns without over-fitting. 95.38% accuracy for both training and validation shows that it can generalize effectively to newly acquired data. Model excels at detecting diseases like “Diabetes”, “Tuberculosis” and “Hepatitis A” obtaining near-perfect accuracy, recall, and F1-score values. Model retains excellent accuracy for some classifications such as “AIDS” but has a lower recall for some of the diseases. The F1-score is approximately 0.96% when the selected feature is based on performance of the entire model as shown in Figure 3.

### 3.4 Statistical analysis of selected models

The statistical test shows a significant improvement in Decision Tree, Random Forest and Gradient Boosting shown in Figure 4. From the Figure 4, it is clear that the Gradient Boosting approach is suitable for applications requiring high accuracy in disease categorization as seen by its better result. ANOVA and chi-square have been used for the evaluation of all three algorithms. Hence, the knowledge of the model’s performance by including feature significance analysis and domain-specific insights will be used in future work. Figure 3a below provides the performance analysis of the models depicting the higher and the low accuracy depending upon the algorithms on the FN and TP cases. The number of point fields in the statistics indicates that there are 9 data points or observations in our dataset. In the context of Regression Analysis, the degree of freedom is often referred to as the number of datapoints minus the number of estimated model parameters.

We have eight degrees of freedom in this situation. Residual sum of squares (RSS) calculates the difference between the sum of the squared values of observed and residual values from the regression model. RSS in this instance is 13921.33. For this paper, the Pearson’s Correlation Coefficient, commonly abbreviated as “r” is 0.70, indicating a moderately strong positive linear relationship between the variables. R-square measures the amount of variance seen in the dependable variable (C) that is defined by the independent variable in the model. Additionally, the adjusted R-squared value is a modified form of R-squared.

![](img/9eefc6d2972274efeb1680c6a31895e5_214_0.png)

