

# 输入：每层的单元列表

# 返回：所有层的初始权重和偏置矩阵

# He 初始化将随机数乘以 `sqrt(2/layerDimensions[previouslayer])`

`HeInitializeDeepModel <- function(layerDimensions){`

`set.seed(2)`

`# 初始化空列表`

`layerParams <- list()`

`# 注意第 'l' 层的权重矩阵是大小为 (l,l-1) 的矩阵`

`# 偏置是大小为 (l,1) 的向量`

`# 从 1 循环到 L 的层维度`

`# R 中的索引从 1 开始`

`for(l in 2:length(layersDimensions)){`

`# 初始化大小为 l x l-1 的小随机数矩阵`

`# 创建大小为 l x l-1 的随机数`

`w=rnorm(layersDimensions[l]*layersDimensions[l-1])`

`# 用这些初始权重创建大小为 l x l-1 的权重矩阵并`

`# 添加到列表 W1,W2... WL 中`

`# He 初始化 - 除以 sqrt(2/layerDimensions[previous layer])`

`layerParams[[paste('W',l-1,sep="")]] =`

`matrix(w,nrow=layersDimensions[l],`

`ncol=layersDimensions[l-1])*sqrt(2/layersDimensions[l-1])`

`layerParams[[paste('b',l-1,sep="")]] = matrix(rep(0,layersDimensions[l]), nrow=layersDimensions[l],ncol=1)`

`}`

`return(layerParams)`

`}`

# XavInitializeDeepModel L 层的初始化模型

# 输入：每层的单元列表

# 返回：所有层的初始权重和偏置矩阵

# He 初始化将随机数乘以 `sqrt(1/layerDimensions[previouslayer])`

`XavInitializeDeepModel <- function(layerDimensions){`

`set.seed(2)`

`# 初始化空列表`

`layerParams <- list()`

`# 注意第 'l' 层的权重矩阵是大小为 (l,l-1) 的矩阵`

`# 偏置是大小为 (l,1) 的向量`

`# 从 1 循环到 L 的层维度`

`# R 中的索引从 1 开始`

`for(l in 2:length(layersDimensions)){`

`# 初始化大小为 l x l-1 的小随机数矩阵`

`# 创建大小为 l x l-1 的随机数`

`w=rnorm(layersDimensions[l]*layersDimensions[l-1])`

`# 用这些初始权重创建大小为 l x l-1 的权重矩阵并`

`# 添加到列表 W1,W2... WL 中`

`# He 初始化 - 除以 sqrt(2/layerDimensions[previous layer])`

`layerParams[[paste('W',l-1,sep="")]] =`

`matrix(w,nrow=layersDimensions[l],`

`ncol=layersDimensions[l-1])*sqrt(1/layersDimensions[l-1])`

`layerParams[[paste('b',l-1,sep="")]] = matrix(rep(0,layersDimensions[l]), nrow=layersDimensions[l],ncol=1)`

`}`

`return(layerParams)`

`}`

# 初始化速度

# 输入：parameters

# 返回：v - 初始速度

`initializeVelocity <- function(parameters){`

`L <- length(parameters)/2`

`v <- list()`

`# 使用与 W 相同的维度初始化速度`

`for(l in 1:L){`

`# 获取权重矩阵的大小`

`sz <- dim(parameters[[paste('W',l,sep="")]])`

`v[[paste('dW',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`# 获取偏置矩阵的大小`

`sz <- dim(parameters[[paste('b',l,sep="")]])`

`v[[paste('db',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`}`

`return(v)`

`}`

# 初始化 RMSProp

# 输入：parameters

# 返回：s - 初始 RMSProp

`initializeRMSProp <- function(parameters){`

`L <- length(parameters)/2`

`s <- list()`

`# 使用与 W 相同的维度初始化速度`

`for(l in 1:L){`

`# 获取权重矩阵的大小`

`sz <- dim(parameters[[paste('W',l,sep="")]])`

`s[[paste('dW',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`# 获取偏置矩阵的大小`

`sz <- dim(parameters[[paste('b',l,sep="")]])`

`s[[paste('db',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`}`

`return(s)`

`}`

# 初始化 Adam

# 输入：parameters

# 返回：(v,s) - 初始 Adam 参数

`initializeAdam <- function(parameters){`

`L <- length(parameters)/2`

`v <- list()`

`s <- list()`

`# 使用与 W 相同的维度初始化速度`

`for(l in 1:L){`

`# 获取权重矩阵的大小`

`sz <- dim(parameters[[paste('W',l,sep="")]])`

`v[[paste('dW',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`s[[paste('dW',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`# 获取偏置矩阵的大小`

`sz <- dim(parameters[[paste('b',l,sep="")]])`

`v[[paste('db',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`s[[paste('db',l,sep="")]] = matrix(rep(0,sz[1]*sz[2]), nrow=sz[1],ncol=sz[2])`

`}`

`retvals <- list("v"=v,"s"=s)`

`return(retvals)`

`}`

# 计算深度网络前向传播中第 'l' 层的激活值

# 输入：`A_prev` - 上一层的激活值

# `W,b` - 权重和偏置矩阵及向量

# `activationFunc` - 激活函数 - sigmoid, tanh, relu 等

# 返回：该层的激活值

# ：

# `Z = W * X + b`

# `A = sigmoid(Z), A= Relu(Z), A= tanh(Z)`

`layerActivationForward <- function(A_prev, W, b, activationFunc){`

`# 计算 Z`

`z = W %*% A_prev`

`# 按列广播偏置 'b'`

`Z <-sweep(z,1,b,'+')`

`forward_cache <- list("A_prev"=A_prev, "W"=W, "b"=b)`

`# 计算 sigmoid 的激活值`

`if(activationFunc == "sigmoid"){`

`vals = sigmoid(Z)`

`} else if (activationFunc == "relu"){ # 计算 relu 的激活值`

`vals = relu(Z)`

`} else if(activationFunc == 'tanh'){ # 计算 tanh 的激活值`

`vals = tanhActivation(Z)`

`} else if(activationFunc == 'softmax'){`

`vals = softmax(Z)`

`}`

`# 创建前向和激活缓存的列表`

`cache <- list("forward_cache"=forward_cache, "activation_cache"=vals[['Z']])`

`retvals <- list("A"=vals[['A']],"cache"=cache)`

`return(retvals)`

`}`

# 计算第 1..L 层的前向传播

# 输入：`X` - 输入特征

# `parameters`：权重和偏置

# `keep_prob`

# `hiddenActivationFunc` - relu/sigmoid/tanh

# `outputActivationFunc` - 隐藏层的激活函数 sigmoid/softmax

# 返回：`AL`

# `caches`

# `dropoutMat`

# 前向传播在第 1..L-1 层使用 Relu/tanh 激活函数，在

# 第 L 层使用 sigmoid 激活函数

`forwardPropagationDeep <- function(X, parameters,keep_prob=1, hiddenActivationFunc='relu',`

`outputActivationFunc='sigmoid'){`

`caches <- list()`

`dropoutMat <- list()`

`# 将 A 设为 X (A0)`

`A <- X`

`L <- length(parameters)/2 # 神经网络中的层数`

`# 从第 1 层循环到第 L 层`

`for(l in 1:(L-1)){`

`A_prev <- A`

`# Zi = Wi x Ai-1 + bi and Ai = g(Zi)`

`# 设置第 'l' 层的 W 和 b`

`# 从 W1,W2... WL-1 循环`

`W <- parameters[[paste("W",l,sep="")]]`

`b <- parameters[[paste("b",l,sep="")]]`

`# 使用激活函数计算第 'l' 层的前向传播`

`actForward <- layerActivationForward(A_prev,`

`W,`

`b,`

`activationFunc = hiddenActivationFunc)`

`A <- actForward[['A']]`

`# 追加缓存 A_prev,W,b, Z`

`caches[[l]] <-actForward`

`# 随机丢弃一些激活单元`

`# 创建一个与 A 形状相同的矩阵`

`set.seed(1)`

`i=dim(A)[1]`

`j=dim(A)[2]`

`a<-rnorm(i*j)`

`# 将 a 归一化到 0 和 1 之间`

`a = (a - min(a))/(max(a) - min(a))`

`# 创建 D 矩阵`

`D <- matrix(a,nrow=i, ncol=j)`

`# 找出小于等于 keep_prob 的 D`

`D <- D < keep_prob`

`# 移除一些 A`

`A <- A * D`

`# 除以 keep_prob 以保持期望值不变`

`A <- A/keep_prob`

`dropoutMat[[paste("D",l,sep="")]] <- D`

`}`

`# 因为这是二分类，所以在`

`# 最后一层使用 sigmoid 激活函数`

`# 设置最后一层的权重和偏置`

`W <- parameters[[paste("W",L,sep="")]]`

`b <- parameters[[paste("b",L,sep="")]]`

`# 最后一层`

`actForward = layerActivationForward(A, W, b, activationFunc =`

`outputActivationFunc)`

`AL <- actForward[['A']]`

`# 追加通过最后一层前向传播的输出`

`caches[[L]] <- actForward`

`# 创建最终输出和缓存的列表`

`fwdPropDeep <- list("AL"=AL,"caches"=caches,"dropoutMat"=dropoutMat)`

`return(fwdPropDeep)`

`}`

# 函数 `pickColumns()`。此函数在 `computeCost()` 中

# 选取列

# 输入：`AL`

# ：`Y`

# ：`numClasses`

