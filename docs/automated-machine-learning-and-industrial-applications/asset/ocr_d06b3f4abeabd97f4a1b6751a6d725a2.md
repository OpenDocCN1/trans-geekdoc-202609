In Equation 14.1 γ, the discount factor and output action Q represent the expected reward of taking a certain action at a time (t + i) and following the optimal policy afterward. The key steps in the RL pipeline include specifying the reward function, selecting observations, and tuning hyperparameters. Automating RL involves updating hyperparameters and functions based on feedback from the environment [59].

c) Bayesian Optimization: Bayesian optimization (BO) addresses optimization challenges like high dimensionality. It provisions point-wise evaluations without function derivatives making it a black-box method [60]. BO does not require prior information; it starts with a randomized population and selects promising candidates to construct a Bayesian network. New candidates are generated using joint distribution encoding and added to the population.

+   BO uses the following two main approaches:
+   - Gaussian Process (GP): Models uncertainty and forecast mean for any input point [61].
+   - Acquisition Function (AF): Determines the next best point to evaluate based on GP’s uncertainty and mean [62].

d) Gradient-Based Optimization: This method adjusts parameters by moving in the direction of the gradient. The step size is determined by the learning rate.

Gradient Descent: Minimizes an objective function by affecting in the way of the negative gradient. It starts with an initial guess and iteratively finds a local minimum [63].

![](bbox=[0.25, 0.655, 0.8, 0.835])

Figure 14.3 Gradient descent stuck in local minimum.