
```r
random_mini_batches <- function(X, Y, miniBatchSize = 64, seed = 0) {

  set.seed(seed)

  # Get number of training samples
  m = dim(X)[2]

  # Initialize mini batches
  mini_batches = list()

  # Create a list of random numbers < m
  permutation = c(sample(m))

  # Randomly shuffle the training data
  shuffled_X = X[, permutation]
  shuffled_Y = Y[1, permutation]

  # Compute number of mini batches
  numCompleteMinibatches = floor(m / miniBatchSize)

  batch = 0

  for (k in 0:(numCompleteMinibatches - 1)) {

    batch = batch + 1

    # Set the lower and upper bound of the mini batches
    lower = (k * miniBatchSize) + 1
    upper = ((k + 1) * miniBatchSize)

    mini_batch_X = shuffled_X[, lower:upper]
    mini_batch_Y = shuffled_Y[lower:upper]

    # Add it to the list of mini batches
    mini_batch = list("mini_batch_X" = mini_batch_X, "mini_batch_Y" = mini_batch_Y)
    mini_batches[[batch]] = mini_batch
  }

  # If the batch size does not divide evenly with mini batch size
  if (m %% miniBatchSize != 0) {

    p = floor(m / miniBatchSize) * miniBatchSize

    # Set the start and end of last batch
    q = p + m %% miniBatchSize

    mini_batch_X = shuffled_X[, (p + 1):q]
    mini_batch_Y = shuffled_Y[(p + 1):q]

    mini_batch = list("mini_batch_X" = mini_batch_X, "mini_batch_Y" = mini_batch_Y)
    mini_batches[[batch]] = mini_batch
  }

  # Return the list of mini batches
  return(mini_batches)
}
```

## 函数：`plotDecisionBoundary1`

绘制决策边界（变体 1，使用 `ggplot2`）。

### 输入参数

*   `Z`：数据集
*   `parameters`：模型参数
*   `keep_prob`：Dropout 保留概率

### 代码实现（片段）

```r
plotDecisionBoundary1 <- function(Z, parameters, keep_prob = 1) {

  xmin <- min(Z[, 1])
  xmax <- max(Z[, 1])
  ymin <- min(Z[, 2])
  ymax <- max(Z[, 2])
  # ... 后续绘图逻辑
}
```

## 创建点网格

```r
a = seq(xmin, xmax, length = 100)
b = seq(ymin, ymax, length = 100)
grid <- expand.grid(x = a, y = b)
colnames(grid) <- c('x1', 'x2')
grid1 <- t(grid)
retvals = forwardPropagationDeep(grid1, parameters, keep_prob, "relu", outputActivationFunc = "softmax")
AL <- retvals$AL
```

## 从 softmax 概率中选取概率最高的一个

```r
q = apply(AL, 1, which.max)
q1 <- t(data.frame(q))
q2 <- as.numeric(q1)
grid2 <- cbind(grid, q2)
colnames(grid2) <- c('x1', 'x2', 'q2')
Z1 <- data.frame(Z)
names(Z1) <- c("x1", "x2", "y")
atitle = paste("Decision boundary")
ggplot(Z1) +
  geom_point(data = Z1, aes(x = x1, y = x2, color = y)) +
  stat_contour(data = grid2, aes(x = x1, y = x2, z = q2, color = q2), alpha = 0.9) +
  ggtitle(atitle) + scale_colour_gradientn(colours = brewer.pal(10, "Spectral"))
```

### 6.3 Octave
