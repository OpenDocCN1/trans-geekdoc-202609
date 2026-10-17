# 5.3.1 Practice Question

Create a new column called DBP_CHANGE that is equal to the difference between a patient's first and fourth diastolic blood pressure readings. Then, sort the data frame by this new column in increasing order and print the first four rows. The first four DBP_CHANGE values in the head of the resulting data frame should be –66, –64, –64, and –62.

```
# Insert your solution here:
```

# 5.4 Summarizing and Grouping

If we want to understand how many observations there are for each given race category, we could use the table() function as we described in earlier chapters. Another similar function is the count() function. This function takes in a data frame and one or more columns and counts the number of rows for each combination of unique values in these columns. If no columns are specified, it counts the total number of rows in the data frame. In the following code, we find the total number of observations (31,265) and the number by race and year. We can see that the number in each group fluctuates quite a bit!

```
count(nhanes_df)
#> n
#> 1 31265
count(nhanes_df, RACE, YEAR)
#> RACE YEAR n
#> 1 Mexican American 1999 713
#> 2 Mexican American 2001 674
#> 3 Mexican American 2003 627
#> 4 Mexican American 2005 634
#> 5 Mexican American 2007 639
#> 6 Mexican American 2009 672
#> 7 Mexican American 2011 322
#> 8 Mexican American 2013 234
#> 9 Mexican American 2015 287
#> 10 Mexican American 2017 475
#> 11 Other Hispanic 1999 181
#> 12 Other Hispanic 2001 129
#> 13 Other Hispanic 2003 80
#> 14 Other Hispanic 2005 96
```