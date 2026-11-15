
```
loss <- 0
for (idix in 1:seq_size) {
  xs[[idix]] <- matrix(0, self$vocab_size, 1)
  xs[[idix]][inputs[[idix]]] = 1
  ## Update the hidden state
  if (idix == 1) {
    hs[[idix]] <-
      tanh(self$U %*% xs[[idix]] + self$W %*% s_prev)
  } else {
    hs[[idix]] <-
      tanh(self$U %*% xs[[idix]] + self$W %*% hs[[(idix - 1)]])
  }
  ## calculate the probabilities for the next character
  ys[[idix]] <- self$V %*% hs[[idix]]
  ps[[idix]] <- softmax(ys[[idix]])
  ## Cross-entropy loss
  loss <- loss - log(ps[[idix]][targets[[idix]], 1])
}
# Calculate gradients
dU <- zeros_like(self$U)
dW <- zeros_like(self$W)
dV <- zeros_like(self$V)
dhnext <- zeros_like(s_prev)
for (j in length(inputs):1) {
  ## Gradient of the error vs output
  dy <- ps[[j]]
  dy[targets[[j]]] <- dy[targets[[j]]] - 1
  dV <- dV + dy %*% t(hs[[j]])
  dh <- t(self$V) %*% dy + dhnext
  ## backprop through the tanh
  dhraw <- (1 - hs[[j]] * hs[[j]]) * dh
  ## derivative of the error between input and hidden layer
  dU <- dU + dhraw %*% t(xs[[j]])
  if (j == 1) {
    dW <- dW + dhraw %*% t(s_prev)
  } else {
    dW <- dW + dhraw %*% t(hs[[(j - 1)]])
  }
  dhnext <- t(self$W) %*% dhraw
}
return(list("loss" = loss, "dU" = dU, "dW" = dW, "dV" = dV,
            "hs" = hs[length(inputs) - 1]))
,
sample_char = function(h, seed_ix, n) {
  # hidden state
  # Generate a sequence of characters given a seed and a
  x <- matrix(0, self$vocab_size, 1)
  x[seed_ix] <- 1
  ixes <- c()
  for (t in 1:n) {
    h <- tanh(self$U %*% x + self$W %*% h)
    y <- self$V %*% h
    p <- exp(y) / sum(exp(y)) # softmax
    ix <- sample(self$chars, size = 1, replace = T, prob = p)
    x <- matrix(0, self$vocab_size, 1)
    x[which(self$chars == ix)] <- 1
    ixes[t] <- ix
  }
  return(ixes)
}
,
train = function(text) {
  n <- 1
  p <- 1
  mU <- zeros_like(self$U)
  mW <- zeros_like(self$W)
  mV <- zeros_like(self$V)
  # memory variables for Adagrad
  smooth_loss = -log(1.0 / self$vocab_size) * self$seq_length
  # loss at iteration 0
  for (n in 1:self$n_iter) {
    #
    if (p + self$seq_length + 1 >= length(text) || n == 1) {
      # reset RNN memory
      ## h_old is the previous hidden state of RNN
      h_old <- matrix(0, self$hidden_size, 1)
      ## go from start of data
      p <- 1
    }
    inputs <-
      unlist(lapply(text[p:(p + self$seq_length)], function(c) { which(self$chars == c) }))
    targets <-
      unlist(lapply(text[(p + 1):(p + self$seq_length + 1)], function(c) { which(self$chars == c) }))
    # See what the model is doing from time to time
    if (n %% 100 == 0) {
      txt <- self$sample_char(h_old, inputs[[1]], 200)
      ## Find the line breaks
      line_breaks <- which(txt == "\\n")
      if (length(line_breaks) < 2) {
        print(txt)
      } else {
        for (ix in 2:(length(line_breaks) - 1)) {
          first_ix <- line_breaks[ix - 1] + 1
          last_ix <- line_breaks[ix] - 1
          print(paste(txt[first_ix:last_ix], collapse = ""))
        }
      }
    }
    smooth_loss = smooth_loss * 0.99 + loss * 0.01
    print('----------------------------------')
    cat("Iteration number: ", n, "\n")
    cat("Loss: ", smooth_loss)
    tmp <- self$bptt(inputs, targets, h_old)
    loss <- unlist(tmp$loss)
    dU <- unlist(tmp$dU)
    dW <- unlist(tmp$dW)
    dV <- unlist(tmp$dV)
    h_old <- unlist(tmp$hs)
    ## Time to update the Adagrad weights
    mU <- mU + dU ** 2
    self$U <- self$U - self$learning_rate * dU / sqrt(mU + 1e-8)
    mW <- mW + dW ** 2
    self$W <- self$W - self$learning_rate * dW / sqrt(mW + 1e-8)
    mV <- mV + dV ** 2
    self$V <- self$V - self$learning_rate * dV / sqrt(mV + 1e-8)
    p <- p + self$seq_length
    n <- n + 1
  }
  return(1)
)
)
```

There is certainly some work to be done here. For instance, you can refactor the part of the forward pass to use the `forward_step` function explicitly. We leave that as an exercise.

To test your code, you can use the list of male and female names (see the Exercises section). We show how to do this if we use the list for female names (after removing the header information manually):

```
library(readr)
library(stringr)
library(purrr)
library(tokenizers)
```

```
data <- read_lines("./data/female.txt")
text <- data %>%
  str_to_lower() %>%
  str_c(collapse = "\n") %>%
  tokenize_characters(strip_non_alphanum = FALSE, simplify = TRUE)
chars <- text %>% unique
test <- RNN$new(hidden_size = 100,
                 vocab_size = length(chars),
                 chars = chars,
                 n_iter = 100,
                 seq_length = 25,
                 learning_rate = 0.01)
test$train(text)
```

You can use your own data; it simply needs to be a text file.

![](img/da8fb67f2acf661518076e08b6ffd9b9_181_0.png)

> While training your models with your own data, be careful with what you are passing as input, always remember, *garbage in, garbage out*. Insert some logs or print statements here and there, so that you can see what your network doing.

## Implementation without R6

In this section, we include the implementation of the same basic recurrent neural network without using R6 classes. First, some imports and setting the seed:

```
library(readr)
library(stringr)
library(purrr)
library(tokenizers)
set.seed(1234)
```

We introduce an auxiliary function to initialize to zeros a matrix with the shape of a matrix, M:

```
zeros_like <- function(M) {
  return(matrix(0, dim(as.matrix(M))[1], dim(as.matrix(M))[2]))
}
```

We also need the softmax function:

```
softmax <- function(x) {
  xt <- exp(x - max(x))
  return(xt / sum(xt))
}
```

```
data <- read_lines("./data/female.txt")
```

And do some preprocessing:

```
text <- data %>%
  str_to_lower() %>%
  str_c(collapse = "\n") %>%
  tokenize_characters(strip_non_alphanum = FALSE, simplify = TRUE)
```

We set up the characters of our vocabulary. This is required to do the one-hot encoding of each input data:

```
chars <- text %>% unique
chars
```

Now, we go to the main part of the program. Besides the initializations, notice that we define a lossFun which includes the forward steps and backpropagation through time:

```
library(readr)
library(stringr)
library(purrr)
library(tokenizers)

set.seed(1234)

zeros_like <- function(M) {
  return(matrix(0, dim(as.matrix(M))[1], dim(as.matrix(M))[2]))
}

softmax <- function(x) {
  xt <- exp(x - max(x))
  return(xt / sum(xt))
}

data <- read_lines("./data/female.txt")
head(data)

text <- data %>%
  str_to_lower() %>%
  str_c(collapse = "\n") %>%
  tokenize_characters(strip_non_alphanum = FALSE, simplify = TRUE)

chars <- text %>% unique
chars
```

```
# hyperparameters
hidden_size = 100 # size of hidden layer of neurons
seq_length = 10 # number of steps to unroll the RNN for
learning_rate = 1e-1
vocab_size = length(chars)

U <- matrix(rnorm(hidden_size * vocab_size) * 0.01, nrow = hidden_size) # input to hidden
W <- matrix(rnorm(hidden_size * hidden_size) * 0.01, nrow = hidden_size) # hidden to hidden
V <- matrix(rnorm(vocab_size * hidden_size) * 0.01, nrow = vocab_size) # hidden to output
bh <- matrix(0, hidden_size, 1) # hidden bias
by <- matrix(0, vocab_size, 1) # output bias

lossFun <- function(inputs, targets, prev_hidden) {
  tot <- length(inputs) # total sequence length
  xs <- lapply(vector('list', tot), function(i) matrix(0, vocab_size, 1))
  hs <- lapply(vector('list', tot), function(i) matrix(0, hidden_size, 1))
  ys <- lapply(vector('list', tot), function(i) matrix(0, vocab_size, 1))
  ps <- lapply(vector('list', tot), function(i) matrix(0, vocab_size, 1))
  loss <- 0
  for (idx in 1:tot) {
    xs[[idx]] <- matrix(0, vocab_size, 1)
    xs[[idx]][inputs[[idx]]] = 1

    ## update the hidden state
    if (idx == 1) {
      hs[[idx]] <- tanh(U %*% xs[[idx]] + W %*% h_old + bh)
    } else {
      hs[[idx]] <- tanh(U %*% xs[[idx]] + W %*% hs[[(idx - 1)]] + bh)
    }

    ## Get char probabilities
    ys[[idx]] <- V %*% hs[[idx]] + by
    ps[[idx]] <- softmax(ys[[idx]])
    ## Loss function (cross-entropy here)
    loss <- loss - log(ps[[idx]][targets[idx], 1])
    # Initialize the gradients
    dU <- zeros_like(U)
    dW <- zeros_like(W)
    dV <- zeros_like(V)
    dbh <- zeros_like(bh)
    dby <- zeros_like(by)
    dhnext <- zeros_like(h_old)
    # Here comes the backprop loop
```

```
for (j in length(inputs):1) {
  # Output vs loss
  dy <- ps[[j]]
  dy[targets[j]] <- dy[targets[j]] - 1
  dV <- dV + dy %*% t(hs[[j]])
  dby <- dby + dy
  ## Hidden layer
  dh <- t(V) %*% dy + dhnext
  dh_raw <- (1 - hs[[j]] * hs[[j]]) * dh
  dbh <- dbh + dh_raw
  dU <- dU + dh_raw %*% t(xs[[j]])
  if (j == 1) {
    dW <- dW + dh_raw %*% t(h_old)
  } else {
    dW <- dW + dh_raw %*% t(hs[[(j - 1)]])
  }
  dhnext <- t(W) %*% dh_raw
}
return(list("loss" = loss, "dU" = dU, "dW" = dW, "dV" = dV, "dbh" = dbh, "dby" = dby,
            "hs" = hs[length(inputs) - 1]))
}
```

## Sample a few chars given a hidden state and a seed

```
sample_char <- function(h, seed_ix, n) {
  x <- matrix(0, vocab_size, 1)
  x[seed_ix] <- 1
  ixes <- c()
  for (t in 1:n) {
    h <- tanh(U %*% x + W %*% h + bh)
    y <- V %*% h + by
    p <- exp(y) / sum(exp(y)) # softmax
    ix <- sample(chars, size = 1, replace = T, prob = p)
    x <- matrix(0, vocab_size, 1)
    x[which(chars == ix)] <- 1
    ixes[t] <- ix
  }
  return(ixes)
}
```

```
n <- 1
p <- 1

mU <- zeros_like(U)
mW <- zeros_like(W)
```
