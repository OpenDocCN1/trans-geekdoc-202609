# Confusion matrix:

Here we see the accuracy of our classification model with the two extracted principal components.

Since these PCs were chosen to explain the most variance they explained around 60 percent of the variance. Therefore we should get good accuracy because our two PCs are actually the directions of maximum variance in our dataset.

It's a confusion matrix with three classes, so it won't be a confusing matrix of 2x2 but since we now have three classes this will be a confusion matrix of 3x3.

You can see we get excellent results because in the diagonal we will get the correct prediction.

14 correct predictions of the class for the customer of segment number one.

+   - 15 correct predictions of the customer segment two.
- 6 correct predictions of the customer segment three.

So using PCA we got a very good prediction. 35 correct prediction out of 36 total/observations. i.e. 35/37 = 97.2% accuracy.

Visualization: We edit the label of the variables.

And we use 3-colors to visualize our three customer_segments.

```
ListedColormap(('red', 'green', 'orange'))
```

![](bbox=[0.195, 0.433, 0.755, 0.683])

![](bbox=[0.195, 0.713, 0.755, 0.963])