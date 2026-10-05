# Data Processing

| index | patientid | date | bp_systolic | bp_diastolic |
|---|---|---|---|--|
| 0 | 1 | 02/01/22 | 120 | 76.0 |
| 1 | 1 | 02/02/22 | 127 | 75.0 |
| 2 | 1 | 02/03/22 | 127 | 70.0 |
| 3 | 1 | 02/04/22 | 127 | 76.0 |
| 4 | 1 | 02/05/22 | -20 | 74.0 |

Notice there are some irregularities with data types. The systolic pressure column contains integers, while the diastolic blood pressure column looks like floating point values, `flo`. For consistency and to avoid issues later, we should investigate the data further, think about which type makes sense, and make the appropriate conversions.

We can check the data types of the dataframe by retrieving its dtypes like this:

```
df.dtypes

OUT:
patientid    int64
date         object
bp_systolic  int64
bp_diastolic float64
```

This confirms our suspicion. One thing to note is that a missing value in a column will result in the entire column having the float data type. Let's summarize the data next by calling describe() which is a fast way to compute column counts, percentiles, means, and standard deviations (std).

```
df.describe()
```

| | patientid | bp_systolic | bp_diastolic |
|---|---|---|--|
| count | 98.000000 | 98.000000 | 98.000000 |
| mean | 2.595960 | 124.171717 | 75.653061 |
| std | 0.978537 | 16.744198 | 5.143512 |
| min | 1.000000 | -26.000000 | 70.000000 |
| 25% | 2.000000 | 122.000000 | 73.250000 |
| 50% | 3.000000 | 128.000000 | 74.000000 |
| 75% | 3.000000 | 128.000000 | 77.000000 |
| max | 4.000000 | 200.000000 | 120.000000 |

Notice there are 99 systolic blood pressure values, but only 98 diastolic values. Let's check for missing values by calling the isnnull() function on the bp_diastolic column: