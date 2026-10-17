The previous plots are all displayed as a single figure. If we want to display multiple plots next to each other, we can specify the graphical parameters using the par() function by updating the argument mfrow = c(nrow, ncol) with the number of columns and rows we would like to use for our figures. We use this to display the distribution of log blood lead level between those with and without hypertension next to the previous plot.

```
par(mfrow = c(1, 2))

# boxplot
boxplot(log(LEAD) ~ HYP, data = nhanes_df, xlab = "Hypertension",
        ylab = "Log Blood Lead Level")

# scatter plot
plot(nhanes_df$SBP1, nhanes_df$DBP1, col = as.factor(nhanes_df$HYP),
     xlab = "Systolic Blood Pressure",
     ylab = "Diastolic Blood Pressure")
abline(v = 130, col = "blue")
abline(h = 80, col = "blue")
```

![](bbox=[0.12, 0.53, 0.83, 0.76])

We then reset to only display a single plot for future images using the par() function again.

```
par(mfrow = c(1, 1))
```