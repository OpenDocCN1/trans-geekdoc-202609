Here is the output of the above code:

![](bbox=[0.136, 0.137, 0.553, 0.342])

From the plot, you can learn that there is a linear relationship between the weight and height of the individual.
Let's find out how the variables are correlated to each other:

```
>>> sl_data.corr()
```

The above code displays the following correlation matrix:

| Height | Weight |
| Height | 1.000000 | 0.942603 |
| Weight | 0.942603 | 1.000000 |

You can clearly note that the height and weight are correlated to each other depending on a Pearson correlation value of 0.94. A Pearson correlation ranges from -1 to + 1, thus when the number is more positive, the relation between the two variables is stronger if they increase or decrease together. In case the correlation value is negative, then the relation between the two variables is strong, but it's in the opposite direction.
Let's build a linear regression model using the weight as the dependent variable and x as the independent variable.