```
ACTUAL_VS_PREDICTED = range(len(y_test))
pyplot.plot(ACTUAL_VS_PREDICTED,y_test,label='Original')
pyplot.plot(ACTUAL_VS_PREDICTED,Predictions,label='Predicted')
pyplot.legend()
pyplot.show()
```

#Plotting the predicted values and the actual values to check for any outliers.

![](bbox=[0.1, 0.23, 0.64, 0.52])

```
feature_importances = pd.Series(RF.feature_importances_, index =x.columns) feature_importances.nlargest(20).plot(kind = 'barh')
```

#This plot represents the global feature importance.

![](bbox=[0.1, 0.65, 0.59, 0.9])