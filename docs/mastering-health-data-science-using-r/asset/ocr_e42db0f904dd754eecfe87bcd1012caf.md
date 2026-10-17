```
#> [9] "LEAD" "BMI_CAT" "LEAD_QUANTILE" "HYP"
#> [13] "ALC" "DBP1" "DBP2" "DBP3"
#> [17] "DBP4" "SBP1" "SBP2" "SBP3"
#> [21] "SBP4"
```

To start our exploration, we look at whether there are any missing values. We use the complete.cases() function to observe that there are no complete cases. We also see that the subsequent blood pressure measurements and alcohol use have the highest percentage of missing values. For demonstration, we choose to only keep the first systolic and diastolic blood pressure measurements and do a complete case analysis using the na.omit() function to define our complete data frame nhanes_df.

```
sum(complete.cases(NHANESsample))
#> [1] 0
apply(NHANESsample, 2, function(x) sum(is.na(x)))/nrow(NHANESsample)
#> ID AGE SEX RACE EDUCATION
#> 0.000000 0.000000 0.000000 0.000000 0.000672
#> INCOME SMOKE YEAR LEAD BMI_CAT
#> 0.000000 0.000000 0.000000 0.000000 0.000000
#> LEAD_QUANTILE HYP ALC DBP1 DBP2
#> 0.000000 0.000000 0.026867 0.060035 0.063905
#> DBP3 DBP4 SBP1 SBP2 SBP3
#> 0.070974 0.891124 0.060035 0.063905 0.070942
#> SBP4
#> 0.891124
```

```
nhanes_df <- na.omit(subset(NHANESsample,
select = -c(SBP2, SBP3, SBP4, DBP2, DBP3,
DBP4)))
```

In the last chapter, we introduced the table() and summary() functions to quickly summarize categorical and quantitative vectors. We can observe that over half of the observations never smoked and that the most recent NHANES cycle in the data is 2017-2018.

```
table(nhanes_df$SMOKE)
#> NeverSmoke QuitSmoke Stillsmoke
#> 13774 8019 6799
summary(nhanes_df$YEAR)
```