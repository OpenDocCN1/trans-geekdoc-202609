114 Linear Regression — Key Machine Learning Concepts

# TABLE 5.2 Mockup Training Dataset with Columns for $y_i$ and $x_i^2$

| | $y_i$ | $x_i$ | $y_i, x_i$ | $x_i^2$ |
|---|---|---|---||
| i | Grade | StudyTime | GradeStudyTime | Squared |
| 1 | 65 | 2 | 130 | 4 |
| 2 | 82 | 3 | 246 | 9 |
| 3 | 93 | 7 | 651 | 49 |
| 4 | 93 | 8 | 744 | 64 |
| 5 | 83 | 4 | 332 | 16 |

linear regression, and we have to rely on *trial-and-error* for most other machine learning models.

Below are the formulas for the optimal $eta s$ for a univariate regression based on a training dataset with $N$ observations. As before, we abbreviate the outcome variable *Grade* with $y$ and the only predictor *StudyTime* with $x^2$:

```
$$\beta_{1,opt} = \frac{N\sum_{i=1}^{N} y_i x_i - \sum_{i=1}^{N} y_i\sum_{i=1}^{N} x_i}{N\sum_{i=1}^{N} x_i^2 - (\sum_{i=1}^{N} x_i)^2} \quad (5.7)$
```

```
$$\beta_{2,opt} = \frac{\sum_{i=1}^{N} y_i - \beta_1\sum_{i=1}^{N} x_i}{N}$ \quad (5.8)$
```

You can see the values for $\beta_{opt,1}$ and $\beta_{opt,2}$ are only based on data from the training dataset. The two equations might look scary to readers unfamiliar with summation notation. However, it is actually not that difficult to calculate the values for $\beta_{opt,1}$ and $\beta_{opt,2}$ if we use $R$.

Again, we use the mockup dataset (see Columns 2 and 3 of [Table 5.2]) to demonstrate how $\beta_{opt,1}$ and $\beta_{opt,2}$ can be calculated with $R$ based on Equations (5.7) and (5.8).

We start with summation $\sum_{i=1}^{N} x_i$. The term means we sum up all $x$, considering that $i$ takes values starting from 1 and ending with $N$ (being 5 in our case). Because $i$ is the row number in [Table 5.1], $\sum_{i=1}^{N} x_i$ stands for the $x$ column in Table 5.1. The same applies to $\sum_{i=1}^{N} y_i$.

With this knowledge, we can easily use $R$ to calculate $\sum_{i=1}^{N} x_i$ and $\\sum_{i=1}^{N} y_i$.

```
SumOfX=sum(DataMock$StudyTime)
SumOfY=sum(DataMock$Grade)
```

> In the Digital Resource Section 5.7 you can find a link to a short blog article that shows how Equations (5.7) and (5.8) can be derived.