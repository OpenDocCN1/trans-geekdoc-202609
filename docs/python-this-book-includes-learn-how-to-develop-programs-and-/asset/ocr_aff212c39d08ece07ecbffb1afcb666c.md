code:

```
>>> fig, ax = plt.subplots(1, 1)
>>> ax.scatter(y_valid, ypred)
>>> ax.set_xlabel('Actual')
>>> ax.set_ylabel('Predicted')
>>> plt.show()
```

Below you can see the output of the previous code:

![](bbox=[0.118, 0.317, 0.467, 0.492])

Now, let's plot the scatter for the alternate model:

![](bbox=[0.118, 0.569, 0.467, 0.744])

This really shows that the models aren't good enough because the predictions aren't quite random.

To create an accurate model, you need some more variables, which will have an effect on the average points that are scored.

The previous model was build using the statsmodels package. Next, you will build a model using SciKit.