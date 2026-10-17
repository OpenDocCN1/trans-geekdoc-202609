# 8

# # Visualization with ggplot2

The package **ggplot2** (Wickham 2016) is another useful package in the **tidyverse** that allows statisticians to use visualizations to communicate key findings and results in a compelling format. In this chapter, we learn about the three main components in a ggplot object and then expand on that format by learning more about the different layers we can use to create various plots. As with the **dplyr** functions, there are many functions to cover, and they build upon one another.

The three packages we use in this chapter are **tidyverse**, **HDSinRdata**, and **patchwork** (Pedersen 2022), the last of which is a nice package for combining multiple plots together into a single figure. We use the data from the Pittsburgh pain clinic (Alter et al. 2021) introduced in **Chapter 3** to create our visuals. You can refresh your memory about this data by reading the data documentation. For the purposes of this chapter, we take a sample of 5,000 patients that are complete cases at baseline to reduce the computation time to display each plot. You can ignore how the code used to find this sample works.

```
```r
library(tidyverse)
library(HDSinRdata)
library(patchwork)
data(pain)

# sampling data
set.seed(5)
pain_df_sub <- subset(pain,
                      select = -c(PAIN_INTENSITY_AVERAGE,FOLLOW_UP))
pain_df <- pain[complete.cases(pain_df_sub), ]
pain_df <- pain_df[sample(1:nrow(pain_df), 5000, replace = FALSE),]
```
```