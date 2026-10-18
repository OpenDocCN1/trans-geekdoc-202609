
Instead, we can employ a technique called random search. Rather than trying every possible combination of parameters, random search proceeds as follows:

1. Randomly select a combination of hyperparameter values
2. Use cross-validation to train and evaluate a model using those hyperparameter values
3. Record the performance metric of the model (usually mean misclassification error for classification tasks)
4. Repeat (iterate) steps 1 to 3 as many times as your computational budget allows
5. Select the combination of hyperparameter values that gave you the best-performing model

Unlike grid search, random search isn’t guaranteed to find the best set of hyperparameter values. However, with enough iterations, it can usually find a good combination that performs well. By using random search, we can run 500 combinations of hyperparameter values, instead of all 120,000 combinations.

Let's define our random search using the `makeTuneControlRandom()` function. We tell the function how many iterations of the random search procedure we want to use, with the `maxit` argument. You should try to set this as high as your computational budget allows, but in this example we’ll stick to 20 to prevent the example from taking too long. Next, I describe our cross-validation procedure. Remember I said in chapter 3 that I prefer k-fold cross-validation unless the process is computationally expensive? Well this is computationally expensive, so I’m compromising by using hold-out cross-validation instead.

### Listing 6.11 Defining the random search

```
randSearch <- makeTuneControlRandom(maxit = 20)
cvForTuning <- makeResampleDesc("Holdout", split = 2/3)
```

There’s something else we can do to speed up this process. R, as a language, doesn’t make that much use of multi-threading (using multiple CPUs simultaneously to accomplish a task). However, one of the benefits of the mlr package is that it allows multi-threading to be used with its functions. This helps you use multiple cores/CPUs on your computer to accomplish tasks such as hyperparameter tuning and cross-validation, much more quickly. If you don’t know how many cores your computer has, you can find out in R by running `parallel::detectCores()`.

If your computer only has one core: the 90s called. They want their computer back.

To run an mlr process in parallel, we place its code between the `parallelStartSocket()` and `parallelStop()` functions from the parallelMap package. To start our hyperparameter tuning process, we call the `tuneParams()` function and supply as arguments:

- the first argument is the name of the learner
- `task` = the name of our task
- `resampling` = our cross validation procedure (defined in code listing 6.11)
- `par.set` = our hyperparameter space (defined in code listing 6.10)
- `control` = the search procedure (random search, defined in code listing 6.11)

> **WARNING** The computer I'm writing this on has four cores and the code below takes nearly a minute to run on it. It is of the utmost importance that you go make a cup of tea while it runs. Milk and no sugar, please.

```
library(parallelMap)
library(parallel)

parallelStartSocket(cpus = detectCores())

tunedSvmPars <- tuneParams("classif.svm", task = spamTask,
resampling = cvForTuning,
par.set = svmParamSpace,
control = randSearch)

parallelStop()
```

> **TIP** The degree hyperparameter only applies to the polynomial kernel function, and the gamma hyperparameter doesn't apply to the linear kernel. Does this create errors when the random search selects combinations that don't make sense? Nope. If the random search selects the sigmoid kernel, for example, it simply ignores the value of the degree hyperparameter.

Welcome back after our interlude! You can print the best-performing hyperparameter values and the performance of the model built with them by calling `tunedSvmPars`, or extract just the named values themselves (so you can train a new model using them) by calling `tunedSvmPars$x`. Looking at code listing 6.13, we can see that the 1st degree polynomial kernel function (equivalent to the linear kernel function), with a cost of 5.82 and gamma of 1.56, gave the best-performing model.

```
tunedSvmPars
tune result:
Op. pars: kernel=polynomial; degree=1; cost=5.82; gamma=1.56
mmce.test.mean=0.0645372
tunedSvmPars$x
$kernel
[1] "polynomial"
$degree
[1] 1
$cost
[1] 5.816232
$gamma
[1] 1.561584
```

> **IMPORTANT** Are your values different to mine? They probably are! This is the nature of the random search. It may find different winning combinations of hyperparameter values each time it's run. To reduce this variance, we should commit to increasing the number of iterations it makes.

Now we've tuned our hyperparameters, let's build our model using the best-performing combination. Recall from chapter 3 that we use the `setHyperPars()` function to combine a learner with a set of pre-defined hyperparameter values. The first argument is the learner we want to use, and the `par.vals` argument is the object containing our tuned hyperparameter values. We then train a model using our `tunedSvm` learner with the `train()` function.

```
tunedSvm <- setHyperPars(makeLearner("classif.svm"),
    par.vals = tunedSvmPars$x)
tunedSvmModel <- train(tunedSvm, spamTask)
```

> **TIP** As we already defined our learner in code listing 6.8, we could simply have run `setHyperPars(svm, par.vals = tunedSvmPars$x)` to achieve the same result.

You've built your model using tuned hyperparameters. In this section you'll cross-validate your model to estimate how it will perform on new, unseen data.

Recall from chapter 3 that it’s important to cross-validate *the entire model building process*. This means that any *data-dependent* steps in your model building process (such as hyperparameter tuning), need to be included in your cross-validation. If you don’t include them, your cross-validation is likely to give you an over-optimistic estimate (a *biased* estimate) of how well the model will perform.

> **TIP**
> 
> What counts as a *data-independent* step in model building? Things like removing nonsense variables by hand, changing variable names and types, or replacing a missing value code with `NA`. These steps are data-independent because they would be the same regardless of the values in the data.

Recall also that to include hyperparameter tuning in our cross-validation, we need to use a *wrapper function*, that wraps together our learner and hyperparameter tuning process. The cross-validation process is shown in code listing 6.15.

As mlr will use nested cross-validation (where hyperparameter tuning is performed in the inner loop, and the winning combination of values is passed to the outer loop), we first define our outer cross-validation strategy using the `makeResampleDesc()` function. In this example, I’ve chosen 3-fold cross-validation for the outer loop. For the inner loop, we’ll use the `cvForTuning` resampling description we defined in code listing 6.11 (hold-out cross-validation with a 2/3 split).

Next, we make our wrapped learner using the `makeTuneWrapper()` function. The arguments are:

- the first argument is the name of the learner
- `resampling` = our inner loop cross-validation strategy
- `par.set` = the hyperparameter space we defined in code listing 6.10
- `control` = the search procedure we defined in code listing 6.11

As the cross-validation will take a while, it’s prudent to start parallelization with the `parallelStartSocket()` function. Now to run our nested cross-validation, we call the `resample()` function, where the first argument is our wrapped learner, the second argument is our task, and the third argument is our outer cross-validation strategy.

> **WARNING**
> 
> This takes a little over a minute on my four core computer. In the meantime you know what to do. Milk and no sugar please. Do you have any cake?

### Listing 6.15 Cross-validating the model-building process

```
outer <- makeResampleDesc("CV", iters = 3)

svmWrapper <- makeTuneWrapper("classif.svm", resampling = cvForTuning,
    par.set = svmParamSpace,
    control = randSearch)

parallelStartSocket(cpus = detectCores())
cvWithTuning <- resample(svmWrapper, spamTask, resampling = outer)

parallelStop()
```

Now let’s take a look at the result of our cross-validation procedure by printing the contents of the `cvWithTuning` object.

### Listing 6.16 Extracting the cross-validation result

```
cvWithTuning

Resample Result
Task: spamTask
Learner: classif.svm.tuned
Aggr perf: mmce.test.mean=0.0988956
Runtime: 73.89
```

We’re correctly classifying 1 - 0.099 = 0.901 = 90.1% of emails as spam or not spam. Not bad for a first attempt!

## 6.7 Strengths and weaknesses of the SVM algorithm

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether the SVM algorithm will perform well for your task.

The strengths of the SVM algorithm are:

- It’s very good at learning complex non-linear decision boundaries
- It performs very well on a wide variety of tasks
- It makes no assumptions about the distribution of the predictor variables

The weaknesses of the SVM algorithm are:

- It is one of the most computationally expensive algorithms to train
- It has multiple hyperparameters which need to be tuned simultaneously
- It can only handle continuous predictor variables (although recoding a categorical variable as numeric may help in some cases)
