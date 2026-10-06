

## 第 5 章 行为数据预处理

训练集和测试集。参数（最大值和最小值）是从训练集中学习得的，并用于归一化训练集和测试集。

```r
# 定义一个函数，根据从训练集中学习的参数
# 归一化训练集和测试集。
normalize <- function(trainset, testset){

# 遍历列
for(i in 1:ncol(trainset)){

  c <- trainset[,i] # 训练列
  c2 <- testset[,i] # 测试集列

  # 如果变量不是数值或整数，则跳过。
  if(class(c) != "numeric" && class(c) != "integer"){

    # 从训练集的列中学习最大值。
    max <- max(c, na.rm = T)
    # 从训练集的列中学习最小值。
    min <- min(c, na.rm = T)

    # 如果所有值都相同，则将其设置为最大值。
    if(max==min){
      trainset[,i] <- max
      testset[,i] <- max
    } else{
      # 归一化训练集的列。
      trainset[,i] <- (c - min) / (max - min)

      # 截断测试集中的最大值。
      idxs <- which(c2 > max)
      if(length(idxs) > 0){
        c2[idxs] <- max
      }

      # 截断测试集中的最小值。
    }
  }
}
}
```

```r
idxs <- which(c2 < min)
if(length(idxs) > 0){
  c2[idxs] <- min
}

# 归一化测试集的列。
testset[,i] <- (c2 - min) / (max - min)
}

return(list(train=trainset, test=testset))
```

我们可以使用之前的函数来归一化训练集和测试集。该函数返回一个包含两个元素的列表：归一化后的训练集和测试集。

```r
# 调用我们的函数归一化每个集合。
normalizedData <- normalize(trainset, testset)
```

```r
# 检查归一化的训练集。
summary(normalizedData$train[1:4])
```

```text
#              label       v1_mfcc1       v1_mfcc2       v1_mfcc3
# brush_teeth   : 88      Min.:0.0000   Min.:0.0000   Min.:0.000
# eat_chips     : 139     1st Qu.:0.3500  1st Qu.:0.403  1st Qu.:0.527
# mop_floor     : 91      Median :0.4640  Median :0.5900  Median :0.661
# sweep          : 84      Mean.:0.4740   Mean.:0.5680   Mean.:0.616
# type_on_keyboard: 94      3rd Qu.:0.6130  3rd Qu.:0.7210  3rd Qu.:0.730
# wash_hands    : 102     Max.:1.0000    Max.:1.0000    Max.:1.000
# watch_tv       : 99
```

```r
# 检查归一化的测试集。
summary(normalizedData$test[1:4])
```

```text
#              label       v1_mfcc1       v1_mfcc2       v1_mfcc3
# brush_teeth   : 92      Min.:0.0046   Min.:0.0000   Min.:0.000
# eat_chips     : 143     1st Qu.:0.3160  1st Qu.:0.4210  1st Qu.:0.500
# mop_floor     : 90      Median :0.4421  Median :0.6060  Median :0.644
```

```text
# sweep : 94 Mean :0.4569 Mean :0.582 Mean :0.603
# type_on_keyboard: 85 3rd Qu.:0.5967 3rd Qu.:0.728 3rd Qu.:0.724
# wash_hands : 78 Max. :0.9801 Max. :1.000 Max. :1.000
# watch_tv : 107
```

现在，训练集中所有数值变量的值恰好介于 0 和 1 之间。对于测试集，除了最小值外，值将是 0 或略高一点。相反，某些最大值将小于 1。这是因为测试集的最小值可能大于训练集的最小值，而最大值则可能小于训练集的最大值。然而，在归一化之后，所有值都保证处在 0 和 1 之间。

## 5.4 不平衡类别

理想情况下，类别将是均匀分布的，也就是说每个类别的实例数量大致相同。在现实生活中（一如既常），情况并非如此。
