
If everything went well, the history plot will show us a learning curve that looks like the following. This suggests that our model is training correctly:

![](img/da8fb67f2acf661518076e08b6ffd9b9_197_0.png)

### Training of our model in Keras

Perhaps we could increase the number of epochs? That's something you can try as an exercise!

It is now time to generate some of the samples:

```
start_idx <- sample(1:(length(text) - max_length), size = 1)
name <- text[start_idx:(start_idx + max_length - 1)]
generated <- ""
for(i in 1:10){
  x <- sapply(chars, function(x) {
    as.integer(x == name)
  })
  dim(x) <- c(1, dim(x))
  preds <- predict(model, x)
  next_idx <- sample_mod(preds, 0.3)
  next_char <- chars[next_idx]

  generated <- str_c(generated, next_char, collapse = "")
  name <- c(name[-1], next_char)
  cat(generated)
  cat("\n\n")
}
```

With a simple modification of the preceding code you can generate names of different lengths. For this, we need to replace our preceding fixed length with a randomly sampled length, noted random_len in the following code snippet:

```
n_iter <- 100
for(iter in 1:n_iter){
  start_idx <- sample(1:(length(text) - max_length), size = 1)
  name <- text[start_idx:(start_idx + max_length - 1)]
  generated <- " "
  random_len <- sample(5:10, 1)
  for(i in 1:random_len){
    x <- sapply(chars, function(x) {
      as.integer(x == name)
    })
    dim(x) <- c(1, dim(x))
    preds <- predict(model, x)
    next_idx <- sample_mod(preds, 0.1)
    next_char <- chars[next_idx]
    generated <- str_c(generated, next_char)
    name <- c(name[-1], next_char)
    # cat(generated)
    # cat("\n\n")
  }
  cat(generated)
}
```

Among the generated samples (which might be different in your computer) are:

Asarara, Lalaraso

Which sound rather convincingly like Spanish last names.

Of course, you can adapt the preceding model to any other text, perhaps including text like HTML or LaTeX.

A subtlety here is that we used character-level prediction. You can try to adapt the text to word-level prediction, to make it work like the auto-complete function of a smartphone.

## Exercises

- Try the LSTM example for `Alice in Wonderland` to generate baby names using the datasets compiled by Mark Kantrowitz, available at: https://www.cs.cmu.edu/Groups/AI/areas/nlp/corpora/names/0.html.
- Music generation is also a sequential prediction problem, as we mentioned. You can take a look at the version of the Nottingham Music Database written in ABC notation at http://abc.sourceforge.net/NMD/ to teach the computer to write music, using a similar recurrent neural network.
- Refactor the code on our recurrent neural network from scratch (the R6 implementation) so that it uses the `forward_step` function within the `bptt` function.
- We ignored bias terms in our recurrent neural network implementations. How will that affect the performance, if at all? Try to modify the code to include bias terms.
- Modify the code for the network using the cross-entropy method to use natural evolution strategies: https://blog.openai.com/evolution-strategies/.

## Summary

In this chapter, we introduced different architectures for recurrent neural networks, and pointed out some of their limitations and capabilities. By introducing a naive Markovian model, we compared the efficiency of introducing such complicated architectures. When applied to the text generation problem, we saw that these different architectures had a noticeable improvement in the quality of the predictions. For training networks, we introduced different methods. The classical backpropagation algorithm and other gradient-free methods that are useful to solve black-box optimization problems.

## Sentiment Analysis with Word Embeddings

In this chapter, we turn to the problem of sentiment analysis. Sentiment analysis is an umbrella term for a number of techniques to figure out how a speaker feels about a certain topic or piece of content.

A vanilla case study of sentiment analysis is **polarity**. Given a document or text string (for instance, a Tweet, a review, or a comment on a social network), the aim is to determine whether the author feels good, bad, or neutral about the item or topic in question.

At first look, this problem might seem trivial: A lookup table with positive and negative words, and simply counting the word frequencies should do, right? Not so fast. Here are a few examples of why this is tricky:

- Their decadent desserts made me hate myself
- You should try this place if you love cold food
- Disliking cake is not really my thing

What can we see in these examples?

- Negative terms used in a possibly positive sense
- Positive terms used sarcastically
- Two negative terms that imply something positive

Note that we have not dealt with spelling mistakes, neologisms and use of multiple languages, just to name a few potential issues in real-life situations.

As you can see, sentiment analysis is a very complicated task, and we will merely scratch the surface.

The human element is the most important element in sentiment analysis. The accuracy of a sentiment analysis system depends on how much it agrees with human judgement. And how accurate could that be? Unfortunately not that much. Some researchers report disagreement rates as high as 20%. This means that if your sentiment analysis system has an accuracy of 70%, although seemingly unimpressive, it will still be good, since humans would agree on 80% of the classifications of a perfect sentiment analysis system. But, beware!

These figures are not exactly comparable, since the computer will have issues identifying subtleties that are best guessed by humans, such as sarcasm, jokes, or the subtle differences in meaning from the examples shown previously.

Nonetheless, there seems to be an increasing awareness from individuals and organizations about the importance of their presence online. We can measure that impact by the mushrooming of agencies and professionals specializing in social media monitoring. This has contributed to increased attention in the field from researchers (both in universities and industries), and we believe that it is likely that we will see significant advances in the area.

Our focus, as stated elsewhere in the book, is to introduce you to the algorithms in the simplest way possible. We will use a well-known dataset, which shares many of the properties of real-life datasets that you will find out there.

### Warm-up – data exploration

Let's get things moving with a tiny example. Let's look at this tiny reviews corpus:

```
text <- c("The food is typical Czech, and the beer is good. The service is
quick, if short and blunt, and the waiting on staff could do with a bit of
customer service training",
"The food was okay. Really not bad, but we had better",
"A venue full of locals. No nonsense, no gimmicks. Only went for
drinks which were good and cheap. People friendly enough.",
"Great food, lovely staff, very reasonable prices considering the
location!")
```

We will do some simple analysis here, which will help us appreciate some of the subtleties of sentiment analysis.

## Working with tidy text

For this, we will use the `tidytext` package. This package is built on the philosophy of tidy data, introduced by Hadley Wickham in his 2014 paper (https://www.jstatsoft.org/article/view/v059i10). A dataset is tidy if the following three conditions are satisfied:

- Each variable is a column
- Each observation is a row
- Each type of observational unit is a table

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
