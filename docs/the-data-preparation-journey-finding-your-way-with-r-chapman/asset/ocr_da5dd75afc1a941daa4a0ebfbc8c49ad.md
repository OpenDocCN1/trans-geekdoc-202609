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