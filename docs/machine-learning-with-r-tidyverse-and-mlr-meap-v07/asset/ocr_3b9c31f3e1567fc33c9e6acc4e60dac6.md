Instead, we can employ a technique called random search. Rather than trying every possible combination of parameters, random search proceeds as follows:

+   1. Randomly select a combination of hyperparameter values
+   2. Use cross-validation to train and evaluate a model using those hyperparameter values
+   3. Record the performance metric of the model (usually mean misclassification error for classification tasks)
+   4. Repeat (iterate) steps 1 to 3 as many times as your computational budget allows
+   5. Select the combination of hyperparameter values that gave you the best-performing model

Unlike grid search, random search isn’t guaranteed to find the best set of hyperparameter values. However, with enough iterations, it can usually find a good combination that performs well. By using random search, we can run 500 combinations of hyperparameter values, instead of all 120,000 combinations.

Let's define our random search using the makeTuneControlRandom() function. We tell the function how many iterations of the random search procedure we want to use, with the maxit argument. You should try to set this as high as your computational budget allows, but in this example we’ll stick to 20 to prevent the example from taking too long. Next, I describe our cross-validation procedure. Remember I said in chapter 3 that I prefer k-fold cross-validation unless the process is computationally expensive? Well this is computationally expensive, so I’m compromising by using hold-out cross-validation instead.

# Listing 6.11 Defining the random search

```
randSearch <- makeTuneControlRandom(maxit = 20)
cvForTuning <- makeResampleDesc("Holdout", split = 2/3)
```



There’s something else we can do to speed up this process. R, as a language, doesn’t make that much use of multi-threading (using multiple CPUs simultaneously to accomplish a task). However, one of the benefits of the mlr package is that it allows multi-threading to be used with its functions. This helps you use multiple cores/CPUs on your computer to accomplish tasks such as hyperparameter tuning and cross-validation, much more quickly. If you don’t know how many cores your computer has, you can find out in R by running parallel::detectCores().



If your computer only has one core: the 90s called. They want their computer back.

To run an mlr process in parallel, we place its code between the parallelStartSocket() and parallelStop() functions from the parallelMap package. To start our hyperparameter tuning