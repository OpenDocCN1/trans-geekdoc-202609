
## How to do it...

Here is how we go about analyzing documents using tf-idf:

- 1. Extract the text of all 62 chapters in the book Pride and Prejudice. Then, return chapter-wise occurrence of each word. The total words in the book are approx 1.22M.

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

- 2. Calculate the rank of words such that the most frequently occurring words have lower ranks. Also, visualize the term frequency by rank, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_243_0.png)

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

- 3. Calculate the tf-idf value for each word using the bind_tf-idf function:

```
Pride_Prejudice_chapters <- Pride_Prejudice_chapters %>%
bind_tf_idf(word, chapter, n)
```

- 4. Extract and visualize the top 15 words with higher values of tf-idf, as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_244_0.png)

tf-idf values of top 15 words

```
Pride_Prejudice_chapters %>%
select (-totalwords) %>%
arrange (desc (tf_idf))
```

```
Pride_Prejudice_chapters %>%
arrange (desc (tf_idf)) %>%
mutate(word = factor(word, levels = rev(unique(word)))) %>%
group_by (book) %>%
top_n(15) %>%
ungroup %>%
ggplot (aes(word, tf_idf, fill = book)) +
geom_col(show.legend = FALSE) +
labs(x = NULL, y = "tf-idf") +
facet_wrap(~book, ncol = 2, scales = "free") +
coord_flip()
```

## How it works...

As mentioned earlier, one can observe that the tf-idf scores of very common words such as *the* are close to zero and those of fewer occurrence words such as the proper noun *Austen* is close to one.

## Performing sentiment prediction using LSTM network

In this section, we will use LSTM networks to perform sentiment analysis. Along with the word itself, the LSTM network also accounts for the sequence using recurrent connections, which makes it more accurate than a traditional feed-forward neural network.

Here, we shall use the `movie reviews` dataset `text2vec` from the `cran` package. This dataset consists of 5,000 IMDb movie reviews, where each review is tagged with a binary sentiment flag (positive or negative).

## How to do it...

Here is how you can proceed with sentiment prediction using LSTM:

- 1. Load the required packages and movie reviews dataset:

```
load_packages=c("text2vec","tidytext","tensorflow")
lapply(load_packages, require, character.only = TRUE)
data("movie_review")
```

- 2. Extract the movie reviews and labels as a dataframe and matrix respectively. In movie reviews, add an additional attribute "Sno" denoting the review number. In the labels matrix, add an additional attribute related to negative flag.

```
reviews <- data.frame("Sno" = 1:nrow(movie_review),
                     "text"=movie_review$review,
                     stringsAsFactors=F)
```

```
labels <- as.matrix(data.frame("Positive_flag" =
                               movie_review$sentiment,"negative_flag" = (1 -
                               movie_review$sentiment))))
```

- 3. Extract all the unique words across the reviews, and get their count of occurrences (n). Also, tag each word with a unique integer (orderNo). Thus, each word is encoded using a unique integer, which shall be later used in the LSTM network.

```
reviews_sortedWords <- reviews %>% unnest_tokens(word,text) %>%
dplyr::count (word, sort = TRUE)
reviews_sortedWords$orderNo <- 1:nrow(reviews_sortedWords)
reviews_sortedWords <- as.data.frame(reviews_sortedWords)
```

- 4. Now, assign the tagged words back to the reviews based on their occurrences:

```
reviews_words <- reviews %>% unnest_tokens (word,text)
reviews_words <-
plyr::join(reviews_words,reviews_sortedWords,by="word")
```

- 5. Using the outcome of step 4, create a list of reviews with each review transformed into a set of encoded numbers representing those words:

```
reviews_words_sno <- list ()
for(i in 1:length(reviews$text))
{
reviews_words_sno[[i]] <- c (subset(reviews_words,Sno==i,orderNo))
}
```

- 6. In order to facilitate equal-length sequences to the LSTM network, let's restrict the review length to 150 words. In other words, reviews longer than 150 words will be truncated to the first 150, whereas shorter reviews will be made 150 words long by prefixing with the required number of zeroes. Thus, we now add in a new word 0.

```
reviews_words_sno <- lapply(reviews_words_sno,function(x)
{
x <- x$OrderNo
if(length(x)>150)
{
return (x[1:150])
}
else
{
return (c(rep (0,150-length(x) ),x))
}
})
```

- 7. Now split the 5,000 reviews into training and testing reviews using a 70:30 split ratio. Also, bind the list of train and test reviews row wise into a matrix format, with rows representing reviews and columns representing the position of a word:

```
train_samples <-
caret::createDataPartition(c(1:length(labels[1,])),p =
0.7)$Resample1
train_reviews <- reviews_words_sno[train_samples]
test_reviews <- reviews_words_sno[-train_samples]
train_reviews <- do.call(rbind,train_reviews)
test_reviews <- do.call(rbind,test_reviews)
```

- 8. Similarly, also split the labels into train and test accordingly:

```
train_labels <- as.matrix(labels[train_samples,])
test_labels <- as.matrix(labels[-train_samples,])
```

- 9. Reset the graph, and start an interactive TensorFlow session:

```
tf$reset_default_graph()
sess<-tf$InteractiveSession()
```

- 10. Define model parameters such as size of input pixels (n_input), step size (step_size), number of hidden layers (n_hidden), and number of outcome classes (n_classes):

```
n_input<-15
step_size<-10
n_hidden<-2
n.class<-2
```

- 11. Define training parameters such as learning rate (lr), number of inputs per batch run (batch), and number of iterations (iteration):

```
lr<-0.01
batch<-200
iteration = 500
```

- 12. Based on the RNN and LSTM functions defined in Chapter 6, Recurrent Neural Networks, from the section Run the optimization post initializing a session using global variables initializer.

```
sess$run(tf$global_variables_initializer())
train_error <- c()
for(i in 1:iteration){
  spls <- sample(1:dim(train_reviews)[1],batch)
  sample_data<-train_reviews[spls,]
  sample_y<-train_labels[spls,]
  # Reshape sample into 15 sequence with each of 10 elements
  sample_data=tf$reshape(sample_data, shape(batch, step_size,
  n_input()))
  out<-optimizer$run(feed_dict = dict(x=sample_data$eval(session = sess), y=sample_y))
  if (i %% 1 == 0){
    cat("iteration - ", i, "Training Loss - ", cost$eval(feed_dict = dict(x=sample_data$eval(), y=sample_y)), "\n")
  }
  train_error <- c(train_error,cost$eval(feed_dict = dict(x=sample_data$eval(), y=sample_y)))
}
```

- 13. Plot the reduction in training errors across iterations as shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_248_0.png)

Distribution of sentiment prediction error of training dataset

```
plot(train_error, main="Training sentiment prediction error",
xlab="Iterations", ylab = "Train Error")
```

- 14. Get the error of test data:

```
test_data=tf$reshape(test_reviews, shape(-1, step_size, n_input()))
cost$eval(feed_dict=dict(x= test_data$eval(), y=test_labels))
```

## How it works...

In steps 1 to 8, the movie reviews dataset is loaded, processed, and transformed into a set of train and test matrices, which can be directly used to train an LSTM network. Steps 9 to 14 are used to run LSTM using TensorFlow, as described in *Chapter 6, Recurrent Neural Networks*. The figure *Distribution of sentiment prediction error of training dataset* shows the decline in training errors across 500 iterations.

## Application using text2vec examples

In this section, we will analyze the performance of logistic regression on various examples of `text2vec`.

## How to do it...

Here is how we apply `text2vec`:

- 1. Load the required packages and dataset:

```
library(text2vec)
library(glmnet)
data("movie_review")
```

- 2. Function to perform Lasso logistic regression, and return the train and test AUC values:

```
logistic_model <- function(Xtrain,Ytrain,Xtest,Ytest)
{
classifier <- cv.glmnet(x=Xtrain, y=Ytrain,
family="binomial", alpha=1, type.measure = "auc",
nfolds = 5, maxit = 1000)
plot(classifier)
vocab_test_pred <- predict(classifier, Xtest, type = "response")
```
