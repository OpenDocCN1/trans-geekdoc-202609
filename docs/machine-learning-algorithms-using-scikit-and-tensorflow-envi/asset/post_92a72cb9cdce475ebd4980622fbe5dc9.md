
and decision tree technique. Compared to previous literature which tried a similar method, this work is different in terms of adding futuristic information into the criteria. Decision tree is used to modify existing filtering techniques for more accurate prediction of Taiwan stock market data (2006). Mohammad M Ghiasi applied decision tree to classify breast cancer. Random forest techniques are used to modify classical techniques for detection of breast cancer and classification into malignant and benign lumps. Their model vastly outperformed classical techniques in terms of its performance and it is easy to deploy as well for other healthcare applications (2021). Jun Wu applied a decision tree to modernize the classification of agriculture data. A decision tree classifier is utilized for classification and prediction of agriculture information. The main advantage of this approach is that it works for complete as well an incomplete datasets, therefore more generalized approach for all kinds of agricultural data with enhanced performance by the model (U. et al., 2009).

Shujun Huang used support vector machine classifier to extract meaningful information from cancer genomics datasets. It resulted in the discovery of advanced biomarkers, advanced drug targets and provide more insights on genes of cancer disease (Huang et al., 2018). Byvatov E developed SVM and neural models in medical field with improved outcomes in classification and prediction task (Byvatov & Schneider, 2003). Artificial intelligence based approach is used to build an electrical forecasting model with improved outcomes with better accuracy (Ahmad et al., 2014; Deka, 2014). Mathias M. Adankon proposed an approach for model selection using an advanced approach for handwritten character recognition. LS-SVM method is used for the classification task and shows best performance and generalized approach for other applications as well (Adankon & Cheriet, 2009).

Mucahid Mustafa Saritas proposed an approach for breast cancer analysis based on various parameters of blood routine dataset. ANN and Naïve Bayes classification algorithms were used for analysis and classification of the data and performance of the approaches are evaluated based on different metrics (Saritas & Yasar, 2019). M. Wiggins analyzes ECG data using Bayesian classification technique. Patients were classified based on age and ECG. Findings show improved performance when compared to the existing classifiers (Wiggins et al., 2008). Joanna Kazmierska analyzes risk of cancer disease after radiotherapy using naïve bayes classifier approach (Kazmierska & Malicki, 2008). Naive Bayes algorithms are widely used in various applications including recommendation systems as they are easy to implement. However, some challenges still remain the same, such as the requirements of the predictor. They have used a large training dataset to eliminate the above said problem, leading to higher accuracy (Rrmoku et al., 2022).

## 3. MACHINE LEARNING ALGORITHMS

The fundamental of any machine learning model lies in the algorithm part of it. Now we will describe major ML algorithms in detail.

### 3.1 Linear Regression

Linear regression is one of the fundamental algorithms in ML which is used to predict continuous variable. It is commonly used for predictive analysis and modeling. It is mainly used in finding out relationship between variables and forecasting variable. Regression models are based on number of dependent and independent variables. It predicts a continuous value, for example, CO2 emission from a car.

Figure 4. Linear regression

![](img/20813928ec98c7f6fbdbab0d52bde2f1_43_0.png)

Here, continuous data is used to learn a function for predicting a dependent variable. For example, we want to establish a relationship between some variables x and related y variables. A relationship between these variables is learned through a hypothesis. Hypothesis is a straight line in case of a linear regression problem. Linear model uses parameters called weight and bias which are adjusted based on the trained data points. Further, an error is used to assess the performance of the developed model, known as mean square error. Predicting a house price based on various factors is a linear regression problem.

Linear regression is a regression model whose value is predicted by an integer number, and doesn't require an activation function or any threshold value. Logistic regression is a classification model where we predict values by 0 or 1, it also requires both an activation function and a threshold value. In linear regression we use root mean square energy method for prediction of next value, whereas in logistic regression we use precision to predict or we predict based on maximum likelihood estimation. The graph of a logistic regression is S shaped for positive and Z shaped for negative.

The cost function is given by:

```
j(w,b) = \frac{1}{2m} \sum_{i=1}^m (yi - h(xi)^2
```

where w=weight and b=bias.

Here's an example of how to implement linear regression using scikit-learn in Python (Simplilearn, n.d.). In this example the necessary modules from scikit learn are first imported. Next, we define our sample data. We have an array X that represents the input features and an array y that represents the target variable. We then create a Linear Regression object called regression. This will be our linear regression model. To train the model, we call the fit() method on the regression object, passing in the input features X and the target variable y.

Figure 5. How to implement linear regression using scikit-learn in Python (Simplilearn, n.d.)

```
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt

# Sample data
X = np.array([[1], [2], [3], [4], [5]]) # Input features
y = np.array([2, 4, 5, 4, 5]) # Target variable

# Create a linear regression model
regression = LinearRegression()

# Train the model
regression.fit(X, y)

# Make predictions on the training data
y_pred = regression.predict(X)

# Calculate the mean squared error
mse = mean_squared_error(y, y_pred)
print("Mean Squared Error:", mse)

# Plot the data points and the regression line
plt.scatter(X, y, color='blue', label='Actual')
plt.plot(X, y_pred, color='red', label='Predicted')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.show()
```

Once the model is trained, we can make predictions on the training data by calling the predict() method on the regression object and passing in X. The predicted values are stored in the y_pred array. To evaluate the performance of our model, we calculate the mean squared error (MSE) between the actual target variable y and the predicted values y_pred. The MSE is a common metric used to measure the quality of regression models.

Finally, we visualize the data points and the regression line using matplotlib. The scatter() function is used to plot the actual data points, and the plot() function is used to plot the predicted regression line. We also add labels to the x-axis and y-axis and include a legend for clarity. The resulting plot will show the data points as blue dots and the regression line as a red line. Running the code will output the mean squared error and display the scatter plot with the actual data points and the predicted regression line.

### 3.2 Logistic Regression

A binary dependent variable—one with just two potential outcomes, like yes or no—and one or more independent variables are analysed using the statistical technique known as logistic regression. Data is frequently divided into two or more groups using machine learning and data science techniques. A probability between 0 and 1 that represents the chance of the dependent variable falling into a certain category is the output of a logistic regression model. Binary classification issues (where the dependent variable has two potential outcomes) and multiclass classification problems may both be solved using logistic regression models (where the dependent variable has more than two possible outcomes). The logistic function, which converts any input with a real value to a number between 0 and 1, serves as the foundation for the logistic regression model. Given the values of the independent variables, the logistic function is used to model the likelihood of the dependent variable. The maximum likelihood estimation method is used to estimate the parameters of a logistic regression model. The model may be used to forecast the likelihood that a fresh set of data points will fall within a specific category of the dependent variable once the parameters have been calculated. For a variety of prediction problems, the machine learning and data science sectors of finance, healthcare, and marketing frequently employ the popular and effective method of logistic regression.

Here's an example of how to implement logistic regression using scikit-learn in Python (Towards-datascience, n.d.-a):

In this example the necessary modules from scikit learn are first imported. Next, we define our sample data. We have an array X that represents the input features and an array y that represents the target variable. The target variable is binary, with values of 0 or 1. Next, we create a LogisticRegression object called logreg. This will be our logistic regression model. To train the model, we call the fit() method on the logreg object, passing in the input features X and the target variable y.

Once the model is trained, we can make predictions on the training data by calling the predict() method on the logreg object and passing in X. The predicted values are stored in the y_pred array. To evaluate the performance of our model, we calculate the accuracy by comparing the actual target variable y with the predicted values y_pred. The accuracy is a common metric used to measure the performance of classification models.

Finally, we visualize the data points and the decision boundary using matplotlib. The scatter() function is used to plot the actual data points, and the plot() function is used to plot the predicted probabilities of the positive class. The predicted probabilities are obtained using the predict_proba() method of the logreg object. We also add labels to the x-axis and y-axis and include a legend for clarity. The resulting plot will show the data points as blue dots and the decision boundary as a red curve. Running the code will output the accuracy and display the scatter plot with the actual data points and the decision boundary.
