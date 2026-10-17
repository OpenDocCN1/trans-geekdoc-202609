```
#> (Intercept) x
#> 0.0671 0.9946
```

# 18.1.3 Return Values

If we read the documentation for `lm()` by calling `?lm`, we can see that there are a lot of arguments that have default values. The other thing to note about the `lm` documentation is that there are multiple values returned. In fact, the type of object returned is a list containing all the different things we want to know about the results such as the coefficients.

```
simp_model <- lm(y ~ x)
simp_model$coefficients
#> (Intercept) x
#> 0.0671 0.9946
```

Since R only allows you to return one object, packaging the return values into a list is a useful way to return multiple outputs from a function. In the following example, we create a function `coin_flips()` that takes in a probability `prob` and a number of iterations `n` (with default value 10) and simulates `n` coin flips where the coin has a probability of `prob` of landing on heads. The function returns the percentage of trials that were heads and the results of the coin flips. We can access each of these returned values by using the names `percent_heads` and `results`.

```
coin_flips <- function(prob, n = 10){
# Flips a coin with probability prob of heads for n trials

results <- rbinom(n = n, size = 1, prob = prob)
return(list(percent_heads = sum(results)/n, results = results))
}
trial <- coin_flips(0.6)
trial$percent_heads
#> [1] 0.5
trial$results
#> [1] 0 0 0 1 1 1 0 1 0 1
```

One important thing to know about R and return values: if you don't specify a return statement but assign the output of our function to an object, it will assign the value to the last computed object by default. In the following code, the value returned is 3. Avoid unexpected behavior by always using the `return()` function.