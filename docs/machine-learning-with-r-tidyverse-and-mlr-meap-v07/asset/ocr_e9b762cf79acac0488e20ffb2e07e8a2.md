# 16.5 Solutions to exercises

+   1. Increase the iter.max of our k-means learner to 200

```
```r
kMeans <- makeLearner("cluster.kmeans",
                       par.vals = list(iter.max = 200, nstart = 10))

tunedK <- tuneParams(kMeans, task = gvhdTask,
                     resampling = kFold,
                     par.set = kMeansParamSpace,
                     control = gridSearch,
                     measures = list(db, dunn, G1))

# the error about not converging disappears when we set iter.max to 200
```
```

+   2. Use k-means to cluster the GvHD.pos dataset

```
```r
gvhdPosTib <- as_tibble(GvHD.pos)

gvhdPosScaled <- scale(gvhdPosTib)

gvhdPosTask <- makeClusterTask(data = gvhdPosScaled)

tunedKPos <- tuneParams(kMeans, task = gvhdPosTask,
                         resampling = kFold,
                         par.set = kMeansParamSpace,
                         control = gridSearch,
                         measures = list(db, dunn, G1))

kMeansTuningDataPos <- generateHyperParsEffectData(tunedKPos)

gatheredTuningDataPos <- gather(kMeansTuningDataPos$data,
                                key = "Metric",
                                value = "Value",
                                c(-centers, -iteration, -algorithm))

ggplot(gatheredTuningDataPos, aes(centers, Value, col = algorithm)) +
  facet_wrap(~ Metric, scales = "free_y") +
  geom_line() +
  geom_point() +
  theme_bw()

tunedKMeansPos <- setHyperPars(kMeans, par.vals = list("centers" = 4))

tunedKMeansModelPos <- train(tunedKMeansPos, gvhdPosTask)

kMeansModelDataPos <- getLearnerModel(tunedKMeansModelPos)

mutate(gvhdPosTib,
       kMeansCluster = as.factor(kMeansModelDataPos$cluster)) %>%
  ggparms(mapping = aes(col = kMeansCluster)
          upper = list(continuous = "density")) +
  theme_bw()

# the optimal number of clusters is less clear than for GvHD.control
```
```