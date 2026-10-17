# Case Study: Cleaning Tuberculosis Screening Data

In this chapter, we put some of our R skills together in a case study. This case study focuses on data cleaning and pre-processing. We use the tb_diagnosis_raw data from the HDSinRdata package. This data contains information on 1,634 patients in rural South Africa who presented at a health clinic with tuberculosis-related symptoms and were tested for tuberculosis (TB) using Xpert MTB/RIF. Our goal is to clean this data to reflect the pre-processing described in Baik et al. (2020). This paper uses this data to derive a simple risk score model for screening patients for treatment while awaiting Xpert results. We use the tidyverse packages as well as the summary tables from gtsummary.

```
library(HDSinRdata)
library(tidyverse)
library(gt)
library(gtsummary)
```

To begin, read in the data and review the description of the original columns. Some things to note in the data documentation are the ways unknown, missing, or refused values are coded as well as how some of the columns are related to each other.

```
# Read in data
data("tb_diagnosis_raw")

# Inspect variable descriptions
# ?tb_diagnosis_raw
```

To start, we select variables needed for our analysis. In particular, we drop columns related to the participation in the survey and about seeking care. Since some of these variables contain long or vague names, we also rename most of the variables.