time is written T[hh][mm][ss] or T[hh]:[mm]:[ss], with hours (on a 24-hour clock) followed by minutes and seconds.

When we are working with dates, the objective of our cleaning is to transform the date into the ISO 8601 standard and then, where appropriate, transform that structure into a date type variable. The benefits of the date type format are many, not the least of which are the R tools built to streamline analysis and visualization that use date type variables, (Wickham et al., 2023b, Chapter 18) and those same tools allow us to tackle cleaning variables that capture date elements.

One such package is {lubridate}, part of the tidyverse.

# 12.2.1 Creating a date-time field

The first way that dates might be represented in your data is as three separate fields, one for year, one for month, and one for day. These can be assembled into a single date variable using the make_date(), or a single datetime variable using make_datetime().

In the {Lahman}(Friendly et al., 2020) table “People”, each player’s birth date is stored as three separate variables. They can be combined into a single variable using make_date():

```
Lahman::People |>
  slice_head(n = 10) |>
  select(playerID, birthYear, birthMonth, birthMonth, birthDay) |>
  # create date-time variable
  mutate(birthDate = make_datetime(birthYear, birthMonth, birthDay))
```

| ## | playerID | birthYear | birthMonth | birthDay | birthDate |
|---|---|---|---|---|---|
| ## 1 | aardsda01 | 1981 | 12 | 27 | 1981-12-27 |
| ## 2 | aaronha01 | 1934 | 2 | 5 | 1934-02-05 |
| ## 3 | aronto01 | 1939 | 8 | 5 | 1939-08-05 |
| ## 4 | aasedo01 | 1954 | 9 | 8 | 1954-09-08 |
| ## 5 | abadan01 | 1972 | 8 | 25 | 1972-08-25 |
| ## 6 | abadfe01 | 1985 | 12 | 17 | 1985-12-17 |
| ## 7 | abadijo01 | 1850 | 11 | 4 | 1850-11-04 |
| ## 8 | abbated01 | 1877 | 4 | 15 | 1877-04-15 |
| ## 9 | abbeybe01 | 1869 | 11 | 11 | 1869-11-11 |
| ## 10 | abbeych01 | 1866 | 10 | 14 | 1866-10-14 |

The second problematic way dates are stored is in a variety of often ambiguous sequences. This might included text strings for the month (for example “Jan”,