
## 8.2 Essential R Packages for Machine Learning

Some of the most used modelling packages that are particularly useful for machine modelling of the spread of infectious diseases and evaluating DALYs variation due to infectious include:

### 8.2.1 Meta-Packages

- 1. {tidymodels}¹ This framework provides a collection of packages for modelling and machine learning tasks, including {tidyr}, {dplyr}, and ggplot2. It offers a consistent and tidy workflow for preprocessing, model building, evaluation, and visualisation.
- 2. {caret}² The caret framework for Classification and REg provides a unified interface for training and evaluating machine learning models. It supports a wide range of algorithms and offers convenient functions for hyperparameter tuning and model selection.
- 3. {mlr3}³ This is a modern and extensible framework for machine learning. It provides a unified interface for modelling tasks, making it easy to train and evaluate a wide range of machine learning algorithms.

### 8.2.2 Engines

Engines are the actual implementations of machine learning algorithms. They perform the computations necessary to train and evaluate models. Engines can be integrated into various meta-packages/frameworks to leverage their specific algorithms and computational efficiencies. Each engine might have its own set of parameters and functionalities, which can be accessed through the high-level interfaces provided by meta-packages.

- 1. {randomForest}: For random forest models.
- 2. {xgboost}: An optimised distributed gradient boosting library designed to be highly efficient, flexible, and portable. It implements machine learning algorithms under the gradient boosting framework.
- 3. {glmnet}: For lasso and ridge regression.
- 4. {nnet}: For neural networks.
- 5. {kernel}: For kernel-based machine learning methods.
- 6. {e1071}: For support vector methods and other functions.
- 7. {lme4}: For linear and generalised mixed-effects models.
- 8. {mgcv}: For generalised additive models.
- 9. {rpart}: For recursive partitioning and regression trees.
- 10. {h2o}: A powerful machine learning framework that can be efficiently integrated with {tidymodels}. {h2o} offers a range of machine learning algorithms, including linear models, tree-based models, and ensemble methods, with efficient handling of large datasets and support for parallel computing.

> ¹Silge and Julia, Tidy Modeling with r.
> ²Max Kuhn, The Caret Package, n.d., https://topepo.github.io/caret/.
> ³Mlr-Org, n.d., https://mlr-org.com/.

{keras3}, the R interface to Keras, is a deep learning technique which provides high-level neural networks API written in Python. Designed to enable fast experimentation with deep learning models on top of {tensorflow} (an open-source machine learning framework developed by Google).

### 2.2.3 Time Series Analysis

- 1. {forecast}: For forecasting functions.
- 2. {prophet}: Specifically designed for time series forecasting with an emphasis on flexibility and ease of use. Developed by Facebook, prophet can handle various time series patterns, including seasonality, holiday effects, and trend changes, making it suitable for modelling infectious disease over time.
- 3. {fpp3}:4 this package is part of the Forecasting: Principles and Practice (3rd edition) offering data and tools for forecasting time series data, such as the import of the {fable} package with the ARIMA() model which is relevant for modelling disease spread over time.

### 2.2.4 Bayesian Analysis

- 1. {rms}: For Bayesian generalised multivariate non-linear multilevel models using Stan.
- 2. {rstan}: For Bayesian inference using Stan.

### 2.2.5 Specialized Tools

- 1. {spdep} is a powerful tools for spatial statistics, it provides a set of functions for analysing spatial dependencies and autocorrelation in spatial data, particularly relevant in infectious disease modelling. It also incorporates spatial effects into models and allows for a better understanding of how infectious diseases spread across space.
- 2. {INLA}:5 Integrated Nested Laplace Approximations (INLA) is a package for Bayesian inference using the INLA method. It is particularly useful for spatial and spatio-temporal modelling, which can be relevant for studying the spread of infectious diseases.

These packages offer a diverse set of tools and techniques for modelling infectious disease spread and assessing its impact on health metrics like DALYs. These packages provide valuable insights into the dynamics of infectious diseases and can be used to inform public health interventions and policies. However, whether these are the most suitable depends on various factors, including:

- the specific requirements of the analysis
- the expertise of the researcher
- the nature of the data being used

Each package has its strengths and weaknesses, and the choice of package often depends on factors such as:

- the complexity of the modelling task
- the type of data available
- the preferred modelling approach (e.g., frequentist vs. Bayesian).

For example, tidymodels provides a tidy and consistent workflow for modelling tasks, while ml3 offers extensive support for machine learning algorithms and hyperparameter tuning.

It's also worth considering other packages that may be relevant for specific aspects of the analysis, such as spatial modelling (e.g., spdep) and time forecasting (e.g., prophet).

The features and capabilities of each package should be carefully evaluated in relation to their specific research objectives before choosing the one that best meets needs and objectives. And it is worth considering that experimenting with different packages and techniques may be beneficial to identify the most effective approach for a given analysis.

## 8.3 Model Framework Application Examples

In this section we provide some examples of the application of different model frameworks. Data are used, as introduced in Chapter 7, to demonstrate the application of model frameworks such as ml3, h2o, and keras for machine learning tasks.

We have already shown an application of the {tidymodels} meta-package in Chapter 6 and Chapter 7, particularly useful for testing out different types of models with the help of key functions such as workflow(), workflow_set(), and workflow_map().

### 8.3.1 Example: DALY Due to Dengue with ml3

The dataset for this example is from the {nmsidR} package, which contains data on Deaths, DALYs, YLDs, YLLs, Prevalence, and Incidence due to selected infectious diseases from 1980 to 2021.

```r
library(tidyverse)
hmsidR::infectious_diseases %>%
# [1] "year"               "location_name" "location_id"    "cause_name"
# [5] "Deaths"             "DALYs"           "YLDs"             "YLLs"
# [9] "Prevalence"         "Incidence"
```

Let's have a look at the locations where Dengue has been reported:

```r
nmsidR::infectious_diseases %>%
filter(cause_name == "Dengue") %>%
distinct(location_name)
# A tibble: 5 x 1
# location_name
# <chr>
# 1 Malawi
# 2 Central African Republic
# 3 Lesotho
# 4 Eswatini
# 5 Zambia
```

And look at how the health metrics shape up over the years for Dengue:

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_134_0.png)

**Figure 8.1** Health Metrics due to Dengue

The trend of the metrics in some locations is quite flat ranging around zero, while in others it is more evident. YLLs are the leading cause of DALYs, but YLDs are also contributing to the burden. We focus on DALYs due to Dengue in three locations, Malawi, Zambia, and Central African Republic. The data from 2017 to 2021 (5 years) is not included and held out to be testing, as shown in Chapter 9. Data are preprocessed to remove missing values, the values of DALYs only appeared in 1990, and then grouped by location id; the location name is removed.

```r
dalys_dengue <- hmsidR::infectious_diseases %>%
  filter(cause_name == "Dengue",
  arrange(year),
  location_name %in% c("Eswatini", "Lesotho")) %>%
  drop_na() %>%
  group_by(location_id) %>%
  select(-location_name)
```

```r
dalys_dengue %>%
head()
# # A tibble: 6 x 7
# # Groups: location_id [3]
#   year location_id Deaths DALYs YLDs YLLs Prevalence
#   <int> <chr> <num> <num> <num> <num> <num>
# 1    1990     1   182.0   7.59  5.35  2.24      33.7
# 2    1991     1   191.0   6.88  6.64  0.23      42.4
# 3    1990     2   169.0   2.25 -13.1  0.00      22.0
# 4    1991     1   191.0   8.57  8.54  0.23      52.5
# 5    1991     1   182.0   8.68  6.47  2.21      40.9
# 6    1991     2   169.0   2.23  2.22  0.12      13.0
```

The {mlr3} is a meta-package particularly useful for its syntax, it guides the user through the machine learning steps by providing a consistent naming convention. It is also useful for benchmarking different models. In addition to the {mlr3} package, {mlr3learners}, {mlr3viz}, and {mlr3verse}, and {data.table} packages are also loaded. Each of these

> ^4Forecasting: Principles and Practice (3rd Ed), n.d., https://otexts.com/fpp3/
^5R-INLA Project - What is INLA?” n.d., https://www.r-inla.org/what-is-inla.
