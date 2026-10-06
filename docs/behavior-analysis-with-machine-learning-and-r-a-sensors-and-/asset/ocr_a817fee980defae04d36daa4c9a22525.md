# CHAPTER 3. PREDICTING BEHAVIOR WITH ENSEMBLE LEARNING

training and inference. Another disadvantage of ensemble methods is that they are more difficult to interpret. Still, there exist agnostic interpretability methods (Molnar, 2019) that can help to analyze the results. In the next section, I will show you how to implement your own Bagging model with decision trees in R.

# 3.1.1 Activity recognition with Bagging

bagging_activities.R iterated_bagging_activities.R

In this section, we will implement Bagging with decision trees. Then, we will test our implementation on the SMARTPHONE ACTIVITIES dataset. The following code snippet shows the implementation of my_bagging() function. The complete code is in the script bagging_activities.R. The function accepts three arguments. The first one is the formula, the second one is the train set, and the third argument is the number of base learners (10 by default). Here, we will use the rpart package to train the decision trees.

```
# Define our bagging classifier.
my_bagging <- function(theFormula, data, ntrees = 10){

N <- nrow(data)

# A list to store the individual trees
models <- list())

# Train individual trees and add each to 'models' list.
for(i in 1:ntrees){

# Bootstrap instances from data.
idxs <- sample(1:N, size = N, replace = T)

bootstrappedInstances <- data[idxs],

treeModel <- rpart(as.formula(theFormula),
    bootstrappedInstances,
    xval = 0,
```