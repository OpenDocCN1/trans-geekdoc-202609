+   1. Go to File
2. Click New Project
3. Choose New Directory or Existing Directory.

This directory points to the folder that usually contains the dataset to be analyzed. This is called as the working directory. Make sure there is a folder named as data in the folder. If there is not, create one. Make the dataset stroke.data is inside the data folder in the working directory.

# 8.6.2 Loading libraries

Next, we will load the necessary packages. We will use 5 packages

+   1. the built in stat package - to run Generalized Linear Model. This is already loaded by default.
2. haven - to read SPSS, STATA and SAS dataset
3. tidverse - to perform data transformation
4. gsummary - to provide nice results in a table
5. broom - to tidy up the results
6. LogisticDx - to do model assessment
7. here - to ensure proper directory

To load these packages, we will use the function library():

```
library(haven)
library(tidyverse)

# Attaching core tidyverse packages             tidyverse 2.0.0 ---

# v dplyr      1.1.1  vread      2.1.4
# v forcats    1.0.0  string    1.5.0
# v ggplot2    3.4.2  v tibble    3.2.1
# v lubridate  1.9.2  v tidyr     1.3.0
# v purrr      1.0.1
---
Conflicts
tidyverse_conflicts() --
# x dplyr::filter() masks stats::filter()
# x dplyr::lag()    masks stats::lag()
# i      Use  the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

```
library(gtsum)
```