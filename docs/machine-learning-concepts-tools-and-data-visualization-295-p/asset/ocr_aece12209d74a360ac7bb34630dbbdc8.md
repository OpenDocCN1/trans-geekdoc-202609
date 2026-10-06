# Machine Learning: Concepts, Tools and Data Visualization

By expanding the scope of the R Script visualization, you can see that it ran successfully. Figure 12-15 shows the distribution curve for the “ToothGrowth” data.

![](bbox=[0.095, 0.178, 0.904, 0.483])

Figure 12-15 ToothGrowth distribution curve

# Source (12-15)

```
# dataset <- data.frame(dose, len, supp)
# dataset <- unique(dataset)

tootDen <- density(dataset$len)
plot(toothDen, main = "Tooth length", xlab="length")
```

If you plot each histogram and distribution curve in the previous example as a plot, you can effectively determine the distribution of the “ToothGrowth” data. Enter the following source in the R Script window, as shown in Figure 12-16.

Figure 12-17 shows the result of plotting the histogram and the distribution curve. You can see that the “ToothGrowth” data does not exactly match the normal distribution.