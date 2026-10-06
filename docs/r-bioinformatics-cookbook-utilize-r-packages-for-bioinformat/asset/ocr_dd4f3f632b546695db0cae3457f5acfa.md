# Phylogenetic Analysis and Visualization

```
"X11" = readr::col_integer(), "X12" = readr::col_
integer(),
"X13" = readr::col_integer(),
"X14" = readr::col_double(),
"X15" = readr::col_double(),
"X16" = readr::col_integer(),
"X17" = readr::col_integer(),
"X18" = readr::col_integer(),
"X19" = readr::col_double(),
"X20" = readr::col_number(),
"X21" = readr::col_double()
)

data.table::setnames(x = hits,
old = paste0("X", 1:length(col_names)),
new = col_names)

data.table::setkeyv(hits, c("query_id", "subject_id"))
return(hits)

```

+   - Set up a function to filter the best hits:

```
filter_best_hits <- function(x) {

min_val <- min(x$value)
evaluate <- alig_length <- NULL
res <- dplyr::filter(x, evaluate == min_val)
if (nrow(res) > 1) {
  max_len <- max(res$alig_length)
res <- dplyr::filter(res, alig_length == max_)
}

if (nrow(res) > 1) {
  res <- dplyr::slice(res, 1)
}
return(res)

```