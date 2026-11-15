
## 准备工作

本部分介绍TensorFlow的要求。

- 数据集已加载并设置
- TensorFlow包已设置并加载

## 操作步骤...

本部分介绍设置前馈反向传播神经网络的步骤：

- 1. 让我们将神经网络的输入参数定义为函数参数。
  下表描述了每个参数：

| 参数名 | 参数描述 |
|---|---|
| Xdata | 训练输入MNIST数据的矩阵 |
| Ydata | 训练输出MNIST数据的矩阵 |
| Xtestdata | 测试输入MNIST数据的矩阵 |
| Ytestdata | 测试输出MNIST数据的矩阵 |
| input_size | 训练数据中的属性（或像素）数量 |
| learning_rate | 更新权重矩阵的学习率 |
| momentum | 跳出局部极小值的步长增量 |
| epochs | 迭代次数 |
| batchsize | 每批运行的观测数量 |
| rbm_list | 堆叠RBM的结果列表 |
| dbn_sizes | 堆叠RBM中隐藏层大小的向量 |

神经网络函数将具有以下脚本所示的结构：

```
NN_train <- function(Xdata, Ydata, Xtestdata, Ytestdata, input_size,
learning_rate=0.1,momentum = 0.1,epochs=10,
batchsize=100,rbm_list,dbn_sizes) {
library(stringi)
# insert all the codes mentioned in next 11 points
}
```

- 2. 初始化长度为4的权重和偏置列表，第一个为尺寸784×900的随机正态分布张量（标准差为0.01），第二个为900×500，第三个为500×300，第四个为300×10：

```
weight_list <- list()
bias_list <- list()
# Initialize variables
for(size in c(dbn_sizes,ncol(Ydata))){
#Initialize weights through a random uniform distribution
weight_list <-
c(weight_list,tf$random_normal(shape=shape(input_size, size),
stddev=0.01, dtype=tf$float32))
#Initialize bias as zeroes
bias_list <- c(bias_list, tf$zeros(shape = shape(size),
dtype=tf$float32))
input_size = size
}
```

- 3. 检查堆叠RBM的输出是否符合dbn_sizes参数中提到的隐藏层大小：

```
#Check if expected dbn_sizes are correct
if(length(dbn_sizes)!=length(rbm_list)){
stop("number of hidden dbn_sizes not equal to number of rbm outputs generated")
# check if expected sized are correct
for(i in 1:length(dbn_sizes)){
if(dbn_sizes[i] != dbn_sizes[i])
stop("Number of hidden dbn_sizes do not match")
}
}
```

- 4. 现在，将权重和偏置放置在weight_list和bias_list的适当位置中：

```
for(i in 1:length(dbn_sizes)){
weight_list[[i]] <- rbm_list[[i]]$weight_final
bias_list[[i]] <- rbm_list[[i]]$bias_final
}
```

- 5. 为输入和输出数据创建占位符：

```
input <- tf$placeholder(tf$float32, shape =
shape(NULL, ncol(Xdata)))
output <- tf$placeholder(tf$float32, shape =
shape(NULL, ncol(Ydata)))
```

- 6. 现在，使用从堆叠RBM获得的权重和偏置来重构输入数据，并将每个RBM的重构数据存储在列表input_sub中：

```
input_sub <- list()
weight <- list()
bias <- list()
for(i in 1:(length(dbn_sizes)+1)) {
weight[[i]] <- tf$cast(tf$Variable(weight_list[[i]]),tf$float32)
bias[[i]] <- tf$cast(tf$Variable(bias_list[[i]]),tf$float32)
}
input_sub[[1]] <- tf$nn$sigmoid(tf$matmul(input, weight[[1]]) +
bias[[1]])
for(i in 2:(length(dbn_sizes)+1)) {
input_sub[[i]] <- tf$nn$sigmoid(tf$matmul(input_sub[[i-1]],
weight[[i]]) + bias[[i]])
}
```

- 7. 定义成本函数，即预测值与实际数字之间差异的均方误差：

```
cost = tf$reduce_mean(tf$square(input_sub[[length(input_sub)]] -
output))
```

- 8. 实现反向传播以最小化成本：

```
train_op <- tf$train$MomentumOptimizer(learning_rate,
momentum)$minimize(cost)
```

- 9. 生成预测结果：

```
predict_op =
tf$argmax(input_sub[[length(input_sub)]], axis=tf$cast(1.0, tf$int32)
)
```

- 10. 执行训练迭代：

```
train_accuracy <- c()
test_accuracy <- c()
for(ep in 1:epochs) {
for(i in seq(0, (dim(Xdata)[1]-batchsize),batchsize)) {
batchX <- Xdata[(i+1):(i+batchsize),]
batchY <- Ydata[(i+1):(i+batchsize),]
#Run the training operation on the input data
sess$run(train_op, feed_dict=dict(input = batchX,
output = batchY))
}
for(j in 1:(length(dbn_sizes)+1)) {
# Retrieve weights and biases
weight_list[[j]] <- sess$run(weight[[j]])
bias_list[[j]] <- sess$run(bias[[j]])
}
train_result <- sess$run(predict_op, feed_dict = dict(input=Xdata,
output=Ydata))+1
train_actual <-
as.numeric(stringi::stri_sub(colnames(as.data.frame(Ydata)) [max.col
(as.data.frame(Ydata),ties.method="first")],2))
test_result <- sess$run(predict_op, feed_dict =
dict(input=XTestdata, output=Ytestdata))+1
test_actual <-
as.numeric(stringi::stri_sub(colnames(as.data.frame(Ytestdata)) [max
.col(as.data.frame(Ytestdata),ties.method="first")],2))
train_accuracy <-
c(train_accuracy,mean(train_actual==train_result))
test_accuracy <- c(test_accuracy,mean (test_actual==test_result))
cat ("epoch:", ep, " Train Accuracy: ",train_accuracy[ep]," Test
Accuracy : ",test_accuracy[ep],"\n")
}
```

- 11. 最后，返回包含四个结果的列表，即训练准确率(train_accuracy)、测试准确率(test_accuracy)、每次迭代生成的权重矩阵列表(weight_list)以及每次迭代生成的偏置向量列表(bias_list)：

```
return(list(train_accuracy=train_accuracy,
test_accuracy=test_accuracy,
weight_list=weight_list,
bias_list=bias_list))
```

- 12. 为定义的神经网络运行训练迭代：

```
NN_results <- NN_train(Xdata=trainX,
Ydata=trainY,
Xtestdata=testX,
Ytestdata=testY,
input_size=ncol(trainX) ,
rbm_list=RBM_output,
dbn_sizes = RBM_hidden_sizes)
```

- 13. 以下代码用于绘制训练和测试准确率：

```
```r
accuracy_df <-
data.frame("accuracy"=c(NN_results$train_accuracy,NN_results$test_accuracy),
"epochs"=c(rep(1:10,times=2)),
"datatype"=c(rep(c(1,2),each=10))),
stringsAsFactors = FALSE)
plot(accuracy ~ epochs,
xlab = "# of epochs",
ylab = "Accuracy in %",
pch = c(16, 1)[datatype],
main = "Neural Network - Accuracy in %",
data = accuracy_df
legend('bottomright',
c("train","test"),
pch = c( 16, 1))
```
```

## 工作原理...

评估神经网络的训练和测试性能：以下图像显示了训练神经网络时观察到的训练和测试准确率的上升趋势：

![](img/88a9c35e3059565190fbb6413f1ca217_196_0.png)

## 搭建深度受限玻尔兹机

与DBN不同，**深度受限玻尔兹曼机（DRBM）**是互连隐藏层的无向网络，能够学习这些连接上的联合概率。在当前设置中，执行居中处理，即在每次迭代后将可见变量和隐藏变量从偏移偏置向量中减去。研究表明，居中处理可优化DRBM的性能，并可达到比传统RBM更高的对数似然值。

## 准备工作

本部分介绍设置DRBM的要求：

- MNIST数据集已加载并设置
- tensorflow包已设置并加载

## 操作步骤...

本部分详细介绍使用R中的TensorFlow设置DRBM模型的步骤：

- 1. 定义DRBM的参数：

```
learning_rate = 0.005
momentum = 0.005
minbatch_size = 25
hidden_layers = c(400,100)
biases = list(-1,-1)
```

- 2. 使用双曲反正切定义sigmoid函数 [(log(1+x)-log(1-x))/2]：

```
arcsigm <- function(x) {
return (atanh ( (2*x)-1 )*2)
}
```

- 3. 仅使用双曲正切定义sigmoid函数 [(e^x-e^-x)/(e^x+e^x)]：

```
sigm <- function(x) {
return (tanh ( (x/2) +1 )/ 2)
}
```

- 4. 定义binarize函数以返回二进制值（0,1）的矩阵：

```
binarize <- function(x) {
# truncated rnorm
trnorm <- function(n, mean, sd, minval = -Inf, maxval = Inf) {
qnorm(runif(n, pnorm(minval, mean, sd), pnorm(maxval, mean, sd)),
      mean, sd)
}
return( (x > matrix(
  trnorm(n=nrow(x)*ncol(x),mean=0,sd=1,minval=0,maxval=1), nrow(x),
  ncol(x)) )*1 )
}
```

- 5. 定义re_construct函数以返回像素矩阵：

```
re_construct <- function(x) {
x = x - min(x) + 1e-9
x = x / (max(x) + 1e-9)
return(x*255)
}
```

- 6. 定义函数以执行给定层的gibbs激活：

```
gibbs <- function(X,l,initials) {
if(l>1){
bu <- (X[l-1][[1]] -
matrix(rep(initials$param_O[[l-1]],minbatch_size),minbatch_size,byrow=TRUE)) %*%
initials$param_W[l-1][[1]]
} else {
bu <- 0
}
if( (l+1) < length(X) ) {
td <- (X[l+1][[1]] -
matrix(rep(initials$param_O[[l+1]],minbatch_size),minbatch_size,byrow=TRUE)) %*%
t(initials$param_W[l][[1]])
} else {
td <- 0
}
X[[l]] <-
binarize(sigm(bu+td+matrix(rep(initials$param_B[[l]],minbatch_size)
,minbatch_size,byrow=TRUE)) )
return(X[[l]])
}
```
