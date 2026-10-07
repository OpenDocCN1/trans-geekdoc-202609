It's the real training set containing the input data of the NN.

iloc [:, 1:2] Start from column indexed1 and end at (2-1)=1 indexed column and exclude column indexed2 First ':':
take the rows,

data_iloc[3]
Gives the 4th row.

data_iloc[1:3]
will row indexed 1.2 and ends 3 (i.e. 2nd, 3rd rows excluding 4th row). iloc[k:m] starts from k (including k), ends at
m-1 excluding.

data_iloc[i:j, n:m]
row starting from i and ends at j-1 excluding j. Columns starting from n (including n, and at m-1 excluding m.

"values" transform the data to NumPy-array. So we don't have a vector, we have a NumPy array of one column.

# 12.3.3 Feature scaling
We know there standardization and normalization. What are we going to use this time for RNN: In previous chapter we used
standard.

| Standardization | Normalization |
| --- | --- |
| X_stand = x - mean(x) / standard deviation (x) | X_norm = x - min(x) / max(x) - min(x) |

Normalization is more relevant for RNN: Whenever you build an RNN and especially if there is a sigmoid function as the
activation function in the output Layer of RNN, I well recommend to apply Normalization.

+   We are going to use the MinMaxScaler class from module of sklearn.
from sklearn.preprocessing import MinMaxScaler

+   Create next scaled sc to have some input arguments, feature_range (0, 1), that's the default feature
range.
The new scaled sc will between zero and one.
sc = MinMaxScaler(feature_range=(0, 1))

The last thing we need to do, is of course to apply apply normalization to training_set,
training_set = sc.fit_transform(training_set)

+   We create a new variable train_scaled because it is recommended to keep your original datasets.
Then we fit_transformer as we did in previous chapters, which will not only fit your sc to the
training_set, also transform, that is scale it.
Hit means just to get the max of the data

The transform method, is to compute for each of the stock prices of the training set, the scaled stock prices across
normalization formula.

```
# feature scaling
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler(feature_range=(0, 1))
train_scaled = sc.fit_transform(training_set)
```

After executing the code, we obtained our training set scaled/normalized. The last values are close to 1 because
remember, the stock price was going up 2012 and 2016 is. getting closer to max value.