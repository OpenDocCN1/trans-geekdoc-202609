# CHAPTER 4. EXPLORING AND VISUALIZING BEHAVIORAL DATA 120

not easy to be directly in touch with the people who conducted the initial study. One of the reasons may be that you found the dataset online and the project is already over. In those cases, you can try to contact the authors. I have done that several times and they were very responsive. It is also a good idea to find experts in the field even if they were not involved in the project. This will allow you to understand things from their perspective and possibly to explain patterns/values that you may find in the process.

# 4.2 Summary Statistics

Now that you understand how the data was collected and what is the meaning of each variable, it is time to find out how the actual data looks like. It is always a good idea to start looking at some summary statistics. This provides some general insights about the data and will help you in deciding future pre-processing steps. In R, an easy way to do this is with the summary() function. The following code reads the SMARTPHONE ACTIVITIES dataset and to limited space, only prints a summary of the first 5 columns, column 33, 35 and the last one (the class).

```
# Read activities dataset.
dataset <- read.csv(file.path(datasets_path, stringsAsFactors = T))
# Print first 5 columns,
# column 33, 35 and the last one (the class).
summary(dataset[,c(1,5,33,35,ncol(dataset))))
```

| UNIQUE_ID | user | X0 | X1 |

| Min. : 1.0 | Min. :1.00 | Min. :000000 | Min. :000000 |
| 1st Qu.:.136.0 | 1st Qu.:.100.0 | 1st Qu.:.060600 | 1st Qu.:070700 |
| Median :271.0 | Median :19.00 | Median :090000 | Median :100000 |
| Mean :284.4 | Mean :18.87 | Mean :099414 | Mean :099895 |
| 3rd Qu.:.412.0 | 3rd Qu.:.28.00 | 3rd Qu.:012000 | 3rd Qu.:012000 |
| Max. :.728.0 | Max. :36.00 | Max. :1.000000 | Max. :081000 |

| X2 | ZAVG | class |

| Min. :000000 | Min. :0 :07.22 | 29 | Downstairs:528 |
| 1st Qu.:.08000 | 1st Qu.:0 :07.21 | 27 | Jogging :1625 |
| Median :010000 | Median :0 :07.11 | 26 | Sitting :306 |
| Mean :099837 | Mean :0 :01.13 | 26 | Standing :246 |