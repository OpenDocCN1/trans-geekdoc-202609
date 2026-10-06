# CHAPTER 5. PREPROCESSING BEHAVIORAL DATA

| 1 | 3 | 0 | 5 | 2 | | 1 | 3 | 0 | 5 | 2 | | 1 | 3 | 0 | 5 | 2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---||
| 1.3 | | | | | | 1.3 | 2.6 | | | | | 1.3 | 2.6 | 2.3 | | |

Iteration 1
Iteration 2
Iteration 3

Figure 5.6: Simple moving average by step with window size = 3.

| 1 | 3 | 0 | 5 | 2 | | 1 | 3 | 0 | 5 | 2 | | 1 | 3 | 0 | 5 | 2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---||
| 1.3 | | | | | | 1.3 | 2.6 | | | | | 1.3 | 2.6 | 2.3 | |

Iteration 1
Iteration 2
Iteration 3

Figure 5.7: Centered moving average by step with window size = 3.

moving average values at the beginning and the end will be empty. Also note that the window size should be odd. In practice, both versions produce very similar results.
In the preprocessing.R script the function movingAvg() implements the simple moving average procedure. In the following code that the output vector will have the same size as the original but the last elements will contain NA values when the window can not be moved to the right.

```
movingAvg <- function(x, w = 5){
# Applies moving average to x with a window of size w.
n <- length(x) # Total number of points.
smoothedX <- rep(NA, n)

for(i in 1:(n-w+1)){
  smoothedX[i] <- mean(x[i:(i+w-1)])
}

return(smoothedX)
}
```

We can apply this function to a segment of accelerometer data from the SHEEP AND