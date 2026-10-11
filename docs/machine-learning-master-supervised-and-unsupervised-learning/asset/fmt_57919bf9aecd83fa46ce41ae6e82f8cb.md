
# Random Forest Algorithm

Random Forest is a well-known machine learning algorithm that uses the supervised learning method. In machine learning, it can be used for both classification and regression problems. It is based on ensemble learning, which is a method of combining multiple classifiers to solve a complex problem and improve the model's performance.

Random Forest is a classifier that combines a number of decision trees on different subsets of a dataset and averages the results to improve the dataset's predictive accuracy. Instead of relying on a single decision tree, the random forest takes the predictions from each tree and predicts the final output based on the majority votes of predictions.

The greater the number of trees in the forest, the more accurate it is and the problem of overfitting is avoided.

Each tree in the random forest produces a class prediction, and the class with the most votes becomes the prediction of our model (see figure). Figure 2.22 is showing the random forest algorithm visualization and having the Six 1's and three 0's therefore Prediction is 1:

![](image-29spmveq.jpg)
Figure 2.22: Random Forest Algorithm Visualization

## Working of the Random Forest Algorithm

The random forest is created in two phases: the first is to combine N decision trees to create the random forest, and the second is to make predictions for each tree created in the first phase.

The following steps and Figure 2.23 can be used to explain the working process:

![](image-h2b6prgj.jpg)
Figure 2.23: Working of the Random Forest algorithm

1. Choose K data points at random from the training data set.
2. Create decision trees for the data points chosen (subsets).
3. Choose N for the number of decision trees you want to create.
4. Repeat Steps I and II.
5. Find the predictions of each decision tree for new data points and assign the new data points to the category with the most votes.

Assume you have a dataset with a variety of fruit images. As a result, the random forest classifier is given this dataset. Each decision tree is given a subset of the dataset to work with. During the training phase, each decision tree generates a prediction result, and when a new data point appears, the random forest classifier predicts the final decision based on the majority of results. Figure 2.24 is showing the random forest fruit's instance example:

![](image-yl32mdbs.jpg)
Figure 2.24: Random Forest Fruit's instance example

Source: https://www.javatpoint.com/machine-learning-random-forest-algorithm

## Advantages of Random Forest Algorithm

The following are some reasons why we should use the random forest algorithm:

- Less training time required as compared to other algorithms.
- Output with high accuracy.
- Effective for the large dataset.
- Used for the classification and regression.
- Prevents the overfitting problems.
- It can be used for identifying the most important features from the training dataset i.e., feature engineering.

## Disadvantages of Random Forest Algorithm

Despite the fact that random forest can be used for both classification and regression tasks, it is not better suited to regression.

## Applications of Random Forest Algorithm

The random forest algorithm concept is most commonly used in four sectors as follows:

- **Banking**: This algorithm is primarily used in the banking industry to identify loan risk.
- **Medical**: The disease trends and risks can be identified with the help of this algorithm.
- **Land Development**: This algorithm can identify areas with similar land use.
- **Marketing**: This algorithm can be used to spot marketing trends.

## Summary

- Supervised learning is distinguished by the use of labeled datasets to train algorithms that accurately classify data or predict outcomes.
- Supervised machine learning can be further classified into regression and classification.
- Regression algorithms are used if there is a relationship between one or more input variables and the output variable.
- Simple linear regression is a type of linear regression where we have only one independent variable to predict the dependent variable.
- If there is more than one independent variable for the prediction of a dependent variable, then this type of linear regression is known as multiple linear regression.
- Classification is the process to group the output into different classes based on one or more input variables.
- The Naïve Bayes classifiers algorithm is a supervised learning algorithm that solves classification problems and is based on the Bayes theorem.
- The Naive Bayes Model is classified into three types: Gaussian Naïve Model, Multinomial Naïve Model and Bernoulli Naïve Model.
- A decision tree is a supervised learning technique that can be applied to classification and regression problems.
- The K-Nearest Neighbors (K-NN) algorithm stores all available data and classifies a new data point based on its similarity to the existing data.
- K-NN also known as a lazy learner algorithm because it doesn't learn from the training set right away.
- A regression model with a categorical target variable is known as logistic regression.
- The predictions of linear regression are continuous (numbers in a range).
- The predictions of logistic regression are discrete (only specific values or categories are allowed).
- Logistic regression is mainly categorized into three types: Binary, Multinomial, and Ordinal.
- Support Vector Machine (SVM) Algorithm produces significant accuracy while using less computing power.
- There are two types of SVM: Linear and Non-linear.
- Random forest is a well-known machine learning algorithm that uses the supervised learning method.

## Exercise (MCQs)

1. Supervised learning and unsupervised clustering both require at least one.
   - hidden attribute.
   - output attribute.
   - input attribute.
   - categorical attribute.

2. Supervised learning differs from unsupervised clustering in that supervised learning requires:
   - at least one input attribute.
   - input attributes to be categorical.
   - at least one output attribute.
   - output attributes to be categorical.

3. A regression model in which more than one independent variable is used to predict the dependent variable is called:
   - a simple linear regression model
   - a multiple regression models
   - an independent model
   - none of the above

4. A _______________ is a decision support tool that uses a tree-like graph or model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility.
   - Decision tree
   - Graphs
   - Trees
   - Neural Networks

5. Decision trees can be used for classification tasks.
   - True
   - False

6. Sentiment analysis is an example of:
   - Regression
   - Classification
   - Clustering
   - Reinforcement learning
   - 1 Only
   - 1 and 2
   - 1 and 3
   - 1, 2 and 4

7. In supervised learning
   - Classes are not predefined
   - Classes are predefined
   - Classes are not required
   - Classification is not done

8. What are the two types of learning?
   - Improvised and unimprovised
   - Supervised and unsupervised
   - Layered and unlayered
   - None of the above

9. _______________ algorithm stores all available data and classifies a new data point based on its similarity to the existing data.
   - Naive Bayes
   - K-Nearest Neighbors
   - Decision Tree
   - Support Vector Machine

10. Random forest is a well-known machine learning algorithm that uses:
    - Supervised learning
    - Unsupervised learning
    - Hybrid learning
    - None of these

## Answer

- a
- b
- c
- a
- a
- iv
- b
- b
- b
- a
