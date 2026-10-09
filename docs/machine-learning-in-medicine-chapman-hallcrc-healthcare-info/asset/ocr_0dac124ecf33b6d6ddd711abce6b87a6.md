Further study tried to improve the classification of NAFLD using previously described variables and some others (i.e. diastolic blood pressure and uric acid) [18], but with a dimensionality reduction with a lasso regression combined with a multivariable logistic regression. In this case, the model was structured with eight variables (including gender, age, total cholesterol, BMI, waistline, diastolic blood pressure, serum uric acid, and course of disease on high-density lipoprotein-cholesterol) and had an accuracy in the training and validation set of 0.848 and 0.809 respectively.

ML algorithms also have been used in the edge of the knowledge of metabolic disease, which includes lipidomics and glycomics. These "omics", includes a larger list of variables and could explain more about the phenomenon behind the disease. Perkakis (2019) evaluated 49 healthy subjects and 31 patients with biopsy-proven NAFLD. The author previously measured some hormone variables also: adiponectin, leptin, activin A and follistatin. The "omics" variables were measured by mass spectrometry and liquid chromatography-mass spectrometry. The ML algorithms included in the analysis were SVM, k nearest neighbor, and random forest. In this case, the SVM model with a non-linear kernel had the highest accuracy (with lipidomics variables and with other variables) [19]. However, the uniqueness of the DT algorithm is that it often imitates the human-level thinking, which makes it easier to understand the data and makes some reasonable interpretations. Unlike black-box algorithms such as neural network and SVM, the logic behind the DT algorithm is comprehensible and easy to explicate [20].

# 11.3 METHODOLOGY

DT is one of the most popular ML algorithms used for both classification and regression problems [20]. A DT exploits a tree-like model where each node represents a feature (attribute), each link (branch) exhibits a decision (rule) and each leaf embodies an outcome (categorical or continuous value). The algorithm of the proposed DT-based model aiming to diagnose LVH and NAFLD is mentioned in Algorithm 11.1.

Algorithm 11.1: Decision Tree Algorithm

```
**Input:** Set of possible instances X and label Y
**Output:** A Decision Tree f : X -> Y
**function** DECISION_TREE(X, Y)
    1. Assign all training instances to the root of the tree. Set current node to root node.
```