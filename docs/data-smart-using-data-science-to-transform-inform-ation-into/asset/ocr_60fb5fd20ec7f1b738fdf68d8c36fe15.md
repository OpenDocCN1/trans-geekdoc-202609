So, that's a bit on the pregnancy duration problem. Let's move on to the harder problem of finding outliers in the call center employee performance data. It's in the CallCenter.csv sheet on the book's website. Loading it up and summarizing, you get the following:

```
> CallCenter <- read.csv("CallCenter.csv")
> summary(CallCenter)
```

| ID | AvgTix | Rating | Tardies |
|---|---|---|---|
| Min. :130564 | Min. :143.1 | Min. :2.070 | Min. :0.000 |
| 1st Qu.:134402 | 1st Qu.:153.1 | 1st Qu.:3.210 | 1st Qu.:1.000 |
| Median :137906 | Median :156.1 | Median :3.505 | Median :1.000 |
| Mean :137946 | Mean :156.1 | Mean :3.495 | Mean :1.465 |
| 3rd Qu.:141771 | 3rd Qu.:159.1 | 3rd Qu.:3.810 | 3rd Qu.:2.000 |
| Max. :145176 | Max. :168.7 | Max. :4.810 | Max. :4.000 |

| Graveyards | Weekends | SickDays | PercSickOnFri |
|---|---|---|---|
| Min. :0.000 | Min. :0.0000 | Min. :0.000 | Min. :0.0000 |
| 1st Qu.:1.000 | 1st Qu.:1.0000 | 1st Qu.:0.000 | 1st Qu.:0.0000 |
| Median :2.000 | Median :1.0000 | Median :2.000 | Median :0.2500 |
| Mean :1.985 | Mean :0.9525 | Mean :1.875 | Mean :0.3522 |
| 3rd Qu.:2.000 | 3rd Qu.:1.0000 | 3rd Qu.:3.000 | 3rd Qu.:0.6700 |
| Max. :4.000 | Max. :2.0000 | Max. :7.000 | Max. :1.0000 |

| EmployeeDevHrs | ShiftSwapsReq | ShiftSwapsOffered |
|---|---|---|
| Min. : 0.00 | Min. :0.000 | Min. :0.00 |
| 1st Qu.: 6.00 | 1st Qu.:1.000 | 1st Qu.:0.00 |
| Median :12.00 | Median :1.000 | Median :1.00 |
| Mean :11.97 | Mean :1.448 | Mean :1.76 |
| 3rd Qu.:17.00 | 3rd Qu.:2.000 | 3rd Qu.:3.00 |
| Max. :34.00 | Max. :5.000 | Max. :9.00 |

Just as you did previously, you need to scale and center the data. To do so, you need use only the scale() function.

```
> CallCenter.scale <- scale(CallCenter[2:11])
```

Now that the data is prepped, you need to send it through an local outlier factor (LOF) function. Luckily that's part of the Rlof package.

```
install.packages('Rlof')
library(Rlof)
```

To call the lof() function, you supply it the data and a k value (this example uses 5, just like in the exercise), and the function spits out LOFs.

```
CallCenter.lof <- lof(CallCenter.scale, 5)
```

Data with the highest factors (LOFs usually hover around 1) are the oddest points. For instance, you can highlight the data associated with those employees whose LOF is greater than 1.5 and assign it to data frame for further investigation.

```
> which(CallCenter.lof > 1.5)
[1] 299 374
> Callcenter.df <- CallCenter[which(CallCenter.lof > 1.5), ] %>% data.frame()
```