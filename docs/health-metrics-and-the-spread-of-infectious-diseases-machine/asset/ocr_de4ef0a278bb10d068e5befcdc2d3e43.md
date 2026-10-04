# The Steps of Building a Model

Here we use the ode(y) function from the {deSolve} package for solving the differential equations in the SEIR model function that we created.

```
output <- deSolve:ode(y = initial_state,
             times = times,
             func = SEIR,
             parms = c(beta = beta,
                      sigma = sigma,
                      gamma = gamma))
```

The output is class "deSolve", "matrix":
class(output)
# [1] "deSolve" "matrix"

So, it needs to be converted to a dataframe of time, susceptible, exposed, and infected. All simulated values in 100 days of an epidemic.
simulated_data <- as.data.frame(output)

```
head(simulated_data)
# time S E I R
# 1 0.999000 1.000000 0.000000 0.000000 0.000000
# 2 1.998567 0.918661 0.093247 0.002385 0.023846
# 3 2.998452 0.869953 0.175673 0.009150 0.145043
# 4 3.998812 0.848381 0.257051 0.012108 0.198289
# 5 4.997594 0.849639 0.321100 0.033411 0.384118
# 6 5.996890 0.869986 0.381543 0.051999 0.799977
```

This plot shows the simulated data of the SEIR model, with the number of susceptible, exposed, and recovered individuals decreases over time as they become exposed and infected, while the number of exposed and infectious individuals increases before eventually decreasing as individuals recover from the infection.

```
# Plot simulated data
gplot(simulated_data
```

# 6.3.2 Random Forest

The next step is to calibrate this model by using a machine learning algorithm. A random forest is a type of model that uses an algorithm called ensemble learning to build multiple decision trees and combine their predictions to make accurate predictions. It works by splitting the data into subsets and building a decision tree for each subset. The final prediction is made by aggregating the predictions of all decision trees. Unlike mechanistic