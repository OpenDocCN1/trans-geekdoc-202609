# Learning check

(LC.10) What positive values of the gain variable in flights correspond to? What about negative values? And what about a zero value?

(LC.11) Could we create the dep_delay and arr_delay columns by simply subtracting dep_time from sched_dep_time and similarly for arrivals? Try the code out and explain differences between the result and what actually appears in flights.

(LC.12) What can we say about the distribution of gain? Describe it in a few sentences using the plot and the gain_summary data frame values.

# 3.6 arrange and sort rows

One of the most commonly performed data-wrangling tasks is to sort a data frame's rows in the alphanumeric order of one of the variables. The dplyr package arrange() function allows us to sort/reorder a data frame's rows according to the values of the specified variable.

Suppose we are interested in determining the most frequent destination airports for all domestic flights departing from New York City in 2023:

```
freq_dest <- flights |>
group_by(dest) |
summarize(num_flights = n())
freq_dest
```

```
# tibble: 118 x 2
dest      num_flights
<chr>    <int>
1 ABQ      228
2 ACK       916
3 AGS       20
4 ALB     1581
5 ANC       95
6 ATL     17570
7 AUS      4848
8 AVL      1617
9 AVP      145
10 BDL     701
# i 108 more rows
```