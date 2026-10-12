
## 5. What are some common methods for generating diversity in ensemble methods, such as bagging, boosting, and stacking? How do these techniques enhance the ensemble's predictive power?

## 6. In what scenarios would ensemble methods be particularly beneficial and suitable for a data mining project? Are there any specific domains or types of problems where ensemble methods have shown significant success?

## 7. Discuss the computational complexity of ensemble methods. Are there any techniques or optimizations that can be employed to improve their efficiency for large datasets?

## 8. Explain the concept of ensemble size and its impact on the performance of ensemble methods. How does the number of models in the ensemble affect prediction accuracy and computational resources?

## 9. What are some potential challenges or limitations of ensemble methods that researchers and practitioners should be aware of? How can these challenges be addressed or mitigated in practice?

# Chapter Exercises

## Exercise 1: Ensemble Models for the Bank Dataset

1.  Open the `bank` dataset in SPSS Modeler.

2.  Sample the entire dataset. Refer to Appendix A for variable names and descriptions.

3.  Partition the data:
    *   Split the data using a 60–20–20 ratio (train: 60%, test: 20%, validation: 20%).

4.  Perform data modification as follows:
    *   Impute missing values.
    *   Normalize the data.

5.  Set `CRSCORE` (credit scores) as the target variable.

6.  Build an ensemble model **using the** Ensemble node for seven individual models. Configure it as follows:
    *   **Linear regression** (from [Chapter 7](#chapter7.xhtml) Exercise 1)
    *   **Pruned CHAID tree** (from [Chapter 8](#chapter8.xhtml) Exercise 1)
    *   **Pruned C5.0 tree** (from [Chapter 8](#chapter8.xhtml) Exercise 1)
    *   **MLP 3 model** (from [Chapter 9](#chapter9.xhtml) Exercise 1)
    *   **MLP 4 model** (from [Chapter 9](#chapter9.xhtml) Exercise 1)
    *   **RBF 3 model** (from [Chapter 9](#chapter9.xhtml) Exercise 1)
    *   **RBF 4 model** (from [Chapter 9](#chapter9.xhtml) Exercise 1)

7.  Compare the ensemble model **with the seven individual models using the** test results**. Determine which model has the** best performance. Interpret the variable importance results.

8.  Build six ensemble models using the Ensemble feature in the Decision Tree and Neural Net nodes as follows:
    *   CHAID boosting
    *   CHAID bagging
    *   MLP 3 boosting
    *   MLP 3 bagging
    *   MLP 4 boosting
    *   MLP 4 bagging

9.  Compare the model fit metrics between these ensemble models using the test results. Identify which model has the best performance. Interpret the variable importance results.

## Exercise 2: Ensemble Models for the Passengers Dataset

1.  Open the `passengers` dataset **in** SPSS Modeler.

2.  Sample 20% of the full data. Set return (decision to return to the airline) as the target variable and change its role to binary. Refer to Appendix B for variable names and descriptions.

3.  Partition the data:
    *   Split the data using a 60–20–20 ratio (train: 60%, test: 20%, validation: 20%).

4.  Perform data modification as follows:
    *   Replace zero values for Likert-scale variables with missing values.
    *   Impute missing values.
    *   Normalize data.

5.  Build an ensemble model **using the** Ensemble node **for** seven individual models. Configure it as follows:
    *   **Logistic regression** (from [Chapter 7](#chapter7.xhtml), Exercise 2)
    *   **Pruned CHAID tree** (from [Chapter 8](#chapter8.xhtml), Exercise 2)
    *   **Pruned CART tree** (from [Chapter 8](#chapter8.xhtml), Exercise 2)
    *   **MLP 1 model** (from [Chapter 9](#chapter9.xhtml), Exercise 2)
    *   **MLP 4 model** (from [Chapter 9](#chapter9.xhtml), Exercise 2)
    *   **RBF 2 model** (from [Chapter 9](#chapter9.xhtml), Exercise 2)
    *   **RBF 4 model** (from [Chapter 9](#chapter9.xhtml), Exercise 2)

6.  Compare the ensemble model with the seven individual models using the test results. Determine which model has the best performance. Interpret the variable importance results.

7.  Build six ensemble models using the Ensemble feature in the Decision Tree and Neural Net nodes as follows:
    *   CART boosting
    *   CART bagging
    *   MLP 1 boosting
    *   MLP 1 bagging
    *   MLP 4 boosting
    *   MLP 4 bagging

8.  Compare the model fit metrics between these ensemble models using the test results. Identify which model has the best performance. Interpret the variable importance results.

# 11 Presenting Results and Writing Data Mining Reports

DOI: [10.1201/9781003468196-13](https://doi.org/10.1201/9781003468196-13)

## Learning Outcomes

Upon the completion of this chapter, you will be able to:

1.  Explain the importance of writing an effective data mining project report.
2.  Differentiate between academic research reports, technical reports, and business reports.
3.  Identify the target audience for your report and determine the right writing styles.
4.  Outline the general structure of a data mining project report.
5.  Describe the purpose and content of primary sections in a report.
6.  Evaluate approaches for effective writing.
7.  Implement various approaches to hook the audience and keep their interest in your report.
8.  Write an effective title, abstract, introduction, literature review, methodology, results, discussions, and conclusions for a data mining report.

## Introduction

![](images/ufig11_1.jpg)

In previous chapters, we have learned the most important parts of data mining: understanding the data, preparing the data, and analyzing the data. We have gone through all the steps in the `SEMMA` (Sample-Explore-Modify-Model-Assess) process, including `sample`, `explore`, `modify`, `model`, and `assess`. This process led us to the final data mining results, the champion model, and a deep understanding of its structure and patterns. The next step is to write up the report. Sounds simple enough? Not really. Data mining is a complex process with many steps and decisions. It involves machine learning algorithms, configurations, and results, which consist of multiple diagrams, tables, and graphs. Given the abundance of information, it is crucial to select and present the appropriate results and write the report in a well-organized format to avoid confusing the readers. While we may have conducted thorough analyses and achieved useful results, failure to produce a quality report may result in stakeholders misunderstanding our outcomes or making incorrect decisions, leading to business failures or incidents.

In this chapter, I provide specific guidelines for writing a data mining report, with a focus on result presentation. Through examples, tips, and recommendations, I will demonstrate the key components of report writing using a hypothetical study on airline recommendations as an illustrative case. While this isn’t an actual research study, I will provide guidelines on how to write critical sections of the report. However, for important sections such as Introduction, Methodology, and Results, I will show specific examples of how to write statements or explanations.
