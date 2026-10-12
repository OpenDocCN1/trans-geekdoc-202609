
*   Use bootstrap samples when building trees: **Checked**
*   Use out-of-bag samples to estimate the generalization accuracy: **Checked**
*   Use extremely randomized trees: **Checked**
*   Enable parallel model building: **Checked**
*   Replicate results: **Checked**
*   Hyper-parameter optimization:
    *   Target: **0.05**
    *   Max iterations: **10,000**
    *   Max Evaluations: **500**

7.  Compare the model fit metrics between these four models using the testing results.
8.  Select the champion model and justify this selection with the necessary evidence.
9.  Present the results of the champion model.
10.  Evaluate the reliability and validity of the champion model.
11.  Present the variable importance chart and interpret the results.

### Exercise 2: Random Forest Models for the Passengers dataset

1.  Open the **passengers** dataset in SPSS Modeler.
2.  Sample 20% of the full data. Set **return** (decision to return to the airline) as the target variable and change its role to binary. See the variable names and descriptions in Appendix B.
3.  Partition the data using a split ratio of 60–40 (train: 60%; test: 20%; validation: 20%)
4.  Perform data modification as follows:
    *   Replace zero values for Likert-scale variables with missing values.
    *   Impute missing values.
5.  Configure five random forest models for this dataset as follows.

#### Random Forest 1

*   Basic Settings:
    *   Number of trees: **10**
    *   Maximum tree depth: **10**
    *   Minimum leaf node size: **1**
    *   Number of features to use for splitting: **auto**
*   Advanced Settings:
    *   Use bootstrap samples when building trees: **Checked**
    *   Use out-of-bag samples to estimate the generalization accuracy: **Checked**
    *   Hyper-parameter optimization: **Unchecked**

#### Random Forest 2

*   Basic Settings:
    *   Number of trees: **30**
    *   Maximum tree depth: **30**
    *   Minimum leaf node size: **1**
    *   Number of features to use for splitting: **auto**
*   Advanced Settings:
    *   Use bootstrap samples when building trees: **Checked**
    *   Use out-of-bag samples to estimate the generalization accuracy: **Checked**
    *   Enable parallel model building: **Checked**
    *   Hyper-parameter optimization:
        *   Target: **0.01**
        *   Max iterations: **1000**
        *   Max evaluations: **300**

#### Random Forest 3

*   Basic Settings:
    *   Number of trees: **100**
    *   Maximum tree depth: **50**
    *   Minimum leaf node size: **1**
    *   Number of features to use for splitting: **auto**
*   Advanced Settings:
    *   Use bootstrap samples when building trees: **Checked**
    *   Use out-of-bag samples to estimate the generalization accuracy: **Checked**
    *   Use extremely randomized trees: **Checked**
    *   Enable parallel model building: **Checked**
    *   Hyper-parameter optimization:
        *   Target: **0.05**
        *   Max iterations: **5000**
        *   Max evaluations: **500**

#### Random Forest 4

*   Basic Settings:
    *   Number of trees: **300**
    *   Maximum tree depth: **200**
    *   Minimum leaf node size: **1**
    *   Number of features to use for splitting: **auto**
*   Advanced Settings:
    *   Use bootstrap samples when building trees: **Checked**
    *   Use out-of-bag samples to estimate the generalization accuracy: **Checked**
    *   Use extremely randomized trees: **Checked**
    *   Enable parallel model building: **Checked**
    *   Replicate results: **Checked**
    *   Hyper-parameter optimization:
        *   Target: **0.05**
        *   Max iterations: **10,000**
        *   Max evaluations: **500**

7.  Compare the model fit metrics between these four models using the testing results.
8.  Select the champion model and justify this selection with the necessary evidence.
9.  Present the results of the champion model.
10.  Evaluate the reliability and validity of the champion model.
11.  Present the variable importance chart and interpret the results.

# 15 Gradient Boosting

DOI: [10.1201/9781003468196-18](https://doi.org/10.1201/9781003468196-18)

## Learning Outcomes

Upon the completion of this chapter, you will be able to:

1.  Describe the principles and concepts of gradient boosting as a powerful machine learning algorithm.
2.  Discuss the advantages and disadvantages of using gradient boosting compared to other machine learning methods.
3.  Explain the iterative process of building an ensemble of weak learners in gradient boosting.
4.  Categorize different loss functions in gradient boosting.
5.  Define gradient descent and explain its important role in gradient boosting.
6.  Compare traditional gradient boosting, Gradient Boosting Additive Models (GBAM), and Stochastic Gradient Boosting (SGB).
7.  Describe the importance of hyperparameter tuning in gradient boosting and its impact on model performance.
8.  Build and train gradient boosting models using SPSS Modeler.

## Introduction

![](images/ufig15_1.jpg)

This chapter introduces gradient boosting, an ensemble method that also utilizes decision trees. Gradient boosting is a tree-boosting technique that constructs a series of decision trees, which together form a single predictive model. It is a highly effective method for making predictions and selecting important variables. Does it sound similar to random forest? Yes, both methods involve combining multiple decision trees to produce more robust and accurate predictions. However, they operate differently, and we will compare these two methods later in this chapter.

Gradient boosting begins with an initial decision tree model and improves it by using the residuals from the previous model as the target for the next step. Imagine multiple trees connected in sequence, with each tree building on the errors of the previous one—this forms the structure of a gradient boosting model. If each tree in the sequence is created from a random sample of the training data, the method is referred to as stochastic gradient boosting. This chapter covers the principles and concepts of gradient boosting, how it differs from random forest, the gradient boosting process, and how to implement gradient boosting using SPSS Modeler.

## What Is Gradient Boosting?

![](images/ufig15_2.jpg)

Gradient boosting is a widely used machine learning method for both classification and association models. It is an ensemble learning technique that combines multiple weak models to form a stronger, more accurate model. The key idea behind gradient boosting is to iteratively add new models to the ensemble, each one designed to correct the errors made by the previous models.

Here's how gradient boosting works: the algorithm uses a loss function to measure the difference between predicted and actual values (prediction errors) and then trains new models iteratively to reduce those errors. At each iteration, a new model is trained to predict the difference between the current predictions and the actual values, also known as residuals. The new model is trained to predict these residuals using the variables in the data. Once trained, the new model is added to the ensemble, and the ensemble's predictions are updated by adding the predictions of this new model. This process continues iteratively, with each new model correcting the errors of the previous models, until the overall error is minimized or a predefined number of iterations is reached.

The term “gradient” in gradient boosting refers to the use of the gradient of the loss function to optimize the model. The gradient provides information about the direction and magnitude of the error, helping update the model parameters effectively.
