
# Building and optimizing your model 281

In the following subsection, we optimize our XGBoost solution using Bayesian optimization to strive to perform as well as possible on our problem.

## 7.2.5 Optimizing your model

Since XGBoost works quite well for the problem, we'll take some time to refine our parameters and test different boosting approaches and objectives. We are going to use Optuna, a Bayesian optimizer presented in the previous chapter, because it can efficiently explore a GBDT hyperparameter search space, adaptively choosing in a short set of rounds, based on the outcomes of the previous experiments, the next set of hyperparameters to be evaluated.

If you don't have Optuna available on your system, you can install it by issuing the command `pip install optuna` in a shell or a notebook cell.

Listing 17 performs hyperparameter optimization using Optuna for our previously tested XGBoost Regressor to find the best hyperparameters that minimize the MAE of the model on the Tokyo Airbnb dataset. The core of the listing is the objective function that suggests to Optuna different hyperparameter values using `trial.suggest_...` methods. In particular, it tests the `gbtree` (gradient boosting) and the `gblinear`. This booster utilizes a linear model as its base learner, incorporating both L1 and L2 regularization instead of employing a decision tree. Regarding the objective function, it tests the squared error, the gamma objective, and the Tweedie, blending aspects of the gamma and Poisson distributions. When selecting the booster or chosen parameters, it makes modifications and additions to fit the requirements of the gblinear booster or the Tweedie. Finally, it creates an XGBoost Regressor with the suggested hyperparameters at each test and performs cross-validation to evaluate the MAE. The process is repeated for a specified number of trials (60 in this case). After optimization, the best achieved MAE and corresponding best hyperparameters are printed.

# Listing 17 Optimizing the XGBoost regressor

```python
import optuna

def objective(trial):
    params = {
        'booster': trial.suggest_categorical(
            'booster',
            ['gbtree', 'gblinear']
        ),
        'objective': trial.suggest_categorical(
            'objective',
            ['reg:squarederror', 'reg:gamma', 'reg:tweedie']
        ),
        'n_estimators': trial.suggest_int(
            'n_estimators', 100, 1000
        )
```

# Defines an optimization objective function using the Optuna library

# Dictionary containing hyperparameters for optimization, including booster type, objectives, and others

```python
'learning_rate': trial.suggest_float(
  'learning_rate', 0.01, 1.0, log=True
),
'subsample': trial.suggest_float(
  'subsample', 0.3, 1.0
),
'colsample_bytree': trial.suggest_float(
  'colsample_bytree', 0.3, 1.0
),
'max_depth': trial.suggest_int('max_depth', 1, 7),
'min_child_weight': trial.suggest_int('min_child_weight', 1, 7),
'reg_lambda': trial.suggest_float(
  'reg_lambda', 1e-9, 100.0, log=True
),
'reg_alpha': trial.suggest_float(
  'reg_alpha', 1e-9, 100.0, log=True
)
```

# Adjusts hyperparameters based on the booster type

```python
if params['booster'] == 'gblinear':
  keys_to_remove = {
    'colsample_bytree', 'max_depth',
    'min_child_weight', 'subsample'
  }
  params = {
    key:value for key, value in params.items()
    if key not in keys_to_remove
  }
```

# Suggests the additional parameter 'tweedie_variance_power' for a tweedie objective

```python
if params['objective'] == 'reg:tweedie':
  # Must be between range [1, 2) :
  params['tweedie_variance_power'] = trial.suggest_float(
    'tweedie_variance_power', 1.01, 1.99
  )
```

# Initializes an XGBoost Regressor with the suggested hyperparameters

```python
xgb = XGBRegressor(**params)
pipeline = Pipeline(
  ['processing'
)
```

# Performs cross-validation using the defined pipeline and optimizing for MAE

```python
cv = cv_split(X, y=X['neighbour_more_than_30'])
cv_scores = cross_validate(
  estimator=model_pipeline,
  X,
  y,
  scoring='neg_mean_absolute_error',
  cv=cv_splits
)
```

# Calculates the MAE from the negative MAE scores

```python
cv_evaluation = np.mean(
  np.abs(cv_scores['test_score'])
)
return cv_evaluation
```

# Returns the calculated evaluation metric to be minimized

```python
sqlite_db = "sqlite:///sqlite.db"
```

# Building and optimizing your model

```python
study_name = "optimize_XGBoost_tokyo_airbnb"
study = optuna.create_study(
    storage=sqlite.db,
    study_name=study_name,
    direction="minimize",
    load_if_exists=True
)

study.optimize(objective, n_trials=60)
print(study.best_value)
print(study.best_params)
```

# Creates an Optuna study with
# storage in SQLite database

# Performs optimization for
# 60 trials

# Prints the best achieved
# value

# Prints the best hyperparameters
# hyperparameters found during optimization

# CHAPTER 7 An end-to-end example using XGBoost
