# 1.4 Explore your first datasets

# 1.4.4 Identification and measurement variables

There is a difference between the variables that you will encounter in data frames. There are identification variables and measurement variables. For example, let's explore the airports data frame by showing the output of glimpse(airports):

![](bbox=[0.118, 0.193, 0.882, 0.223])

```
Rows: 1,251
Columns: 8
$ faa <chr>"AAF", "AAP", "ABE", "ABI", "ABL", "ABQ", "ABR", "ABY", "AC-
$ name <chr>"Apalachia Regional Airport", "Andreau Airpark", "Leigh -
$ lat <dbl>29.7, 29.7, 40.7, 32.4, 67.1, 35.0, 31.5, 31.6, -
$ lon <dbl>-85.0, -95.6, -75.4, -99.7, -157.9, -106.6, -98.4, -84.2, -
$ alt <dbl>20, 79, 393, 1791, 3355, 1382, 197, 471, 516, 721, -
$ tz <tz>-5, -6, 5, -6, -7, -6, -5, -6, -8, -5, -10, -6, -9-
$ dst <chr>"A", "A", "A", "A", "A", "A", "A", -
$ tzone <chr>"America/New_York", "America/Chicago", "America/New_York", ~
```

The variables faa and name are identification variables that uniquely identify each airport. faa provides the airport's unique FAA code, while name gives its official name. These variables are used to uniquely identify each row in a data frame. The remaining variables (lat, lon, alt, tz, tzone) are often called measurement or characteristic variables: variables that describe properties of each observational unit. For example, lat and long describe the latitude and longitude of each airport.

Furthermore, sometimes a single variable might not be enough to uniquely identify each observational unit: combinations of variables might be needed. It is not an absolute rule, for organizational purposes it is considered good practice to have your identification variables in the leftmost columns of your data frame.

# Learning check

(LC1.5) What properties of each airport do the variables lat, lon, alt, dst, and tzone describe in the airports data frame? Take your best guess.

(LC1.6) Provide the names of variables in a data frame with at least three variables where one of them is an identification and the other two are not.