
Just like when we used k-NN for classification, selecting the best performing value of *k* is critical to model performance. If we select a *k* that is too low, we may produce a model that is overfitted and makes predictions with high variance. If we select a *k* that is too high, we may produce a model which is underfit and makes predictions with high bias.

Figure 12.3 How the k-NN algorithm predicts continuous variables. The crosses represent new data for which we wish to predict the journey length. For the one, three, and five-nearest neighbor models, the nearest neighbors to each new datum are highlighted in a lighter shade. In each case, the predicted value is the mean journey length of the nearest neighbors.

## 12.2 Using tree-based learners to predict a continuous variable

In this section, I’ll show you how you can use tree-based algorithms to predict a continuous outcome variable. Back in chapter 7, I showed you how tree-based algorithms (such as the rpart algorithm) split up a feature space into separate regions, one binary split at a time. The algorithm tries to partition the feature space such that each region contains only cases from a particular class. Put another way, the algorithm tries to learn binary splits that result in regions that are as pure as possible.

**NOTE** Remember that the *feature space* refers to all possible combinations of predictor variable values, and that *purity* refers to how homogeneous the cases are within a single region.

To refresh your memory of this, I’ve reproduced figure 4 from chapter 7, showing how a feature space of two predictor variables can be partitioned to predict the membership of three classes.

Figure 12.4 How splitting is performed for classification problems. Cases belonging to three classes are plotted against two continuous variables. The first node splits the feature space into rectangles based on the value of variable 2. The second node further splits the feature space based on the value of variable 1.

Classification with tree-based algorithms is a bit like herding animals into their pens on a farm. It’s quite obvious that we want one pen for the chickens, one for the cows, and one for the alpacas (I don’t think you see many alpacas on farms, but I’m particularly fond of them). So conceptually, it’s quite easy for us to picture splitting regions of the feature space up into different pens for different categories. But perhaps it’s not so easy for us to picture splitting the feature space up to predict a continuous variable.

So how does this partitioning work for regression problems? Well, in exactly the same way actually; the only difference is that instead of each region representing a class, it represents a value of the continuous outcome variable.

Take a look at figure 12.5 where we’re creating a regression tree using our journey length example. The nodes of the regression tree split the feature space (departure time) into distinct regions. Each region represents the mean of the outcome variable of the cases inside it. When making predictions on new data, the model will predict the value of the region the new data falls into. The leaves of the tree are no longer classes, but numbers. This is illustrated for situations with one and two predictor variables in figure 12.5, but extends to any number of predictors.

Figure 12.5 How splitting is performed for regression problems. The feature space is split into shaded regions based on the nodes of the tree next to each plot. The predicted journey length is shown inside each region. The dashed line in the top plot demonstrates how journey length is predicted from departure time based on the tree. The bottom plot shows a two predictor situation.

Just like for classification, regression trees can handle both continuous and categorical predictor variables (with the exception of XGBoost which requires categorical variables to be numerically encoded). The way splits are decided for continuous and categorical variables is the same as for classification trees, except that instead of finding the split that has the highest Gini gain, the algorithm looks for the split with the lowest sum of squares.

**NOTE** Recall from chapter 7 that the Gini gain is the difference between the Gini indices of the parent node and of the split. The Gini index is a measure of impurity, and is equal to `1 - (p(A)^2 + p(B)^2)` where `p(A)` and `p(B)` are the proportions of cases belonging to classes A and B, respectively.

For each candidate split, the algorithm calculates the sum of squared residuals for the left and right split, and adds them together to form the sum of squared residuals for the split as a whole. Take a look at figure 12.5. The algorithm is considering the candidate split of a departure time before 7:45. For each case where the departure time was before 7:45, the algorithm calculates the mean journey length, finds the residual error (the difference between each case’s journey length and the mean), and squares it. The same is done for the cases where the departure time was after 7:45, with their respective mean. These two sum of squared residual values are added together to give the sum of squares for the split. If you prefer to see this in mathematical notation, it’s shown in equation 12.1.

```
SS_split = \sum_{i \in left} (y_i - \hat{y}_{left})^2 + \sum_{i \in right} (y_i - \hat{y}_{right})^2
```

where i left and i right indicate cases belonging to the left and right splits, respectively.

The candidate split with the lowest sum of squares is chosen as the split for any particular point in the tree, so for regression trees, purity refers to how spread the data are around the mean of the node.

Figure 12.6 How candidate splits are chosen for regression problems. The measure of purity is the sum of squares for the split, which is the combined sums of squares for the left and right nodes. Each sum of squares is the vertical distance between each case and the predicted value for the leaf it belongs to.

In this section, I’ll teach you how to define a k-NN learner for regression, tune the k hyperparameter, and train a model so you can use it to predict a continuous variable.

Imagine you’re a chemical engineer, trying to predict the amount of heat released by various batches of fuel-based measurements you made on each batch. We’re first going to train a k-NN model on this task, and then compare how it performs to a random forest and XGBoost model, later in the chapter.

Let’s start by loading the mlr and tidyverse packages.

```
library(mlr)

library(tidyverse);
```

## 12.3.1 Loading and exploring the fuel dataset

The mlr package, conveniently, comes with several pre-defined tasks to help you experiment with different learners and processes. The dataset we’re going to work with in this chapter is contained inside mlr’s `fuelsubset.task`. We load this task into our R session the same way we would any built-in dataset: using the `data()` function. We can then use mlr’s `getTaskData()` function to extract the data from the task, so we can explore it. As always, I used the `as_tibble()` function to convert the data frame into a tibble.

We have a tibble containing 129 different batches of fuel, and 367 variables/features! In fact, there are so many variables that I’ve truncated the printout of the tibble to remove the names of the variables that didn’t fit inside my console.

> **TIP**  Run `names(fuelTib)` to return the names of all the variables in the dataset. This is useful when working with large datasets with too many columns to visualize in the console.

The *heat* variable is the amount of energy released by a certain quantity of fuel when it is combusted (measured in mega joules). The *h20* variable is the percentage humidity in the fuel’s container. The remaining variables show how much ultraviolet or near-infrared light of a particular wavelength each batch of fuel absorbs (each variable represents a different wavelength).

> **TIP**  To see all the tasks that come built into mlr, use `data(package = "mlr")`.
