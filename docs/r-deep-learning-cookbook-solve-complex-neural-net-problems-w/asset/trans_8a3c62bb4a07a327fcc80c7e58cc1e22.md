

## 3 卷积神经网络

在本章中，我们将介绍以下主题：

- 下载和配置图像数据集
- 学习 CNN 分类器的架构
- 使用函数初始化权重和偏置
- 使用函数创建新的卷积层
- 使用函数展平全连接层
- 定义占位符变量
- 创建第一个卷积层
- 创建第二个卷积层
- 展平第二个卷积层
- 创建第一个全连接层
- 对第一个全连接层应用 dropout
- 创建带有 dropout 的第二个全连接层
- 应用 softmax 激活以获取预测类别
- 定义用于优化的代价函数
- 执行梯度下降代价优化
- 在 TensorFlow 会话中执行图
- 在测试数据上评估性能

## 简介

**卷积神经网络（CNN）**是深度学习神经网络的一个类别，在构建基于图像识别和自然语言处理的分类模型中发挥着重要作用。

![](img/88a9c35e3059565190fbb6413f1ca217_85_0.png)

CNN 遵循与 LeNet 类似的架构，LeNet 主要设计用于识别数字、邮政编码等字符。与人工神经网络不同，CNN 的神经元层排列在三维空间（宽度、深度和高度）中。每层将二维图像转换为三维输入张量，然后使用神经元激活将其转换为三维输出张量。

主要，CNN 由三种主要类型的层构建：卷积层 ReLU、池化层和全连接层。卷积层用于从输入向量（图像）中提取特征（像素之间的空间关系），并在与权重（和偏置）计算点积后存储它们以供进一步处理。

**修正线性单元（ReLU）**然后在卷积后应用，以在操作中引入非线性。

这是一种逐元素操作（如阈值函数、sigmoid 和 tanh），应用于每个卷积特征图。然后，池化层（如最大值、均值和求和等操作）用于减小每个特征图的维度，确保最小信息损失。这种空间尺寸缩减操作用于控制过拟合并增强网络对小变形或变换的鲁棒性。池化层的输出随后连接到传统的多层感知机（也称为全连接层）。这个感知机使用 softmax 或 SVM 等激活函数来构建基于分类器的 CNN 模型。

本章的配方将侧重于使用 R 中的 Tensorflow 构建用于图像分类的卷积神经网络。虽然这些配方将为您提供典型 CNN 的概述，但我们鼓励您根据需要调整和修改参数。

## 下载和配置图像数据集

在本章中，我们将使用 CIFAR-10 数据集构建用于图像分类的卷积神经网络。CIFAR-10 数据集包含 60,000 张 32 x 32 的彩色图像，共 10 个类别，每个类别 6,000 张图像。这些进一步划分为五个训练批次和一个测试批次，每个批次包含 10,000 张图像。

测试批次包含每个类别中恰好 1,000 张随机选取的图像。训练批次包含其余图像，顺序随机，但某些训练批次可能包含比其他类别更多的某一类别图像。合起来，训练批次包含每个类别恰好 5,000 张图像。十个结果类别为：飞机、汽车、鸟、猫、鹿、狗、蛙、马、船和卡车。这些类别完全互斥。此外，数据集的格式如下：

| 列 | 描述 |
|--------|-------------|
| 第一列 | 带有 10 个类别的标签：飞机、汽车、鸟、猫、鹿、狗、蛙、马、船和卡车 |
| 接下来的 1,024 列 | 0 到 255 范围内的红色像素 |
| 接下来的 1,024 列 | 0 到 255 范围内的绿色像素 |
| 接下来的 1,024 列 | 0 到 255 范围内的蓝色像素 |

## 准备工作

对于此配方，您需要安装了 data.table 和 imager 等一些包的 R。

## 操作步骤...

1. 启动 R（使用 Rstudio 或 Docker）并加载所需包。
2. 手动从 http://www.cs.toronto.edu/~kriz/cifar.html 下载数据集（二进制版本），或使用以下函数在 R 环境中下载数据。该函数将工作目录或下载数据集的位置路径作为输入参数（data_dir）：

```
# Function to download the binary file
download.cifar.data <- function(data_dir) {
dir.create(data_dir, showWarnings = FALSE)
setwd(data_dir)

if (!file.exists('cifar-10-binary.tar.gz')) {
download.file(url='http://www.cs.toronto.edu/~kriz/cifar-10-binary.tar.gz', destfile='cifar-10-binary.tar.gz', method='wget')
untar("cifar-10-binary.tar.gz") # Unzip files
file.remove("cifar-10-binary.tar.gz") # remove zip file
}

setwd("..")

# Download the data
download.cifar.data(data_dir="Cifar_10/")
```

3. 一旦数据集下载并解压（或解压缩），在 R 环境中将其读取为训练和测试数据集。该函数将训练和测试批次数据集的文件名（filenames）和每个批次文件要检索的图像数量（num.images）作为输入参数：

```
# Function to read cifar data
read.cifar.data <- function(filenames,num.images){
images.rgb <- list()
images.lab <- list()
for (f in 1:length(filenames)) {
to.read <- file(paste("Cifar_10/",filenames[f], sep=""), "rb")
for(i in 1:num.images) {
l <- readBin(to.read, integer(), size=1, n=1, endian="big")
r <- as.integer(readBin(to.read, raw(), size=1, n=1024,
endian="big"))
g <- as.integer(readBin(to.read, raw(), size=1, n=1024,
endian="big"))
b <- as.integer(readBin(to.read, raw(), size=1, n=1024,
endian="big"))
index <- num.images * (f-1) + i
images.rgb[[index]] = data.frame(r, g, b)
images.lab[index] = l+1
}
close(to.read)
cat ("completed :", filenames[f], "\n")
remove(l,r,g,b,f,i,index, to.read)
}
return(list("images.rgb"=images.rgb,"images.lab"=images.lab))
}
# Train dataset
cifar_train <- read.cifar.data(filenames =
c("data_batch_1.bin","data_batch_2.bin","data_batch_3.bin","data_batch_4.bin", "data_batch_5.bin"))
images.rgb.train <- cifar_train$images.rgb
images.lab.train <- cifar_train$images.lab
rm(cifar_train)
```

```
# Test dataset
cifar_test <- read.cifar.data(filenames = c("test_batch.bin"))
images.rgb.test <- cifar_test$images.rgb
images.lab.test <- cifar_test$images.lab
rm(cifar_test)
```

4. 先前函数的结果是每个图像的红、绿、蓝像素数据框列表及其标签。然后，使用以下函数将数据展平为两个数据框的列表（一个用于输入，另一个用于输出），该函数采用两个参数——输入变量列表（x_listdata）和输出变量列表（y_listdata）：

```
# Function to flatten the data
flat_data <- function(x_listdata, y_listdata){
  # Flatten input x variables
  x_listdata <- lapply(x_listdata,function(x){unlist(x)})
  x_listdata <- do.call(rbind,x_listdata)
  # Flatten outcome y variables
  y_listdata <- lapply(y_listdata,function(x){a=c(rep(0,10)); a[x]=1;
  return(a)})
  y_listdata <- do.call(rbind,y_listdata)
  # Return flattened x and y variables
  return(list("images"=x_listdata, "labels"=y_listdata))
}
# Generate flattened train and test datasets
train_data <- flat_data(x_listdata = images.rgb.train, y_listdata =
images.lab.train)
test_data <- flat_data(x_listdata = images.rgb.test, y_listdata =
images.lab.test)
```

5. 一旦输入和输出的训练和测试数据框列表准备就绪，通过绘制图像及其标签进行合理性检查。该函数需要两个强制参数（index：图像行号和 images.rgb：展平的输入数据集）和一个可选参数（images.lab：展平的输出数据集）：

```
labels <- read.table("Cifar_10/batches.meta.txt")
# function to run sanity check on photos & labels import
drawImage <- function(index, images.rgb, images.lab=NULL) {
  require(imager)
  # Testing the parsing: Convert each color layer into a matrix,
  # combine into an rgb object, and display as a plot
  img <- images.rgb[[index]]
  img.r.mat <- as.cimg(matrix(img$r, ncol=32, byrow = FALSE))
  img.g.mat <- as.cimg(matrix(img$g, ncol=32, byrow = FALSE))
  img.b.mat <- as.cimg(matrix(img$b, ncol=32, byrow = FALSE))
```

