
There are four reasons to use pretrained embeddings. First, we save time and resources. Second, it increases replicability across studies. Third, our focal corpus may be too small for training purposes. Finally, embeddings trained on only our focal corpus may be overfit.

- THIS SECTION NEEDS:
  - tidyverse
  - stringi
  - textclean
  - keras
  - reticulate

## Neural Networks with Pretrained Embeddings

We’ll use posts on a popular discussion board from Reddit (i.e., a subreddit) called “Am I the Asshole” (AITA). The guidelines are simple: “Tell us about any non-violent conflict you have experienced; give us both sides of the story, and find out if you’re right, or you’re the asshole.” Forum members decide which party is in the wrong: the author, the other party, everyone, no one—or in some cases, not enough information to determine. Predicting “who is the asshole” using text is a complicated classification task.

```
data(corpus_reddit_aita10k, package = "text2map.corpora")

df_aita <- corpus_reddit_aita10k |>
mutate(text = stri_trans_general(text,
id = "Any-Latin; Latin-ASCII"),
text = tolower(text),
text = replace_curly_quote(text),
text = replace_contraction(text),
text = gsub("[[:punct:]]+", " ", text),
text = gsub("[[:digit:]]+", " ", text),
text = str_squish(text)
)
```

We will use Python packages again, so set the conda environment.

```
use_condaenv(condaenv = "myenv")
```

Let’s use the embeddings we used previously, the fastText embeddings trained on the Common Crawl, found in text2map.pretrained. We’ll assume the model is already downloaded.

```
# load the model each session
data("vecs_fasttext300_commoncrawl", package = "text2map.pretrained")
ft_wv <- vecs_fasttext300_commoncrawl # rename so it's tidier
```

Let’s turn our corpus into a document-sequence matrix using only the first 2,000 words in each post.

```
n_words <- 2000

seq_trn <- df_aita |>
seq_builder(text, maxlen = n_words) |>
as.matrix()
```

We also need to prepare the outcome variable, which has five categories indicating who is in the wrong according to the majority: Other, Nobody, Author, Everybody, and Info (more information is needed). Let’s first convert these five categories to integers from 0 to 4[^20] then create a keras-friendly matrix.

[^20]: Python starts counting from 0, and keras uses Python.

```
df_aita <- df_aita |>
mutate(labeln = case_when(
  label == "AUTHOR" ~ 0,
  label == "OTHER" ~ 1,
  label == "NOBODY" ~ 2,
  label == "EVERYBODY" ~ 3,
  label == "INFO" ~ 4,
)
)
y_trn <- to_categorical(df_aita$labeln, num_classes = 5)
```

Put our “weights” (i.e., our pretrained embeddings) into a list, and add it to the weights argument in layer_embedding() and do not allow training ( trainable = FALSE ).

```
ke_mod <- keras_model_sequential()
ke_mod <- ke_mod |>
layer_embedding(
input_dim = nrow(ft_wv),
output_dim = 300L,
input_length = n_words,
weights = list(ft_wv),
trainable = FALSE)
layer_global_average_pooling1d() |>
layer_dense(units = 50, activation = "relu") |>
layer_dense(units = 5, activation = "sigmoid")
```

```
ke_mod <- ke_mod |>
compile(loss = "categorical_crossentropy",
optimizer = "sgd",
metrics = "accuracy"
)
```

```
history <- ke_mod |>
fit(seq_trn, y_trn, epochs = 10)
```

We didn’t use a test set this time. We’ll just use the model to get the labels for our training data. Note that each post has a probability of being classified as one of the five labels.

```
preds <- ke_mod |> predict(seq_trn)
colnames(preds) <- c("AUTHOR", "OTHER", "NOBODY",
"EVERYBODY", "INFO")
df_aita <- cbind(df_aita, preds)
```

Let’s see how well our model predicts the community judgment for one post: “AITA for feeding my vegan nephew meat?” The gist of this post is the author taking their 7-year-old nephew out to eat while their parents went on a date. The parents and the child are vegan. When the author asked the kid where he would like to eat, he says “Five Guys” — a popular hamburger restaurant. The author’s sister stated they were “out of line to change his diet without their permission.” The scores were:

- 631: the sister is in the wrong.
- 276: the author is.
- 229: nobody is.
- 26: everyone is.
- 7: more information is needed.

So, the majority sided with the author that the “other” party is in the wrong. Let’s see how our model did.

```
df_aita |> filter(title == "AITA for feeding my vegan nephew meat?") |> select(AUTHOR:INFO)
```

| AUTHOR | OTHER | NOBODY | EVERYBODY | INFO |
|---|---|---|---|---|
| 0.7772692 | 0.9145786 | 0.5613233 | 0.3398936 | 0.07852602 |

That tracks the vote tally pretty closely!

Suppose our research calls for sorting documents into multiple categories, and the methods discussed in **Core Deductive** are not producing desired results; then using pretrained embeddings with neural networks is a good choice. However, at least some documents must be labeled. What if we don’t have labeled data? We’ll discuss one classification strategy for unlabeled documents next.

- THIS SECTION NEEDS:
  - tidyverse
  - textclean
  - text2map
  - text2map.pretrained
  - stringi
  - gutenbergr

## Concept Mover’s Distance with Pretrained Embeddings

Recall that supervision means we’re using labels to train the classifier. They are not optional. A strength of dictionary methods is that they do not require labeling.

Could we augment dictionary methods with pretrained models? Specifically, could we use word embeddings to account for the semantic similarities between terms? Good news everybody! We can with **Concept Mover’s Distance** (CMD) (Stoltz and Taylor 2019a; Taylor and Stoltz 2021). This method extends dictionary methods as we’ll need one or more “anchor” terms. We’ll then use pretrained word embeddings to augment this process by weighting each word in our documents by its cosine to these anchors.[^21]

[^21]: To do this, CMD relies on Word Mover’s Distance; see Extended Inductive.

Our anchor list defines a location in the embedding space. In the simplest scenario, this is a single word—say “death.” We then associate each word in our DTM with a location in the embedding space. Documents, then, are clouds of locations. We want to measure the *minimum cost* of moving all the words in our documents to this single point. Cost is a function of distance and weight: for us, cosine and relative frequency, respectively.

We’ll try to predict the “deaths” in 37 plays from Shakespeare’s First Folio using metadata we created about the plays. This includes the unique ID of the work hosted on Project Gutenberg. We’ll then use gutenbergr to download each play, creating a dataframe where each row is a line in the play. Let’s also collapse these lines so there is one row per play.

```
data("meta_shakespeare", package = "text2map")
my_mirror <- "mirrors.xmission.com/gutenberg/"
df_text <-
  select(gutenberg_id) |>
  gutenberg_download(mirror = my_mirror) |
  group_by(gutenberg_id) |>
  summarize(text = paste(text, collapse = " ")) |>
  mutate(gutenberg_id = as.character(gutenberg_id))
```

These are OCRed documents, so let’s transliterate, and take care of these pesky curly quotes, expand any contractions we can, and then remove punctuation and numbers. Then, build a DTM.

```
df_text <- df_text |>
  mutate(text = replace_non_ascii(text),
         text = tolower(text),
         text = replace_curly_quote(text),
         text = replace_contraction(text),
         text = gsub("[[:punct:]]+", " ", text),
         text = gsub("[[:digit:]]+", " ", text),
         text = str_squish(text)
  )
dtm <- df_text |>
  dtm_builder(text, doc_id = gutenberg_id)
```

Load the fastText embeddings.

```
data("vecs_fasttext300_commoncrawl", package = "text2map.pretrained")
ft_wv <- vecs_fasttext300_commoncrawl # rename so it’s tidier
```

Since “death” is similar to “life,” let’s also calculate each play’s engagement with the semantic direction life-death, rather than just the single word “death.”[^22]

```
terms <- cbind(c("death", "demise", "dying"),
                 c("life", "birth", "living"))
dir_death <- get_direction(terms, ft_wv)
```

In a DTM, each document is represented as a distribution of word counts. How “sensitive” is each estimate to a given distribution of words? We can test this sensitivity by resampling (with replacement) from each document’s word distribution. We do this by setting the sens_interval
