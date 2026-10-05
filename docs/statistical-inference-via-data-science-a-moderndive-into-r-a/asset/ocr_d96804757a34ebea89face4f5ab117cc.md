# 3.8 Other verbs

We've seen that the flights data frame in the nycflights23 package contains 19 different variables. You can identify the names of these 19 variables by running the glimpse() function from the dplyr package:

```
glimpse(flights)
```

However, say you only need two of these 19 variables, say carrier and flight. You can select() these two variables:

```
flights |>
select(carrier, flight)
```

This function makes it easier to explore large datasets since it allows us to limit the scope to those variables we care about. For example, if select() only a smaller number of variables is as shown in Figure 3.9, it will make viewing the dataset in RStudio's viewer more digestible.

Let's instead want to drop, or de-select, certain variables. For example, consider the variable year in the flights data frame. This variable isn't quite a “variable” because it is 2023 and doesn't change. You may want to remove this variable from the data frame. We can deselect year by using the sign:

```
flights_no_year <- flights | select(-year)
```

Another way of selecting columns/variables is by specifying a range of columns:

```
flight_arr_times <- flights |> select(month:day, arr_time:sched_arr_time)
flight_arr_times
```

This will select() all columns between month and day, as well as between arr_time and sched_arr_time, and drop the rest.

The helper functions starts_with(), ends_with(), and contains() can be used to select variables/columns that match those conditions. For examples,

Lastly, the select() function can also be used to reorder columns when used with the everything() helper function. For example, suppose we want the hour, minute, and