# Working with tidy text

For this, we will use the `tidytext` package. This package is built on the philosophy of tidy data, introduced by Hadley Wickham in his 2014 paper (https://www.jstatsoft.org/article/view/v059i10). A dataset is tidy if the following three conditions are satisfied:

+   - Each variable is a column
+   - Each observation is a row
+   - Each type of observational unit is a table

The `tidytext` package helps us turn our text into tidy form, by putting one token per row. Let's start by loading `dplyr` and `tidytext`. If you don't have `tidytext`, install it first using `install.packages("tidytext")`.

Load the packages and let's transform our text into a data frame:

```
library(tidytext)
library(dplyr)
text_df <- data_frame(line = 1:4, text = text)
```

The `unnest_tokens` function is where the magic of `tidytext` begins:

```
text_df <- text_df %>%
unnest_tokens(word, text)
head(text_df)
# A tibble: 6 x 2
  line word
  <int> <chr>
1     1 the
2     1 food
3     1 is
4     1 typical
5     1 czech
6     1 and
```

As you can see, our text was transformed as one token (the default is one word = one token) per row. First, let's get rid of stop words:

```
data(stop_words)
head(stop_words)
text_df <- text_df %>% anti_join(stop_words)
```