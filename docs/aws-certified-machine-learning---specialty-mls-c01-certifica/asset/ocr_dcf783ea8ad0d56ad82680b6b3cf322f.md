# Creating a linear regression model from scratch

You are going to use a very simple dataset, with only two variables:

+   * x: Represents the person's number of years of work experience
+   * y: Represents the person's average salary

You want to understand the relationship between x and y and, if possible, predict the salary (y) based on years of experience (x). Real problems very often have far more independent variables and are not necessarily linear. However, this example will give you the baseline knowledge to master more complex algorithms.

To find out what the alpha and beta coefficients are (or slope and y intercept if you prefer), you need to find some statistics related to the dataset. In Table 6.3, you have the data and these auxiliary statistics.

| X (INDEPENDENT) | Y (DEPENDENT) | X MEAN | Y MEAN | COVARIANCE (X,Y) | X VARIANCE | Y VARIANCE |
|---|---|---|---|---|---|---|
| 1 | 1.000 | | | 21.015 | 20 | 21.808.900 |
| 2 | 1.500 | | | 14.595 | 12 | 17.388.900 |
| 3 | 3.700 | | | 4.925 | 6 | 3.880.900 |
| 4 | 5.000 | | | 1.005 | 2 | 448.900 |
| 5 | 4.000 | | | 835 | 0 | 2.788.900 |
| 6 | 6.500 | | | 415 | 0 | 688.900 |
| 7 | 7.000 | | | 1.995 | 2 | 1.768.900 |
| 8 | 9.000 | | | 8.325 | 6 | 11.088.900 |
| 9 | 9.000 | | | 11.655 | 12 | 11.088.900 |
| 10 | 10.000 | | | 19.485 | 20 | 18.748.900 |
| COUNT | 10 | 5,50 | 5.670,00 | 8.425,00 | 8,25 | 8.970.100,00 |

Table 6.3 – Dataset to predict average salary based on the amount of work experience

As you can see, there is an almost perfect linear relationship between x and y. As the amount of work experience increases, so does the salary. In addition to x and y, you need to compute the following statistics: the number of records, the mean of x, the mean of y, the covariance of x and y, the variance of x, and the variance of y. Figure 6.2 depicts formulas that provide a mathematical representation of variance and covariance (respectively), where x bar, y bar, and n represent the mean of x, the mean of y, and the number of records, respectively: