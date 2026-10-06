# Making base R objects "tidy"

The tidyverse packages (including dplyr, tidyr, and ggplot2) have a huge influence on data processing and analysis in R, through their application of the "tidy" way of working. In essence, "tidy" means that data is kept in a particular format, which each row holds a single observation of some variable, and columns the variables recorded and contain all values for those variables across all observations. Such a structure means that analytics have predictable input and can be built into complex pipelines with relative ease. Most base R objects are not tidy, and it can often take significant programming to extract the parts that are needed downstream. In this recipe, we will look at some functions to automatically convert some common base R objects into a tidy dataframe.

# Getting ready

We'll need tidyr, broom, and also biobroom from Bioconductor. For data, we'll use the danmacacle/rbioinfocookbook package and the built-in mtcars and iris datasets.

# How to do it...

Making base R objects tidy can be done using the following steps:

+   1. Tidy an lm object:

+   2. Tidy a t.test object:

```
t_test_result <- t.test(x = rnorm(20), y = rnorm(20) )
tidy(t_test_result)
```

+   3. Tidy an ANOVA object:

```
anova_result <- aov(Petal.Length ~ Species, data = iris)
tidy(anova_result)
post_hoc <- TukeyHSD(anova_result)
tidy(post_hoc)
```

+   4. Tidy a Bioconductor ExpressionSet object:

```
library(biobroom)
library(BioBase)
library(rbioinfocookbook)
```