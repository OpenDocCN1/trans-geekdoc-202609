This looks like:

![](bbox=[0.106, 0.154, 0.894, 0.545])

Features correlated with negative sentiment

Now let’s take a closer look at the performance using the ROC curve. We can write our own function instead of using an extra package:

```
roc <- function(y_test, y_preds){
  y_test <- y_test[order(y_preds, decreasing = T)]
  return(data.frame(fpr=cumsum(!y_test)/sum(!y_test),
                    tpr=cumsum(y_test)/sum(y_test) ))
}
```

We can now generate predictions and plot the curve using the base R graphics:

```
y_preds <- predict(model, X_test, type="response")
plot(roc(y_test, y_preds), xlim=c(0,1), ylim=c(0, 1))
```