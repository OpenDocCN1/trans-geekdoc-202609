| Research Work | ML Algorithm | Area of Focus/Work Done |
| :--- | :--- | :--- |
| Multiple Disease Prediction Using Different Machine Learning Algorithms Comparatively [Godse et al. 2019] | • Naive Bayes Algorithm<br>• K-Nearest Algorithm<br>• Decision Tree Algorithm<br>• Random Forest Algorithm<br>• SVM | • High accuracy achieved using weighted KNN<br>• Proposed system aimed at bridging the gap between doctors and patients<br>• Support prediction for multiple sickness prediction<br>• Builds doctor's recommendation system<br>• Web/android application deployed for user |
| A ML Model for Early Prediction of Multiple Diseases to Cure Lives [Kumar et al. 2021] | • Decision Tree<br>• Random Forest<br>• Naïve Bayes<br>• KNN algorithms | • Model build predicts the disease in compliance with symptoms entered by patients<br>• GUI based interaction system with users |

# 2 PROPOSED WORK

Methodology used in the paper involves several steps to predict diseases from symptoms using machine learning algorithms. The dataset contains features and corresponding disease labels. The aim is to predict diseases from symptoms using machine learning algorithms applied on the dataset based on two major specifications of binary classification, one on the basis of True Positives [TP] and the other False Negatives [FN].

# 2.1 Methodology

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