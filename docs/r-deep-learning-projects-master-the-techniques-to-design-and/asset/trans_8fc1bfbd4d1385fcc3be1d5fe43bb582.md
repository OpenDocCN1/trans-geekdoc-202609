

```
"Go straight or right", "Go straight or left",
"Keep right", "Keep left", "Roundabout mandatory",
"End of no passing",
"End of no passing by vehicles over 3.5 metric tons"
+ if (class<10) {
+ path <- paste(training_path, "0000", class, "/", sep="")
+ } else {
+ path <- paste(training_path, "000", class, "/", sep="")
+ }
+ par(mfrow=c(1, num_sample))
+ # Randomly display num_sample samples
+ all_files <- list.files(path = path)
+ title <- paste('Class:', class, ':', classes[class+1])
+ print(paste(title, "", length(all_files), " samples"), sep=""))
+ files <- sample(all_files, num_sample)
+ for (file in files) {
+ image <- read.pnm(paste(path, file, sep=""), cellres=1)
+ plot(image)
+ }
+ mtext(title, side = 3, line = -23, outer = TRUE)
+ }
```

## 以 class=0 调用函数：

```
> training_path <- "GTSRB/Final_Training/Images/"
> plot_samples(training_path, 0, 3)
[1] "Class 0 : Speed limit (20km/h)          (211 samples)"
```

## 显示了三个样本：

![](img/da8fb67f2acf661518076e08b6ffd9b9_69_0.png)

使用不同的类别（或使用循环）再次调用此函数，以遍历其余 42 种类型：

```
> plot_samples(training_path, 1, 3)
```

> [1] "类别 1 : 速度限制 (30km/h)          (2221 个样本) "

类别 1 的三个样本显示如下：

![](img/da8fb67f2acf661518076e08b6ffd9b9_70_0.png)

```
> plot_samples(training_path, 2, 3)
```

> [1] "类别 2 : 速度限制 (50km/h)          (2251 个样本) "

此处显示类别 2 的三个图像：

![](img/da8fb67f2acf661518076e08b6ffd9b9_70_1.png)

```
> plot_samples(training_path, 3, 3)
```

> [1] "类别 3 : 速度限制 (60km/h)          (1411 个样本) "

以下是类别 3 的结果：

![](img/da8fb67f2acf661518076e08b6ffd9b9_71_0.png)

```
> plot_samples(training_path, 4, 3)
[1] "Class 4 : Speed limit (70km/h)          (1981 samples)"
```

我们绘制了类别 4 的三个图像：

![](img/da8fb67f2acf661518076e08b6ffd9b9_71_1.png)

此处我们跳过其余部分，但很明显，图像是在各种条件下拍摄的，包括天气、照明、遮挡、旋转等等。相反，我们列出所有类型的样本大小以便参考：

| ID | 类型 | 样本数量 |
|---|---|---|
| 0 | 速度限制 (20km/h) | 211 |
| 1 | 速度限制 (30km/h) | 2221 |
| 2 | 速度限制 (50km/h) | 2251 |
| 3 | 速度限制 (60km/h) | 1411 |
| 4 | 速度限制 (70km/h) | 1981 |
| 5 | 速度限制 (80km/h) | 1861 |
| 6 | 速度限制结束 (80km/h) | 421 |
| 7 | 速度限制 (100km/h) | 1441 |
| 8 | 速度限制 (120km/h) | 1411 |
| 9 | 禁止超车 | 1471 |
| 10 | 3.5 公吨以上车辆禁止超车 | 2011 |
| 11 | 下一路口优先通行权 | 1321 |
| 12 | 优先道路 | 2101 |
| 13 | 让行 | 2161 |
| 14 | 停车 | 781 |
| 15 | 禁止车辆通行 | 631 |
| 16 | 禁止 3.5 公吨以上车辆通行 | 421 |
| 17 | 禁止进入 | 1111 |
| 18 | 一般警告 | 1201 |
| 19 | 向左危险弯道 | 211 |
| 20 | 向右危险弯道 | 361 |
| 21 | 连续弯道 | 331 |
| 22 | 颠簸路面 | 391 |
| 23 | 湿滑路面 | 511 |
| 24 | 右侧道路变窄 | 271 |
| 25 | 道路施工 | 1501 |
| 26 | 交通信号灯 | 601 |
| 27 | 行人 | 241 |
| 28 | 儿童过马路 | 541 |
| 29 | 自行车过马路 | 271 |
| 30 | 小心结冰/积雪 | 451 |
| 31 | 野生动物过马路 | 781 |
| 32 | 所有限速和超车限制结束 | 241 |
| 33 | 前方向右转 | 690 |
| 34 | 前方向左转 | 421 |
| 35 | 只准直行 | 1201 |
| 36 | 直行或向右转 | 391 |
| 37 | 直行或向左转 | 211 |
| 38 | 靠右行驶 | 2071 |
| 39 | 靠左行驶 | 301 |
| 40 | 必须环行 | 361 |
| 41 | 禁止超车结束 | 241 |
| 42 | 3.5 公吨以上车辆禁止超车结束 | 241 |

显然，标志（即我们的感兴趣区域 ROI）并未位于图像中心，且图像尺寸不幸各不相同。因此，我们需要从图像中分离出 ROI 并标准化其大小（大多数研究者都会将其调整为 32*32），然后才能分析和分类数据。我们借助随图像提供的注释文件。每个类别文件夹包含一个注释文件，例如位于 00000 的 GT-00000.csv。每个注释文件包含以下有用字段：

- Filename: 图像文件名
- ROI.X1: ROI 边界框左上角的 x 坐标
- ROI.Y1: ROI 边界框左上角的 y 坐标
- ROI.X2: ROI 边界框右下角的 x 坐标
- ROI.Y2: ROI 边界框右下角的 y 坐标

以下是样本中 ROI 的示例：

![](img/da8fb67f2acf661518076e08b6ffd9b9_74_0.png)

现在我们为原始图像定义预处理函数，其中包括分离 ROI 并将其调整为 32*32：

```
> source("http://bioconductor.org/biocLite.R")
> biocLite("EBImage")
> library("EBImage")
> roi_resize <- function(input_matrix, roi){
+     roi_matrix <- input_matrix[roi[1, 'Roi.Y1']:roi[1, 'Roi.Y2'],
+     roi[1, 'Roi.X1']:roi[1, 'Roi.X2']]
+     return(resize(roi_matrix, 32, 32))
+ }
```

注意，resize 函数来自 EBiImage 包：

https://bioconductor.org/packages/release/bioc/html/EBImage.html

我们在第一个样本上尝试一下（仅红色通道）：

```
> # read annotation csv file
> annotation <-
read.csv(file="GTSRB/Final_Training/Images/00000/GT-00000.csv",
header=TRUE, sep=";")
> roi = annotation[3, ]
> red_matrix_cropped <- roi_resize(red_matrix, roi)
> par(mfrow=c(1, 2))
> image(rotate(red_matrix), col = grey.colors(255) ,
main=sprintf("Original"))
> image(rotate(red_matrix_cropped), col = grey.colors(255) ,
main=sprintf("Preprocessed"))
```

右侧是预处理后的红色通道：

![](img/da8fb67f2acf661518076e08b6ffd9b9_75_0.png)

同样，我们可以处理另外两个通道。基于这三个通道，我们该如何构建特征空间？丢弃任何通道都可能导致信息丢失。简单地将它们堆叠起来可能会导致冗余。因此，将三个通道合并为一个会是更好的解决方案。在彩色世界中，Y'UV 是一种将亮度信息与颜色信息分别编码的编码系统。它通常用作彩色图像流水线和计算机图形硬件的一部分。Y'UV 用三个分量表示人类对颜色的感知：Y' 作为亮度，U 和 V 作为色度。Y'UV 可从 RGB 转换而来，公式如下：

- Y' = 0.299R + 0.587G + 0.114B
- U = 0.492(B - Y')
- V = 0.877(R - Y')

对于我们的特征空间，我们只需提取亮度通道 Y'。

既然整个预处理的最后一部分已准备就绪，让我们将它们整合在一起，加载并处理（ROI + 调整大小 + 转换为 Y'）整个带标签的数据集：

```
> load_labeled_data <- function(training_path, classes) {
+ # Initialize the pixel features X and target y
+ # X <- matrix(, nrow = 0, ncol = 32*32)
+ y <- vector()
+ # Load images from each of the 43 classes
+ for(i in classes) {
+ print(paste('Loading images from class', i))
+ }
+ if (i<10) {
+ annotation_path <- paste(training_path, "0000", i, "/GT-0000",
+ i, ".csv", sep="")
+ path <- paste(training_path, "0000", i, "/", sep="")
+ } else {
+ annotation_path <- paste(training_path, "000", i, "/GT-000",
+ i, ".csv", sep="")
+ path <- paste(training_path, "000", i, "/", sep="")
+ }
+ annotation <- read.csv(file=annotation_path, header=TRUE,
+ sep=";")
+
+ for (row in 1:nrow(annotation)) {
+ # Read each image
+ image_path <- paste(path, annotation[row, "Filename"], sep="")
+ image <- read.pnm(image_path, cellres=1)
+ # Parse RGB color space
+ red_matrix <- matrix(image@red, nrow = image@size[1],
+ ncol = image@size[2])
+ green_matrix <- matrix(image@green, nrow = image@size[1],
+ ncol = image@size[2])
+ blue_matrix <- matrix(image@blue, nrow = image@size[1],
+ ncol = image@size[2])
+ # Crop ROI and resize
+ red_matrix_cropped <- roi_resize(red_matrix,
+ annotation[row, ])
+ green_matrix_cropped <- roi_resize(green_matrix,
+ annotation[row, ])
+ blue_matrix_cropped <- roi_resize(blue_matrix,
+ annotation[row, ])
+ # Convert to brightness, e.g. Y' channel
+ x <- 0.299 * red_matrix_cropped + 0.587 *
+ green_matrix_cropped + 0.114 * blue_matrix_cropped
+ X <- rbind(X, matrix(x, 1, 32*32))
+ y <- c(y, i)
+ }
+ }
+ return(list("x" = X, "y" = y))
+ }
```

如前所述定义数据加载函数后，我们将其应用于整个原始数据集：

```
> classes <- 0:42
> data <- load_labeled_data(training_path, classes)
```

