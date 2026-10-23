```
dl = learn.dls.test_dl(test_df)
```

Now we can tell the learner to return the predictions from the test-dataloader.

```
raw_test_preds = learn.get_preds(dl=dl)
```

If we look at the returned data we see a 2x1 array with the predictions and None. This None is our ground-truth. Because we do not have any groundtruth values for the test-dataloader, we get this None. The other thing we see is that this prediction is the log of the specific values because we had calculated the log on the dependent variable of our training data. To get the real values we have to undo this.

```
raw_test_preds
(tensor([[ 8.3973], [ 8.8718], [ 9.1772], ..., [ 8.6769], [10.0459], [ 8.8722]]),
None) np.exp(raw_test_preds[0])
```

```
tensor([[ 4434.9902], [ 7128.1777], [ 9674.0586], ..., [ 5866.0742],
[23061.6875], [ 7130.9248]])
```

Now we get the “true” prediction values. If we want to get a single-array instead of the column vector, we have to transpose it with the help of the .T function.

```
test_preds = np.exp(raw_test_preds[0]).numpy().T[0]
```

# 23.4 Permutation Importance

The main goal of this technique is to get an insight into which columns are more or less important for the accuracy of your model. We can do this by shuffling each column in the dataframe and analyzing how changing a particular column affects the y-values. If we do this shuffling, we are losing all the relations this column had with the model and we get an idea on how this variable affected the outcome of the model.

We can do these permutation tests on the training data or on the testdata.
These two give us different answers.
The one on the validation set tells you:

> “While the model was training, what was it looking at?”

Whereas, the one on the training data tells you: