| function | purpose |
|---|---|
| str_match() | extracts the text of the match and parts of the match within parenthesis |
| str_replace() and str_replace_all() | replaces the matches with new text |
| str_remove() and str_remove_all() | removes the matches |
| str_split() | splits up a string at the pattern |

The first step will be to remove the space where the pattern is " " using the stringr::str_remove() function. This step would then be repeated with pattern = "-"

```
str_remove(string = pc_kimberley_all,
    pattern = " ")
```

## [1] "V1A2B3"  "V1A2B3"  "v1a2B3"  "v1a-2b3"

More efficiently, we can use a regular expression with both a space and a hyphen inside the square brackets, which has the result of replacing either a space or a hyphen.

```
pc_kimberley_clean <- str_remove(string = pc_kimberley_all,
    pattern = "[ -]")
```

The second step will be to capitalize the letters. The {stringr} function for this is str_to_upper. (There are also parallel str_to_lower, str_to_title, and str_to_sentence functions.)

```
pc_kimberley_clean <- str_to_upper(pc_kimberley_clean)
pc_kimberley_clean
```

## [1] "V1A2B3" "V1A2B3" "V1A2B3" "V1A2B3"

If this was in a dataframe, these functions can be added to a mutate() function, and applied in a pipe sequence, as shown below.

```
# convert string to tibble
pc_kimberley_tbl <- as_tibble(pc_kimberley)
```