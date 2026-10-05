# 1.4 Explore your first datasets

# 1.4.2 flights data frame

We'll begin by exploring the flights data frame and get an idea of its structure. Run the following code in your console, either by typing it or by cutting-and-pasting it. It displays the contents of the flights data frame in your console. Note that depending on the size of your monitor, the output may vary slightly.

flights

```
# A tibble: 435,352 x 19
year month day_time sched_dep_time_dep_time delay arr_time
<int> <int> <int> <int> <dbl> <dbl>
1 2023 1 1 2038 203 328
2 2023 1 1 18 2300 78 228
3 2023 1 1 31 2344 47 500
4 2023 1 1 33 2140 173 238
5 2023 1 1 36 2048 228 223
6 2023 1 1 50 500 3 808
7 2023 1 1 52 510 10 948
8 2023 1 1 54 530 -6 645
9 2023 1 1 57 520 17 926
10 2023 1 1 57 545 2 845
# i 435,342 more rows
# i 12 variables: sched_arr_time <int>, arr_delay <dbl>
# carrier <chr>, flight <int>, tailname <chr>, origin <chr>, dest <chr>
# air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>
# time_hour <dtt>
```

Let's unpack this output:

+   A 435,352 x 19: A tibble is a specific kind of data frame in R. This particular data frame has

+   435,352 rows corresponding to different observations. Here, each observation is a flight.
19 columns corresponding to 19 variables describing each observation.

+   year, month, day_time, sched_dep_time, dep_dep_time, and arr_time are the different columns, in other words, the different variables of this dataset.

+   We then have the first 10 rows corresponding to the first 10 flights. R is only showing the first 10 rows, because if it showed all 435,352 rows, it would overwhelm your screen.

+   ... with 435,342 rows' and 11 more variables: indicating to us that 435,352 more rows of data and 11 more variables could not fit in this screen.