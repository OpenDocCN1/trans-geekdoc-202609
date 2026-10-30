|  | GarageArea | TotalBsmtSF | YearBuilt | 1stFlrSF | MasVnrArea | TotRmsAbvGrd | GrLivArea |
|---|---|---|---|---|---|---|---|
| 30 | 250 | 649 | 1920 | 649 | 0.0 | 6 | 1317 |
| 88 | 0 | 1013 | 1915 | 1013 | 0.0 | 6 | 1526 |
| 462 | 360 | 864 | 1965 | 864 | 0.0 | 5 | 864 |
| 523 | 884 | 3138 | 2007 | 3138 | 762.0 | 11 | 4676 |
| 632 | 544 | 1386 | 1977 | 1411 | 209.0 | 6 | 1411 |
| 1298 | 1418 | 6110 | 2008 | 4692 | 796.0 | 12 | 5642 |
| 1324 | 895 | 1795 | 2006 | 1795 | 428.0 | 7 | 1795 |

# Figure 7.33: Outlier Table

Now we will delete the outliers via the index lists.

```
raw_data = raw_data.drop(raw_data.index[outliers])
raw_data.reset_index(drop=True, inplace=True)
raw_data.shape()
```

[23]: (1453, 81)

# Figure 7.34: New Data shape

So, we have removed 7 rows of outliers which were most common.