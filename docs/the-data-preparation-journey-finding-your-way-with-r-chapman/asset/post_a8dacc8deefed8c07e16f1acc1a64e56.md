
For the second analysis, we might be interested in determining if there is any seasonality in the Canadian labour force:

```
lfs_canada_employment |>
  group_by(month(REF_DATE)) |>
  summarize(mean(VALUE))
```

```
## # A tibble: 12 x 2
##  `month(REF_DATE)` `mean(VALUE)`
##                 <dbl>         <dbl>
## 1                1        17841.
## 2                2        17960.
## 3                3        17907.
## 4                4        17848.
## 5                5        18255.
## 6                6        18539.
## 7                7        18514.
## 8                8        18514.
## 9                9        18423.
## 10              10        18458.
## 11              11        18421.
## 12              12        18369.
```

## 12.3 Cleaning strings

> “Strings are not glamorous, high-profile components of R, but they do play a big role in many data cleaning and preparation tasks.” —{stringr} reference page

R provides some robust tools for working with character strings. In particular, the {stringr}(Wickham, 2019b) package is very flexible. But before we get there, we need to take a look at regular expressions.

### 12.3.1 Regular expressions

> “Some people, when confronted with a problem, think: ‘I know, I’ll use regular expressions.’ Now they have two problems.” — Jamie Zawinski

Regular expressions are a way to specify a pattern of characters. This pattern can be specific letters or numbers (“abc” or “123”) or character types (letters, digits, white space, etc.), or a combination of the two.

An excellent resource for learning the basics is the vignette “Regular Expressions,” hosted at the {stringr} package website “Regular Expressions”, stringr.tidyverse.org¹.

Here are some useful regex matching functions. Note that the square brackets enclose the regex to identify a single character. In the examples below, with three sets of square brackets, “[a][b][c]” contains three separate character positions, whereas “[abc]” is identifying a single character.

| character | what it does |
|---|---|
| “abc” | matches “abc” |
| “[a][b][c]” | matches “abc” |
| “[abc]” | matches “a”, “b”, or “c” |
| “[a-c]” | matches any of “a” to “c” (that is, matches “a”, “b”, or “c”) |
| “[ ^abc]” | matches anything except “a”, “b”, or “c” |
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

An example of a unicode character² is the “interobang”, a combination of question mark and exclamation mark.

```
interrobang <- "\u2048"
interrobang
```

## [1] "?!"

Canadian postal codes follow a consistent pattern:

- letter digit letter, followed by a space or a hyphen, then digit letter digit

The regex for this is shown below, with the component parts as follows:

- ^ : start of string
- [A-Za-z] : all the letters, both upper and lower case
- \d : any numerical digit
- [ -]? : space or hyphen; “?” to make either optional (i.e. it may be there or not)
- $ : end of string

```
# regex for Canadian postal codes
# ^ : start of string
# [A-Za-z] : all the letters upper and lower case
# \d : any numerical digit
# [ -]? : space or hyphen,
#         ? to make either optional (i.e. it may be there or not)
# $ : end of string

postalcode <- "^[A-Za-z]\\d[A-Za-z][ -]?\\d[A-Za-z]\\d$"
```

> “If your regular expression gets overly complicated, try breaking it up into smaller pieces, giving each piece a name, and then combining the pieces with logical operations.” —Wickham

²The full list of unicode characters can be found at the Wikipedia webpage (Wikipedia contributors, 2022a).

and Grolemund, R for Data Science (Wickham and Grolemund, 2016, p.209)

The regular expression for Canadian postal codes can be shortened, using the case sensitivity operator, “(?i)”. Putting this at the beginning of the expression applies it to all of the letter identifiers in the regex; it can be turned off with “(?-i)”.

```
# option: (?i) : make it case insensitive
#       (?-i) : turn off insensitivity
postalcode <- "(?i)^[A-Z]\\d[A-Z][ -]?\\d[A-Z]\\d$(?-i)"
```

The postal code for the town of Kimberley, British Columbia, is “V1A 2B3”. Here’s a list with some variations of that code, which we will use to test our regular expression.

```
# list of postal codes
pc_kimberley <- c("V1A2B3", "V1A 2B3", "v1a 2B3xyz", "v1a-2b3")
```

### 12.3.2 Data cleaning with {stringr}

Armed with the power of regular expressions, we can use the functions within the {stringr} package to filter, select, and clean our data.

```
library(stringr)
```

As with many R packages, the reference page provides good explanations of the functions in the package, as well as vignettes that give working examples of those functions. The reference page for {stringr} is stringr.tidyverse.org³.

Let’s look at some of the functions within {stringr} that are particularly suited to cleaning tasks.

³https://stringr.tidyverse.org/

### 12.3.2.1 String characteristics

| function | purpose |
|---|---|
| str_subset() | character; returns the cases which contain a match |
| str_which() | numeric; returns the vector location of matches |
| str_detect() | logical; returns TRUE if pattern is found |

The {stringr} functions str_subset() and str_which() return the strings that have the pattern, either in whole or by location.

```
# which strings have the postal code pattern?
str_subset(pc_kimberley, postalcode)
```

## [1] "V1A2B3"  "V1A 2B3" "v1a-2b3"

```
# which strings have the postal code pattern, by location?
str_which(pc_kimberley, postalcode)
```

## [1] 1 2 4

Another of the {stringr} function, str_detect(), tests for the presence of a pattern and returns a logical value (true or false). Here, we test the list of four postal codes using the postalcode object that contains the regular expression for Canadian postal codes.

```
str_detect(string = pc_kimberley, pattern = postalcode)
```

## [1] TRUE TRUE FALSE TRUE

As we see, the third example postal code—which contains an extra digit at the end—returns a “FALSE” value. It might contain something that looks like a postal code in the first 7 spaces, but because it has the extra letter, it is not a postal code. To find a string that matches the postal code in any part of a string, we have to change our regex to remove the start “^” and end “$” specifications:

```
# remove start and end specifications
postalcode <- "(?i)[A-Z]\\d[A-Z][ -]?\\d[A-Z]\\d(?-i)"
```

```
str_detect(string = pc_kimberley, pattern = postalcode)
```

## [1] TRUE TRUE TRUE TRUE

All of the strings have something that matches the structure of a Canadian postal code. How can we extract the parts that match?

If we rerun the str_subset() and str_which() functions, we see that all four of the strings are now returned.

```
# which strings have the pattern?
str_subset(pc_kimberley, postalcode)
```

## [1] "V1A2B3"  "V1A 2B3"  "v1a 2B3xyz" "v1a-2b3"

```
# which strings have the pattern ("e"), by location?
str_which(pc_kimberley, postalcode)
```

## [1] 1 2 3 4

With those two functions, we can identify which strings have the characters that we're looking for. To retrieve a particular string, we can use str_extract():

```
pc_kimberley_all <- str_extract(pc_kimberley, postalcode)
pc_kimberley_all
```

## [1] "V1A2B3"  "V1A 2B3" "v1a 2B3"  "v1a-2b3"

### 12.3.2.2 Replacing and splitting functions

How can we clean up this list so that our postal codes are in a consistent format?

Our goal will be a string of six characters, with upper-case letters and neither a space nor a hyphen.

This table shows the functions we will use.
