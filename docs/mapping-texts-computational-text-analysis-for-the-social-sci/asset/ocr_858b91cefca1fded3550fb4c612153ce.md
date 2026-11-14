```
df_trek <- df_trek |>
  group_by(number) |>
  summarize(text = paste0(line, collapse = "\n"),
            doc_id = first(title),
            airdate = first(airdate))

dim(df_trek) # how many rows and columns now?

[1] 26 4
```

# DOCUMENT FEATURES

What a *feature* refers to depends on how we tokenize the document and how we categorize or summarize those tokens. As we mentioned earlier, the most common document-feature matrix is a document-term matrix (DTM). This represents documents by a vector of term counts and the positions in the vector are types of words.

# THIS SECTION NEEDS:

+   - tidyverse
+   - tidytext
+   - tokenizers
+   - reshape2
+   - quanteda
+   - text2map

Once tokenized, each document is a list of tokens. We then count how often each *unique* token<sup>10</sup> occurs in each document. With a single document, we represent its content as a vector of numbers. The position in the vector references a unique type. The number is how often that type occurs in that document.

> This is called a *type* in contrast to a *token*.

There are two things to note when transforming a token list into a token-count list. First, we won't retain the *order of the words* in a document. Second, we collapse tokens that are *precisely* the same characters. For example, "The" and "the" would be counted as distinct tokens, as would "Raúl" and "Raul." Let's use an excerpt from Mary Shelley's *Frankenstein*.

```
doc <- "nothing is so painful to the human mind
 as a great and sudden change the sun might
 shine or the clouds might lower but nothing
 could appear to me as it had done the day
 before a fiend had snatched from me every
 hope of future happiness no creature had ever
 been so miserable as I was so frightful an
 event is single in the history of man"
```

We'll tokenize using `strsplit()` and the regular "space." The output of this function is a **token list**. Next, we'll use `table` to count how many times each unique token occurs in the document, creating a **token-count list**.

```
# tokenize by splitting into words by space
docs_tokens <- strsplit(doc, " ", fixed = TRUE)

# get word frequencies
docs_freqs <- table(docs_tokens)
```