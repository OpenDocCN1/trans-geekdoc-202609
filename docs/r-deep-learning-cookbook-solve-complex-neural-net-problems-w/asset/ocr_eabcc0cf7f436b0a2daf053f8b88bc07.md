# # How to do it...

Here is how we go about analyzing documents using tf-idf:

+   1. Extract the text of all 62 chapters in the book Pride and Prejudice. Then, return chapter-wise occurrence of each word. The total words in the book are approx 1.22M.

```
Pride_Prejudice_chapters <- austen_books_df %>%
  group_by(book) %>%
  filter(book == "Pride & Prejudice") %>%
  mutate(linenumber = row_number(),
   chapter = cumsum(str_detect(text, regex("^chapter [\\divxlc]",
     ignore_case = TRUE)))) %>%
  ungroup() %>%
  unnest_tokens(word, text) %>%
  count(book, chapter, word, sort = TRUE) %>%
  ungroup()
```

+   2. Calculate the rank of words such that the most frequently occurring words have lower ranks. Also, visualize the term frequency by rank, as shown in the following figure:

![](bbox=[0.28, 0.5, 0.72, 0.71])

This figure shows lower ranks for words with higher term-frequency (ratio) value

```
freq_vs_rank <- Pride_Prejudice_chapters %>%
mutate(rank = row_number(),
 term_frequency = n/totalwords)
freq_vs_rank %>%
 ggplot(aes(rank, term_frequency)) +
 geom_line(size = 1.1, alpha = 0.8, show.legend = FALSE) +
 scale_x_log10() +
 scale_y_log10()
```