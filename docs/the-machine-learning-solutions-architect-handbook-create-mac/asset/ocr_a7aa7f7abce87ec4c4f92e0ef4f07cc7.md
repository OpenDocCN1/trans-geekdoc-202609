III. Enter the following code blocks into different cells and see the execution results for each step. This is the same exercise we did in Chapter 3, Machine Learning Algorithms.

```
! pip3 install matplotlib
import pandas as pd
churn_data = pd.read_csv('churn.csv')
churn_data.head()
```

```
# The following command calculates the various statistics for the features.
churn_data.describe()
```

```
# The following command displays the histograms for the different features.
# You can replace the column names to plot the histograms for other features
churn_data.hist(['CreditScore', 'Age', 'Balance'])
```

```
# The following command calculate the correlations among features
churn_data.preprocessing.corr()
```

```
from sklearn.preprocessing import OrdinalEncoder
encoder = OrdinalEncoder()
churn_data['Geography_code'] = encoder.fit_transform(churn_data['Geography'])
churn_data['Gender_code'] = encoder.fit_transform(churn_data['Gender'].drop() =
churn_data.drop(columns=['Geography', 'Gender', 'RowNumber', 'Surname'], inplace=True)
```

```
# import the train_test_split class for data split
from sklearn.model_selection train_test_split
# Split the dataset into training (80%) and testing (20%).
```

```
churn_train, churn_test = train_test_split(churn_data, test_size=0.2)
```