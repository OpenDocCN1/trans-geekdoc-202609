
# Autotuning Feature in SAS Visual Data Mining and Machine Learning

## Overview and Invocation

When the `Autotune` feature is used, `SAS Visual Data Mining and Machine Learning` returns the optimal number of units for each hidden layer. `Autotuning` is invoked by selecting the `Performing Autotuning` property on the `Options` tab in the `Neural Network` node. `Autotuning` is available only when the number of hidden layers is less than six.

The `Autotuning` statement activates the tuning optimization algorithm, which searches for the best hidden layers and regularization parameters based on the problem and specified options. If the algorithm used to train the neural network is based on the `Stochastic Gradient Descent`, the `Autotune` feature also searches for the best values of the learning rate and annealing rate.

In addition, the `Autotune` feature searches for the best hyperparameter values for the following:
- `Number of hidden layers`
- `Number of neurons`
- `L1 and L2 regularizations`
- `Learning rate`
- `Annealing rate`
- `Search method` — `Bayesian`, `Genetic algorithm`, `Grid`, `Latin hypercube sample`, `Random`
- `Validation method` — `Partition`, `Cross validation`
- `Objective function` (class and interval targets)

You can also define the search method for the hyperparameters, as `Bayesian`, `Genetic algorithm`, `Latin hypercube sample`, or `Random sample`. The `genetic algorithm` method uses an initial `Latin hypercube sample` that seeds a genetic algorithm to generate a new population of alternative configurations at each iteration. The `Latin Hypercube` method performs an optimized grid search that is uniform in each tuning parameter, but random in combinations. The `Random` method generates a single sample of purely random configurations. The `Bayesian` method uses priors to seed the iterative optimization.

You can specify the number of tuning evaluations in one iteration. This option is available only if the `Search method` is `Genetic algorithm` or `Bayesian`. Similarly, you can specify the maximum number of tuning evaluations and the maximum number of tuning iterations. For the search method, `Random` or `Latin hypercube` is also possible to specify a sample size.

## Validation and Search Control

Finally, you can specify the validation method for finding the objective value, including partition and cross validation — including the proportion of the validation data set and the number of folds for cross validation — and the objective function, depending on the level of the target variable. `Autotuning` searches for the best combination of the neural network parameters. Performing autotuning can substantially increase run time. It runs based on some options, which limit the search of all possible combinations in terms of the neural network parameters.

## Parameter Specifications

### `Number of Hidden Layers`
Specifies whether to autotune the number of hidden layers. It ranges from 1 to 5. The default initial value is 1. The default range is from 0 to 2.

### `Number of Neurons`
Specifies whether to autotune the number of neurons. It ranges from 1 to 1000. The default initial value is 1. The default range is from 1 to 100.

### `L1 Weight Decay`
Specifies whether to autotune the `L1` weight decay parameter. It penalizes the absolute value for the weights. Different values of `L1` are tried between the range defined by `From` and `To`. The default initial value for the `L1` is 0. The default range is from 0 to 10.

### `L2 Weight Decay`
Specifies whether to autotune the `L2` weight decay parameter. It penalizes the square value for the weights. Different values of `L2` are tried between the range established by `From` and `To`. The default initial value for the `L2` is 0. The default range is from 0 to 10.

### `Learning Rate`
Specifies whether to autotune the learning rate for the hidden layers. It controls the size of the weight changes. It ranges from 0 (exclusive) to 1. The default initial value is 0.1. The default initial value for the learning rate is 0.1. The default for the range is from 0.01 to 1. It works just for the `SGD` algorithm.

### `Annealing Rate`
Specifies whether to autotune the annealing rate for the hidden layers. It automatically reduces the learning rate as `SGD` progresses. The default initial value is 0.001. The default range is from 0.000001 to 0.1. It works just for the `SGD` algorithm.

### `Search Options`
Specifies the options for autotuning searching. The following options are available:
- `Bayesian` uses priors to seed the iterative optimization.
- `Genetic algorithm` uses an initial `Latin hypercube sample` that seeds a genetic algorithm. The genetic algorithm generates a new population of alternative configurations at each iteration.
- `Grid` uses the lower bound, upper bound, and midrange values for each autotuned parameter, with the initial value (or values) used as the baseline model.
- `Latin hypercube sample` performs an optimized grid search that is uniform in each tuning parameter, but random in combinations.
- `Random` generates a single sample of purely random configurations.

### `Number of evaluations per iteration`
Specifies the number of tuning evaluations in one iteration. This option is available only if the `Search method` is `Genetic algorithm` or `Bayesian`. The default value is 10. It ranges from 2 to 2,147,483,647.

### `Maximum number of evaluations`
Specifies the maximum number of tuning evaluations. This option is available only if the `Search method` is `Genetic algorithm` or `Bayesian`. The default value is 50. It ranges from 3 to 2,147,483,647.

### `Maximum number of iterations`
Specifies the maximum number of tuning iterations. This option is available only if the `Search method` is `Genetic algorithm` or `Bayesian`. The default value is 5. It ranges from 1 to 2,147,483,647.

### `Sample size`
Specifies the sample size. This option is available only if the `Search method` is `Random` or `Latin Hypercube sample`. The default value is 50. It ranges from 2 to 2,147,483,647.

There are some general options associated with the autotuning search.

### `Validation method`
Specifies the validation method for finding the objective value. If your data is partitioned, then that partition is used. `Validation method`, `Validation data proportion`, and `Cross validation number of folds` are all ignored.
- `Partition` specifies using the partition validation method. With partition, you specify proportions to use for randomly assigning observations to each role.
  - `Validation data proportion` specifies the proportion of data to be used for the `Partition` validation method. The default value is 0.3.
- `K-fold cross validation` specifies using the cross validation method. In cross validation, each model evaluation requires k training executions (on k-1 data folds) and k scoring executions (on one holdout fold). This increases the evaluation time by approximately a factor of k.
  - `Cross validation number of folds` specifies the number of partition folds in the cross validation process (the k defined above). Possible values range from 2 to 20. The default value is 5.

### Objective Functions

#### `Nominal target objective function`
Specifies the objective function to optimize for tuning parameters for a nominal target. Possible values are average squared error, area under the curve, F1 score, F0.5 score, gamma, Gini coefficient, Kolmogorov-Smirnov statistic, multi-class log loss, misclassification rate, root average squared error, and Tau. The default value is misclassification rate.

#### `Interval target objective function`
Specifies the objective function to optimize for tuning parameters for an interval target. Possible values are average squared error, mean absolute error, mean squared logarithmic error, root average squared error, root mean absolute error, and root mean squared logarithmic error. The default value is average squared error.

### Time Limits

`Maximum time (minutes)` specifies the maximum time in minutes for the optimization tuner.

`Maximum training time for single model (in minutes)` specifies the maximum time in minutes for a single model to train. If left blank (the default), there is no maximum time.

## Figure and Demo

![Figure 1.1 Some JMP Help Options](`Images/Image733.png`)

Demo 10.1: Improving a Neural Network Model by Changing the Network Learning and Optimization Parameters
