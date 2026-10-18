Recall from chapter 3 that it’s important to cross-validate *the entire model building process*. This means that any *data-dependent* steps in your model building process (such as hyperparameter tuning), need to be included in your cross-validation. If you don’t include them, your cross-validation is likely to give you an over-optimistic estimate (a *biased* estimate) of how well the model will perform.

> **TIP**
> 
> What counts as a *data-independent* step in model building? Things like removing nonsense variables by hand, changing variable names and types, or replacing a missing value code with `NA`. These steps are data-independent because they would be the same regardless of the values in the data.

Recall also that to include hyperparameter tuning in our cross-validation, we need to use a *wrapper function*, that wraps together our learner and hyperparameter tuning process. The cross-validation process is shown in code listing 6.15.

As mlr will use nested cross-validation (where hyperparameter tuning is performed in the inner loop, and the winning combination of values is passed to the outer loop), we first define our outer cross-validation strategy using the `makeResampleDesc()` function. In this example, I’ve chosen 3-fold cross-validation for the outer loop. For the inner loop, we’ll use the `cvForTuning` resampling description we defined in code listing 6.11 (hold-out cross-validation with a 2/3 split).

Next, we make our wrapped learner using the `makeTuneWrapper()` function. The arguments are:

+   - the first argument is the name of the learner
+   - `resampling` = our inner loop cross-validation strategy
+   - `par.set` = the hyperparameter space we defined in code listing 6.10
+   - `control` = the search procedure we defined in code listing 6.11

As the cross-validation will take a while, it’s prudent to start parallelization with the `parallelStartSocket()` function. Now to run our nested cross-validation, we call the `resample()` function, where the first argument is our wrapped learner, the second argument is our task, and the third argument is our outer cross-validation strategy.

> **WARNING**
> 
> This takes a little over a minute on my four core computer. In the meantime you know what to do. Milk and no sugar please. Do you have any cake?