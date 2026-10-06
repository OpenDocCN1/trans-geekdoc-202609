# Reformatting and extracting existing data into new columns stringr

6. Extract the length information:

```
lengths <- str_match(info, "LENGTH=(\d+)\$")[,2]
```

7. Combine all captured information into a data frame:

```
results <- data.frame(
  ids = ids,
  description = description,
  chromosome = as.integer(chr[2]),
  start = as.integer(chr[3]),
  end = as.integer(chr[4]),
  strand = strand,
  length = as.integer(lengths)
)
```

And gives us a very nice, reformatted data frame.

# How it works...

The R code uses the stringr library to extract, split, and manipulate information from a vector of sequence names (ath_seq_names) and assigns the resulting information to different variables. The rbioinfo library provides the initial ath_seq_names vector.

The first step of the recipe uses the str_extract() function from stringr to extract a specific pattern. The "ATd.*" regex matches any string that starts with "AT", followed by one digit, "G", then any number of characters, a dot, and finally one digit. stringr operations are vectorized so that all entries are processed.

Steps 2 and 3 are similar and use the str_split() function to split the seq_names vector by the "|" character; the simplify option returns a matrix of results with a column for each substring. The str_trim() function removes troublesome leading and trailing whitespace from the substring. The third and fourth columns of the resulting matrix are saved.

The following line of code uses the str_match() function to extract substrings from the info variable that matches the "chr(\d+) :(\d+)" regex. This matches any string that starts with "chr", followed by one digit, then ":", then one or more digits, then "-", and finally or more digits. The '()' bracket symbols marks the piece to save; each saved piece goes into a column in matrix.

The next line of code uses the str_locate() function to find the position of the first occurrence of EWARD or REVERSE in the info variable. This position is then used to extract the character at that position using str_sub(). The last line of code ends with one str_match() function to extract the substring that starts with "LENGTH=" and one or more digits from the info variable.