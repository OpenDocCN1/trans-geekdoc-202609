Then we create the grid where or the base of our plot using the xlim and ylim. As we did before we create values for the lines using the linspace() function and create the grid using the meshgrid() function and then use the vstack() function to vertically stack the arrays where the values are reshaped using the ravel() function. We also call the decision_function() to get the valyes for the boundaries and margins

Next we use the data to plot the boundaries and margins using the contour() function to draw the lines and specify the linyles and the other properties using the respective parameters

Atlas, we check whether to plot the support vectors or not plot them if to using the scatter() functions by using support_vectors_0 and 1 indexed values in the array

Finally we can plot our data clusters and call the MMH() function and pass our SVC model

```
In [41]: plt.scatter(X1,X2,c=y)
MMH(CModel)
```

![](bbox=[0.1367, 0.5935, 0.8395, 0.8535])

Finally we have the maximum marginal hyperplane plotted for our data clusters with the support vectors