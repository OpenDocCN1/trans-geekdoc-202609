
coded in R and not always in Python. The R offering in Bayesian packages in general (https://cran.r-project.org/web/views/Bayesian.html) and in Bayesian learning in particular is probably unmatched.

There are currently several ML frameworks available in R.

- caret: https://topepo.github.io/caret/index.html, a compilation of more than 200 ML models;
- tidymodels: https://github.com/tidymodels, a recent collection of packages for ML workflow (developed by Max Kuhn at RStudio, which is a token of high quality material!);
- rtemis: https://rtemis.netlify.com, a general purpose package for ML and visualization;
- mlr3: https://mlr3.mlr-org.com/index.html, also a simple framework for ML models;
- h2o: https://github.com/h2oai/h2o-3/tree/master/h2o-r, a large set of tools provided by h2o (coded in Java);
- Open ML: https://github.com/openml/openml-r, the R version of the OpenML (www.openml.org) community.

Moreover, via the reticulate package, it is possible (but not always easy) to benefit from Python tools as well. The most prominent example is the adaptation of the tensorflow and keras libraries to R. Thus, some very advanced Python material is readily available to R users. This is also true for other resources, like Stanford's CoreNLP library (in Java) which was adapted to R in the package coreNLP (which we will not use in this book).

## Coding instructions

One of the purposes of the book is to propose a large-scale tutorial of ML applications in financial predictions and portfolio selection. Thus, one keyword is **REPRODUCIBILITY**! In order to duplicate our results (up to possible randomness in some learning algorithms), you will need running versions of R and RStudio on your computer. The best books to learn R are also often freely available online. A short list can be found here https://rstudio.com/resources/books/. The monograph R for Data Science is probably the most crucial.

In terms of coding requirements, we rely heavily on the **tidyverse**, which is a collection of **packages** (or libraries). The three packages we use most are **dplyr** which implements simple data manipulations (filter, select, arrange), **tidyr** which formats data in a tidy fashion, and **ggplot**, for graphical outputs.

A list of the packages we use can be found in Table 1 below. Packages with a star * need to be installed via *bioconductor*.² Packages with a plus + need to be installed **manually**.³

## TABLE 1: List of all packages used in the book.

| Package | Purpose | Chapter(s) |
|---|---|---|
| BART | Bayesian additive trees | 10 |
| broom | Tidy regression output | 5 |
| CAM+ | Causal Additive Models | 15 |
| caTools | AUC curves | 11 |
| CausalImpact | Causal inference with structural time series | 15 |
| cowplot | Stacking plots | 4 & 13 |
| breakDown | Breakdown interpretability | 14 |
| dummies | One-hot encoding | 8 |
| e1071 | Support Vector Machines | 9 |
| factoextra | PCA visualization | 16 |
| fastAdaboost | Boosted trees | 7 |
| forecast | Autocorrelation function | 4 |
| FNN | Nearest Neighbors detection | 16 |
| ggpubr | Combining plots | 11 |
| glmnet | Penalized regressions | 6 |
| iml | Interpretability tools | 14 |
| keras | Neural networks | 8 |
| lime | Interpretability | 14 |
| lmtest | Granger causality | 15 |
| lubridate | Handling dates | All (or many) |
| naivebayes | Naive Bayes classifier | 10 |
| pcalg | Causal graphs | 15 |
| quadprog | Quadratic programming | 12 |
| quantmod | Data extraction | 4, 12 |
| randomForest | Random forests | 7 |
| rBayesianOptimization | Bayesian hyperparameter tuning | 11 |
| ReinforcementLearning | Reinforcement Learning | 17 |
| Rgraphviz* | Causal graphs | 15 |
| rpart and rpart.plot | Simple decision trees | 7 |
| spBayes | Bayesian linear regression | 10 |
| tidyverse | Environment for data science, data wrangling | All |
| xgboost | Boosted trees | 7 |
| xtable | Table formatting | 4 |

Of all of these packages (or collections thereof), the **tidyverse** and **lubridate** are compulsory in almost all sections of the book. To install a new package in R, just type

```
install.packages("name_of_the_package")
```

in the console. Sometimes, because of function name conflicts (especially with the select() function), we use the syntax package::function() to make sure the function call is from the function.

²One example: https://www.bioconductor.org/packages/release/bioc/html/Rgraphviz.html
³By copy-pasting the content of the package in the library folder. To get the address of the folder, execute the command .libPaths() in the R console.

right source. The exact version of the packages used to compile the book is listed in the “renv.lock” file available on the book’s GitHub web page https://github.com/shokru/mlfactor.github.io. One minor comment is the following: while the functions gather() and spread() from the dplyr package have been superseded by pivot_longer() and pivot_wider(), we still use them because of their much more compact syntax.

As much as we could, we created short code chunks and commented each line whenever we felt it was useful. Comments are displayed at the end of a row and preceded with a single hashtag #.

The book is constructed as a very big notebook, thus results are often presented below code chunks. They can be graphs or tables. Sometimes, they are simple numbers and are preceded with two hashtags ##. The example below illustrates this formatting.

```
1+2 # Example
```

```
## [1] 3
```

The book can be viewed as a very big tutorial. Therefore, most of the chunks depend on previously defined variables. When replicating parts of the code (via online code), please make sure that **the environment includes all relevant variables**. One best practice is to always start by running all code chunks from Chapter 1. For the exercises, we often resort to variables created in the corresponding chapters.

## Acknowledgments

The core of the book was prepared for a series of lectures given by one of the authors to students of master’s degrees in finance at EMLYON Business School and at the Imperial College Business School in the Spring of 2019. We are grateful to those students who asked fruitful questions and thereby contributed to improve the content of the book.

We are grateful to Bertrand Tavit and Gautier Marti for their thorough screening of the book. We also thank Eric André, Aurélie Brossard, Alban Cousin, Frédéric Girod, Philippe Huber, Jean-Michel Maeso, Javier Nogales and for friendly reviews; Christophe Dervieux for his help with bookdown; Mislav Sagovac and Vu Tran for their early feedback; John Kimmel for making this happen and Jonathan Regenstein for his availability, no matter the topic. Lastly, we are grateful for the anonymous reviews collected by John.

## Future developments

Machine learning and factor investing are two immense research domains and the overlap between the two is also quite substantial and developing at a fast pace. The content of this book will always constitute a solid background, but it is naturally destined to obsolescence. Moreover, by construction, some subtopics and many references will have escaped our scrutiny. Our intent is to progressively improve the content of the book and update it with the latest ongoing research. We will be grateful to any comment that helps correct or update the monograph. Thank you for sending your feedback directly (via pull requests) on the book's website which is hosted at https://github.com/shokru/mlfactor.github.io.

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Part I

## Introduction

Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## 1 Notations and data

### 1.1 Notations

This section aims at providing the formal mathematical conventions that will be used throughout the book.

Bold notations indicate vectors and matrices. We use capital letters for matrices and lower case letters for vectors. v' and M' denote the transposes of v and M. M = [m]_{i,j}, where i is the row index and j the column index.

We will work with two notations in parallel. The first one is the pure machine learning notation in which the labels (also called output, dependent variables or predicted variables) y = y_i are approximated by functions of features X_i = (x_{i,1}, ..., x_{i,K}). The dimension of the feature matrix X is I x K: there are I instances, records, or observations and each one of them has K attributes, features, inputs, or predictors which will serve as independent and explanatory variables (all these terms will be used interchangeably). Sometimes, to ease notations, we will write x_i for one instance (one row) of X or x_k for one (feature) column vector of X.

The second notation type pertains to finance and will directly relate to the first. We will often work with discrete returns r_{t,n} = p_{t,n}/p_{t-1,n} - 1 computed from price data. Here t is the time index and n the asset index. Unless specified otherwise, the return is always computed over one period, though this period can sometimes be one month or one year. Whenever confusion might occur, we will specify other notations for returns.

In line with our previous conventions, the number of return dates will be T and the number of assets, N. The features or characteristics of assets will be denoted with x_{t,n}^{(k)}: it is the time-t value of the k^{th} attribute of firm or asset n. In stacked notation, x_{t,n} will stand for the vector of characteristics of asset n at time t. Moreover, r_t stands for all returns at time t while r_n stands for all returns of asset n. Often, returns will play the role of the dependent variable, or label (in ML terms). For the riskless asset, we will use the notation r_{t,f}.

The link between the two notations will most of the time be the following. One instance (or observation) i will consist of one couple (t, n) of one particular date and one particular firm (if the data is perfectly rectangular with no missing field, I = T x N). The label will usually be some performance measure of the firm computed over some future period, while the features will consist of the firm attributes at time t. Hence, the purpose of the machine learning engine in factor investing will be to determine the model that maps the time-t characteristics of firms to their future performance.

In terms of canonical matrices: I_N will denote the (N x N) identity matrix.

From the probabilistic literature, we employ the expectation operator E[.] and the conditional expectation E_t[.], where the corresponding filtration F_t corresponds to all information
