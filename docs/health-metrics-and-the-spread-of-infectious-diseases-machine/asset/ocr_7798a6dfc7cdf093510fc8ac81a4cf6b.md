74

Introduction to Machine Learning

Here, f represents the relationship between the predictors and the response, and epsilon represents the error term, which captures the difference between the observed values of y and the values predicted by the model. To estimate the coefficients of the model function, we employ statistical techniques such as linear regression for continuous response variables, and various machine learning algorithms that include tuning parameters to handle more complex dataset and model specifications. These techniques analyse the relationship between the predictors and the response in the dataset and determine the optimal coefficients that minimise the difference between the observed (y) values and values predicted by the model (y).

Once the model coefficients are estimated, we can use the model function to predict future values of y for new values of predictors xi. This allows us to simulate the effect of different scenarios or make predictions about future outcomes based on the relationships identified in the data. Overall, the model development process is a crucial step in the methodology framework, as it sets the foundation for understanding and analysing the relationships between variables in a given system. It enables us to extract insights from the data, make predictions, and influence decision-making in various fields, including epidemiology, public health, economics, and environmental science.

# 6.3.1 Example: Cholera

The first dataset used is the {HistData} package HistData::CholeraDeaths1849, made of 730 observations and 6 variables, with 2 causes of deaths: cholera and diarrhoea. For this example we select the deaths due to cholera within 12 months in 1849. Let's look at the first 6 rows of the dataset:

```
library(tidyverse)
library(HistData)
```

```
cholera <- HistData::CholeraDeaths1849 %>%
  filter(cause_of_death == "Cholera") %>%
  select(date, deaths)
```

```
cholera %>% head()
# # A tibble: 6 x 2
#    date        deaths
#    <date>      dbl
# 1 1849-01-01   13
# 2 1849-01-02   19
# 3 1849-01-03   28
# 4 1849-01-04   24
# 5 1849-01-05   23
# 6 1849-01-06   39
```

The response variable is y = deaths due to cholera, and the only predictor we are considering on this first step is x = date in days from 1849-01-01 to 1849-12-31. Let's practise our data using the {ggplot2} package with geom_line() as layer.

```
cholera %>%
  ggplot(aes(x = date, y = deaths)) +
  geom_line() +
  labs()
```