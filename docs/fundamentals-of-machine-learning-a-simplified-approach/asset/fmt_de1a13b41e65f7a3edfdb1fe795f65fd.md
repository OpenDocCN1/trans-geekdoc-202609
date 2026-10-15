
Strong programming skills (e.g., `Python`, `R`) and understanding of machine learning frameworks like `TensorFlow`, `Keras`, `scikit-learn`, and `PyTorch`.

9\. Career Paths

Data Science:

Roles include `Data Scientist`, `Data Analyst`, `Business Intelligence Analyst`, and `Data Engineer`.

Focus is often on analyzing data, developing reports, visualizing trends, and driving data-driven decisions for organizations.

Machine Learning:

Roles include `Machine Learning Engineer`, `AI Researcher`, `Data Scientist` (with a focus on ML), and `Deep Learning Engineer`.

Focus is on building and deploying machine learning models, optimizing algorithms, and solving predictive and decision-making problems.

10\. Interrelation

While data science and machine learning are distinct, they are deeply intertwined. Machine learning is one of the many tools within the data science toolbox. Data science uses machine learning techniques to extract insights and build predictive models, but it also relies on traditional statistical methods, data visualization, and reporting to provide a holistic view of the data.

In essence, Data Science is a broader field focused on working with data to extract insights and inform decisions, while Machine Learning is a specialized subfield within Data Science that deals with the development of algorithms that learn from data to make predictions or decisions. Data science encompasses a wider range of tasks beyond machine learning, including data wrangling, exploratory data analysis, and statistical modeling, while machine learning focuses on creating models that can learn from and predict outcomes based on data.

Exercise

1.  Why we need machine learning and how it is different from traditional programming approaches?

2.  Present a scenario where you will prefer Support vector machine (SVM) over the other machine learning algorithm. Justify your preference.

3.  Define Machine Learning. Discuss with examples some useful applications of machine learning.

4.  What are supervised, semi-supervised and unsupervised learning?

5.  What do you mean by a well posed learning problem? Explain the important features that are required to well define a learning problem.

Unit II

REGRESSION

LINEAR REGRESSION AND THE LOGISTIC REGRESSION

Linear regression and logistic regression are both widely used models in statistics and machine learning. However, they are used for different types of prediction problems and have different underlying assumptions and applications. Here's a comparison between the two:

1\. Problem Type

Linear Regression:

Objective: Used for regression tasks, where the goal is to predict a continuous numerical value.

Example: Predicting house prices, temperature, or sales amounts.

Logistic Regression:

Objective: Used for classification tasks, where the goal is to predict a categorical outcome, typically a binary outcome (yes/no, 0/1).

Example: Predicting whether an email is spam (1) or not (0), predicting if a customer will buy a product (1) or not (0).

2\. Output (Dependent Variable)

Linear Regression:

The output is a continuous variable. It predicts a value that can range from negative to positive infinity.

Example: Predicting the price of a house based on its features (size, number of rooms, etc.).

Logistic Regression:

The output is a probability that lies between 0 and 1. It predicts the likelihood of a certain class or event happening.

Example: Predicting the probability that a customer will purchase a product.

3\. Model Equation

Linear Regression:

The model assumes a linear relationship between the dependent variable Y and the independent variables X1,X2,...,Xn

The equation for a simple linear regression is: 

`Y=β0+β1X1+β2X2+⋯+βnXn+ϵ`

where:

*   Y is the dependent variable.

*   Xi​ are the independent variables.

*   β0,β1,...,βn​ are the model coefficients.

*   ϵ is the error term.

Logistic Regression:

The logistic regression model uses the logistic function (also called the sigmoid function) to model the probability of a binary outcome. The equation is:

![](d2d_images/image040.png)

Where:

*   P(Y=1∣X) is the probability that the dependent variable Y equals 1 given the independent variables X.

*   The output is constrained between 0 and 1 due to the sigmoid function.

4\. Assumptions

Linear Regression:

Linearity: The relationship between the dependent and independent variables is linear.

Homoscedasticity: The variance of the residuals (errors) should be constant across all levels of the independent variables.

Independence of errors: The residuals should be independent of each other.

Normality: The residuals should be approximately normally distributed for valid statistical inference.

Logistic Regression:

Linearity of the log-odds: The log-odds of the probability are linearly related to the independent variables.

Independence: The observations must be independent.

No multicollinearity: The independent variables should not be highly correlated with each other.

Large sample size: Logistic regression performs better with a large sample size to ensure stable coefficient estimates.

5\. Error Measurement

Linear Regression:

The error is typically measured using Mean Squared Error (MSE) or Root Mean Squared Error (RMSE). These metrics represent the average squared difference between the predicted and actual values.

Logistic Regression:

The error is measured using Log Loss (also called Binary Cross-Entropy), which measures the performance of a classification model whose output is a probability value between 0 and 1.

Log Loss is calculated as: 

![](d2d_images/image035.png)

Where:

*   y is the actual label (0 or 1).

*   p^​ is the predicted probability for the positive class (1).

6\. Interpretation of Coefficients

Linear Regression:

The coefficients βi​ represent the change in the dependent variable Y for a one-unit change in the corresponding predictor Xi​, holding other variables constant.

Example: Ifβ1​=2, it means that for every 1-unit increase in X1​, Y will increase by 2 units.

Logistic Regression:

The coefficients βi​ represent the change in the log-odds of the probability of the dependent variable being 1 for a one-unit change in the corresponding predictor Xi​, holding other variables constant.

The odds ratio can be interpreted as: Odds Ratio=eβi​​.

Example: If β1=0.5, then the odds of the outcome being 1 (e.g., success) increase by a factor of e^(0.5)≈1. for each one-unit increase in X1​.

7\. Applications

Linear Regression:

Predicting continuous outcomes such as sales numbers, stock prices, temperature, or income based on various factors.

Example: Predicting a person's weight based on their height and age.

Logistic Regression:

Predicting binary outcomes such as whether a customer will buy a product (yes/no), whether an email is spam (spam/not spam), or whether a patient has a particular disease (yes/no).

Example: Predicting if a patient will develop diabetes based on factors like age, weight, and lifestyle.

8\. Performance Evaluation

Linear Regression:

R-squared: Indicates how well the independent variables explain the variance in the dependent variable. Higher values (closer to 1) indicate a better fit.

Adjusted R-squared: Takes into account the number of predictors in the model, useful when comparing models with different numbers of predictors.

Logistic Regression:

Accuracy: The proportion of correct predictions (True Positives + True Negatives) to total predictions.

Confusion Matrix: Helps to assess the number of true positives, true negatives, false positives, and false negatives.

Precision, Recall, F1-score: Measures used to evaluate the model performance, especially in imbalanced datasets.

ROC Curve and AUC (Area Under Curve): Measures the trade-off between true positive rate (sensitivity) and false positive rate (1-specificity).

9\. Model Complexity

Linear Regression:

Simpler model with fewer assumptions (linear relationships).
