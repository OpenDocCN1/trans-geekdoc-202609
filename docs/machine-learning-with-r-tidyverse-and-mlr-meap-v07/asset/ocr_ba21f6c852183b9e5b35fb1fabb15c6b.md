When your data has a mixture of categorical and continuous predictors, as naive Bayes assumes independence between them, it simply uses the appropriate method for estimating the likelihood, depending on whether each predictor is categorical or continuous.



In this section, I’ll teach you how to build and evaluate the performance of a naive Bayes model to predict political party affiliation. Imagine you’re a political scientist. You’re looking for common voting patterns in the mid 1980s that would predict whether a USA congressperson was a Democrat or Republican. You have the voting record of each member of the House of Representatives in 1984, and identify 16 key votes you believe most strongly split the two political parties. Your job is to train a naive Bayes model to predict whether a congressperson was a Democrat or a Republican, based on how they voted throughout the year. Let’s start by loading the mlr and tidyverse packages.

```
library(mlr)
library(tidyverse)
```



Now, let’s load the data, which is built into the mlbench package, convert it into a tibble (with as_tibble()) and explore it a little.

> NOTE Remember that a tibble is just a tidyverse version of a data frame that helps make our lives a little easier.

We have a tibble containing 435 cases and 17 variables of members of the House Representatives in 1984. The Class variable is a factor indicating political party membership, and the other 16 variables are factors indicating how the individuals voted on each of the 16 votes. A value of "y" means they voted in favor, a value of "n" means they voted against, a missing value (NA) means the individual either abstained or did not vote. Our goal is to train a model which can use the information in these variables to predict whether a congressperson was a Democrat or Republican, based on how they voted.