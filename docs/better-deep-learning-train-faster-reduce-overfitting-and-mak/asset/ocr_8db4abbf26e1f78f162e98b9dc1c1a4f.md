```
> 0.763
> 0.766
> 0.771
> 0.769
Scores Mean: 0.768, Standard Deviation: 0.006
```

Listing 20.30: Example output from a repeated evaluation of a model average ensemble on the blobs problem.

In this case, we can see that the average performance of a five-member ensemble on the dataset is 76.8%. This is very close to the average of 77% seen for a single model. The important difference is the standard deviation shrinking from 1.4% for a single model to 0.6% with an ensemble of five models. We might expect that a given ensemble of five models on this problem to have a performance fall between about 74% and about 78% with a likelihood of 99%.

Averaging the same model trained on the same dataset gives us a spread for improved reliability, a property often highly desired in a final model to be used operationally. More models in the ensemble will further decrease the standard deviation of the accuracy of an ensemble on the test dataset given the law of large numbers, at least to a point of diminishing returns. This demonstrates that for this specific model and prediction problem, that a model averaging ensemble with five members is sufficient to reduce the variance of the model. This reduction in variance, in turn, also means a better on-average performance when preparing a final model.

# 20.4 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

+   - **Average Class Prediction**. Update the example to average the class integer prediction instead of the class probability prediction and compare results.
+   - **Save and Load Models**. Update the example to save ensemble members to file, then load them from a separate script for evaluation.
+   - **Sensitivity of Variance**. Create a new example that performs a sensitivity analysis of the number of ensemble members on the standard deviation of model performance on the test set over a given number of repeats and report the point of diminishing returns.

If you explore any of these extensions, I’d love to know.

# 20.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 20.5.1 APIs

+   - Getting started with the Keras Sequential model.
+     https://keras.io/getting-started/sequential-model-guide/
+   - Keras Core Layers API.
+     https://keras.io/layers/core/