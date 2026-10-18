# **Table 2.2** This table contains the same data as table 2.1, but in tidy format

| Athlete | Month | Best |
|---|---:|---:|
| Joana | 0 | 12.50 |
| Debi | 0 | 14.86 |
| Sukhveer | 0 | 12.10 |
| Kerol | 0 | 19.60 |
| Joana | 1 | 12.10 |
| Debi | 1 | 14.90 |
| Sukhveer | 1 | 12.10 |
| Kerol | 1 | 19.70 |
| Joana | 2 | 11.98 |
| Debi | 2 | 14.70 |
| Sukhveer | 2 | 12.00 |
| Kerol | 2 | 19.30 |
| Joana | 3 | 11.99 |
| Debi | 3 | 14.30 |
| Sukhveer | 3 | 11.80 |
| Kerol | 3 | 19.00 |

This time, we have the column Month that contains the month identifiers that were previously used as separate columns, and the Best column, which holds the best times for each athlete, for each month. Does each row represent a single observation? Yes! Does each column represent a variable? Yes! So this data is in tidy format.

Ensuring your data is in tidy format is an important early step in any machine learning pipeline, and so the tidyverse includes the package tidyr, which helps you achieve this. The other packages in the tidyverse work with tidyr and each other to help you:

+   - organize and display your data in a sensible way (tibble)
+   - manipulate and subset your data (dplyr)
+   - plot your data (ggplot2)
+   - replace for loops with a functional programming approach (purrr)

All of the operations available to you in the tidyverse are achievable using base R code, but I strongly suggest you incorporate the tidyverse in your work as it helps you keep your code simpler, more human-readable, and reproducible.