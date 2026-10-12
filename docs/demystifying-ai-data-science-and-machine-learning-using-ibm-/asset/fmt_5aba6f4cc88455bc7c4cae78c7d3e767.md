
2. Sample the entire dataset. Refer to the variable names and descriptions in Appendix A.

3. Do **not** partition the data.

4. Perform data modification as follows:

*   Impute missing values.

5. Select the following variables for cluster analysis:

*   Age
*   Income
*   Length of residency
*   Teller visit
*   Saving balance
*   CD balance
*   Money market balance
*   Mortgage balance
*   Home value
*   Investment balance
*   Loan balance

6. Conduct the cluster analysis using three different approaches:

*   Auto Cluster Node
*   TwoStep Cluster Node
*   K-Means Cluster Node

7. Compare the results across the three models, focusing on:

*   Number of clusters
*   Cluster quality
*   Cluster size

8. Determine the appropriate number of clusters and rerun the analysis using the K-Means Cluster Node.

9. Present the results of the cluster analysis, including:

*   Number of clusters
*   Cluster size
*   Cluster distance
*   Variable importance

10. Perform cluster profiling using the selected variables.

11. Describe the unique characteristics of each cluster based on the cluster profiling results.

12. Discuss how the cluster analysis results can be used to predict individuals’ credit scores and suggest strategies that banks and financial organizations can use to target each cluster.

### Exercise 2: Cluster Analysis for the Passengers Dataset

488.

1. Open the **passengers** dataset in SPSS Modeler.

2. Sample 20% of the full dataset.

3. Do **not** partition the data.

4. Perform data modification as follows:

*   Replace zero values for Likert-scale variables with missing values.
*   Impute missing values.

5. Select the following variables for cluster analysis:

*   Gender
*   Age
*   Type of travel
*   Customer type
*   Ticket class
*   Flight distance

6. Conduct the cluster analysis using three different approaches:

*   Auto Cluster Node
*   TwoStep Cluster Node
*   K-Means Cluster Node

7. Compare the results across the three models, focusing on:

*   Number of clusters
*   Cluster quality
*   Cluster size

8. Determine the appropriate number of clusters and rerun the analysis using the K-Means Cluster Node.

9. Present the results of the cluster analysis, including:

*   Number of clusters
*   Cluster size
*   Cluster distance
*   Variable importance

10. Perform cluster profiling using the selected variables.

11. Describe the unique characteristics of each cluster based on the cluster profiling results.

12. Discuss how the cluster analysis results can be used to predict passengers’ decisions to return to the same airline and suggest strategies that airlines can implement to target each cluster.

489.

# Part III Advanced Data Mining Methods

490 is blank. 491.

# 14 Random Forest

DOI: [10.1201/9781003468196-17](https://doi.org/10.1201/9781003468196-17)

## Learning Outcomes

Upon the completion of this chapter, you will be able to:

1. Describe the principles and concepts of random forest as an ensemble machine learning method.
2. Discuss the advantages and disadvantages of random forest compared to other machine learning methods.
3. Explain how random forest constructs decision trees using random subsets of training data and input variables.
4. Describe how random forest combines predictions from multiple decision trees through voting or averaging.
5. Explore the hyperparameters of random forest and their impact on model performance.
6. Explain the scalability and efficiency of random forest, including its parallelization capabilities.
7. Define out-of-bag evaluation and explain how it affects the model performance.
8. Construct random forest modeling using SPSS Modeler.

## Introduction

![](images/ufig14_1.jpg)

Random forest is one of the most popular and powerful machine learning methods. It is an ensemble learning method that constructs numerous decision trees. We discussed ensemble modeling in [Chapter 10](#chapter10.xhtml), and the concept here is similar, except random forest focuses on combining multiple decision trees. Imagine building many decision tree models (as described in [Chapter 8](#chapter8.xhtml)) and then combining those trees into an ensemble model to create a more robust and accurate predictive model. Visually, this forms a “forest” of trees, which is why it is called **random forest**. Essentially, it is a tree-based method.

For classification models, the output of the random forest is the mode (most frequent class) of the individual trees’ predictions. For regression models, the output is the mean prediction from all individual trees.

Random forest is one of the most accurate learning algorithms and can handle a large number of input variables without needing to delete any. It is simple to use, faster to compute, and more resistant to noise in the data. Moreover, random forests are effective at preventing overfitting. In this chapter, we will introduce and explain the random forest algorithm, as well as how to perform random forest analysis and interpret the results.

## What Is Random Forest?

![](images/ufig14_2.jpg)

492. Random forest is a machine learning algorithm that combines the predictions of multiple decision trees to make more accurate and robust predictions. It is classified as an ensemble learning method, which combines the results of multiple models to create a stronger predictive model.

Specifically, random forest is a bagging algorithm (refer to [Chapter 10](#chapter10.xhtml) for details on bagging). To recap, bagging is an ensemble technique where multiple individual models are trained independently on different random subsets of the training data (sampling with replacement). The final prediction is determined by averaging all individual model predictions for regression tasks or by taking the majority vote for classification tasks.

A random forest operates under the principle that an ensemble of uncorrelated trees will outperform any of the individual trees. Those individual trees are trained like standard trees with separate training data sampled from the dataset. Then, the final prediction of the random forest model is determined based on a majority vote or average of individual trees’ prediction outputs. [Figure 14.1](#chapter14.xhtml#fig14_1) illustrates a random forest model. The idea behind this randomness is to introduce diversity among the trees, reducing the risk of overfitting and improving the predictive power.

![](images/ufig14_3.jpg)![FIGURE 14.1 Illustration of a random forest model. Return to text.⏎](images/fig14_1.jpg)

FIGURE 14.1 Illustration of a random forest model. [Return to text.⏎](#chapter14.xhtml#b14fig14_1)

## Practical Applications of Random Forest

![](images/ufig14_4.jpg)

493. Random forest has numerous practical applications in many domains. Below are some of the common applications of random forest:

1. **Anomaly detection**: This method can be applied to identify anomalies or outliers in datasets. It has been used for network intrusion detection, fraud detection in financial transactions, and detecting anomalies in sensor data.

2. **Recommendation systems**: Organizations can use random forest in recommendation systems to provide personalized recommendations. It can analyze user behavior and preferences to suggest movies, products, or content tailored to individual users.

3. **Aircraft maintenance and fault detection**: Random forest can be applied to predict potential maintenance issues and detect faults in aircraft systems. By analyzing sensor data and historical maintenance records, it can help identify patterns indicative of impending failures or anomalies.
