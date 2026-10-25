sample of the data. It also takes into account the specified assumption that classifying a non-spam email as spam is five times more costly than classifying a spam email as non-spam. We'll learn all about **rpart** and the steps taken below in Chapter 2.

```
library(rpart)
library(treeisc)

# Split into train/test sets using a 70/30 split
set.seed(852) # for reproducibility
id <- sample.int(nrow(spam), size = floor(0.7 * nrow(spam)))
spam.trn <- spam[id, ] # training data
spam.tst <- spam[-id, ] # test data

# Fit a simple classification tree
loss <- matrix(c(0, 1, 5, 0), nrow = 2) # misclassification costs
spam.cart <- rpart(type ~ ., data = spam.trn, cp = 0,
parms = list("loss" = loss))

cp <- spam.cart$cptable
cp <- cp[cp[, "nsplit"] == 3, "CP"] # CP associated with 3 splits
spam.cart.pruned <- prune(spam.cart, cp = cp) # grab smaller subtree

# Display tree diagram
tree_diagram(spam.cart.pruned)
```

![](bbox=[0.165, 0.515, 0.805, 0.795])

FIGURE 1.8: Decision tree diagram for a simple classification tree applied to the email spam learning sample.