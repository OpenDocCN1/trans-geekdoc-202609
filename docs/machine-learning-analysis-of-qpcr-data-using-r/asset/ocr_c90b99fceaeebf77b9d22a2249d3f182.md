There are also more advanced functions to explore the data that requires specialized libraries (*Hmisc and VIM*):

```
```r
> library(Hmisc)
> describe(cleaned)

cleaned

8 Variables    5040 Observations

-------------------------------------------------------------------------------

        Run
n       missing     distinct    Info    Mean    Gmd
5040    0           8           0.968   11.67   5.161
lowest : 1  8  10  12  13, highest: 12 13 14 15 16
Value          1      8     10     12     13     14     15     16
Frequency    714    420    504    588    252    504    630   1428
Proportion  0.142  0.083  0.100  0.117  0.050  0.100  0.125  0.283

-------------------------------------------------------------------------------

        Cycle
n       missing     distinct    Info    Mean    Gmd    .05    .10    .25
5040    0           42          0.999   21.5    13.99  3.0    5.0    11.0
.50     .75         .90         .95
21.5    32.0        38.0        40.0
lowest : 1  2  3  4  5, highest: 38 39 40 41 42

-------------------------------------------------------------------------------

        FAM
n       missing distinct    Info    Mean    Gmd    .05    .10    .25
5040    0       4998        1       2834    382.1  2336   2467   2597
.50     .75     .90         .95
2791    2890    3099        3825
lowest : 2258.000 2260.013 2260.269 2260.344 2260.812
highest: 5766.148 5772.516 5787.097 5806.523 5806.575
```
```