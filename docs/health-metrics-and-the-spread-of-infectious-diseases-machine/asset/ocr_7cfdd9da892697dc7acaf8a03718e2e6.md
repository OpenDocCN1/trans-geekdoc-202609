264 The Case of Malaria

# 16.3.1 Modelling with caret

To train a machine learning model to predict future trends in malaria transmission, we will be using 80% of the original data to train the model and 20% to test it. Then, we will evaluate its performance using the Root Mean Squared Error (RMSE).

The {caret} package provides a unified interface for training and evaluating machine models in R (Chapter 8). It supports a wide range of algorithms and provides tools for hyperparameter tuning, cross-validation, and model evaluation.

```
# Load libraries and check for conflicts
library(caret)
conflicted::conflicts_prefer(dplyr::lag)
```

# 16.3.1.1 Feature Engineering

Create lagged variables to capture the temporal dynamics of malaria transmission. For time series forecasting, it's helpful to create variables, which represent past values of the target variable. This allows the model to learn from previous values.

```
# Create lagged features (e.g., previous year's)
nigeria_cases <- niger_cases %%
arrange(year) %%
mmutate(lag_1 = lag(positive, 1),
       lag_2 = lag(positive, 2),
       lag_3 = lag(positive, 3)) %>%%
drop_na()
```

```
head(nigeria_cases)
# A tibble: 6 x 5
#   year positive lag_1 lag_2 lag_3
#   <int>    dbl   <dbl> <dbl> <dbl>
# 1  1989    134    1276     7  873
# 2  1990    352    134  1276     7
# 3  1992     92    352  134  1276
# 4  1996    331      92    352  134
# 5  1998     98    331    352    92
# 6  1999     36      98    331    92
```

Create partition for training and testing data using the createDataPartition() function from the caret package.

```
set.seed(123)
train_index <- createDataPartition(nigeria_cases$positive,
                                   p = 0.8, list = FALSE)
train <- nigeria_cases[train_index, ]ntest <- nigeria_cases[-train_index, ]
```

# 16.3.1.2 Model Selection and Training (Parameter Calibration)

Define the machine learning model specific for investigating Malaria dynamics. In this case, we will use the time and number of lagged cases to predict the number of infected cases.