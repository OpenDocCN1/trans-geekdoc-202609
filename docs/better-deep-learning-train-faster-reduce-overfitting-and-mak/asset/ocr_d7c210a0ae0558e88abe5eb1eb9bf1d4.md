In this case, we can see comparable performance of the model on both the train and test set of about 84% accuracy, very similar to what we saw in the previous section, if not a little bit better.

```
Train: 0.842, Test: 0.846
```

Listing 9.21: Example output from evaluating an MLP with batch normalization after activation on the two circles problem.

A graph of the learning curves is also created showing classification accuracy on both the train and test sets for each training epoch. In this case, we can see that the model has learned the problem faster than the model in the previous section without batch normalization. Specifically, we can see that classification accuracy on the train and test datasets leaps above 80% within the first 20 epochs, as opposed to 30-to-40 epochs in the model without batch normalization. The plot also shows the effect of batch normalization during training. We can see lower performance on the training dataset than the test dataset: scores on the training dataset that are lower than the performance on the test dataset at the end of the training run. This is likely the effect of the input collected and updated each minibatch.

![](bbox=[0.18, 0.44, 0.82, 0.77])

Figure 9.3: Line Plot Classification Accuracy of MLP With Batch Normalization After Activation Function on Train and Test Datasets Over Training Epochs.

We can also try a variation of the model where batch normalization is applied prior to the activation function of the hidden layer, instead of after the activation function.