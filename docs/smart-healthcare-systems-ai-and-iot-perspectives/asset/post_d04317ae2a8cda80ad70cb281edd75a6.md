
# Section 15.6–15.8: A thorough summary of the main findings and conclusions wraps up the study. It also highlights the beneficial effects of this research on healthcare support systems and offers suggestions for future research endeavors, outlining possible directions for more study.

## 15.2 RELATED WORK

The health of people depends greatly on medical research. Even tiny errors could lead to gravely consequences or even death [15, 16]. The most crucial component and major barrier is the accurate diagnosis and classification of disorders (such as heart disease or other conditions). Many have studied how to use machine learning (ML) models as diagnostic aids in the identification of cardiac disease. Preprocessing techniques combined with the Random Forest (RF) classification algorithm were used by Gupta et al. [17], and they managed an excellent score of 96.9 percent on the Cleveland dataset. This contribution emphasizes the importance of robust prediction in models. Guan et al. [18] constructed a system entirely based on SVM that could accurately identify cardiac disease. By this alternative approach, the 76.5 percent accuracy was attained. This study examines different Support Vector Machine (SVM) algorithms, stressing that disease classification involves a subtle understanding of model selection. Divedwi [19], used LR in their classification model on the Cleveland dataset to achieve an accuracy of 85 percent. This reflects the many techniques of machine learning in diagnosing cardiac disease. Classification system Kumar and Inambari [20] used Particle Swarm Optimization (PSO) as a novel approach to detect cardiac heart disease. Rabbi et al. [21] obtained several ranges of accuracy by applying different learning learning and optimizing features. The highest accuracy of 91.94 percent was reached by the backpropagation method. SVM, KNN, and ANN were compared in their to evaluate the performance. As it turns out, SVM performed better than the other two methods with its accuracy of 85 percent. This points to the need for care in evaluating different machine learning models when applied in healthcare. Amin et al. [22] achieved an even more impressive accuracy of 87.4 percent by employing a new hybrid technique that calls Naive Bayes and Bayes. By bringing attention to outstanding features, the process of improving diagnostic accuracy continues.

By using a variety of feature selection methods and classification strategies, Shilaskar and Ghatol [23] showed that SVM, when combined with optimization approaches, greatly increased accuracy to over 85 percent. With an astounding 92 percent accuracy, Ali et al. [24] presented a SVM-based authority system for heart failure analysis. Their two-step model, which combines prediction with feature reduction, demonstrates the power of advanced ML architectures. Using the Cleveland and Statlog datasets, Fitriyani et al. [25] investigated the use of XGBoost and DBSCAN in a classification model, obtaining excellent accuracy of 98 percent and 95 percent, respectively. Their research emphasizes that dataset selection affects model performance.

## Hybrid Machine Learning to Predict Heart Diseases

Using majority voting methodologies, Bashir et al. [26] created a system that uses SVM, Naive Bayes, and DT with Gini Index (DT-GI) with the intention of predicting cardiac illness and reached a remarkable accuracy of 82%. Disease prediction models gain subtlety from the focus on ensemble approaches and preprocessing processes. Superior data analysis methods were shown by Islam et al. [27] in different research, with logistic regression offering the best accuracy at 86.25 percent. This clarifies the continuous investigation of several machine learning techniques in the analysis of healthcare data. Together, these add to the body of research on machine learning applications in medicine by emphasizing the significance of feature optimization, model selection, and the ever-ending pursuit of increased diagnostic accuracy [28].

## 15.3 MACHINE LEARNING PROCEDURES

### 15.3.1 LOGISTIC REGRESSION (LR)

With insight and predictive powers, LR is a crucial tool in the diagnosis and prognosis of illness [29]. LR functions on valued-input features as a categorical model, making it easier to retrieve important statistical data from the model. LR is used in the context of cardiac disease to forecast a person's chance of developing the illness. Logistic regression involves a binary dependent variable, which represents data as code to indicate the occurrence of an event, such as success, and zero to indicate its absence, such as failure. The main goal of logistic regression analysis is to estimate the logarithmic probability of the occurrence of an event.

From a mathematical perspective, the multiple linear regression functions (specified follows) are estimated in the context of the LR model.

```
Log odds = \beta_0 + \beta_1X_1 + \beta_2X_2
```

In this case, n is the number of features, and $\beta_0, \beta_1, \dots, \beta_n$ are the coefficients corresponding to $X_0, X_1, \dots, X_n$.

### 15.3.2 SUPPORT VECTOR MACHINE (SVM)

The main goal of supervised learning approach SVM is to minimize generalization errors dividing data into classes by drawing a hyperplane. Interestingly, SVM performs well in high-dimensional domains, demonstrating its resilience to larger samples. A training vector in SVM is defined mathematically as:

```
X_i \in Rⁿ, for i = 1,2,...,n
```

In this case, X stands for a training observation, and R^n denotes the predictor space and real-valued feature space.

### 15.3.3 Decision Tree (DT)

Decision Trees are a well-known and comprehensible machine learning technology that provides a clear and hierarchical approach for cardiovascular parameters in the field of heart disease prediction [31, 32]. Decision trees are mathematical constructs that relate observations (X) about an object to inferences (Y) about the item's goal value.

Algorithm for DT Using Heart Disease Data:
- Heart Disease Data, a dataset with binary outcomes (Y) and characteristics (X), is the input.
- Create Decision Tree (decision_tree = DecisionTreeClassifier())
- Fit the model (using decision_tree.fit(Data on Heart Disease))
- Forecast Decision Tree (forecast = predict(NewObservation))

Because decision trees provide healthcare professionals with a clear structure by input data, making it easier for them to understand the predictions made by the model, Decision Trees can help physicians identify important predictors of heart disease by drawing out decision routes relying on variables such as age, blood pressure, cholesterol, and lifestyle choices. This is because cardiac illnesses are very complicated, and factors such as lifestyle choices, family history, and clinical markers play key roles. The adaptability of decision trees become extremely important. For a variety of patient data, decision trees are very flexible: They can handle both numerical and categorical information. To build a tree-like structure, the decision tree breaks down the analyzed data into input attributes [34]. The dataset is divided into smaller groups; decisions are made at each internal node based on features. The process continues until a requirement is satisfied, producing leaf nodes that indicate the final categorization. They could also help medical practitioners to decide which is the most effective form of therapy by highlighting essential characteristics and ranking their significance in predicting cardiac disease. The problem is overfitting cases they to record noise of true.
