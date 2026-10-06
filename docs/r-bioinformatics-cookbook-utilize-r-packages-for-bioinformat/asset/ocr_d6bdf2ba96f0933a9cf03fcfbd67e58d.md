# 352 Turbo-Charging Development in R with ChatGPT

```
factorise_cols <- function(df, col_list ) {
  not_all_na <- function(x) any(!is.na(x))

  for (i in col_list) {
    df <- df %% dplyr::mutate(!!(i) := as.factor(!!(i))
  }
  df %% dplyr::select_if(not_all_na)
}
```

Check the response:

```
# Factorise Selected Columns
#
# This function factorises the selected columns in a data frame.
#
# @param df data frame.
# @param col_list A character vector specifying the names of the columns to be factorised.
# @return A modified data frame with the selected columns factorised.
#
# @export
#
# @examples
# df <- data.frame(
  coll = c("A", "B", "C", NA),
  col2 = c(1, 2, NA, 4),
  col3 = c("X", "Y", "Z", NA)
)
## factorise_cols(df, c("coll", "col3\))
#
# @import dplyr
# @importFrom base as.factor
factorise_cols <- function(df, col_list) {
  not_all_na <- function(x) any(!is.na(x))

  for (i in col_list) {
    df <- df %% dplyr::mutate(!!(i) := as.factor(!!(i))
  }
  df %% dplyr::select_if(not_all_na)
}
```

And that's all we need to create documentation.