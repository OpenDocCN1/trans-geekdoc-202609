# ## Crossover functions

Crossover functions define the algorithm used for reproduction – taking two input solutions and mixing them in such a way as to produce a “child”, representing a new valid solution.

There are a variety of common algorithms to do this, but each needs to be considered in the context of the problem. Any approach will likely need to be tweaked to ensure the “child” created through the process is valid for the scenario.

![](bbox=[0.11, 0.19, 0.5, 0.33])

Two common methods are the one-point crossover and the two-point crossover.

One-point crossover selects a random point in the gene sequence to slice the data. The data from up until the slice point is copied from parent 1 into child 1, and then the rest of child 1’s data comes from parent 2. The inverse can also occur at the same time to create a second child.

Two-point crossover works in a similar manner, except two slice points are selected.

![](bbox=[0.11, 0.35, 0.5, 0.49])

There are other commonly used methods as well, but what matters most is that you are using a randomization function to create offspring that are a mix of the data from two parents.

> > **Top tip!** Choose appropriate genetic operators (selection, crossover, mutation) for your problem, and ensure diversity within the population to avoid premature convergence.

# ## Example: Travelling salesperson

![](bbox=[0.11, 0.54, 0.89, 0.79])

# ### Travelling salesperson – random route

# ### Travelling salesperson – optimized route

Consider the charts to represent a map of 50 cities that a travelling salesperson wishes to visit, with two possible routes for the journey. Clearly, the randomized journey is inefficient, whereas the optimized journey is a lot more efficient.