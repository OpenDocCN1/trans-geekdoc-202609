
## 3.7 join data frames

### 3.7.3 Multiple key variables

Say instead we want to join two data frames by multiple key variables. For example, in Figure 3.7, we see that in order to join the flights and weather data frames, we need more than one key: year, month, day, hour, and origin. This is the combination of these 5 variables act to uniquely identify each observational unit in the weather data frame: hourly weather recordings at each of 3 NYC airports.

We achieve this by specifying a vector of key variables to join using the c() function.
Recall from Subsection 1.2.1 that c() is short for "combine" or "concatenate".

```r
flights_weather_joined <- flights |
  inner_join(weather, by = c("year", "month", "day", "hour", "origin"))
View(flights_weather_joined)
```

Learning check

(LC3.13) Looking at Figure 3.7, when joining flights and weather (or, in other words, matching the hourly values with each flight), why do we need to join by all of year, month, day, hour, and origin, and not just hour?

(LC3.14) What surprises you about the top 10 destinations from NYC in 2023?

## 3.7.4 Normal forms

The data frames included in the nycflights23 package are in a form that minimizes redundancy of data. For example, the flights data frame only saves the carrier code of the airline company; it does not include the actual name of the airline. For example, you will see that the first row of flights has carrier equal to UA, but it does not include the airline name "United Air Lines Inc."

The names of the airline companies are included in the name variable of the airlines data frame. In order to have the airline company name included in flights, we could join these two data frames as follows:

```r
joined_flights <- flights |
  inner_join(airlines, by = "carrier")
View(joined_flights)
```

We are capable of performing this join because each of the data frames has keys in common to relate one to another: the carrier variable in both the flights and airlines data frames. The key variable(s) that we base our joins on are often identification variables as we mentioned previously.

This is an important property of what's known as normal forms of data. The process of decomposing data frames into less redundant tables without losing information is called normalization. More information is available on Wikipedia².

Both dplyr and SQL³ we mentioned in the introduction of this chapter use such normal forms. Given that they share such commonalities, once you learn either of two tools, you can learn the other very easily.

## Learning check

(LC3.15) What are some advantages of data in normal forms? What are some disadvantages?

## 3.8 Other verbs

Here are some other useful data-wrangling verbs:

- select() only a subset of variables/columns.
- relocate() variables/columns to a new position.
- rename() variables/columns to have new names.
- Return only the top_n() values of a variable.

### 3.8.1 select variables

### Subset Variables (Columns)

![](img/445742518041017e8f01f11b0c3190d9_120_0.png)

FIGURE 3.9: Diagram of select() columns.

²https://en.wikipedia.org/wiki/Database_normalization
³https://en.wikipedia.org/wiki/SQL

## 3.8 Other verbs

We've seen that the flights data frame in the nycflights23 package contains 19 different variables. You can identify the names of these 19 variables by running the glimpse() function from the dplyr package:

```r
glimpse(flights)
```

However, say you only need two of these 19 variables, say carrier and flight. You can select() these two variables:

```r
flights |>
  select(carrier, flight)
```

This function makes it easier to explore large datasets since it allows us to limit the scope to those variables we care about. For example, if select() only a smaller number of variables is as shown in Figure 3.9, it will make viewing the dataset in RStudio's viewer more digestible.

Let's instead want to drop, or de-select, certain variables. For example, consider the variable year in the flights data frame. This variable isn't quite a “variable" because it is 2023 and doesn't change. You may want to remove this variable from the data frame. We can deselect year by using the sign:

```r
flights_no_year <- flights | select(-year)
```

Another way of selecting columns/variables is by specifying a range of columns:

```r
flight_arr_times <- flights |> select(month:day, arr_time:sched_arr_time)
flight_arr_times
```

This will select() all columns between month and day, as well as between arr_time and sched_arr_time, and drop the rest.

The helper functions starts_with(), ends_with(), and contains() can be used to select variables/columns that match those conditions. For examples,

Lastly, the select() function can also be used to reorder columns when used with the everything() helper function. For example, suppose we want the hour, minute, and time_hour variables to appear immediately after the year.

### 3.8.2 relocate variables

Another (usually shorter) case to reorder variables is by using relocate() function. This allows you to move variables to a new position. For example, if we want to move the hour, minute, and time_hour variables to appear immediately after the year, month, and day variables, we can use the following code:

```r
flights_reorder <- flights |>
  relocate(hour, minute, time_hour, .after = day)

### 3.8.3 rename variables

One more useful function is rename(), which as you may have guessed changes the name of variables. Suppose we want to only focus on dep_time and arr_time and change dep_time and arr_time to departure_time and arrival_time instead the flights_time_new data frame:

```r
flights_time_new <- flights |>
  select(dep_time, arr_time) |>
  rename(departure_time = dep_time, arrival_time = arr_time)
```

Note in this case we used = within rename(). For example, departure_time = dep_time renames the dep_time variable to departure_time. Note new users forget that the new variable name comes before the equal sign.

### 3.8.4 top_n values of a variable

We can also return the top_n values of a variable using the top_n() function. For example, we can return the top 10 destination airports using the example from 3.7.2. Note that we set the number of values to return to n = 10 and wt = num_flights to indicate that we want the rows corresponding to the top 10 values of num_flights. See the help file for top_n() by running ?top_n for more information.

```r
named_dests | top_n(n = 10, wt = num_flights)
```

Let's further arrange() these results in descending order of num_flights:

```r
named_dests |
  top_n(n = 10, wt = num_flights) |
  arrange(desc(num_flights))
```

Learning check

(LC16) What are some ways to select all of the dest, air_time, and distance variables from flights? Give the code showing how to do this in at least three different ways.

(LC17) How could one use starts_with(), ends_with(), and contains() to select columns from the flights data frame? Provide three different examples in total: one for starts_with(), one for ends_with(), and one for contains().

(LC18) Why might we want to use the select() function on a data frame?

(LC19) Create a new data frame that shows the top 5 airports with the largest arrival delays from NYC in 2023.
