# Another method: Without creating virtual environment in Anaconda/Conda:

+   1. Open anaconda base
2. Run following codes to install TensorFlow in base(root):

```
conda activate base
pip install --tensorflow
```

-- makes pip install packages in your home directory instead, which don't require any special privileges.

> To remove virtual environment, use:
onda env remove --env_name

Data Preprocessing: We're going to build this model in two parts:

+   [1]. Data processing
[2]. Creating the ANN model.

Since our business problem is classification problem. The independent variables have some information about customers in a bank. We are trying to predict a binary outcome for the dependent variable which is:

+   1: if the customer leaves
0: if the customer stays in the bank.

So we will use our classification template (previously done classification model). Also we don't need the visualization part, because problem has 10 independent variables.

We will use the confusion matrix to evaluate the performance of our ANN model.

Choosing the independent variables: We don't need the first 3 variables, RowNumber, CustomerId. Surname because variables has no impact on the "Exited" (dependent variable). We take the rest of the variables which last "Exited" will be our dependent variable.

```
X = dataset.iloc[:, 3:13]
```

In [3:13], 13 means all columns from index 3, excluding 13 indexed column". If the index of last column is unknown, then we can use ":-1" which means all columns from index 3, excluding the last column

How to find out most important independent variables: With our own logic are to see which independent variables might have impact on the dependent variable. But we don't know which independent variable has the most impact on the dependent variable. And what our ANN will find and the correlations by using the bigger weights in the neural network

Encode Categorical: [1,2] means we convert 2nd and 3rd columns. We need to encode before splitting the data.

```
ct = ColumnTransformer([{"OneEncoder", [1, 2]}], remainder='passthrough')
```

We are not using alone to encode variables.

+   - We use One-hot for "Gender", variable because it has only 2-categories.
- We will use One-hot for "Geography" (country), because it has three categories. So we will create 3 dummy variables.

Encode "Gender": 'values' converts string to array. If we use X = dataset.iloc[:, 3:13] instead of X=dataset.iloc[:, 3] Then X won't be an array and a Dataset. We will use [:, 2] for encoding. Encoding a column in a Dataset, we need to use "key" of the column. We use X['Gender']$ instead of X[:, 2].

```
X['Gender'] = label_encoder.fit_transform(X['Gender']) # in case of instead of Array
```

```
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
from sklearn.compose import ColumnTransformer

#Encoder using using LabelEncoder,"Gender" is in 3rd-column, we have X[:, 2]
label_encoder = LabelEncoder()
# Following is to apply numpy array, if we used X = dataset.iloc[:,3:13]
X = np.array(X) if is needed if X is not an Array. i.e. "values" not applied
X[:, 2] = label_encoder.fit_transform(X[:, 2])
print(X)

# For a data we can still encode using Columns "key"
# X['Gender'] = label_encoder.fit_transform(X['Gender'])
```