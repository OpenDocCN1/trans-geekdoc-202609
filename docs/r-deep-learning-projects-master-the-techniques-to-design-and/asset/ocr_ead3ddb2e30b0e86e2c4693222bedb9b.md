We can save both our vector embedding and model for later use:

```
```r
write.csv(vw,"./data/vw.csv", row.names = F)
save_model_hdf5(model,"glove_nn.hdf5")
```
```

# # Bi-directional LSTM networks

Well, our model did not quite work before with simple feed-forward networks. In this section, we will try a different model: Bi-directional LSTM networks.

Recall that LSTM networks preserve parts of the previous information via the hidden state. However, this information is only about the past.

Bidirectional LSTM run both ways—from past to future and back! The LSTM that runs backwards preserves information from the future. Using the two hidden states combined, you are able to keep the context of both past and future. Clearly this would not make sense for stock price prediction! Their use was initially justified in the domain of speech recognition because, as you might know from experience, the context of the full phrase is often needed to understand the meaning of a word. This happens, for instance, when you are trying to simultaneously translate from one language to another.

Ok, so how do we do this? Let's come back to keras. This will make the experience rather smooth, as we have seen before.

For the bidirectional LSTM API, keras expects, per row, one document with a list of words, which are passed over sequentially.

Let's begin with some familiar preprocessing steps:

```
```r
library(purrr)
library(stringr)
library(tm)
library(keras)

df <- read.csv("./data/labeledTrainData.tsv", encoding = "utf-8", quote = "", sep="\t", stringsAsFactors = F)

text <- df$review

corpus <- VCorpus(VectorSource(text))
corpus <- tm_map(corpus, content_transformer(tolower))
corpus <- tm_map(corpus, content_transformer(removePunctuation)))
corpus <- tm_map(corpus, content_transformer(removeNumbers)))
corpus <- tm_map(corpus, content_transformer(removeWords),
```
```