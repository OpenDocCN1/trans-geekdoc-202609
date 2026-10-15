Listing 9.23: Example evaluating an MLP with batch normalization before activation on the two circles problem.

Running the example first prints the classification accuracy of the model on the train and test dataset.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

In this case, we can see comparable performance of the model on the train and test datasets, but slightly worse than the model without batch normalization.

```
Train: 0.832, Test: 0.834
```

Listing 9.24: Example output from evaluating an MLP with batch normalization before activation on the two circles problem.

The line plot of the learning curves on the train and test sets also tells a different story. The plot shows the model learning perhaps at the same pace as the model without batch normalization, but the performance of the model on the training dataset is much worse, hovering around 70% to 75% accuracy, again likely an effect of the statistics collected and used over each minibatch. At least for this model configuration on this specific dataset, it appears that batch normalization is more effective after the rectified linear activation function.