```
y <- mvrnorm(mu = mu, Sigma = var*diag(n))

return(list(X = x, y = y, beta = b, Sigma = cov_mat, sigma = var))
}
```

Next, we will write a function for our model metrics. The only input we need from our model is the estimated coefficients. Otherwise, all of the information comes from the data we generate with the function we just wrote. We will utilize this list format to extract the values needed for our formulas.

```
#' Return model metrics
#'
#' @param coef_est Vector with estimated coefficients
#' @param test_data Withth test set (`simulate_data()` output)
#' @return Vector with relative test error (RTE) and proportion
#' of variance explained (PVE).
get_metrics <- function(coef_est, test_data) {

  # Extract out values needed
  coef_true <- test_data$beta
  Sigma <- test_data$Sigma
  var_y <- test_data$sigma

  # Calculate relative test error
  RTE <- (t(coef_est - coef_true) %*% Sigma %*%
           (coef_est - coef_true) + var_y) /
    var_y

  # Calculate PVE
  # Proportion of variance explained
  PVE <- 1 - (t(coef_est - coef_true) %*% Sigma %*%
               (coef_est - coef_true) + var_y) /
    (var_y + t(coef_true %*% Sigma %*% coef_true))

  return(c(RTE = RTE, PVE = PVE))
}
```

Next, we will write a function that takes in the given parameters, fits the two models, and outputs the evaluation metrics. In this case, we will let the parameters be a named vector that contains all the components needed for the data simulation. We will also include an optional argument to set the random seed. In the code below, we find the time it takes to fit each model