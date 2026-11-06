
The shrinkage parameter, ![Figure 1.1 Some JMP Help Options](Images/Image8671.png)(0<![Figure 1.1 Some JMP Help Options](Images/Image884.png)<1) controls the learning rate of the algorithm. Friedman (2001) found that small values (![Figure 1.1 Some JMP Help Options](Images/Image884.png)) lead to better generalization.

In regression trees with interval targets and least-square loss criterion, the “pseudo” residual, ![Figure 1.1 Some JMP Help Options](Images/Image895.png), and the “guess,” ![Figure 1.1 Some JMP Help Options](Images/Image910.png), are defined as follows:

![Figure 1.1 Some JMP Help Options](Images/Image8231.png)\=![Figure 1.1 Some JMP Help Options](Images/Image830.png)\- ![Figure 1.1 Some JMP Help Options](Images/Image837.png)

![Figure 1.1 Some JMP Help Options](Images/Image8131.png)\= ![Figure 1.1 Some JMP Help Options](Images/Image947.png)

In classification trees with a binary target (![Figure 1.1 Some JMP Help Options](Images/Image9551.png)) and binomial log-likelihood loss criterion, the “pseudo” residuals and ![Figure 1.1 Some JMP Help Options](Images/Image8131.png)are

![Figure 1.1 Some JMP Help Options](Images/Image970.png)\=![Figure 1.1 Some JMP Help Options](Images/Image9791.png)

![Figure 1.1 Some JMP Help Options](Images/Image990.png).

The binary target predictions from the final approximation ![Figure 1.1 Some JMP Help Options](Images/Image10031.png)can be transformed to yield probability estimates.

![Figure 1.1 Some JMP Help Options](Images/GrBooEq2.jpg), ![Figure 1.1 Some JMP Help Options](Images/GrBooEq2-2.jpg)

Friedman (2002) showed that accuracy and speed can be improved by sub-sampling training data randomly (without replacement) at each iteration leading to the stochastic gradient boosting algorithm.

Gradient boosting trains a sequence of trees over multiple iterations similar to boosting. The main difference is that it minimizes a stochastic gradient descent function when oversampling to reduce the residuals of the model.

SAS Visual Data Mining and Machine Learning creates a series of trees, which form a single model. A tree in the series is fit to the residuals of the prediction from the earlier trees in the series. The residual is defined in terms of the derivative of a loss function. For squared error on an interval target, ![Figure 1.1 Some JMP Help Options](Images/Image10261.png). Each time that the data are used to grow a tree, the accuracy of the tree is computed. Successive samples are adjusted to accommodate previous inaccuracies. Each successive sample is weighted per the accuracy of the previous models. (See the SAS Visual Data Mining and Machine Learning documentation for more details.)

## Model Studio: Autotuning Gradient Boosting Parameters

Autotuning searches for the best combination of the gradient boosting parameters. Performing autotuning can substantially increase run time. Autotuning runs based on the following options in Figure 8.8, which limit the search of all possible combinations in terms of the gradient boosting parameters. Figure 8.8: Autotuning Options ![Figure 1.1 Some JMP Help Options](Images/Image1104.png)

### Regularization and Learning Parameters

L1 Regularization penalizes the absolute value for the weights. Different values for L1 are tried between the range defined by From and To. The default initial value for L1 is 0. The default for the range is from 0 to 10. L2 Regularization penalizes the square value for the weights. Different values for L2 are tried between the range established by From and To. The default initial value for L2 is 0. The default for the range is from 0 to 10. Learning Rate controls the size of the weight changes. It ranges from 0 (exclusive) to 1. The default initial value is 0.1. The default initial value for the learning rate is 0.1. The default for the range is from 0.01 to 1. Number of Inputs per Split specifies the number of inputs evaluated per split. The default value is 100. The default range is from 1 to100. Number of Iterations specifies the number of iterations of a boosting series. The default initial value is 100. The range is from 20 to 150. Subsample Rate specifies the subsample rate. The default initial value is 0.5. The default range is from 0.1 to 1.

### Search Options

Search Options specifies the options for autotuning searching. The following options are available: ● Bayesian uses priors to seed the iterative optimization. ● Genetic algorithm uses an initial Latin hypercube sample that seeds a genetic algorithm. The genetic algorithm generates a new population of alternative configurations at each iteration. ● Grid uses the lower bound, upper bound, and midrange values for each autotuned parameter, and the initial value (or values) is used as the baseline model. ● Latin hypercube sample performs an optimized grid search that is uniform in each tuning parameter, but random in combinations. ● Random generates a single sample of purely random configurations. Number of evaluations per iteration specifies the number of tuning evaluations in one iteration. This option is available only if the Search method is Genetic algorithm or Bayesian. The default value is 10. It ranges from 2 to 2,147,483,647. Maximum number of evaluations specifies the maximum number of tuning evaluations. This option is available only if the Search method is Genetic algorithm or Bayesian. The default value is 50. It ranges from 3 to 2,147,483,647. Maximum number of iterations specifies the maximum number of tuning iterations. This option is available only if the Search method is Genetic algorithm or Bayesian. The default value is 5. It ranges from 1 to 2,147,483,647. Sample size specifies the sample size. This option is available only if the Search method is Random or Latin hypercube sample. The default value is 50. It ranges from 2 to 2,147,483,647. There are some general options associated with the autotuning search.

### Validation and Objective Options

Validation method specifies the validation method for finding the objective value. If your data are partitioned, then that partition is used. Validation method, Validation data proportion, and Cross validation number of folds are all ignored. ● Partition specifies using the partition validation method. With partition, you specify proportions to use for randomly assigning observations to each role. ◦ Validation data proportion specifies the proportion of data to be used for the Partition validation method. The default value is 0.3. ● K-fold cross validation specifies using the cross validation method. In cross validation, each model evaluation requires k training executions (on k-1 data folds) and k scoring executions (on one holdout fold). This increases the evaluation time by approximately a factor of k. ◦ Cross validation number of folds specifies the number of partition folds in the cross validation process (the k defined above). Possible values range from 2 to 20. The default value is 5. Nominal target objective function specifies the objective function to optimize for tuning parameters for a nominal target. Possible values are average squared error, area under the curve, F1 score, F0.5 score, gamma, Gini coefficient, Kolmogorov-Smirnov statistic, multi-class log loss, misclassification rate, root average squared error, and Tau. The default value is misclassification rate. Interval target objective function specifies the objective function to optimize for tuning parameters for an interval target. Possible values are average squared error, mean absolute error, mean square logarithmic error, root average squared error, root mean absolute error, and root mean square logarithmic error. The default value is average squared error. Maximum time (minutes) specifies the maximum time in minutes for the optimization tuner. Maximum training time for single model (in minutes) specifies the maximum time in minutes for a single model to train. If left blank (the default), there is no maximum time.

![Figure 1.1 Some JMP Help Options](Images/Image733.png) Demo 8.1: Building a Gradient Boosting Model
