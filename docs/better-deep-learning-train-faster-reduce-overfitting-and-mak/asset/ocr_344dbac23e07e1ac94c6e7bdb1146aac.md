82.2%. Next, a model averaging ensemble with all five members is evaluated on the test set reporting an accuracy of 81.8%, which is better than some, but not all, single models.

```
Model 1: 0.814
Model 2: 0.811
Model 3: 0.822
Model 4: 0.822
Model 5: 0.809
Equal Weights Score: 0.818
```

Listing 21.34: Example output of model performance for ensemble members and equally weighted ensemble.

The optimization process is relatively quick. We can see that the process found a set of weights that pays most attention to models 3 and 4, and spreads the remaining attention out among the other models, achieving an accuracy of about 82.4%, out-performing the model averaging ensemble and individual models.

```
Optimized Weights: [0.1660322 0.09652591 0.33991854 0.34540932 0.05211403]
Optimized Weights Score: 0.824
```

Listing 21.35: Example output for model weights and the performance of the weighted average ensemble.

It is important to note that in these examples, we have treated the test dataset as though it were a validation dataset. This was done to keep the examples focused and technically simpler. In practice, the choice and tuning of the weights for the ensemble would be chosen by a validation dataset, and single models, model averaging ensembles, and weighted ensembles would be compared on a separate test set.

# 21.3 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

+   - **Parallelize Grid Search**. Update the grid search example to use the Joblib library to parallelize weight evaluation.
+   - **Implement Random Search**. Update the grid search example to use a random search of weight coefficients.
+   - **Try a Local Search**. Try a local search procedure provided by the SciPy library instead of the global search and compare performance.
+   - **Repeat Global Optimization**. Repeat the global optimization procedure multiple times for a given set of models to see if differing sets of weights can be found across the runs.

If you explore any of these extensions, I’d love to know.

# 21.4 Further Reading

This section provides more resources on the topic if you are looking to go deeper.