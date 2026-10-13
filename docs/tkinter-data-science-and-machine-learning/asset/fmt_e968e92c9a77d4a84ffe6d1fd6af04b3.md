
result\_et.sort\_values('Values', inplace=True, ascending=False): The `result_et` DataFrame is sorted based on the "Values" column in descending order. This means that the most important features will appear at the top of the DataFrame.

1.  Returning the Result DataFrame:

`return result_et`: Finally, the method returns the `result_et` DataFrame, which contains the feature names and their corresponding importances as calculated by the Extra Trees classifier.

The feature importances calculated by this method can be valuable for feature selection, dimensionality reduction, and gaining insights into which features are most influential in making predictions with machine learning models.

## Feature Importances Using Recursive Feature Elimination (RFE)

In `Process_Data` class, the `feat_importance_rfe()` method in the code is responsible for calculating and returning feature rankings using Recursive Feature Elimination (RFE) with a Logistic Regression model.

```
def feat_importance_rfe(self, X, y):

    model = LogisticRegression()

    #Creates the RFE model

    rfe = RFE(model)

    rfe = rfe.fit(X, y)

    result_lg = pd.DataFrame()

    result_lg['Features'] = X.columns

    result_lg['Ranking'] = rfe.ranking_

    result_lg.sort_values('Ranking', inplace=True , ascending = False)

    return result_lg
```

Let's break down how this method works:

1.  Method Definition:

`def feat_importance_rfe(self, X, y):` This is a method definition that takes three parameters: `self`, which is a reference to the instance of the class, `X`, which is a Pandas DataFrame containing the input features, and `y`, which is a NumPy array containing the target variable.

1.  Creating a Logistic Regression Model:

`model = LogisticRegression():` An instance of the `LogisticRegression` classifier is created. Logistic Regression is used as the base model for feature ranking in the RFE process. The RFE technique aims to select the most important features by iteratively training the model with different subsets of features.

1.  Creating the RFE Model:

`rfe = RFE(model):` An instance of the Recursive Feature Elimination (RFE) technique is created, with the `LogisticRegression` model as its base estimator. RFE is used to perform feature selection by recursively removing the least important features.

1.  Fitting the RFE Model:

`rfe = rfe.fit(X, y):` The RFE model is fitted to the input features `X` and the target variable `y`. During this process, RFE iteratively trains the Logistic Regression model with different subsets of features and assigns rankings to each feature based on their importance.

1.  Creating a Result DataFrame:

*   `result_lg = pd.DataFrame():` An empty Pandas DataFrame called `result_lg` is created to store the feature rankings.

*   `result_lg['Features'] = X.columns:` A column named "Features" is added to the `result_lg` DataFrame, containing the names of the input features.

*   `result_lg['Ranking'] = rfe.ranking_:` Another column named "Ranking" is added to the `result_lg` DataFrame, containing the feature rankings assigned by the RFE process. Lower rankings indicate more important features.

1.  Sorting Feature Rankings:

`result_lg.sort_values('Ranking', inplace=True, ascending=False):` The `result_lg` DataFrame is sorted in descending order based on the "Ranking" column. This means that the features with lower rankings (more important) will appear at the top of the DataFrame.

1.  Returning the Result DataFrame:

`return result_lg:` Finally, the method returns the `result_lg` DataFrame, which contains feature names and their corresponding rankings based on the RFE process.

The RFE technique is used for feature selection, and it helps identify the most important features for a given machine learning task. In this case, the rankings indicate the relative importance of each feature in making predictions using a Logistic Regression model.

## Saving Prediction Result

In `Process_Data` class, the `save_result()` method in the code is responsible for saving the results of a prediction task into a CSV file. This method takes the actual target values (`y_test`), predicted values (`y_pred`), and a file name (`fname`) as input and then saves the results into a CSV file.

```
def save_result(self, y_test, y_pred, fname):

    # Convert y_test and y_pred to pandas Series for easier handling

    y_test_series = pd.Series(y_test)

    y_pred_series = pd.Series(y_pred)

    # Calculate y_result_series

    y_result_series = pd.Series(y_pred - y_test == 0)

    y_result_series = y_result_series.map({True: 'True', False: 'False'})

    # Create a DataFrame to hold y_test, y_pred, and y_result

    data = pd.DataFrame({'y_test': y_test_series, 'y_pred': y_pred_series, 'result': y_result_series})

    # Save the DataFrame to a CSV file

    data.to_csv(fname, index=False)
```

Here's a breakdown of how this method works:

1.  Method Definition:

`def save_result(self, y_test, y_pred, fname):` This is a method definition that takes four parameters: `self`, which refers to the instance of the class, `y_test`, which is a NumPy array or Pandas Series containing the actual target values, `y_pred`, which is a NumPy array or Pandas Series containing the predicted values, and `fname`, which is a string representing the file name for saving the results.

1.  Converting to Pandas Series:

*   `y_test_series = pd.Series(y_test):` The `y_test` array is converted into a Pandas Series called `y_test_series`. This conversion makes it easier to manipulate and combine with other Series.

*   `y_pred_series = pd.Series(y_pred):` Similarly, the `y_pred` array is converted into a Pandas Series called `y_pred_series`.

1.  Calculating the Result Series:

*   `y_result_series = pd.Series(y_pred - y_test == 0):` This line calculates a result series called `y_result_series`. It compares the predicted values (`y_pred`) with the actual values (`y_test`) element-wise and checks if they are equal. The result is a Boolean Series where `True` indicates that the prediction was correct, and `False` indicates an incorrect prediction.

*   `y_result_series = y_result_series.map({True: 'True', False: 'False'}):` The Boolean values in `y_result_series` are mapped to the strings 'True' and 'False', making it more human-readable.

1.  Creating a DataFrame for Results:

`data = pd.DataFrame({'y_test': y_test_series, 'y_pred': y_pred_series, 'result': y_result_series}):` A Pandas DataFrame called `data` is created to hold three columns: 'y_test' (containing actual target values), 'y_pred' (containing predicted values), and 'result' (containing 'True' or 'False' based on correctness of predictions). This DataFrame combines the actual and predicted values along with the result.

1.  Saving the DataFrame to CSV:

`data.to_csv(fname, index=False):` The `data` DataFrame is saved to a CSV file with the name specified by the `fname` parameter. The `index=False` argument ensures that the DataFrame index is not saved in the CSV file.

In summary, this method takes the actual and predicted values, computes whether each prediction was correct or not, and stores this information along with the original values in a CSV file for further analysis and reporting. This can be helpful for evaluating the performance of a machine learning model and comparing actual vs. predicted outcomes.

## Helper_Plot Class

Create a new python file named `helper_plot.py`. Then, define a class named The `Helper_Plot` as utility class designed for plotting and visualizing data. It contains various methods and imports necessary libraries for creating visualizations.

### helper_plot.py

```
from tkinter import *

import seaborn as sns

import numpy as np

from pandastable import Table

from process_data import Process_Data

from sklearn.metrics import confusion_matrix, roc_curve, accuracy_score

from sklearn.model_selection import learning_curve

class Helper_Plot:

    def __init__(self):

        self.obj_data = Process_Data()
```

Let's go through the key aspects of this class:
