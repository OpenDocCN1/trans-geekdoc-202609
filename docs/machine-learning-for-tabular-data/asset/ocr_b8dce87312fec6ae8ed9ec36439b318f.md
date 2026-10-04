# Boosting in Scikit-learn

![](bbox=[0.195, 0.076, 0.636, 0.403])

**Figure 5.8** A process flow chart describing how early stopping works in GBDTs

error

![](bbox=[0.195, 0.536, 0.876, 0.753])

**Figure 5.9** Validation error and training error generally behave when using GBDTs through multiple iterations

Different stopping points may be found for each model trained on the entire folds in a cross-validation process with early stopping. When training on the entire dataset, you can still rely on using early stopping based on a validation sample. Hence, you just need to set a high number of iterations and see when the training stops. Otherwise,