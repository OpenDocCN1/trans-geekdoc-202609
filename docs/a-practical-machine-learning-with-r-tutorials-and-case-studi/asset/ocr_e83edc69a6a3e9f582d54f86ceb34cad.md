# 3 Introduction to R and RStudio

```
## SurvivedPassClass Sex Age FairInPounds
## 1 0 3 male 45 6.975
## 2 0 3 male 19 6.750
## 3 0 3 male 36 0.000
## 4 0 3 male 34 6.496
## 5 0 1 male 40 0.000
## 6 1 3 male 25 0.000
```

If you look carefully at the output, you can see that it includes fares that are 0. These are most likely observations with missing fares. Ideally, these FairInPounds entries should be NA (not available), but in this dataset, they are 0. We can throw out these observations by combining the two conditions with an &;

```
TitanicLowFare=filter(TitanicNarrow,
FairInPounds<7 & FairInPounds>0)
head(TitanicLowFare)
```

```
## SurvivedPassClass Sex Age FairInPounds
## 1 0 3 male 45 6.975
## 2 0 3 male 19 6.750
## 3 0 3 male 34 6.496
## 4 0 3 male 61 6.237
## 5 0 3 male 18 6.496
## 6 0 3 male 20 4.013
```

You can now see that the output contains no observations with 0 fare.

# Analyzing only passengers 60 years and older (seniors):

To analyze only passengers with an age of 60 or greater and then save the results in the new data frame TitanicSeniors, we can use the following R code:

```
TitanicSeniors=filter(TitanicNarrow, Age>=60)
head(TitanicSeniors)
```

```
## SurvivedPassClass Sex Age FairInPounds
## 1 0 2 male 66.0 10.50
## 2 0 1 male 65.0 61.98
## 3 0 1 male 64.0 27.72
## 4 0 1 male 71.0 54.65
## 5 0 3 male 70.5 7.75
## 6 0 1 male 60.0 25.93
```