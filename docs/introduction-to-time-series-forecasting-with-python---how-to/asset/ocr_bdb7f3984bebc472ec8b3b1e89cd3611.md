# ### 18.4.1 Step 1: Define the Supervised Learning Problem

The first step is to load the dataset and create a lagged representation. That is, given the observation at t, predict the observation at t+1.

```
```
# Create lagged dataset
values = DataFrame(series.values)
datframe = concat([values.shift(1), values], axis=1)
datframe.columns = ['t', 't+1']
print(datframe.head(5))
```
```

Listing 18.1: Create the lagged dataset.

This snippet creates the dataset and prints the first 5 rows of the new dataset. We can see that the first row (index 0) will have to be discarded as there was no observation prior to the first observation to use to make the prediction. From a supervised learning perspective, the t column is the input variable, or X, and the t+1 column is the output variable, or y.

| t    | t+1   |
| :--- | :---- |
| 0 NaN | 266.0 |
| 1 266.0 | 145.9 |
| 2 145.9 | 183.1 |
| 3 183.1 | 119.3 |
| 4 119.3 | 180.3 |

Listing 18.2: Example output of creating the lagged dataset.

# ### 18.4.2 Step 2: Train and Test Sets

The next step is to separate the dataset into train and test sets. We will keep the first 66% of the observations for training and the remaining 34% for evaluation. During the split, we are careful to exclude the first row of data with the NaN value. No training is required in this case; it’s just habit. Each of the train and prediction and test sets are then split into the input and output variables.

```
```
# split into train and test sets
X = datframe.values
train_size = int(len(X) * 0.66)
train, test = X[1:train_size], X[train_size:]
train_X, train_y = train[:,0], train[:,1]
test_X, test_y = test[:,0], test[:,1]
```
```

Listing 18.3: Split the lagged dataset.

# ### 18.4.3 Step 3: Persistence Algorithm

We can define our persistence model as a function that returns the value provided as input. For example, if the t value of 266.0 was provided, then this is returned as the prediction, whereas the actual real or expected value happens to be 145.9 (taken from the first usable row in our lagged dataset).

```
```
# persistence model
def model_persistence(x):
    return x
```
```

Listing 18.4: Define persistence prediction.