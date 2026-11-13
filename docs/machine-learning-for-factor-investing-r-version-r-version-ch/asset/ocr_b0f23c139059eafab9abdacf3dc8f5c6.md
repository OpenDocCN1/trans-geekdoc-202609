classifier. Indeed, the curve can be seen as a tradeoff between benefits (probability of detecting good strategies on the y axis) minus costs (odds of selecting the wrong assets on the x axis). Hence being above the 45° is paramount. The best possible classifier has a ROC curve that goes from point (0,0) to point (0,1) to point (1,1). At point (0,1), fallout is null, hence there are no false positives, and recall is equal to one so that there are also no false negatives; the model is always right. The opposite is true: at point (1,0), the model is always wrong.

Below, we use a particular package (`caTools`) to compute a ROC curve for a given set of predictions on the testing sample.

```
if(!require(caTools)){install.packages("caTools")}
```

```
library(caTools) # Package for AUC computation
colAUC(X = predict(fit_RF_C, testing_sample, type = "prob"),
 y = testing_sample$R1M_Usd_C,
 plotROC = TRUE)
```

# ROC Curves

![](bbox=[0.25, 0.376, 0.75, 0.725])

**FIGURE 10.3:** Example of ROC curve.

```
## FALSE TRUE
## FALSE vs. TRUE 0.5003885 0.5003885
```

In Figure 10.3, the curve is very close to the 45° angle and the model seems as good (or, rather, as bad) as a random classifier.

Finally, having one entire curve is not practical for comparison purposes, hence the information of the whole curve is synthesized into the area below the curve, i.e., the integral of the