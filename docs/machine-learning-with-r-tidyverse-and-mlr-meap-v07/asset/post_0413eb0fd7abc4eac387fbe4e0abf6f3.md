
First, I define my search method using the `makeFeatSelControlSequential()` function (wow, the mlr authors really do love their long function names). I use "sfbs" as the method argument to use a sequential floating backward selection. Then, I use the `selectFeatures()` function to perform the feature selection. To this function I supply the learner, task, cross-validation strategy we defined in code listing 9.9, and the search method. It’s as easy as that. When we run the function, every permutation of predictor variables is cross-validated using our `kFold` strategy to get an estimate of its performance. By printing the result of this process, we can see the algorithm selected six predictors that had a slightly lower MSE value than the predictors selected by our filter method in code listing 9.9.

> To see all of the available wrapper methods and how to use them, run `?FeatSelControl`.

Now I need to warn you about a frustrating bug with regards to the sequential floating forward search. As of writing this book, using "sffs" as the feature selection method will throw this error in some circumstances: `Error in sum(x) : invalid 'type' (list) of argument`. If you try to use "sffs" as the search method in our example, you may get such an error. Therefore, while this is very frustrating, I’ve opted to use sequential floating backward search ("sfbs" instead).

```
featSelControl <- makeFeatSelControlSequential(method = "sfbs")
selFeats <- selectFeatures(learner = lin, task = ozoneTask,
resampling = kFold, control = featSelControl)
selFeats
Feature result:
Features (6): Month, Press_height, Humid, Temp_Sand, Temp_Monte, Inv_height
mse.test.mean=20.4038
```

Now, just like we did for the filter method, we can create a new task using the imputed data that contains only those selected predictors, and train a model on it.

```
ozoneSelFeat <- ozoneImp$data[, c("Ozone", selFeats$x)]
ozoneSelFeatTask <- makeRegrTask(data = ozoneSelFeat, target = "Ozone")
wrapperModel <- train(lin, ozoneSelFeatTask)
```

## 9.2.4 Including imputation and feature selection in our cross-validation

I’ve said it many times before but I’m going to say it again: include all data-dependent preprocessing steps in your cross-validation! But up to this point we’ve only needed to consider a single preprocessing step. How do we combine more than one together? Well, mlr makes this process extremely simple for us. When we wrap together a learner and a preprocessing step, we have essentially created a new learner algorithm that includes that preprocessing. So to include an additional preprocessing step, we simply wrap the wrapped learner! I’ve illustrated this for our example in figure 9.9. This results in a sort of Matryoshka doll of wrappers, where one is encapsulated by another, which is encapsulated by another etc.

![](img/a22105d68c35e8d5bd3c7bafb4644881_241_0.png)

Using this strategy we can combine as many preprocessing steps as we like to create a pipeline. The innermost wrapper will always be used first, and then the next innermost and so on.

> **NOTE** As the innermost wrapper is used first, through to the outermost, it’s important to think carefully about the order you wish the preprocessing steps to take!

Let’s reinforce this in your mind by actually doing it. We’re going to make an impute wrapper, then pass that as the learner to a feature selection wrapper. First I redefine our imputation method using the `imputeLearner()` function (we first defined this in code listing 9.4). Then I create an imputation wrapper using the `makeImputeWrapper()` function, which takes the learner as the first argument. I use `list(numeric = imputeMethod)` as the classes argument to apply this imputation strategy to all my numeric predictors (all of them, duh).

Now here comes the neat bit: I create a feature selection wrapper (using `makeFeatSelWrapper()`), and supply the imputation wrapper we created as the learner. This is the crucial step because we’re creating a wrapper with another wrapper! I set the cross-validation method as `kFold` (defined in code listing 9.9), and the method of searching feature combinations as `featSelControl` (defined in code listing 9.11).

### Listing 9.13 Combining imputation and feature selection wrappers

```
imputeMethod <- imputeLearner("regr.rpart")

imputeWrapper <- makeImputeWrapper(lin,
                                   classes = list(numeric = imputeMethod))

featSelWrapper <- makeFeatSelWrapper(learner = imputeWrapper,
                                     resampling = kFold,
                                     control = featSelControl)
```

Now, let’s cross-validate our entire model-building process like good data scientists. After loading our good friends the parallel and parallelMap packages, I define a task using the ozoneClean tibble, which still contains missing data. Next, I define an ordinary 3-fold cross-validation strategy for our cross-validation procedure. Finally, I start parallelization with `parallelStartSocket()`, and start the cross-validation procedure by supplying the learner (the wrapped wrapper), task, and cross-validation strategy to the `resample()` function. This took nearly 90 seconds on my four-core machine, so I suggest you start the process, and then read on for a summary of what the code is doing.

### Listing 9.14 Cross-validating the model building process

```
library(parallel)
library(parallelMap)

ozoneTaskWithNAs <- makeRegrTask(data = ozoneClean, target = "Ozone")

kFold3 <- makeResampleDesc("CV", iters = 3)

parallelStartSocket(cpus = detectCores())

lmCV <- resample(featSelWrapper, ozoneTaskWithNAs, resampling = kFold3)

parallelStop()

lmCV

Resample Result
Task: ozoneClean
Learner: regr.lm.imputed.featsel
Aggr perf: mse.test.mean=20.5394
Runtime: 86.7071
```

The cross-validation process proceeds like this:

- 1. split the data into three-folds
- 2. for each fold:
  - A. use the rpart algorithm to impute the missing values
  - B. perform feature selection:
    - i. use a selection method (such as backward search) to select combinations of features to train models on
    - ii. use 10-fold cross-validation to evaluate the performance of each model
- 3. return the best performing model for each of the three outer folds
- 4. return the mean MSE to give us our estimate of performance

So we can see our model building process gives us a mean MSE of 20.54, suggesting a mean residual error of 4.53 on the original Ozone scale (taking the square root of 20.54).

## 9.2.5 Interpreting the model

Due to their simple structure, linear models are usually quite simple to interpret, because we can look at the slopes for each predictor to infer how much the outcome variable is affected by each. However, whether these interpretations are justified or not depends on whether some model assumptions have been met, so in this section I’ll show you how to interpret the model output and generate some diagnostic plots.

First, we need to extract the model information from our model object using the `getLearnerModel()` function. By calling `summary()` on the model data, we get an output with lots of information about our model. Take a look at code listing 9.15.

The "Call" component would normally tell us the formula we used to create the model (which variables and whether we added more complex relationships between them). As we built this model using mlr we, sadly, don’t get that information here, but the model formula here is all of the selected predictors, combined linearly together.

The "Residuals" component gives us some summary statistics about the model residuals. Here I’m looking to see if the median is approximately zero, and that the first and third quartiles are approximately the same. If they aren’t, this might suggest the residuals are either not normally distributed, or heteroscedastic. In both situations, not only could this negatively impact model performance, it could make our interpretation of the slopes incorrect.

The "Coefficients" component shows us a table of model parameters and their standard errors. The intercept is 41.8, which is the estimate of Ozone level when all other variables are zero. In this particular case it doesn’t really make sense for some of our variables to be zero (month, for example) so we won’t put too much interpretation into this. The estimates for the predictors are their slopes. For example, our model estimates that for a one-unit increase in the Temp_Sand variable, Ozone increases by 0.227 (holding all other variables constant). The "Pr(>|t|)" column contains the *p* values that, in theory, represent the probability of seeing a slope this large, if the population slope was actually zero. Use the *p* values to guide your model-building process by all means, but there are some problems associated with *p* values, so don’t put too much faith in them.

Finally, the "Residual standard error" is the same as RMSE, the Multiple *R*-squared is an
