
Writing your code in an R Markdown or Quarto document also gives you the flexibility to write the code in SQL, if that’s your preferred approach.

This exercise replicates the joins described in the “Relational data” chapter of *R for Data Science* by Hadley Wickham & Garrett Grolemund (Wickham and Grolemund, 2016). Instead of using the R {nycflights13} package (Wickham and RStudio, 2021), we will use a SQLite version of the same database.

In this database, there are five separate tables. The table `flights` in the database contains all 336,776 flights that departed from New York City in 2013. The data comes from the US Bureau of Transportation Statistics and is documented in ?flights

The other tables in the database are:
- `airlines` lets you look up the full carrier name from its abbreviated code,
- `airports` gives information about each airport, identified by the `faa` airport code,
- `planes` gives information about each plane, identified by its `tailnum`,
- `weather` gives the weather at each NYC airport for each hour.

The tables are *related* to `flights` by the fact that they have variables in common. These are known as the “key” variables.

This diagram shows the relationships:

![](img/b86622d1e9ca82b3cbec45faaffaaf26_145_0.png)

FIGURE 10.1 nycflights13.

(From (Wickham and Grolemund, 2016), p.174)

## 10.1.1 Connect to the database

SQL is a language widely used to manipulate and extract data in relational databases. As a consequence, there are many relational databases built in this format. Most often, these databases will be housed on a network server, but for smaller databases, you might install the file on your computer.

In R, we can use the package {dbplyr} (Wickham et al., 2023a) to access SQL databases and SQL functions. In addition, we need {DBI} (Müller, 2022) and {RSQLite} (Müller et al., 2023) to establish the connection to the RSQLite database.

```
library(dbplyr)
library(DBI)
library(RSQLite)
```

The code below establishes the connection to the database and assigns the connection (not the data table!) to the object con_nycf (for “Connection to New York City Flights”). You will note that the {RSQLite} function SQLite() is inside the {DBI} function dbConnect(). The {DBI} package supports a wide range of different database types, including the widely-used MySQL and Postgres.

```
# establish the connection to the database file
con_nycf <-  DBI::dbConnect(RSQLite::SQLite(), "data/nycflights13_sql.sqlite")

# list the tables in the connected database
dbListTables(con_nycf)
```

## [1] "airlines"   "airports"   "flights"    "planes"
## [5] "sqlite_stat1" "sqlite_stat4" "weather"

Now that we have a connection to the database, we can establish a connection to a particular table, using the {dplyr} function tbl(). Note that the flights object is not the table but is the connection to the table.

```
flights <- tbl(con_nycf, "flights")
```

## 10.1.2 Submit queries

With the object “flights” now established in our environment, we can write R code to create a subset of the flights—those that went to Seattle. Again, the flights_SEA object is not a dataframe, but a set of instructions that creates the connection and the query.

```
flights_SEA <- flights |>
  filter(dest == "SEA")
```

We can also use the show_query() function of {dbplyr} to generate the SQL translation of the R code:

```
flights_SEA <- flights |>
  filter(dest == "SEA") |>
  show_query()
```

```
## <SQL>
## SELECT `flights`.*
## FROM `flights`
## WHERE (`dest` = 'SEA')
```

In SQL, we use SELECT to select the columns (or variables) we want (you will note this is the same term as {dplyr}). The asterisk “*” is a wildcard to select all the tables.

FROM indicates which table from which we want to draw the columns.

And finally, the filtering by city uses the SQL function WHERE.

In the code below, we create a summary table of the average flight time from New York to Seattle, by airline.

```
SEA <- flights_SEA |>
  select("month", "carrier", "air_time") |>
  group_by(carrier) |>
  summarize(
    n = n(),
    min_air_time = min(air_time),
    mean_air_time = mean(air_time),
    max_air_time = max(air_time)) |>
  # enter the resulting table into the R environment
  collect()
```

```
## Warning: Missing values are always removed in SQL aggregation functions.
## Use `na.rm = TRUE` to silence this warning
## This warning is displayed once every 8 hours.
```

```
SEA
```

```
## # A tibble: 5 x 5
##   carrier     n min_air_time mean_air_time max_air_time
##   <chr>   <int>        <dbl>         <dbl>        <dbl>
## 1 AA       365          289          336.         385
## 2 AS       714          277          326.         392
## 3 B6       514          283          330.         378
## 4 DL      1213          275          327.         389
## 5 UA      1117          280          326.         394
```

## 10.1.3 Using SQL in your R code

In addition to writing native R code, we can embed SQL inside R code. In the example below, an R chunk in the R Markdown document has R code that uses the dbSendQuery() function. Inside this function, we first name the connection we are using and then inside the quotation marks write SQL code: "SELECT * FROM flights WHERE dest = 'SEA'".

This query instruction gets saved as the object SEA_sql.

The R chunk then has a second line that uses the dbFetch() function to run the SQL query.

Both the dbSendQuery() and dbFetch() are functions from the {DBI} package.

```
SEA_sql <- dbSendQuery(con_nycf,
    "SELECT * FROM flights WHERE dest = 'SEA'")

dbFetch(SEA_sql)
```

## 10.2 Running SQL language chunks in R Markdown

The book *R Markdown: The Definitive Guide* (Xie et al., 2019, Chapter 2.7.3) provides instructions on how to set up your R Markdown in RStudio so that you can run SQL language chunks, including using SQLite.

Once this has been done, our R Markdown document can incorporate native SQL queries into the workflow. Note that in our SQL chunk, we specify the connection. As we continue to work through this example, this is the `con_nycf` object created earlier. The start of our SQL code chunk would contain this text:

```
{sql, connection=con_nycf}
```

```
SELECT *
FROM flights
WHERE dest = 'SEA'
```

## 10.2.1 Mutating joins and summary tables

A mutating join is one that combines variables from two tables, based on matching observations on *keys*.

In this R code, we create a summary table of the flights that went from New York to Seattle, by the name of the airline. The full airline name is not in the `flights` table; to get that, we need to join the airline name from the `airlines` table to the Seattle summary of the `flights` table.

The first step is to establish a connection to the `airlines` table.

```
# establish connection to airlines table
 airlines <- tbl(con_nycf, "airlines")
```

Once the connection is made the tables can be joined using the `left_join()` function from `{dplyr}`, the grouped summary calculation made, and the table sorted from most to least frequent number of flights.

The table is also formatted for publication using the `{gt}` package (Iannone et al., 2023); the core `gt()` function is the first step, and many other formatting options are possible with this package.

```
# join and summary table
flights_SEA_summary <- flights_SEA |>
# select(-origin, -dest) |>
  left_join(airlines, by = "carrier") |>
  group_by(name) |>
  tally() |>
  arrange(desc(n))

flights_SEA_summary |>
  gt()
```

| name | n |
|---|---|
| Delta Air Lines Inc. | 1213 |
| United Air Lines Inc. | 1117 |
| Alaska Airlines Inc. | 714 |
| JetBlue Airways | 514 |
| American Airlines Inc. | 365 |

The SQL code below returns the same table. We can see one difference in how the code is written—it runs “inside out” with the third step coming before the first and second, rather than in the linear manner we are accustomed to in our R pipes.

```
-- 3. select `name` variable from joined table and apply count
SELECT `name`, COUNT(*) AS `n`
FROM (
  SELECT `flights_sea`.*, `name`
  -- 1. query to filter Seattle flights
  FROM (
    SELECT *
    FROM `flights`
    WHERE (`dest` = 'SEA')
  ) AS `flights_sea`
  -- 2. join to airlines table
  LEFT JOIN `airlines`
    ON (`flights_sea`.`carrier` = `airlines`.`carrier`)
)
-- 4. define grouping for COUNT (from step 3) and sort
GROUP BY `name`
ORDER BY `n` DESC
```
