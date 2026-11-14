
- Suburb: Northcote
- Address: 39 Winifred St
- Rooms: 4
- Type: h
- Price: 1.35e+06
- Method: S
- SellerG: Ray
- Date: 23/09/2017
- Distance: 5.3
- Postcode: 3070
- Bedroom2: 4
- Bathroom: 2
- Car: 2
- Landsize: 264
- BuildingArea: 188
- YearBuilt: 1996
- CouncilArea: Darebin City Council
- Lattitude: -37.769
- Longitude: 144.986
- Regionname: Northern Metropolitan
- Propertycount: 11364

We have now identified the three properties most similar to the user's known preference, which are located in the suburbs of Abbotsford, Seddon, and Northcote respectively. To entice the user to return to our online portal, we can email these three property listings from our dataset as content recommendations to the user.

## EVALUATION

If you’re familiar with the mechanics of machine learning, you might have noticed the absence of training and test data used in the models demonstrated thus far. An explanation for this vital question will be revealed later in this chapter, but, first, let’s review the purpose of split validation.

The partitioning of a dataset into training data and test data, known as split validation, is a fundamental part of machine learning. The training data is used to detect general patterns and design a prediction model, while the test data is used to test the model and compare the results. In sum, if we reserve 30% of the data and test it with the model developed from patterns discovered in the initial 70% of the data, will the model’s predictions hold accurate?

If the model’s predictions falter using the test data, this is generally an indicator of overfitting or underfitting. Overfitting happens when the model has to adjust itself to fit patterns in the training data but is too complicated and made-to-measure to replicate its prediction accuracy with the test data or new data. Underfitting, meanwhile, is where the model is too simple and underdeveloped, making it a weak predictor of the training and test data.

There are numerous techniques to compare the performance of the model using the training data and the test data. For classification-based models, a popular method is the confusion matrix, which is a simple table that tabulates the performance of classification algorithms like Naive Bayes Classifier and logistic regression.

| | Predicted 0 | Predicted 1 |
|---|---|---|
| **Actual is 0** | Correct | Incorrect |
| **Actual is 1** | Incorrect | Correct |

Table 9: Confusion matrix

In Table 10, there are a total of 105 data points in the dataset. As highlighted diagonally below, the model predicted 50 data points correctly as “0” and 48 cases as “1”.

| | Predicted 0 | Predicted 1 |
|---|---|---|
| Actual is 0 | 50 | 5 |
| Actual is 1 | 2 | 48 |

Table 10: Results added to the confusion matrix

Meanwhile, the same model incorrectly predicted five data points as “1” and two data points as “0”. This means that five data points were classified as “1”, when in fact they should’ve been classified as “0” (false-positive), and two data points were predicted to be “0” but should have been classified as “1” (false-negative). Reviewing the results of the confusion matrix for the training and test datasets can then be used to make comparisons regarding prediction performance.

### Coding Example

Below is a code example of the same Bayes’ model used to recommend online advertisements in Chapter 7, but, this time, using split validation and a confusion matrix to analyze prediction accuracy.

```
# Import libraries
import pandas as pd
from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report, confusion_matrix

# Import dataset
df = pd.read_csv('~/Downloads/advertising.csv')

# Delete variables
del df['Ad Topic Line']
del df['Timestamp']
del df['City']
del df['Male']
del df['Country']

# Assign X and y variables
X = df.drop('Clicked on Ad', axis=1)
y = df['Clicked on Ad']

# Split the data into training and test sets (70/30)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=10)

# Assign model
model = GaussianNB()

# Fit the algorithm to the training data
model.fit(X_train, y_train)

# Assign a new variable to the prediction of the X test data
model_predict = model.predict(X_test)

# Confusion matrix
print(confusion_matrix(y_test, model_predict))
```

```
[[138 8]
 [ 6 148]]
```

In this example, the model incurs 8 false-positives and 6 false-negatives among the 300 cases.

### Other Methods

Other methods of evaluation used in conjunction with split validation are root mean square error (RMSE) and mean absolute error (MAE), which are used for numeric predictions rather than classification problems.

In the case of RMSE, the evaluation starts by taking a subset of user ratings (i.e., 80%) as the training set, designing a recommender system based on that data and then using the built model to predict the ratings of the remaining (20% of) users from the test set. By comparing the results of the model and the true values of the test set, you may discover that a user rated an item 5-stars but the model predicted 3.5 stars. The error here is 1.5 stars. Using RMSE, you can then compute the average of the errors and generate a final error rate.

Mean absolute error, meanwhile, is less sensitive to large errors and doesn’t penalize poor predictions as heavily as RMSE. As an example, if the model regularly predicted 5-stars and the actual user rating was 1-star, then the final error score would not be as high as the equivalent RMSE error score.

In the case of the famous Netflix Prize launched in 2007, teams were handed a training and test set of real user ratings, and their target was to achieve RMSE of less than 10%.

Although the Netflix Prize helped to popularize attention for RMSE at the time, the company has since moved away from this evaluation metric—going so far as passing on the winning model from the Netflix Prize. More than a decade on, the currency of offline methods including RMSE, MAE, confusion matrix, and split validation (training and test data) have widely fallen out of favor in the domain of recommender systems. While these methods are still used for internal feedback prior to production and for academic research, the industry has drifted away from pure machine learning and the credo of split validation. Internet companies and recommender system specialists have shifted to online evaluation methods such as A/B testing, click-through-rates (CTR), and ROI (return on investment) metrics as well as qualitative research.

Although statistically sound in its approach, split validation encounters problems when faced with the realities of human interaction. While a confusion matrix is effective at comparing the results of the training and test data in an offline environment, numerous real-world factors cause the model to unravel when put into operation.

Recommending items highly correlated to a target user who is already familiar with a proposed combination of movies, such as those of the Harry
