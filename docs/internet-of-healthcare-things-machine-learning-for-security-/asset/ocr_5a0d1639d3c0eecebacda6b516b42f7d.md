# Regression

# Classification

| Regression | Y=f(x)+e | Classification |
|---|---|---|n| Target Y is continuous | | Target Y is categorical |
| Popular Methods | | Popular methods |
| Linear Regression | | Logistic Regression |
| Generalized Additive models | | SVM, Decision Tree, Random Forest |

Figure 10.2 Predictive models.

The key cohort study is to define the right inclusion and exclusion criteria to figure out what patient to include. Prospective study versus retrospective and Cohort study versus case-control. Depending upon the combinations, there are four different options: Prospective-cohort, Prospective-case-control, Retrospective-cohort, and Retrospective-case-control as shown in Figure 10.2.

# 10.3.1 Cohort Study

The group of patients with the risk of being exposed.

+   1. Target: Heart failure Readmission.
2. Cohort: All the patients discharged from the hospital
3. Key: Define the right inclusion/exclusion criteria.

The first 13 rows of Table 10.1 are dependent variables and row 14 is an independent variable [16–20].nThe total number of observations considered are 303 in the dataset, 25% was split for validation. Hence the training and testing samples used are mentioned below:

+   * Training samples Used: 227 Observations
* Testing Samples Used: 176 Observations

# 10.4 Training Models

# 10.4.1 Artificial Neural Network (ANN)

The training and testing samples in ANN with 500 Epochs are considered for training. The ANN details are mentioned in Table 10.2. The activation functions considered are rectified linear activation function (ReLU) and Sigmoid [21–25].