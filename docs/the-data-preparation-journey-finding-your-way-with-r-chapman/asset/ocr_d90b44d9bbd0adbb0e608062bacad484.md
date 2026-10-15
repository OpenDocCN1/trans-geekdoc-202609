# noc_occupation_title

This variable combines two values: the three-digit NOC code and the title of the occupation.

We will use the {tidyr} function `separate_wider_delim()` to split it into two variables. The function gives us the arguments to name the new columns that result from the separation and the character string that will be used to identify the separation point, in this case “:”. **Don’t forget the space!**

This function also has an argument `cols_remove =`. The default is set to TRUE, which removes the original column. Set to FALSE if it retains the original column; we won’t use that here but it can be useful.

There are also `separate_wider_*()` functions based on fixed-width positions and regular expressions.

```
noc_table_clean <- noc_table |>
  tidyr::separate_wider_delim(
    cols = noc_occupation_title,
    delim = ": ",
    names = c("noc", "occupation_title")
  )

gt(head(noc_table_clean))
```

| noc | occupation_title | certification_training_requirements | employment |
|---:|---|---|---:|
| 063 | Accommodation service managers | A university degree or college diploma in hotel management or other related discipline or equivalent job experience | 6,479 |
| 652 | Occupations in travel and accommodation | Related post-secondary diploma; On the job training | 5,771 |
| 673 | Cleaners | On the job training | 5,083 |
| 631 | Food service supervisors | Post-secondary training in restaurant management or food service admin, or; Equivalent job experience | 3,479 |
| 632 | Chefs and cooks | Cook’s apprenticeship program and training; Chef’s Red Seal certification | 1,542 |
| 112 | Human resources professionals | Related post-secondary degree or diploma | 1,271 |

**FIGURE 12.2** *NOC table: step 2.*