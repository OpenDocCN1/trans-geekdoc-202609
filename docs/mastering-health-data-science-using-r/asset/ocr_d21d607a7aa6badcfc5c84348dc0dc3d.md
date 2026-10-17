In this chapter, we look at hypothesis testing in R. We start with single sample distributions and tests, and then we look at hypothesis tests for comparing two samples. Examples include testing for positive correlations, performing two-sample paired t-tests, and testing for equal variance among groups. The data we use in this section comes from the Texas Health and Human Services Department and includes the reported number of induced terminations of pregnancy (ITOPs) from 2016 to 2021, stratified by both race and county (Texas Health & Human Services Commission 2016-2021). The data also contains the rate of abortions per 1000 females aged 15-49. Read the data documentation to see the full variable descriptions.

We use the **tidyverse**, **gt**, and **gtsummary** packages to help manipulate and summarize the data. The **car** package (Fox, Weisberg, and Price 2023) contains the function `leveneTest()` to implement a Levene's test for homogeneity of variance across groups, and all other hypothesis tests are available in base R.

```
library(tidyverse)
library(car)
library(HDSinRdata)
library(gt)
library(gtsummary)

data(tex_itop)
```

# 11.1 Univariate Distributions and One-Sample Tests

Let's begin by looking at a single outcome of interest - the number of induced terminations of pregnancy (referred to as ITOPs or abortions below) in 2021 per 1000 females ages 15-49 in each county. We use the number of females ages 15-49 as a proxy to scale the number of abortions by the population size,