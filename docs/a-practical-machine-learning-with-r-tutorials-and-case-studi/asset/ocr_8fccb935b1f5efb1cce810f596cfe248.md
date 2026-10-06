# Step 7 - Tune the Workflow and Train All Models: The tune_grid() trains models for all hyper-parameter combinations stored in the data frame ParGrid using all resampled stored in the previous step in FoldsForTuning.

```
TuneResults=tune_grid(TuneWFModel, resamples=FoldsForTuning,
grid=ParGrid, metrics=metric_set(<LIST OF METRICS>),
control_grid(verbose=TRUE)
```

The optional metrics argument specifies the metrics that are calculated. For example, metric_set(<LIST OF METRICS>) with metric_set(rmse, rsq, max) for a regression or with metric_set(accuracy, specificity) for a classification problem.

The argument control_grid(verbose=TRUE) is optional. When used like here with verbose=TRUE, the tuning reports its progress to the R Console.

# Step 8 - Extract the Best Hyper-Parameter(s): Because all results for the specified metrics are stored in the tuning object TuneResult, we can use select_best() to extract the best hyper-parameter(s) for the metrics we are interested in:

```
BestHyperPar=select_best(TuneResults, "<METRIC>\')
```

You need to specify which metric should be used to identify the best-performing model by substituting <METRIC> with the metric of your choice. Note that only metrics specified previously in Step 7 can be chosen.

# Step 9 - Finalize and Train the Best Workflow Model: You can use the command finalize_workflow() to substitute the TuneWFModel with the values from BestHyperPar. Afterward, the fit(DataTrain) trains the finalized workflow model with your training data:

```
BestWFModel=TuneWFModel |
finalize_workflow(BestHyperPar) |
fit(DataTrain)
```

# Step 10 - Assess Prediction Quality Based on the Testing Data: This step should only be performed after the model is completed and no further changes are planned otherwise, you cannot use the testing data.

```
DataTestWithBestModel-augment(BestWFModel, DataTest)
metrics(DataTestWithBestModel, truth=<OUTCOME VARIABLE>,
estimate=.pred)
```