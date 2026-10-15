can be specific letters or numbers (“abc” or “123”) or character types (letters, digits, white space, etc.), or a combination of the two.

An excellent resource for learning the basics is the vignette “Regular Expressions,” hosted at the {stringr} package website “Regular Expressions”, stringr.tidyverse.org¹.

Here are some useful regex matching functions. Note that the square brackets enclose the regex to identify a single character. In the examples below, with three sets of square brackets, “[a][b][c]” contains three separate character positions, whereas “[abc]” is identifying a single character.

| character | what it does |
|---|---|
| “abc” | matches “abc” |
| “[a][b][c]” | matches “abc” |
| “[abc]” | matches “a”, “b”, or “c” |
| “[a-c]” | matches any of “a” to “c” (that is, matches “a”, “b”, or “c”) |
| “[ˆabc]” | matches anything except “a”, “b”, or “c” |
| “^” | match start of string |
| “$” | match end of string |
| “.” | matches any string |

| character | frequency of match |
|---|---|
| “?” | 0 or 1 |
| “+” | 1 or more |
| “*” | 0 or more |
| “{n}” | exactly n times |
| “{n,}” | n or more |
| “{n,m}” | between n and m times |

These also need to be escaped:

| character | what it is |
|---|---|
| “”” | double quotation mark |
| “‘” | single quotation mark |
| “\” | backslash |
| “\d” | any digit |
| “\n” | newline (line break) |
| “\s” | any whitespace (space, tab, newline) |
| “\t” | tab |
| “\u…” | unicode characters* |

¹ https://stringr.tidyverse.org/articles/regular-expressions.html