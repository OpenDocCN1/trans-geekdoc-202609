```
#stringi
stri_extract_all_words(df_punct$text)

#quanteda
tokens(df_punct$text)
tokens(df_punct$text, remove_punct = FALSE)
tokens(df_punct$text, remove_punct = TRUE, remove_symbols = TRUE)

#tidytext
unnest_tokens(df_punct, word, text)
unnest_tokens(df_punct, word, text, strip_punct = FALSE)

#tokenizers
tokenize_words(df_punct$text)
tokenize_words(df_punct$text, strip_punct = FALSE)
```

Finally, there is the question of numbers. It is common to remove the Arabic numerals (0, 1, 2, 3, 4, 5, 6, 7, 8, 9) and, like removing all punctuation, it is easy with base R .

```
string_numbers <- c("1,000", "4", "40-50 feral hogs",
                    "1st place!", "$20 million",
                    "f1,000", "11/16/1980", "8:30 PM")

# compare two ways to remove all numerals
gsub("[[:digit:]]+", "", string_numbers)
gsub("\\d+", "", string_numbers)
```

The implied goal of removing numerals is to limit the feature space.
But, an alternative to deleting is to replace them with their alphabetic equivalents. One could build a dictionary to match each number and replace it with the appropriate word, but we may want to be careful to treat, ordinals, dates, or times differently. Luckily, textclean provides functions for replacing each with their written equivalents.11

11 Under the hood, it is a lot of fancy regex.

```
replace_number(string_numbers)
replace_ordinal(string_numbers)
replace_money(string_numbers)
replace_date(string_numbers)
replace_time(string_numbers)
```

Beyond encoding, lowercasing, transliterating, punctuation, and numbers, we may encounter, on a case-by-case basis, a range of special characters specifically related to data obtained from the Web. If, for example, we get text data from Twitter, we need to deal with hashtags and usernames (e.g., #ReadBannedBooks, @levarburton) and emojis. If we scrape Web data, it often has HTML markup tags. rvest provides html_text() and textclean has replace_html() to remove HTML syntax, or we could use gsub() with a regex pattern to strip markup text.12

12 For help with hashtags, handles, urls, emojis, and other unique cases, see textclean .