

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

我们可以看到结果有显著改善！

```r
> summary(results)
Call:
summary.resamples(object = results)
Models: RF, GBM, LB, NB 
Number of resamples: 10 
```

| 模型 | 最小值 | 下四分位数 | 中位数 | 均值 | 上四分位数 | 最大值 | NA数量 |
|------|--------|------------|--------|------|------------|--------|--------|
| RF | 0.7820 | 0.7892 | 0.7946 | 0.79340 | 0.7972 | 0.8012 | 0 |
| GBM | 0.7904 | 0.7952 | 0.7978 | 0.79732 | 0.7996 | 0.8036 | 0 |
| LB | 0.6904 | 0.6978 | 0.7040 | 0.70388 | 0.7098 | 0.7176 | 0 |
| NB | 0.6728 | 0.6810 | 0.6900 | 0.68824 | 0.6957 | 0.7008 | 0 |

点图和箱图显示如下：

![点图展示不同分类器在适当预处理后的表现](img/da8fb67f2acf661518076e08b6ffd9b9_229_0.png)

Dotplot showing the different classifiers after proper preprocessing

和箱图：

![箱图展示不同分类器在适当预处理后的表现](img/da8fb67f2acf661518076e08b6ffd9b9_230_0.png)

Boxplot showing the different classifiers after proper preprocessing

请记住，谈到软件（尤其是数据科学也不例外）：
**垃圾进，垃圾出：** 请始终注意你输入到模型中的数据！最强大的模型在喂入错误数据时也会产生不理想的结果！记录（或至少打印到控制台）你正在执行的任何预处理步骤非常重要。将模型视为神秘黑箱是一件非常危险的事情，而且不幸的是太过常见。

如前所述，向量嵌入并非真正的深度学习，而是一种特征表示方法。但是，我们可以将向量嵌入与深度神经网络相结合，希望获得更好的结果。

## 向量嵌入和神经网络

是时候将向量嵌入和神经网络相结合，希望创建更强健的模型。让我们通过训练一个神经网络作为分类器，对工作流进行简单扩展。我们从现在熟悉的预处理和向量嵌入开始：

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

现在让我们尝试使用上下文向量，而不是主词向量：

```r
wv_context <- glove$components
wv <- as.data.frame(wv_main+t(wv_context))
wv$word <- row.names(wv)
df <- wv %>% inner_join(text_df)
```

然后最终创建训练矩阵：

```r
df <- df %>% group_by(line) %>% summarize_all(mean) %>% select(1:51)
df$label <- as.factor(imdb$sentiment)
```

最后，创建一个具有单层的基准神经网络模型：

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

调用 fit 方法将触发训练过程。训练完成后，我们可以通过绘图函数查看训练情况：

```r
plot(history)
```

这给我们带来了一些略显失望的结果：

![我们单层神经网络（20个神经元）的性能](img/da8fb67f2acf661518076e08b6ffd9b9_233_0.png)

Performance of our single layer neural network with 20 neurons

这为什么令人失望？好吧，我们强大的 20 个神经元神经网络并未优于随机森林。我们如何改进这个结果？

看来在这种情况下，神经网络（或者至少是前馈神经网络）可能帮助不大，或者至少我们通过添加更多层未能发现显著改进。实际上，三层或更多层似乎会使结果变差，我们甚至观察到了过拟合。

> 奥卡姆剃刀应当占主导地位。你保留的模型应尽可能简单。复杂的模型在生产环境中可能用处不大，因为部署它需要解决技术上的复杂问题。此外，当我们无法解释模型时，当模型应用于与训练和测试略有不同的数据时，可能会出现意外结果。

我们可以保存向量嵌入和模型以备后用：

```r
write.csv(vw,"./data/vw.csv", row.names = F)
save_model_hdf5(model,"glove_nn.hdf5")
```

## 双向 LSTM 网络

嗯，之前用简单的前馈网络，我们的模型效果不太理想。在本节中，我们将尝试一种不同的模型：双向 LSTM 网络。

请回顾，LSTM 网络通过隐藏状态保留部分先前的信息。但是，这些信息仅关于过去。

双向 LSTM 双向运行——从过去到未来，再返回！反向运行的 LSTM 保留来自未来的信息。结合使用两个隐藏状态，你可以保留过去和未来的上下文。显然，这对于股票价格预测来说毫无意义！它们最初在语音识别领域得到证明是合理的，因为，正如你从经验中可能知道的那样，理解一个词的含义通常需要完整短语的上下文。例如，当你尝试同时从一种语言翻译成另一种语言时就会发生这种情况。

好吧，那我们怎么做呢？让我们回到 keras。这将使体验相当顺畅，正如我们之前所见。

对于双向 LSTM API，keras 期望每行一个文档，包含一个单词列表，这些单词将按顺序传递。

让我们从一些熟悉的预处理步骤开始：

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

