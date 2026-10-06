
| | Age | Gender | Watched | Genre |
|---|---|---|---|--|
| 0 | 19 | Male | Comedy | Mystery |
| 1 | 19 | Female | Romance | Drama |
| 2 | 19 | Male | Romance | Drama |

In the second run we printed the first three rows of our dataset and by looking we can say that if a 18 years old male (whose sample isn’t present in the dataset) has previously watched a Comedy movie so most likely he’ll like a Mystery movie too along with the Comedy movies.

So we have created our Movie Recommender Model using very little dataset, now it’s up to you to test the model or even take opinions from your relatives and recommend them using the model!

## 22 ML APPLICATION 2

- Advertisement handling

![](img/d75fea3635f5553f1cb0585b399b1b4b_208_0.png)

## ML APPLICATION 2

**Problem:** You have to create an ad to a user or not. If yes then which show an ad to. where Car or Insurance advt. where the age of the user and user class i.e. a group provided from another model based on the user's past search results are provided as input. You are provided with the following dataset

![](img/d75fea3635f5553f1cb0585b399b1b4b_209_0.png)

Once again we need to decide which method to use and clearly this is a problem of classification. We can use the KNN classifier algorithm for this task.

So let's move onto jupyter notebook and import the algorithm, LabelEncoder, pandas library and the dataset

```
In [1]: import pandas
from sklearn.neighbors import KNeighborsClassifier
from sklearn.preprocessing import LabelEncoder
dt = pandas.read_csv('advertisement.csv')
dt.head(3)
```

| Age | Search | Ad |
|---|---|---|
| 0 | 18 | Cars | Car |
| 1 | 19 | Automobiles | None |
| 2 | 21 | Automobiles | None |

We again have very less data to work with. We have the Age and Search as input and Ad as output. But we need to preprocess the labels.

```
In [2]: Enc = LabelEncoder()
Enc.fit(['Cars','Automobiles','Health','Car',
'Insurance', 'None'])
for col in ['Search','Ad']:
    dt[col] = Enc.transform(dt[col])
```

We encoded the values in the Search and Ad column using the Enc Encoder. Now we can move onto the next step of data splitting as mentioned earlier we don't have enough data for splitting it into training and testing set. So we need to create the training set ourselves. Let's take a look at the whole dataset:

We have 20 rows and 3 columns of data. We already know the input i.e. Age and Search and the output i.e. Ad where the input Search will be provided by another classifier which will classify the user into Cars, Automobiles, Health and None classes on the basis of previous searches. We can visually create a understanding from the data that a person of age 18-28 should only be shown Car advertisement when the person is in Cars, else the Insurance advertisement when the person is in Health class. Similarly, a person of age 30 or more should be shown the Car advertisement if the person is in Cars or Automobiles class and vice versa.

| Age | Search | Ad |
|---|---|---|
| 18 | Cars | Car |
| 19 | Automobiles | None |
| 21 | Automobiles | None |
| 22 | Cars | Car |
| 23 | None | None |
| 25 | None | None |
| 26 | Health | Insurance |
| 27 | Cars | Car |
| 18 | Health | Insurance |
| 19 | None | None |
| 20 | None | None |
| 22 | Automobiles | None |
| 26 | None | Insurance |
| 30 | Health | Insurance |
| 14 | Automobiles | Car |
| 29 | Cars | Car |
| 29 | Health | Insurance |
| 29 | None | Insurance |
| 32 | Automobiles | Car |
| 32 | Health | Insurance |

