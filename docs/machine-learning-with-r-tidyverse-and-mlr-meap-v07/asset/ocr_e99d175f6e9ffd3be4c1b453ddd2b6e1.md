```
```r
tunedK$x

knnTuningData <- generateHyperParsEffectData(tunedK)

plotHyperParsEffect(knnTuningData, x = "k", y = "mmce.test.mean",
                    plot.type = "line") +
                    theme_bw()

tunedKnn <- setHyperPars(makeLearner("classif.knn"), par.vals = tunedK$x)

tunedKnnModel <- train(tunedKnn, irisTask)
```
```

+   6. Cross-validate this iris k-NN model using nested cross-validation, where the outer cross-validation is hold-out with a 2/3 split

```
```r
inner <- makeResampleDesc("CV")

outerHoldout <- makeResampleDesc("Holdout", split = 2/3, stratify = TRUE)

knnWrapper <- makeTuneWrapper("classif.knn", resampling = inner,
                              par.set = knnParamSpace,
                              control = gridSearch)

holdoutCVWithTuning <- resample(knnWrapper, irisTask,
                                resampling = outerHoldout)

holdoutCVWithTuning
```
```

+   7. Repeat the nested cross-validation using 5-fold, non-repeated cross-validation as the outer loop. Which of these methods gives you a more stable MMCE estimate when you repeat them?

```
```r
outerKfold <- makeResampleDesc("CV", iters = 5, stratify = TRUE)

kFoldCVWithTuning <- resample(knnWrapper, irisTask,
                              resampling = outerKfold)

kFoldCVWithTuning

resample(knnWrapper, irisTask, resampling = outerKfold)

# repeat each validation procedure 10 times and save the mmce value
# WARNING: this may take a few minutes to complete

kSamples <- map_dbl(1:10, ~resample(
  knnWrapper, irisTask, resampling = outerKfold)$aggr
)

hSamples <- map_dbl(1:10, ~resample(
  knnWrapper, irisTask, resampling = outerHoldout)$aggr
)

hist(kSamples, xlim = c(0, 0.11))
hist(hSamples, xlim = c(0, 0.11))

# holdout CV gives more variable estimates of model performance
```
```