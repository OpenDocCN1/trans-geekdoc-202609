# The more, the merrier – calculating n-grams instead of single words

The reason for such an odd result in the previous section can be traced back to the context. Notice that review 3 had the phrase No nonsense, no gimmicks, which is largely positive, but has two negative words attached to it. How can we take context into account? Enter n-grams. An n-gram is a sequence of n consecutive items (words, or in the case of speech, phonemes) from a given sequence of text or speech. Let’s make this clear with an example and use 2-grams, or bigrams:

```
text_df <- data_frame(line = 1:4, text = text)
text_df <- text_df %>%
unnest_tokens(bigram, text, token="ngrams", n=2)
text_df
```

This gives us the following:

```
# A tibble: 70 x 2
  line bigram
  <int> <chr>
1 1 the food
2 1 food is
3 1 is typical
4 1 typical czech
5 1 czech and
6 1 and the
7 1 the beer
8 1 beer is
9 1 is good
10 1 good the
# ... with 60 more rows
```

So, we now see that consecutive words are put together. Already, this can be helpful enough to determine the negations of negative words that are actually positive, as in our preceding review 3. Let’s find out which negative words are negated. First, we split the two words of the bigram into two columns:

```
library(tidytr)
text_df <- text_df %>% separate(bigram, c("w1","w2"), sep=" ")
text_df
```