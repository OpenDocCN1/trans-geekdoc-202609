# REGRESSION

We used the predict() method and passed the test height values test_X as arguments and stored the predictions in the pred_y. Then we created a data frame using the pred_y values (we flattened the array using the flatten() function to change it to 1-D array from 2-D array before passing it as values) and test_y actual values (we sliced the Weight(lbs) column and extracted it's values) and plotted a grouped bar graph using the plot() function and bar to kind parameter and also specified the size of the plot using figsize parameter

As you can observe, the predicted values as blue and actual values are orange so we can tell visually what is the performance of our model. Most of the bars are close to each other but some are way taller or shorter than the other i.e. our model is performing good but in some cases it predicted wrong. We can also visualize the regression line and data points

```
In [4]: pyplot.scatter(tst_X, tst_y, color='black')
pyplot.plot(tst_X, pred_y, color='yellow')
plt.show()
```

![](bbox=[0.118, 0.613, 0.821, 0.866])

We used the scatter() function to plot the data points and plot() function to plot the regression line