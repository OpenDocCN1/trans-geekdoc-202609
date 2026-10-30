# Method:

Next, we will specify the search strategy from the grid, random search, and bayes:

It iterates over all the possible combinations to find the parameter values.

It chooses the random sets of values.

It uses a gaussian process to model our function and then chooses the parameters which will optimize the probability of improvement into our model. It is also called *Bayesian*

# Parameters:

Next, check out the following links for the parameter’s description:

https://lightgbm.readthedocs.io/en/latest/Parameters.html

The last code line from the preceding **sweep_id** will store the project name and configuration setup which we will be providing during LightGBM Model Training.

# Prepare Data for LightGBM: