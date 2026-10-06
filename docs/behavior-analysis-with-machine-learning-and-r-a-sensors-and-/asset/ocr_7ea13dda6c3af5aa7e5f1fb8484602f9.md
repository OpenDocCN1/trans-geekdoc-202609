```
cp = 0
models <- c(models, list(treeModel))
}
res <- structure(list(models = models),
     class = "my_bagging")
return(res)
}
```

First, a list that will store each individual learner is defined models <- list(). Then the function iterates ntrees times. In each iteration, a bootstrapped train set is generated and used to train a rpart model. The xval = 0 parameter tells rpart not to perform validation internally. The cp parameter is also set to 0. This value controls the amount of pruning. The default is 0.01 leading to smaller trees. This makes the trees to be more similar but we want diversity we are setting this to 0 so bigger trees are generated and as a consequence, more diverse.

Finally, an object of class "my_bagging" is returned. This is just a list containing the trained base learners. The class = "my_bagging" argument is important. This tells R that this object is of type my_bagging. Setting the class will allow us to use the generic predict() function and R will automatically call the corresponding predict.my_bagging() function we will shortly define. The class name and the function name after predict. need to be the.

```
# Define the predict function for my_bagging.
predict.my_bagging <- function(object, newdata){

trees <- length(object$models)
N <- row(newata)

# Matrix to store predictions for each instance
# in newdata and for each tree.
M <- matrix(data = rep("",N * ntrees), nrow = N)

# Populate matrix.
```