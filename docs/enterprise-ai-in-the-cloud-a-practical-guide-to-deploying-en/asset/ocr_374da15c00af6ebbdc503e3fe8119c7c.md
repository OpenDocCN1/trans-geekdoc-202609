provide the best model.

If you used random search, the system would randomly sample the maximum depth of the tree from a uniform distribution between 1 and 50 and randomly sample the number of trees from a uniform distribution between 100 and 500.

> NOTE While random search will not give the best possible model, it will be faster than the grid search approach.

# Bayesian Search

Bayesian search is a hyperparameter optimization technique well suited to noise or use cases that are more complex for a grid or random search. It is more efficient than grid or random search but can be complex to implement and may need some knowledge of Bayesian statistics.

> TIP Bayesian search can be used for any machine learning model but may not be as effective as a grid or random search for more straightforward objective functions.

The Bayesian search uses Bayesian statistics to find the best hyperparameters and works by building a probabilistic model of the objective function being optimized. It has been successfully used in many applications such as spam filtering and credit card fraud detection.

# MODEL VALIDATION

This section discusses how to validate the models and the metrics that you have to use.

# Choosing the Right Validation Techniques

You will need to validate your model using the validation dataset during the training phase when it is being developed and optimized.