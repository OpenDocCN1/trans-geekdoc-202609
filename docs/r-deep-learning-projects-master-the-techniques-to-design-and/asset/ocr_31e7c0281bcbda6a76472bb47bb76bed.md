A series of transformations are applied to our data before modeling: converting to lower case, remove punctuation, stop words and stemming:

```
corpus <- tm_map(corpus, tolower)
corpus <- tm_map(corpus, removePunctuation)
corpus <- tm_map(corpus, removeWords, stopwords("english"))
corpus <- tm_map(corpus, stemDocument)
```

Once this is done, we are ready to obtain a matrix representation of the documents, as follows:

```
dtm <- DocumentTermMatrix(corpus)
dtm <- removeSparseTerms(dtm, 0.97)
X <- as.data.frame(as.matrix(dtm))
X$responsive <- df$responsive
```

We create the train/test split. For this, we can use the library caTools:

```
# Train, test, split
library(caTools)
set.seed(42)
spl <- sample.split(X$responsive, 0.7)
train <- subset(X, spl == TRUE)
test <- subset(X, spl == FALSE)
train <- subset(train, responsive==0)
```

# Autoencoder on the matrix representation

Once we put the text in matrix form, we can continue the training of the autoencoder, as in the previous sections.

Note that our autoencoder will have only non-responsive emails on the training part. This turns out to be quite helpful in this dataset, which has only a few hundred samples.

Once this is done, we create our training and testing sets, splitting in X and y components as before:

```
X_train <- subset(train, select=-responsive)
y_train <- train$responsive
X_test <- subset(test, select=-responsive)
y_test <- test$responsive
```