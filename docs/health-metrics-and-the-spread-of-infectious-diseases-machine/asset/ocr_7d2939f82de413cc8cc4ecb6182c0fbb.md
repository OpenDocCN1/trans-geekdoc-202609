242

COVID-19 Outbreaks

```
cv_wkf <- workflow_set(
  preproc = list(id = cv_recipe),
  models = list(Decision_tree = cart,
  Random_Forest = rand_forest,
  Knn = knn,
  SVM = svm))
```

```
cv_wkf
# # A workflow/table: 4 x 4
# wflow_id      info    option result
# <chr>         <list> <list> <list>
# 1 id_Decision_tree tibble [1 x 4] <opts[0]> <list [0]
# 2 id_Random_Forest tibble [1 x 4] <opts[0]> <list [0]
# 3 id_Knn         tibble [1 x 4] <opts[0]> <list [0]
# 4 id_SVM         tibble [1 x 4] <opts[0]> <list [0]
```

Create a workflow_map() to fit the models to the training data. We use the `finetune` package to tune the `race_anova` function to tune the hyperparameters of the models. The `race_ctrl` object specifies the control parameters for the tuning process, such as the number of resamples and the grid size. The `parallel_over` argument allows the tuning process to run in parallel over multiple cores for faster computation.

```
# Fit the models to the training data
library(finetune)
set.seed(112233)
race_ctrl <-
  control_race(save_pred = TRUE,
  parallel_over = "everything",
  save_workflow = TRUE)
```

```
race_results <- cv_wkf %>%
workflow_map("tune_race_anova",
  seed = 1503,
  resamples = cv_folds,
  grid = 3,
  control = race_ctrl)
```

```
race_results
# # A workflow/table: 4 x 4
# wflow_id      info    option result
# <chr>         <list> <list> <list>
# 1 id_Decision_tree tibble [1 x 4] <opts[3]> <race[+]
# 2 id_Random_Forest tibble [1 x 4] <opts[3]> <race[+]
# 3 id_Knn         tibble [1 x 4] <opts[3]> <race[+]
# 4 id_SVM         tibble [1 x 4] <opts[3]> <race[+]
```

Then we collect the metrics for the models to evaluate their performance. We filter the results for the root mean squared error (rmse) and arrange them in ascending order to identify the best-performing model.

```
rmse <- collect_metrics(race_results) %%
filter(.metric == "rmse") %%>%
```