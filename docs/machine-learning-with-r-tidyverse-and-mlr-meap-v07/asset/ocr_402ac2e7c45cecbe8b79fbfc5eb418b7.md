# Listing 6.5 Cross-validating the naive Bayes model

```
```r
kFold <- makeResampleDesc(method = "RepCV", folds = 10, reps = 50,
                           stratify = TRUE)

bayesCV <- resample(learner = bayes, task = voteSTask,
                    resampling = kFold,
                    measures = list(mmce, acc, fpr, fnr))

bayesCV$aggr

mmce.test.mean  acc.test.mean  fpr.test.mean  fnr.test.mean
    0.09820658     0.90179342     0.08223259     0.10819658
```
```

Our model correctly predicted 90% of test set cases in our cross-validation. That’s not bad! Now let’s use our model to predict the political party of a new politician, based on their votes.

# Listing 6.6 Using the model to make predictions

```
```r
politician <- tibble(V1 = "n", V2 = "n", V3 = "y", V4 = "n", V5 = "n",
                     V6 = "y", V7 = "y", V8 = "y", V9 = "y", V10 = "y",
                     V11 = "n", V12 = "y", V13 = "n", V14 = "n",
                     V15 = "y", V16 = "n")

politicianPred <- predict(bayesModel, newdata = politician)

getPredictionResponse(politicianPred)

[1] democrat
Levels: democrat republican
[source]
```
```

Our model predicts the new politician is a Democrat.

# EXERCISE 6.2

Wrap your naive Bayes model inside the `getLearnerModel()` function. Can you identify the prior probabilities and the likelihoods for each vote?

# 6.3 Strengths and weaknesses of naive Bayes

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether naive Bayes will perform well for your task.

The strengths of naive Bayes are:

+   - It can handle both continuous and categorical predictor variables
+   - It’s computationally inexpensive to train
+   - It commonly performs well on topic classification problems where we want to classify documents based on the words they contain
+   - It has no hyperparameters to tune