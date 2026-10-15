# Listing 15.12: Example of an overfit MLP on the two moons problem.

Running the example reports the model performance on the train and test datasets. We can see that the model has better performance on the training dataset than the test dataset, one possible sign of overfitting.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

```
Train: 1.000, Test: 0.914
```

# Listing 15.13: Example output from the overfit MLP on the two moons problem.

A figure is created showing line plots of the model loss and accuracy on the train and test sets. We can see that expected shape of an overfit model where test accuracy increases to a point and then begins to decrease again.

![](bbox=[0.165, 0.44, 0.81, 0.78])

# Figure 15.2: Line Plots of Accuracy on Train and Test Datasets While Training Showing an Overfit.