CHAPTER 9	TECHNIQUES FOR IMPROVING MODEL PERFORMANCE

```
train_features = np.array(
    train_df.select('scaled_features')
        .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
train_labels = np.array(
    train_df.select('Close')
        .rdd.map(lambda x: x.Close).collect())
test_features = np.array(
    test_df.select('scaled_features')
        .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
test_labels = np.array(
    test_df.select('Close')
        .rdd.map(lambda x: x.Close).collect()
)
return (train_features,
    train_labels,
    test_features,
    test_labels
)
```

Transitioning to the next method, we have the create_and_train_model method, which creates and trains the neural network model:

+   - Defines a sequential neural network model with multiple dense layers

+   - Compiles the model with the Adam optimizer and Mean Squared Error loss

+   - Trains the model on the training data

592