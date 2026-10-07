# Naïve Bayeses Algorithm 55

Now that our function is ready, we will apply this function to our input data. We will treat only the text in the **X_train** dataset for the moment, as this is what we will use for training our model.

Before applying the function, we convert all the data to lowercase. This is so that all the similar words appear the same. For example, the word "Same" may be used in the text as "Same", "SAME", "same" or in any other way. If we do not convert the text to lower or upper case, all the different representations of the word will appear as distinct entities. Having add value to the spam detector. Suppose we consider that the word "free" is used in SMS texts. If we treat the other representations of "free" differently, our model will weaken.

```
X_train = X_train.str.lower()
X_train = X_train.apply(cleanData)
X_train.head()
```

```
0 lookatme thanks purchase video clip lookatme...
1 aight hit get cash
2 dawachts plan
3 going take babe
4 need lar jus testing e phone card dunno networ...
```

dtype: object

# Forming TF-IDF (Converting text to numbers)

Now that we have a clean data set, need to convert this text data to numbers the computer can use it to model it. There are several ways to convert text data to numbers. We will use two such methods.

We will now create **TF-IDF Vectors**. To make the TF-IDF Vectors, we will use the **TfidfVectorizer** from the Scikit-Learn library as follows:

```
from `sklearn.feature_extraction.text` import TfidfVectorizer
```

```
tfidf = TfidfVectorizer(min_df = 0, use_idf = True, n_range = (1, 4))
tfidText = tfidf.fit_transform(X_train)
print('Shape of original Training Data:', X_train.shape)
print('Shape of transformed Training Data:', tfidf.shape)
Shape of original Training Data: (5014,)
Shape of transformed Training Data: (5014, 87653)
```