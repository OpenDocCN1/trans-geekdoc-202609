
punctuation

```r
library(tokenizers)
tokens <- tokenize_words(imdb$review, stopwords = stopwords())
```

```r
# Create vocabulary. The tokens are simple words here.
token_iterator <- itoken(tokens)
vocab <- create_vocabulary(token_iterator)
```

```r
# Kill sparse terms
vocab <- prune_vocabulary(vocab, term_count_min = 5L)
vectorizer <- vocab_vectorizer(vocab)
```

```r
# use window of 5 for context words
tcm <- create_tcm(token_iterator, vectorizer, skip_grams_window = 5L)
glove <- GlobalVectors$new(word_vectors_size = 50,
                 vocabulary = vocab,
                 x_max = 10)
wv_main <- glove$fit_transform(tcm,
                 n_iter = 10,
                 convergence_tol = 0.05)
```

```r
text <- unlist(imdb$review)
text_df <- data_frame(line = 1:25000, text = text)
text_df <- text_df %>%
     unnest_tokens(word, text)
```

```r
wv <- as.data.frame(wv_main)
wv$word <- row.names(wv)
df <- wv %>% inner_join(text_df)
```

```r
# Now we need to create the trained matrix
df <- df %>% group_by(line) %>% summarize_all(mean) %>% select(1:51)
df$label <- as.factor(imdb$sentiment)
```

```r
library(caret)
control <- trainControl(method="cv", repeats=5)
```

```r
# Train the different models
set.seed(7)
```

```r
modelRF <- train(label~., data=df, method="rf", trControl=control)
```

```r
set.seed(7)
modelGbm <- train(label~., data=df, method="gbm", trControl=control,
verbose=FALSE)
```

```r
set.seed(7)
modelLogitBoost <- train(label~., data=df, method="LogitBoost",
trControl=control)
```

```r
set.seed(7)
modelNaiveBayes <- train(label~., data=df, method="nb", trControl=control)
```

```r
# collect resamples: this is useful for the plots
results <- resamples(
list(RF=modelRF,
GBM=modelGbm,
LB=modelLogitBoost,
NB=modelNaiveBayes))
```

```r
# summarize and check the model performance
summary(results)
bwplot(results)
dotplot(results)
```

We can see a significant improvement in the results!

```r
> summary(results)
Call:
summary.resamples(object = results)
Models: RF, GBM, LB, NB 
Number of resamples: 10 
```

| Model | Min. | 1st Qu. | Median | Mean | 3rd Qu. | Max. | NA's |
|-------|------|---------|--------|------|---------|------|------|
| RF | 0.7820 | 0.7892 | 0.7946 | 0.79340 | 0.7972 | 0.8012 | 0 |
| GBM | 0.7904 | 0.7952 | 0.7978 | 0.79732 | 0.7996 | 0.8036 | 0 |
| LB | 0.6904 | 0.6978 | 0.7040 | 0.70388 | 0.7098 | 0.7176 | 0 |
| NB | 0.6728 | 0.6810 | 0.6900 | 0.68824 | 0.6957 | 0.7008 | 0 |

The dotplot and boxplot here are shown as follows:

![](img/da8fb67f2acf661518076e08b6ffd9b9_229_0.png)

Dotplot showing the different classifiers after proper preprocessing

And the boxplot:

![](img/da8fb67f2acf661518076e08b6ffd9b9_230_0.png)

Boxplot showing the different classifiers after proper preprocessing

Remember, when it comes to software in general, and data science is not the exception:

**Garbage in, garbage out:** Always pay attention to the data you are feeding to the models! The most powerful models available will produce unsatisfactory results when feeding them with the wrong data! It's important to log, or at least print, to the console, any preprocessing steps you are doing. Treating models as a magic black box is a very dangerous thing, and unfortunately too common.

As we mentioned earlier, vector embeddings is not proper deep learning, rather a feature representation method. However, we can combine vector embeddings with deep neural networks and, hopefully, get better results.

## Vector embeddings and neural networks

It's time to combine vector embeddings and neural networks to, hopefully, create more robust models. Let's do a simple extension to our workflow by training a neural network as a classifier. We start with the now familiar preprocessing and vector embedding:

```r
library(plyr)
library(dplyr)
library(text2vec)
library(tidytext)
library(caret)
library(tokenizers)
imdb <- read.csv(".//data/labeledTrainData.tsv"
                 , encoding = "utf-8"
                 , quote = ""
                 , sep="\t"
                 , stringsAsFactors = F)
tokens <- tokenize_words(imdb$review, stopwords = stopwords())
# Boring boilerplate preprocessing
token_iterator <- itoken(tokens)
vocab <- create_vocabulary(token_iterator)
vocab <- prune_vocabulary(vocab, term_count_min = 5L)
vectorizer <- vocab_vectorizer(vocab)
# Create context and embedding
tcm <- create_tcm(token_iterator, vectorizer, skip_grams_window = 5L)
glove <- GlobalVectors$new(word_vectors_size = 50,
 vocabulary = vocab,
 x_max = 10)
wv_main = glove$fit_transform(tcm,
 n_iter = 10,
 convergence_tol = 0.01)
text <- unlist(imdb$review)
text_df <- data_frame(line = 1:length(text), text = text)
text_df <- text_df %>%
unnest_tokens(word, text)
```

Let's try now with the context vector as well, instead of the main word vector:

```r
wv_context <- glove$components
wv <- as.data.frame(wv_main+t(wv_context))
wv$word <- row.names(wv)
df <- wv %>% inner_join(text_df)
```

To then finally create the trained matrix:

```r
df <- df %>% group_by(line) %>% summarize_all(mean) %>% select(1:51)
df$label <- as.factor(imdb$sentiment)
```

And finally, create a baseline neural network model with a single layer:

```r
library(keras)

X <- df[,2:51]
y <- df[, 52]

y <- to_categorical(y[["label"]])
y <- y[,2:3]

model <- keras_model_sequential()
model %>%
  layer_dense(activation='relu', units =20, input_shape=c(50)) %>%
  layer_dense(units=2, activation = 'softmax')

model %>% compile(
  loss = 'categorical_crossentropy',
  optimizer = optimizer_rmsprop(),
  metrics = c('accuracy')
)

history <- model %>% keras::fit(
  as.matrix(X), y,
  epochs = 30, batch_size = 128,
  validation_split = 0.2
)
```

Calling the fit method triggers the training procedure. Once the training is done, we can see how it went by using the plot function:

```r
plot(history)
```

Which gives us some slightly disappointing results:

![](img/da8fb67f2acf661518076e08b6ffd9b9_233_0.png)

Performance of our single layer neural network with 20 neurons

Why is that disappointing? Well, our mighty neural network with 20 neurons did not improve upon, say, random forests. How can we improve this result?

It seems to be that neural networks in this case, or at least feed-forward neural networks might not be of much help here, or at least we were not able to find significant improvements by adding more layers. Actually it seemed to worsen results with three or more layers, and we even observed over-fitting.

> Occam's razor should prevail. The model you keep should be as simple as possible. A complicated model might be of little use in production because of the technical complications needed to deploy it. Furthermore, when we have no way of interpreting the model, unexpected results might happen when the model is applied to slightly different data from that used for training and testing.

We can save both our vector embedding and model for later use:

```r
write.csv(vw,"./data/vw.csv", row.names = F)
save_model_hdf5(model,"glove_nn.hdf5")
```

## Bi-directional LSTM networks

Well, our model did not quite work before with simple feed-forward networks. In this section, we will try a different model: Bi-directional LSTM networks.

Recall that LSTM networks preserve parts of the previous information via the hidden state. However, this information is only about the past.

Bidirectional LSTM run both ways—from past to future and back! The LSTM that runs backwards preserves information from the future. Using the two hidden states combined, you are able to keep the context of both past and future. Clearly this would not make sense for stock price prediction! Their use was initially justified in the domain of speech recognition because, as you might know from experience, the context of the full phrase is often needed to understand the meaning of a word. This happens, for instance, when you are trying to simultaneously translate from one language to another.

Ok, so how do we do this? Let's come back to keras. This will make the experience rather smooth, as we have seen before.

For the bidirectional LSTM API, keras expects, per row, one document with a list of words, which are passed over sequentially.

Let's begin with some familiar preprocessing steps:

```r
library(purrr)
library(stringr)
library(tm)
library(keras)

df <- read.csv("./data/labeledTrainData.tsv", encoding = "utf-8", quote = "", sep="\t", stringsAsFactors = F)

text <- df$review

corpus <- VCorpus(VectorSource(text))
corpus <- tm_map(corpus, content_transformer(tolower))
corpus <- tm_map(corpus, content_transformer(removePunctuation))
corpus <- tm_map(corpus, content_transformer(removeNumbers))
corpus <- tm_map(corpus, content_transformer(removeWords),
```
