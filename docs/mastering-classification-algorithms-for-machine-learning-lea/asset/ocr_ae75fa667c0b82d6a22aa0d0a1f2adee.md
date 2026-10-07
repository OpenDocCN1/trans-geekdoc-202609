# Mastering Classification Algorithms for Machine Learning

| 4 | 0.0 | 0.0 | 1.0 |
| 5 | 0.0 | 1.0 | 0.0 |
| 6 | 0.0 | 0.0 | 1.0 |
| 7 | 0.0 | 0.0 | 1.0 |
| 8 | 0.0 | 0.0 | 1.0 |
| 9 | 0.0 | 1.0 | 0.0 |

Note that three columns are created for the three values in the “Designation” column. We will get as if we add these columns to our original data frame:

```
df = pd.concat([df, dfTemp], axis = 1)
df[['Name', 'Designation', 'Designation_Director', 'Designation_Manager', 'Designation_Programmer']]
```

| Name | Designation | Designation_Director | Designation_Manager |
| 0 | Partha | | 1.0 | 0.0 |
| 1 | Deepshree | Manager | 0.0 | 1.0 |
| 2 | Riya | Programmer | 0.0 | 0.0 |
| 3 | Ranoo | Programmer | 0.0 | 0.0 |
| 4 | Ujala | Programmer | 0.0 | 0.0 |
| 5 | Anita | Manager | 0.0 | 1.0 |
| 6 | Nomita | Programmer | 0.0 | 0.0 |
| 7 | Anil | Programmer | 0.0 | 0.0 |
| 8 | Amarendra | Programmer | 0.0 | 0.0 |
| 9 | Anuj | Manager | 0.0 | 1.0 |

| Designation_Programmer | |
| 0 | 0.0 |
| 1 | 0.0 |
| 2 | 1.0 |
| 3 | 1.0 |