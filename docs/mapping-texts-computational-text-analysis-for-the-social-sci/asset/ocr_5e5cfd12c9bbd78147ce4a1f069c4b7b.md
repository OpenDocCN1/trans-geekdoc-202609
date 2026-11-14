# Table 7.6: Common Text Wrangling Decisions

| Step | Specification |
| :--- | :--- |
| Punctuation | What punctuation is removed and retained? |
| Transliteration | Are some characters replaced with equivalents? |
| Numbers | Are all numbers removed? Are they replaced? |
| Lowercasing | Are all tokens lowercased? Are some retained? |
| Stopped Words | Were tokens removed (stopped)? Which words? |
| Stemming | Are tokens stemmed? How are they stemmed? |
| Lemmatizing | Are tokens lemmatized? How are they lemmatized? |

Typically, we do not want our findings to change drastically by any single decision; if it does, we need to theorize why this might be the case.

Using mutate(), we can remove a task by “commenting out” a line with the # . For example, if we want to remove all numbers, rather than replace them with their written equivalents, we comment out all the five replace_* lines, and uncomment gsub() that matches the [[ :digit:]]+ regex pattern.

```
```
df_text <- df_text |> mutate(
  ## transliterate and lowercase
  text = stri_trans_general(
    text,
    id = "Any-Latin;Latin-ASCII"
  ),
  text = tolower(text),
  ## punctuation
  text = replace_curly_quote(text),
  text = gsub("[\\W+_-]+[\\w+]|[[;punct:]]+", "\\\\1", text),
  text = replace_contraction(text),
  text = gsub("[[;punct:]]+", " ", text),
  ## numbers
  # text = replace_number(text),
  # text = replace_ordinal(text),
  # text = replace_money(text),
  # text = replace_date(text),
  # text = replace_time(text),
  text = gsub("[[ :digit:]]+", " ", text),
  ## spaces
  text = gsub("[[ :space:]]+", " ", text),
  text = trimws(text)
)
```
```

What about the more specialized issues we raised, such as hashtags, encoding problems, misspellings, etc? We only need to run these if we think these issues are present. How do we know they are present? If we gain an intimate knowledge of our documents by reading some, we’ll pick up on the peculiarities of the corpus. Another helpful tool is provided by textclean called check_text , which checks for twenty-three possible issues.

Altering text in ways discussed here is as much about dimension reduction as more advanced techniques we’ll discuss later. Each step potentially limits the “feature space” we are using to represent our