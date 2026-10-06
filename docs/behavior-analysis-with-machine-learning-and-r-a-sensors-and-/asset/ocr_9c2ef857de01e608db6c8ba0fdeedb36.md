```
# Populate matrix.
for(i in 1:nfeatures){
  feature.values <- data[which(data$class == c),i]
  M[i,1] <- mean(feature.values)
  M[i,2] <- sd(feature.values)
}

list.means.sds[c] <- list(M)

```

```
# Compute prior probabilities.
priors <- table(data$class) / nrow(data)

return(list(means.sds=list.means.sds,
  priors=priors))

```

The function iterates through each class and for each, it creates a matrix M with F rows and 2 columns where F is the number of features. The first column stores the means and the second standard deviations. Those matrices are saved in a list indexed by the class name so at prediction time we can retrieve each matrix individually. At the end, the prior probabilities are computed. Finally, a list is returned. The first element of the list is the list of matrices and the second element are the priors.

The next function will make predictions based on the learned parameters. Its first argument is the learned parameters and the second parameter is a data frame with the instances we want to make predictions for.

```
# Function to make predictions using
# the learned parameters.
ive.bayes.predict <- function(params, data){
```

```
# Variable to store the prediction for each instance.
predictions <- NULL
```

```
n <- nrow(data)
```