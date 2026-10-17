```
visit_info <- data.frame(
  name.f = c("Phillip", "Phillip", "Phillip", "Jessica",
             "Jessica"),
  name.l = c("Johnson", "Johnson", "Richards", "Smith",
             "Abrams"),
  measure = c("height", "age", "age", "age", "height"),
  measurement = c(45, 186, 50, 37, 156)
)
```

```
contact_info <- data.frame(
  first_name = c("Phillip", "Phillip", "Jessica", "Margaret"),
  last_name = c("Richards", "Johnson", "Smith", "Reynolds"),
  email = c("pr@aol.com", "phillipj@gmail.com",
            "jesssmith@brown.edu", "marg@hotmail.com")
)
```

```
left_join(visit_info, contact_info,
          by = c("name.f" = "first_name"))
```

```
#> Warning in left_join(visit_info, contact_info, by =
c(name.f = "first_name")): Detected an unexpected
many-to-many relationship between `x` and `y`.
#> i Row 1 of `x` matches multiple rows in `y`.
#> i Row 1 of `y` matches multiple rows in `x`.
#> i If a many-to-many relationship is expected, set
`relationship =`
#> "many-to-many"` to silence this warning.
#> name.f name.l measure measurement last_name
#> 1 Phillip Johnson height 45 Richards
↦ email
↦ pr@aol.com
#> 2 Phillip Johnson height 45 Johnson
phillipj@gmail.com
#> 3 Phillip Johnson age 186 Richards
pr@aol.com
#> 4 Phillip Johnson age 186 Johnson
phillipj@gmail.com
#> 5 Phillip Richards age 50 Richards
pr@aol.com
#> 6 Phillip Richards age 50 Johnson
phillipj@gmail.com
#> 7 Jessica Smith age 37 Smith
jesssmith@brown.edu
#> 8 Jessica Abrams height 156 Smith
jesssmith@brown.edu
```