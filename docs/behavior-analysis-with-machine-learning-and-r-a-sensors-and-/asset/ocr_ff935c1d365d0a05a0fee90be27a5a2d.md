# ROC curve
AUC = 0.9636425

![](bbox=[0.158, 0.156, 0.842, 0.403])

Figure 10.10: ROC curve and AUC. The dashed line represents a random model.

```
library(PRROC)
roc_obj <- roc.curve(scores.class0 = test.scores$anomaly_score,
weights.class0 = gt.all,
curve = TRUE,
rand.compute = TRUE)
```

```
# Set rand.plot = TRUE to plot the random model's curve.
plot(roc_obj, rand.plot = TRUE)
```

The arguments scores.class0 specifies the returned scores by the Isolation Forest and weights.class0 are the true labels, 1 for the positive class (abnormal) and 0 for the negative class (normal). We use curve=TRUE the method returns a curve with thresholds and their respective sensitivity and FPR. The rand.compute=TRUE instructs the function to also compute the curve of a random model, which is, one that predicts scores at random. Figure 10.10 shows the ROC plot.

Here we can see how sensitivity and FPR increase as the threshold decreases. In the best case we want a sensitivity of 1 and a FPR of 0. This ideal point is located at top left corner but this model does not reach level of performance a bit lower. The dashed line in