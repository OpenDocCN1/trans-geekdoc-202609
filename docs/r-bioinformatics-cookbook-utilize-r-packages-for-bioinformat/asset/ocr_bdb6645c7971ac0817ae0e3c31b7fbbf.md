+   5. Run the ROC analysis:

```
library (DALEXtra)
model <- explain_mlr3(
  data = cancer_x
```

This code builds the model and gives us a feature analysis.

# How it works...

*In step 1*, we carry out the familiar data cleaning and task definition processes before building the trained model in the *learner* object. You can read about this more in detail in the first recipe in this chapter *Defining a task and learner to implement k-nearest neighbors (k-NNs)* in mlr3. *Step 2* is a quick demonstration of how to use the `predict() ` function to use the model to classify unseen data. Here, we simply pass the model in `learner` and a new set of data formatted like that which the model was trained on. The result is a simple vector of class names:

```
## [1] benign malignant malignant benign
## Levels: benign malignant
```

*In step 4*, we can run and plot the feature importance analysis using the `FeatureImp$new()` function, then run the `plot()` method on the resulting imp object. That gives us *Figure 11.4:*: