
## 5.4 Summarizing and Grouping

summarize() that finds the number of observations. In the mean() and median() functions we set na.rm=TRUE to remove NAs before computing these values (otherwise, we could get NA as our output).

```r
nhanes_df %>%
filter(RACE == "Non-Hispanic Black") %>%
summarize(TOT = n(), MEAN_SBP = mean(SBP1, na.rm=TRUE),
          MEAN_DBP = mean(DBP1, na.rm=TRUE))
#>
#>   TOT MEAN_SBP MEAN_DBP
#> 1 6041    129   72.6
```

If we wanted to repeat this for the other race groups, we would have to change the arguments to the filter() function each time. To avoid having to repeat our code and/or do this multiple times, we can use the group_by() function, which takes a data frame and one or more columns with which to group the data. In the following code, we group using the RACE variable. When we look at printed output, it looks almost the same as it did before except that we can see that its class is now a grouped data frame, which is printed at the top. In fact, a grouped data frame (or grouped tibble) acts like a set of data frames: one for each group. If we use the slice() function with index 1, it returns the first row for each group.

```r
nhanes_df %>%
group_by(RACE) %>%
slice(1)
#> # A tibble: 5 x 20
#> # Groups:   RACE [5]
#>    AGE SEX   RACE  EDUCATION PIR SMOKE_STATUS YEAR LEAD
#>  <dbl> <fct> <fct> <fct>     <dbl> <chr>      <dbl> <dbl>
#> 1   70 Male  Mexican~ LessThan~ 1.07 Quit Smoking 1999 1.6
#> 2   61 Female Other H~ MoreThan~ 3.33 Current Smo~ 1999 2.2
#> 3   77 Male  Non-His~ MoreThan~ 5   Never Smoked 1999 5
#> 4   38 Female Non-His~ HS        0.92 Current Smo~ 1999 1.8
#> 5   63 Female Other R~ MoreThan~ 5   Never Smoked 1999 1.2
#> # i 11 more variables: HYP <dbl>, ALC <chr>, DBP1 <dbl>, DBP2 <dbl>,
#> #   DBP3 <dbl>, DBP4 <dbl>, SBP1 <dbl>, SBP2 <dbl>, SBP3 <dbl>,
#> #   SBP4 <dbl>, EVER_SMOKE <chr>
```

Grouping data is very helpful in combination with the `summarize()` function. Like with the `slice()` function, `summarize()` calculates the summary values for each group. We can now find the total number of observations as well as the mean systolic and diastolic blood pressure values for each racial group. Note that the returned summarized data is in a tibble.

```r
nhanes_df %>%
  group_by(RACE) %>%
  summarize(TOT = n(), MEAN_SBP = mean(SBP1, na.rm=TRUE),
            MEAN_DBP = mean(DBP1, na.rm=TRUE))
#> # A tibble: 5 x 4
#>   RACE                   TOT MEAN_SBP MEAN_DBP
#>   <fct>                <int>    <dbl>    <dbl>
#> 1 Mexican American      5277      124.     70.4
#> 2 Other Hispanic        2279      123.     70.1
#> 3 Non-Hispanic White   15473      125.     70.4
#> 4 Non-Hispanic Black    6041      129.     72.6
#> 5 Other Race            2195      122.     72.6
```

After summarizing, the data is no longer grouped by race. If we ever want to remove the group structure from our data, we can use the `ungroup()` function, which restores the data to a single data frame. After ungrouping by race, we can see that we get a single observation returned by the `slice()` function.

```r
nhanes_df %>%
  select(SEX, RACE, SBP1, DBP1) %>%
  group_by(RACE) %>%
  ungroup() %>%
  arrange(desc(SBP1)) %>%
  slice(1)
#> # A tibble: 1 x 4
#>   SEX    RACE                    SBP1  DBP1
#>   <fct>  <fct>                  <dbl> <dbl>
#> 1 Female Non-Hispanic White      270   124
```

### 5.4.1 Practice Question

Create a data frame summarizing the percent of patients with hypertension by smoking status. The result should look like Figure 5.2.

| SMOKE_STATUS | PCT_HYP |
|---|---|
| <chr> | <dbl> |
| Current Smoker | 0.5096351 |
| Never Smoked | 0.5140850 |
| Quit Smoking | 0.6559079 |

Figure 5.2: Grouping and Summarizing Data.

```r
# Insert your solution here:
```

## 5.5 Exercises

The following exercises use the covidcases dataset from the HDSinRdata package. Before completing the exercises, be sure to read the documentation for this data (?covidcases).

```r
data(covidcases)
```

- 1. Suppose we are interested in the distribution of weekly cases by state. First, create a new column in covidcases called region specifying whether each state is in the Northeast, Midwest, South, or West (you can either do this by hand using this list¹ of which states are in which region, or you can use state.region from the datasets package in R). Then, create a data frame summarizing the average and standard deviation of the weekly cases for the Northeast.

- 2. Now, create a data frame with the average and standard deviation summarized for each region rather than for just one selected region as in Question 1. Sort this data frame from highest to lowest average weekly cases. What other information would you need in order to more accurately compare these regions in terms of their average cases?

¹https://en.wikipedia.org/wiki/List_of_regions_of_the_United_States

- 3. Find the ten counties in the Midwest with the lowest weekly deaths in week 15 of this data ignoring ties (use `slice_min()` to find the argument needed for this). What do you notice about the minimum values? See the data documentation for why we observe these values.

- 4. Filter the data to include weeks 9 and 20 (around the start of the pandemic), get the total cases per county during that time frame, and then find the county in each state that had the highest number of total cases.

## Case Study: Cleaning Tuberculosis Screening Data

In this chapter, we put some of our R skills together in a case study. This case study focuses on data cleaning and pre-processing. We use the tb_diagnosis_raw data from the HDSinRdata package. This data contains information on 1,634 patients in rural South Africa who presented at a health clinic with tuberculosis-related symptoms and were tested for tuberculosis (TB) using Xpert MTB/RIF. Our goal is to clean this data to reflect the pre-processing described in Baik et al. (2020). This paper uses this data to derive a simple risk score model for screening patients for treatment while awaiting Xpert results. We use the tidyverse packages as well as the summary tables from gtsummary.

```r
library(HDSinRdata)
library(tidyverse)
library(gt)
library(gtsummary)
```

To begin, read in the data and review the description of the original columns. Some things to note in the data documentation are the ways unknown, missing, or refused values are coded as well as how some of the columns are related to each other.

```r
# Read in data
data("tb_diagnosis_raw")

# Inspect variable descriptions
# ?tb_diagnosis_raw
```

To start, we select variables needed for our analysis. In particular, we drop columns related to the participation in the survey and about seeking care. Since some of these variables contain long or vague names, we also rename most of the variables.

```r
# Select variables and rename
tb_df <- tb_diagnosis_raw %>%
  select(c(xpert_status_fac, age_group, sex, hiv_status_fac,
           other_conditions_fac___1, other_conditions_fac___3,
           other_conditions_fac___88, other_conditions_fac___99,
           symp_fac___1, symp_fac___2, symp_fac___3, symp_fac___4,
           symp_fac___99, length_symp_unit_fac, length_symp_days_fac,
           length_symp_wk_fac, length_symp_mnt_fac, length_symp_yr_fac,
           smk_fac, dx_tb_past_fac, educ_fac)) %>%
  rename(tb = xpert_status_fac, hiv_pos = hiv_status_fac,
         cough = symp_fac___1, fever = symp_fac___2,
         weight_loss = symp_fac___3, night_sweats = symp_fac___4,
         symptoms_missing = symp_fac___99,
         ever_smoke = smk_fac,
         past_tb = dx_tb_past_fac, education = educ_fac)
```

We then use a summary table to understand the initial distributions of the variables observed. This also highlights where we have missing or unknown data.

```r
tbl_summary(tb_df) %>%
as_gt()
```

| Characteristic | N = 1,634 |
|---|---|
| tb | |
| 1 | 765 (47%) |
| 2 | 869 (53%) |
| age_group | |
| [15,25) | 240 (15%) |
| [25,35) | 333 (20%) |
| [35,45) | 385 (24%) |
| [45,55) | 343 (21%) |
| [55,99) | 333 (20%) |
| sex | |
| 1 | 830 (51%) |
| 2 | 804 (49%) |
| hiv_pos | |
| 1 | 632 (39%) |
| 2 | 815 (50%) |
| 77 | 139 (8.5%) |
| 88 | 48 (2.9%) |
| other_conditions_fac___1 | 895 (55%) |
