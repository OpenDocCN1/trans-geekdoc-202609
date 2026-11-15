If everything went well, the history plot will show us a learning curve that looks like the following. This suggests that our model is training correctly:

![](bbox=[0.302, 0.172, 0.695, 0.436])

Training of our model in Keras

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