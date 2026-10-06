# 5.4 Univariate Mockup: Time and Grades

```
cat("First 5 values for beta1:",VecBetaValues[1:5],"\n"
  "Last 5 values for beta1:",VecBetaValues[17:21],"\n"
  "First 5 values for beta2:",VecBeta2Values[1:5],"\n"
  "Last 5 values for beta2:",VecBeta2Values[17:21])
```

```
## First 5 values for beta1: 3.3 3.2 3.3 3.4
## Last 5 values for beta1: 4.6 4.7 4.8 4.9 5
## First 5 values for beta2: 50 51 52 53 54
## Last 5 values for beta2: 66 67 68 69 70
```

As you can see, we printed the first and the last five values for each vector object VecBeta2Values.

Now we have all pairwise combinations of the values generated for $\beta_1$ and $\beta_2$. Because we generated 21 values (21-21) combinations, we will end up with a total of 441 combinations. Formately, we do not have to generate these combinations manually. The R command expand.grid() can generate the store result in the data frame GridBetaPairs and print the first and last five pairs of $\beta_1$ and $\beta_2$:

```
GridBetaPairs<-expand.grid(VecBetaValues, Beta2=VecBetaValues)
print(GridBetaPairs[c(1,2,3,4,5,438,439,440,441,445),])
```

| | Beta2 |
|---|---|
| ## 1 | 3.0 50 |
| ## 2 | 3.1 50 |
| ## 3 | 3.2 50 |
| ## 4 | 3.3 50 |
| ## 5 | 3.4 50 |
| ## 6 | 4.7 70 |
| ## 7 | 4.8 70 |
| ## 8 | 4.9 70 |
| ## 9 | 4.4 70 |
| ## 10 | 5.0 79 |

For each pair of $\beta_1$ and $\beta_2$ (each row in GridBetaPairs), we must calculate the MSE for the pair with the smallest MSE. This method is comprehensive but not computationally efficient, Grid Search is sometimes called a Brute Force approach.

Calculating the MSE for $\beta_1$ and $\beta_2$ is accomplished in the following code block with the apply() command. It applies a function (in this case, fMSE()) to each of the rows of the data frame GridBetaPairs using the $\beta_1$ and $\beta_2$ pairs in each row together