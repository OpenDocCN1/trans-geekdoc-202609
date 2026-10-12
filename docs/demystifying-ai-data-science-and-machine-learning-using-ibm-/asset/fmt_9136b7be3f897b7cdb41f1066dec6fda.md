
## 2. Why is it important to an effective report for a data mining project?

## 3. What are the primary differences between academic research reports, technical reports, and business reports? Discuss in detail those differences.

## 4. Select one data mining project and identify the target audience. What are the expectations of that audience for your data mining report?

## 5. What is the effective writing style for that audience? Why? Describe the pros and cons of that writing style.

## 6. What are the primary sections of a data mining report? Describe the purpose and content of each section.

## 7. What are different ways to hook the audience and keep their interest in your report?

## 8. How do you tell if a report title is effective? What are strategies to write a good title?

## 9. What are the key strategies for writing each section of the report?

# Chapter Exercises

### Exercise 1: Writing the Report for the Bank Dataset

1.  Prepare an outline for a business report for the bank customer project. The purpose is to build a predictive model that accurately predicts a customer's credit score based on their demographic variables and banking information.

2.  Write a project title.

3.  Write an abstract.

4.  Write a brief introduction section, including the problem statement, research questions, purpose statement, significance of the study, and delimitations.

5.  Write a methodology section, including data source, variable description, data mining process, machine learning methods and configurations, and model evaluation metrics.

6.  Choose the results from the following models you completed for the exercises in [Chapters 7](#chapter7.xhtml) and [8](#chapter8.xhtml) (choose the best one for each type):

    *   Linear regression using stepwise.
    *   CART tree.
    *   CHAID tree.
    *   C5.0 tree.
    *   MLP model.

7.  Write a results section to present the findings, including:

    *   Demographic information.
    *   Descriptive statistics results.
    *   Model comparison results.
    *   Champion model identification.
    *   Evaluation of the reliability and validity of the champion model.
    *   Detailed structure and relationships in the champion model.
    *   Explanation of variable importance.

8.  Write a brief discussion section, including discussions of the findings, their implications, and limitations of the analysis.

### Exercise 2: Writing the Report for the Passengers Dataset

1.  Prepare an outline for a business report for the airline passengers project. The purpose is to build a predictive model that accurately predicts a passenger's decision to return to the same airline based on their demographic variables, flight information, and their evaluation of airline services.

2.  Write a project title.

3.  Write an abstract.

4.  Write a brief introduction section, including the problem statement, research questions, purpose statement, significance of the study, and delimitations.

5.  Write a methodology section, including data source, variable description, data mining process, machine learning methods and configurations, and model evaluation metrics.

6.  Choose the results of the models you completed for the exercises in [Chapters 8](#chapter8.xhtml) and [9](#chapter9.xhtml) (choose the best one for each type):

    *   CART tree
    *   CHAID tree.
    *   MLP model
    *   RBF model.

7.  Write a results section to present the findings, including:

    *   Demographic information.
    *   Descriptive statistics results.
    *   Model comparison results.
    *   Champion model identification.
    *   Evaluation of the reliability and validity of the champion model.
    *   Detailed structure and relationships in the champion model.
    *   Explanation of variable importance.

8.  Write a brief discussion section, including discussions of the findings, their implications, and limitations of the analysis.

# 12 Principal Component Analysis

DOI: [10.1201/9781003468196-14](https://doi.org/10.1201/9781003468196-14)

## Learning Outcomes

Upon the completion of this chapter, you will be able to:

1.  Describe the concepts of principal component analysis (`PCA`) as a dimensionality reduction technique in data mining.
2.  Explain the principles and algorithms used in `PCA` for extracting the principal components from a dataset.
3.  Discuss the advantages and disadvantages of `PCA` in the context of data mining.
4.  Explain how `PCA` captures the variance and correlation structure of data through eigenvalues and eigenvectors.
5.  Select the proper number of principal components to retain using the scree plot, cumulative eigenvalue, and explained variance.
6.  Explain component rotation methods used in `PCA` to align principal components with the original variables in order to improve interpretability.
7.  Conduct `PCA` to reduce the number of variables using `SPSS Modeler`.

## Introduction

![](images/ufig12_1.jpg)

When dealing with big data, we often encounter datasets containing a large number of variables, sometimes numbering in the hundreds. These are referred to as high-dimensional datasets. In an effort to improve the accuracy of predictive models, researchers frequently attempt to include all of these variables in the analysis. While this can sometimes be effective, it often leads to issues. As discussed in previous chapters, the number of variables included in the modeling process can significantly impact the model's explanatory power. The more variables involved, the lower the explanatory power might become because the algorithm must account for the variance in all variables. This can result in a model that fails to achieve satisfactory predictive performance. Additionally, a large number of variables may significantly increase computing time, making the modeling process inefficient.

So, how can we reduce the number of variables in a dataset without compromising the model's validity? The solution largely depends on the characteristics of the data. For instance, during the exploration step, we might discover that some variables are irrelevant to the target variable, meaning they do not significantly contribute to the prediction. In such cases, we can use a variable selection tool to filter out the most relevant predictors, reducing the number of variables included in the model. However, in some cases, variables might be relevant but highly correlated with each other, creating subsets of correlated variables within the dataset. Simply discarding some of these variables could result in the loss of valuable information. A more effective solution is to combine these correlated variables into a smaller set of new composite variables. In simpler terms, we replace the original variables with a set of new variables, each representing a combination of the correlated variables. This results in a dataset with fewer dimensions. This approach is known as dimensionality reduction.

The challenge with dimensionality reduction is that it alters the original data. Therefore, the key question becomes: How do we reduce the dimensionality of the data while preserving as much of the original information as possible?

Principal component analysis (`PCA`) is one of the most commonly used techniques for dimensionality reduction in machine learning. `PCA` is a statistical method that helps summarize the variation in a high-dimensional dataset by identifying the most important variables or combinations of variables, known as principal components. `PCA` is widely applied in fields such as computer vision, image processing, data mining, and bioinformatics, among others. In this chapter, we will explore the basic concepts of `PCA`, its practical applications, and the steps involved in implementing `PCA` in machine learning.

## Curse of Dimensionality

![](images/ufig12_2.jpg)
