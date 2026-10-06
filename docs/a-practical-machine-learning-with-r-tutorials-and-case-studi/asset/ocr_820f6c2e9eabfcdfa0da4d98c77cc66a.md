Step 1 - Generate Training and Testing Data: Note, it is assumed that the data frame MyData contains the data you are analyzing.

```
set.seed(087)
Split80<-MyData |
  initial_split(prop=0.8, strata=<OUTCOME VARIABLE>, breaks=5)
DataTrain=training(Split80)
DataTest=testing(Split80)
```

Substitute <OUTCOME VARIABLE> with the name of your outcome variable for the strata. This ensures that the distribution of your outcome variable is similar in the training and testing data.

Step 2 - Create a Recipe: In the code block below, substitute <OUTCOME VARIABLE> with your outcome variable and <PREDICTOR VARIABLE($S)> with a list of your predictor variables separated by \+-signs.

Additionally, you can use a "-", on the right of the "-" to use all predictor variables from the related data frame.

```
Recipe<-recipe(<PREDICTOR VARIABLE($S)>>
  data=DataTrain |
  step_<NAME OF STEP($S) OF STEP>)
```

Note that <NAME OF STEP> stands for an optional pre-processing step of the predictor variables. <ARGUMENT(S) OF STEP> represents optional arguments for the related step\_command.

If you plan to tune a hyper-parameter in a recipe you have to assign the <tune>placeholder rather than a value to the related argument. For example, degree=tune in step\_poly().

You can find a list of available step commands with their names at: https://recipes.tidymodels.org/reference.

Step 3 - Create a Model Design: Substitute <NAME OF ML-COMMAND> with the command for the related machine learning model and optional with arguments for <ARGUMENT(S) OF COMMAND>.

Substitute <PACKAGE NAME> in the engine() command with the package name for the machine learning model and <MODE> in the set\_mode() command with regression or classification.

```
ModelDesign<-NAME OF ML-COMMAND>(<ARGUMENT(S) OF COMMAND)> |
  set_engine("<PACKAGE NAME>") |
  set_mode("<MODE>")
```