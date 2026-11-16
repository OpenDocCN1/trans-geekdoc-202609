Mean absolute percentage error (MAPE) measures the accuracy as a percentage by calculating the average of the summation of all difference between the actual value and predicted value divided by the actual value. In other words, it is the average absolute percent error for each prediction. MAPE is commonly used for reporting the model’s performance, while there are not many zero values and no extremes to data.

\( MAPE = \frac{1}{n} \sum \left| \frac{y - \hat{y}}{y} \right| \) (8.8)

Coefficient of determination or R-squared (\(R^2\)) is the portion of the variance in the current model predictions performance from the constant baseline performance, presenting how much a model is better than the benchmark or other baseline model. The benchmark is chosen by taking the mean of the data and a line representing the mean. \(R^2\) is a scale-free metric, thus even the values are extremely low or high, this metric always is less or equal to 1.

\( R^2 = 1 - \frac{\sum (y - \hat{y})}{\sum (y - \bar{y})^2} \) (8.9)

# 8.5.4 MACHINE LEARNING ALGORITHMS

As it is mentioned before, machine learning algorithms can also be categorized into classification, regression, clustering, and association analysis. In this section, the most common supervised learning algorithms, classification, and regression are introduced.

# 8.5.4.1 Classification Algorithms

There are several classification algorithms; the most commonly used ones are presented as follows [24–26]:

**Logistic Regression:** Logistic regression is widely used for binary classification tasks where an output belongs to one class or another (0 or 1). In this algorithm, a threshold is defined to indicate examples will be labeled into which class using hypothesis and logistic function (usually sigmoid curve). The hypothesis determines the likelihood of events to generate data and fit them into the logarithm function that forms an S-shaped curve called sigmoid. Then, the logarithm function is used to predict the class of new inputs. Logistic regression is also applied to multiclass classification problems by applying the one versus all strategy, however, it has better performance on binary classification tasks.

**K-nearest neighbors (KNN):** This algorithm is one the most basic yet broadly used classifier, which without making any assumptions on data distribution, finds the data with similar characteristics and group them in the