| INPUT | PREDICTION | ERROR |
|---|---|---|
| 6 | 6.181 | - 319 |
| 7 | 7.202 | 202 |
| 8 | 8.223 | - 777 |
| 9 | 9.244 | 244 |
| 10 | 10.265 | 265 |
| 11 | 11.287 | |
| 12 | 12.308 | |
| 13 | 13.329 | |
| 14 | 14.350 | |
| 15 | 15.372 | |
| 16 | 16.393 | |
| 17 | 17.414 | |
| 18 | 18.435 | |
| 19 | 19.456 | |
| 20 | 20.478 | |

Table 6.5 – Model predictions

While you are analyzing regression models, you should be able to know whether your model is of good quality or not. You read about many modeling issues (such as overfitting) in Chapter 1, Machine Learning Fundamentals, and you already know that you always have to check model performance.

A good approach to regression models is performing what is called residual analysis. This is where you plot the errors of the model in a scatter plot and check whether they are randomly distributed (as expected) or not. If the errors are not randomly distributed, this means that your model was unable to generalize the data. Figure 6.5 shows a residual analysis based on the data from Table 6.5.