+   2. replace “-*” with NA
+   3. convert to numeric value

```
noc_table_clean <- noc_table_clean |>
  # remove commas
  mutate(
    employment =
      str_remove_all(employment, ",")
  ) |>
  # replace with NA
  mutate(
    employment =
      str_replace_all(employment, "-\\*", replacement = NA_character_)
  ) |>
  # convert to numeric
  mutate(
    employment =
      as.numeric(employment)
  )

gt(head(noc_table_clean))
```

| noc | occupation_title | certification_training_requirements | employment |
|---|---|---|---|
| 063 | Accommodation service managers | A university degree or college diploma in hotel management or other related discipline or equivalent job experience | 6479 |
| 652 | Occupations in travel and accommodation | Related post-secondary diploma; On the job training | 5771 |
| 673 | Cleaners | On the job training | 5083 |
| 631 | Food service supervisors | Post-secondary training in restaurant management or food service admin, or; Equivalent job experience | 3479 |
| 632 | Chefs and cooks | Cook's apprenticeship program and training; Chef's Red Seal Certification | 1542 |
| 112 | Human resources professionals | Related post-secondary degree or diploma | 1271 |

FIGURE 12.4 NOC table: step 4.