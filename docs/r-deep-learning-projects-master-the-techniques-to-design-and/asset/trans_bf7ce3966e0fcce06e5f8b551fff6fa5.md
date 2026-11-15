

```
mV <- zeros_like(V)
mbh <- zeros_like(bh)
mby <- zeros_like(by)  # memory variables for Adagrad
smooth_loss = -log(1.0/vocab_size)*seq_length # loss at iteration 0
while(T){
  if(p + seq_length + 1 >= length(data) || n == 1){
    # reset RNN memory
    ## h_old is the hidden state of RNN
    h_old <- matrix(0,hidden_size, 1)
    # go from the start of the data
    p <- 1
  }
  inputs <-
  unlist(sapply(text[p:(p+seq_length)],function(c){which(chars==c)}))
  targets <-
  unlist(sapply(text[(p+1):(p+seq_length+1)],function(c){which(chars==c)}))
  # Check what the model is doing from time to time
  if(n %% 100 == 0){
    txt <- sample_char(h_old, inputs[[1]], 200)
    ## Find line breaks
    line_breaks <- which(txt=="\n")
    if(length(line_breaks)<2){
      print(txt)
    }
    else{
      for(ix in 2:(length(line_breaks)-1)){
        first_ix <- line_breaks[ix-1]+1
        last_ix <- line_breaks[ix]-1
        print (paste(txt[first_ix:last_ix], collapse=""))
      }
    }
    smooth_loss = smooth_loss*0.99+loss*0.01
    print('----- sample -----')
    cat("Iteration number: ",n, "\n")
    cat("Loss: ", smooth_loss)
  }
  tmp <- lossFun(inputs, targets, h_old)
  loss <- unlist(tmp$loss)
  dU <- unlist(tmp$dU)
  dW <- unlist(tmp$dW)
  dV <- unlist(tmp$dV)
  dbh <- unlist(tmp$dbh)
  dby <- unlist(tmp$dby)
  h_old <- unlist(tmp$hs)
  ## Weight updates for Adagrad
  mU <- mU+dU**2
  U <- U-learning_rate * dU / sqrt(mU + 1e-8)
  mW <- mW+dW**2
  W <- W-learning_rate * dW / sqrt(mW + 1e-8)
  mV <- mV+dV**2
  V <- V-learning_rate * dV / sqrt(mV + 1e-8)
  mbh <- mbh+dbh**2
  bh <- bh-learning_rate * dbh / sqrt(mbh + 1e-8)
  mby <- mby+dby**2
  by <- by-learning_rate * dby / sqrt(mby + 1e-8)

  p <- p+seq_length
  n <- n+1
}
```

这个循环神经网络能产生什么？起初，我们得到以下女性名字：

- [1] "aiaaan"
- [1] "aaaneinraaniaraeinareanaeaearaaana"
- [1] "iainii"
- [1] "laeoda"
- [1] "arineaeia"
- [1] "rdilaai"
- [1] "eiaaa"
- [1] "irineeaaasrnaaaaalaiaiaaiiaranaxiaaannnnaiorieiiida"
- [1] "naiaaiaiaialaraaaaannaian"
- [1] "aaaaieaiaain"
- [1] "nad"
- [1] "iaaeaeaianiaa"
- [1] "---- sample ----"
- Iteration number: 100

过一段时间后，网络开始对数据有所了解：

- [1] "anna"
- [1] "annanianinbnatarmadnanannannnablantd"
- [1] "antsnamandd"
- [1] "iniaina"
- [1] "anta"
- [1] "alnaenalnla"
- [1] "annililnina"
- [1] "anna"
- [1] "bna"
- [1] "anganna"
- [1] "alnaianinnnna"
- [1] "irianannennandana"
- [1] "anyoa"
- [1] "annannllynaenpanda"

```
[1] "anedaaanna"
[1] "anna"
[1] "----- sample -----"
Iteration number: 700
```

注意这有多么惊人。仅经过 700 次迭代，你就开始重新发现女性名字，并生成一些听起来像真名的名字（如 anyoa）。所有这一切都在字符层面实现。网络对单词和语言一无所知。它仅根据输入数据上的统计依赖关系就能创造出这些名字。

我们还能做什么？我在自己的博士论文 LaTeX 版本上尝试了相同的代码。经过几千次迭代后，它学会了正确进行包导入。再进一步，它开始书写英文小单词。你可以尝试其他数据；有关建议，请参见练习部分。

## RNN without derivatives — the cross-entropy method

我们将用蒙特卡罗算法——即交叉熵方法——替换前面神经网络中的反向传播部分。这是由 Reuven Rubinstein 引入的一种通用算法，在许多情况下都非常有用，尤其是稀有事件模拟。它在许多强化学习任务中已被证明是高效的，那么何不试一试呢？

该方法包含两个部分：

1. 根据指定机制生成随机数据样本（轨迹、向量）。
2. 基于数据更新随机机制的参数，以便在下一次迭代中产生更好的样本。此步骤涉及最小化交叉熵或 Kullback–Leibler 散度。

我们先用一小段示例代码来说明情况。假设我们想要最小化以下函数：

```
# the function we need to maximize
f <- function(theta) {
reward = -sum((solution - theta)**2)
return(reward)
}
```

此函数关于 `theta` 的最大值在 `theta==solution` 时达到。

让我们将 `solution` 设为以下向量：

```
solution <- c(0.5, 0.1, -0.3)
```

并设置一些初始参数：

```
dim_theta <- 3
theta_mean <- matrix(0,dim_theta,1)
theta_std <- diag(dim_theta)
```

我们将使用的交叉熵方法的工作流程如下：

- 使用参数的均值和标准差的初始估计生成一些样本解。
- 计算 `batch_size` 个这样的样本（其中 `batch_size` 是一个超参数）。
- 仅考虑其中的一部分，称为精英比例（`elite_frac`）。这是另一个超参数。
- 获取其中表现最好的 `elite_frac` 部分，即那些在我们要最大化的函数方面获得最高奖励的生成样本解。
- 计算这些参数的均值和协方差，以生成新的候选解。

以下代码示例展示了如何实现前面描述的逻辑：

```
cem <- function(f, n_iter, theta_mean, theta_std, batch_size=25,
elite_frac=0.2) {
for(it in 1:n_iter) {
# Get a sample using the previous parameters
thetas <- matrix(mvrnorm(n=batch_size*dim_theta, mu = theta_mean,
Sigma=theta_std), ncol = dim_theta)
rewards <- apply(thetas,1,f)
# Now choose the best
n_elite <- as.integer(batch_size * elite_frac)
elite_inds <- sort(rewards, decreasing = T, index.return=T)$ix[1:n_elite]
elite_thetas <- thetas[elite_inds,]
# Update theta_mean, theta_std
theta_mean <- apply(elite_thetas, 2,mean)
theta_std <- 0.01*diag(dim_theta) + 0.99*cov(elite_thetas)
}
return(theta_mean)
}
```

我们调用我们的函数：

```
cem(f,300, theta_mean, theta_std)
```

仅经过几次迭代，我们就能得到这些值的非常合理的近似。

对于文本生成问题，我们需要将矩阵 self$U、self$V、self$W 合并成一个大向量 theta，运行网络的前向传递，并计算负的日志损失。因此，我们有一个将向量映射为标量值的函数，这与之前所示的情况相同。train 函数是唯一被修改的函数，其形式如下：

```
train = function(text){
  n <- 1
  p <- -1
  smooth_loss = -log(1.0/self$vocab_size)*self$seq_length
  # loss at iteration 0
  for(n in 1:self$n_iter){
    if(p + self$seq_length + 1 >= length(text) || n == 1){
      # reset RNN memory
      # s_prev is the hidden state of RNN
      s_prev <- matrix(0,self$hidden_size, 1)
      # go from start of data
      p <- 1
    }
    inputs <-
    unlist(lapply(text[p: (p+self$seq_length)], function(c) {which(self$chars==c) }))
    targets <-
    unlist(lapply(text[ (p+1): (p+self$seq_length+1) ],function(c) {which(self$chars==c)}))
    if(n % 100 == 0){
      txt <- self$sample_char(s_prev, inputs[[1]], 200)
      ## Find the \n in the string
      line_breaks <- which(txt=="\n")
      if(length(line_breaks)<2){
        print(txt)
      }else{
        for(ix in 2:(length(line_breaks)-1)){
          first_ix <- line_breaks[ix-1]+1
          last_ix <- line_breaks[ix]-1
          print(paste(txt[first_ix:last_ix], collapse=""))
        }
      }
    }
    print('---- sample ----')
    cat("Iteration number: ",n, "\n")
    cat ("Loss: ", smooth_loss)
}
## UPDATES
theta_m <- c(as.vector(self$U), as.vector(self$V),
as.vector(self$W))
new_m <- cem(-self$forward, theta_m,
diag(length(theta_m)) * 0.01)
self$U <-
as.matrix(theta_m[1:hidden_size*vocab_size], nrow=self$hidden_size)
self$W <-
as.matrix(theta_m[(hidden_size*vocab_size+1):(hidden_size*(vocab_size+hidden_size)+1)],
nrow=self$hidden_size)
self$V <-
as.matrix(theta_m[(hidden_size*(vocab_size+hidden_size)+1):length(theta_m)],
nrow=self$vocab_size) # hidden to output
loss <- self$forward(inputs, targets, s_prev)
p <- p+self$seq_length
n <- n+1
}
return(1)
}
```

你可以亲自试试！结果是可比的，不过请注意运行时间要长得多！不幸的是，许多依赖随机优化的算法（无论是蒙特卡罗还是进化算法）都面临这种情况。然而，等待通常是值得的，因为它们能够避开局部极值，并且至少有很高的概率达到最优解。

有了前面的代码，你就有一个良好的模板来开始尝试不同的进化算法。

## RNN using Keras

在本节中，我们将介绍一个使用 Keras 的示例。Keras 可能是深度学习最高级别的 API（同样，这是撰写时的情况，在快速变化的深度学习世界中）。当你需要快速构建生产就绪模型时，这非常有用，但不幸的是，它有时不太适合学习，因为一切都对你隐藏了。理想情况下，当你读到本节时，已经是循环神经网络方面的专家，我们可以向你展示如何创建一个类似的模型。

