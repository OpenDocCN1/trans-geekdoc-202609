The resulting plot from code listing 11.18 is shown in figure 11.17. Notice that our elastic net model’s parameter estimates are something of a compromise between those estimated by ridge regression, and those estimated by LASSO. The elastic net model’s parameters are more similar to those estimated by pure LASSO, however, because our tuned value of alpha was close to one (remember that when alpha equals one, we get pure LASSO).

![](bbox=[0.1, 0.4, 0.9, 0.6])

EXERCISE 11.4 Redraw the plot in figure 11.17, but remove the facet_wrap() layer and set the position argument of geom_bar() equal to "stack". Which visualization do you prefer?



Let’s use benchmarking to simultaneously cross-validate and compare the performance of our ridge, LASSO, elastic net and OLS modelling processes. Recall from chapter 7 that benchmarking takes a list of learners, a task, and a cross-validation procedure. Then, for each iteration/fold of the cross validation process, a model is trained using each learner, on the same training set, and evaluated on the same test set. Once the entire cross-validation process is complete, we get the mean performance metric (MSE in this case) for each learner, allowing us to compare which would perform best.

We start by defining tuning wrappers for each learner so we can include hyperparameter tuning inside our cross-validation loop. For each wrapper (one for ridge, LASSO, and elastic net), we