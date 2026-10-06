To our surprise the classifier model has an accuracy of 80% i.e. it accurately rated 4 players. But is that it's? If you observe carefully the regressor model is just a bit lagging behind but to it's plus point, when rating Robert the regressor was close or correct. We can also print some metrics to get more insights

```
In [6]: from sklearn import metrics
mae = metrics.mean_absolute_error(tsty,pred_reg)
err = metrics.max_error(tsty,pred_reg)
acc = metrics.accuracy_score(tsty,pred_cls)
print(f'MAE: {mae},where max error is {err}')
print(f'CModel Accuracy: {acc}')

MAE: 0.43157941888947 where max error is0.83933
CModel Accuracy: 0.8
```

So we can draw a conclusion that the regressor is more close-to model i.e. close to the actual values by 0.4 where it can double in worst cases whereas the classifier is on-point model for the correct predictions but if it predicts wrong the values can differ from the actual by 1.0 or more. So according to which model is more preferable?

Well if you think the classifier because it is an on-point model but it comes with it's risks too i.e. the wrong predictions have higher differences from the actual in comparison to the regressors i.e. 0.84

In my opinion both models have their own advantages. But we need to choose one so let's choose the regressor. Why regressor or why not the classifier? Using these models always comes with risks of some wrong predictions we need to keep this in our mind that we must choose the best. The regressor has an average absolute error of 0.4 but it is close to the actual values i.e. most of the times it is less and more that's by