```
fit_RL4$Q <- round(fit_RL4$Q, 3) # Round the Q-matrix
print(fit_RL4) # Show the output
```

```
## State-Action function Q
##     0    0    1    0 -1   -1 -1   -1   0   -1   1   -1   1   0   1   1
## X0.2 0.000 0.000 0.002 -0.017 -0.018 -0.020 0.023 0.025 0.024
## X0.3 0.001 -0.005 0.007 -0.013 -0.019 -0.026 0.031 0.027 0.021
## X3.1 0.003 0.003 0.003 0.002 0.002 0.003 0.002 0.002 0.003
## X2.1 0.027 0.038 0.020 0.004 0.015 0.039 0.013 0.021 0.041
## X2.2 0.021 0.014 0.027 0.038 0.047 0.045 -0.004 -0.011 -0.016
## X2.3 0.007 0.006 0.008 0.054 0.057 0.056 -0.041 -0.041 -0.041
## X1.1 0.027 0.054 0.005 -0.031 -0.005 0.041 0.025 0.046 0.072
## X1.2 0.019 0.020 0.020 0.015 0.023 0.029 0.012 0.014 0.023
## X1.3 0.008 0.019 0.000 -0.036 -0.027 -0.016 0.042 0.053 0.060
##
## Policy
##     X0.2  X0.3  X3.1  X2.1  X2.2  X2.3  X1.1  X1.2  X1.3
##  "1 0" "1 -1" "0 -1" "1 1 " "-1 0 " "-1 0 " "1 1 " "-1 1 " "1 1 "
##
## Reward (last iteration)
## [[1]] 0
```

The matrix is less sparse compared to the one of Chapter 16; we have covered much more ground! Some policy recommendations have not changed compared to the smaller sample, but some have! The change occurs for the states for which only a few points were available in the first trial. With more data, the decision is altered.