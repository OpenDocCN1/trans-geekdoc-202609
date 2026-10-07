```
# creating the bag of words
from sklearn.feature_extraction.text import CountVectorizer
cntvectorizer = CountVectorizer()
cntvectorizer = CountVectorizer(max_features=1500)
X = cntvectorizer.fit_transform(corpus_reviw).toarray()
y = dataset.iloc[:, 1].values
```

```
# Naive Bayes
```

```
# Data Split
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20, random_state=0)
```

```
# Feature-Scaling
```

```
from sklearn.preprocessing import StandardScaler
st = StandardScaler()
X_train = st.fit_transform(X_train)
X_test = st.transform(X_test)
```

```
# Fit train set to Naive Bayes classifier: No parameter is needed
from sklearn.naive_bayes import GaussianNB
classifier = GaussianNB()
classifier.fit(X_train, y_train) # to fit the dataset
```

```
# Predict
y_pred = classifier.predict(X_test)
```

```
# Making the confusion matrix use the function "confusion_matrix"
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_true, y_pred)
# parameters of cm: [[0,0],[1,1]] true values, predicted values
```

```
accuracy (cm[0][0] + cm[1][1]) / cm.shape[0]
```

```
# How can I find the length of a row (or column) of this matrix? Equivalently, how can I know the number of rows or columns?
```

```
# shape is a property of both ndarray and arrays.
# A.shape
will return a tuple (m, n), where m is the number of rows, and n is the number of columns.
```

```
# import nltk
from nltk.corpus import stopwords
print(stopwords.words('english'))
print(set(stopwords.words('english')))
```

```
# python prctc_nlp.py
```

+   We take the test size 20%.
We also don't need any feature scaling because we are only dealing with 0s and 1s.

From the confusion matrix that out of 200 test, 148(true negative 55 true positive) are correct predictions and 54 (false positive 42 false negative) are incorrect predictions and the accuracy is 73%.

+   From 97 negative review we predicted 55 correct
From 103 positive review we predicted 91 correct

| | 0 | 1 |
|---|---||
| 0 | 55 | 42 |
| 1 | 12 | 91 |

```
posve = [k for k in y_test if k==1]
total_posve = len(posve)
```