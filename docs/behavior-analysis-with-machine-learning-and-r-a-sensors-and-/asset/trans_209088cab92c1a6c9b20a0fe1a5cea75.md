

# 第 10 章：检测异常行为

```r
# Print data frame dimensions.
dim(df)
#> [1]    7  3102
```

我们使用 `dim()` 函数来打印数组的维度。从输出中，我们可以看到有 3102 条独立的轨迹，每条轨迹都包含 7 个属性。让我们探索一下单条轨迹的内容。以下代码段提取了第一条轨迹并打印它的结构。

```r
# Read one of the trajectories.
trj <- df[,1]

# Inspect its structure.
str(trj)
#> List of 7
#> frame.number : num [1:37, 1] 826 827 828 829 833 834 835 836 ...
#> bounding.box.x : num [1:37, 1] 167 65 162 159 125 124 126 126 ...
#> bounding.box.y : num [1:37, 1] 67 65 66 58 61 65 71 72 ...
#> bounding.box.w : num [1:37, 1] 40 37 39 34 39 38 38 37 31 ...
#> bounding.box.h : num [1:37, 1] 38 40 40 38 35 34 33 34 35 ...
#> class : num [1, 1] 1
#> classDescription: chr [1, 1] "normal"
```

一条轨迹由 7 部分信息组成：

-1. frame.number: 原始视频中的帧数。
2. bounding.box.x: 边界框的左边缘。
3. bounding.box.y: 边界框的顶边缘。
4. bounding.box.w: 边界框宽度。
5. bounding.box.h: 边界框高度。
6. class: 1=normal（正常），2=rare（稀有）。
7. classDescription: 'normal'（正常）或 abnormal（异常）。

边界框是每个捕获视频帧的坐标。图 10.5 显示了鱼及其边界框的示例。请注意，数据集不包含图像，只有边界框的信息。

![](img/91c149cc24c3e5af2971580c9dda9d8b_336_0.png)

每条轨迹的视频帧数不同。我们可以通过检查其中一个坐标的长度来获取帧数。

```r
# Count how many frames this trajectory has.
length(trj$bounding.box.x))
# [1] 37
```

第一条轨迹有 37 帧，但平均而言只有 10 帧。在我们的分析中，我们将只包含最少 10 帧的轨迹，因为从较短的路径中提取模式可能很困难。此外，我们不会使用边界框本身，而是使用框的中心点。

此时，绘制数据可视化图会是一个好主意。为了实现这一点，我将使用 `anipaths` 包（Scharf, 2020），它包含一个可以制作轨迹的函数！我不会涵盖使用该包的细节，但完整代码在 `visualize_fish.R` 脚本中。输出结果为 'index.html' 文件，其中包含交互式动画。为了简单起见，我选择了 50 条正常轨迹和 10 条异常轨迹进行绘制。图 10.6 显示了生成的图表。该图表还包含了一些播放、暂停、更改动画速度等控制控件。

'normal' 和 'abnormal' 标签是通过专家的视觉检查确定的。异常情况包括诸如躲避捕食者和攻击性运动（由于另一条鱼或因为恐惧）等事件。

![](img/91c149cc24c3e5af2971580c9dda9d8b_337_0.png)

图 10.6：使用 `anipaths` 包生成的动画轨迹示例。

## 10.2.2 预处理与特征提取

现在我们已经探索并可视化了数据，可以开始预处理和特征提取了。如之前提到的，数据库包含边界框，但我们想使用框的中心来定义轨迹。以下代码段（来自 `extract_features.R`）显示了如何计算框的中心。

```r
# Make times start at 0.
times <- trj$frame.number - trj$frame.number[1]
```

```r
tmp <- data.frame(x.coord, y_coord, time=times)
```

给定轨迹 `trj` 中所有帧时间的中心点 x 和 y 坐标将存储在 `x.coord` 和 `y.coord` 中。下一行“偏移”了帧号，使它们都从 0 开始（以简化预处理）。最后，我们将坐标和帧时间存储在一个时间数据框中，以便进一步的预处理。

![](img/91c149cc24c3e5af2971580c9dda9d8b_338_0.png)

图 10.7：数据库的第一条轨迹。

此时，我们将使用 `trajr` 包（McLean and Volponi, 2018），它包含了对轨迹进行绘制和操作的函数。`TrajFromCoords()` 函数可以从数据框创建一个轨迹对象。注意，数据框需要预定义的顺序，这就是为什么我们首先存储 x 坐标，然后是 y 坐标，最后是 `tmp` 数据框中的时间。

```r
tmp.trj <- TrajFromCoords(tmp, fps = 1)
```每秒帧数设置为 1。现在我们可以绘制 `tmp.trj`。

```r
plot(tmp.trj)
```

从图 10.7 可以看到点之间存在很大的时间间隙。这是因为某些帧缺失了。如果打印轨迹的前几行，我们可以看到例如第 4、5、6 帧是缺失的。

```r
head(tmp.trj)
# x y time polar displacement
# 1 187.0 66.0 0 187.0 66.0
# 2 183.5 66.0 1 183.5 66.0
# 3 181.5 85.0 2 181.5 85.0
# 4 176.0 85.0 3 176.0 85.0
# 5 144.5 75.5 4 144.5 75.5
```

接下来，尝试填充这些间隙是一个好主意。`TrajResample()` 函数通过沿轨迹进行线性插值来实现这一点。

```r
resampled <- TrajResample(tmp, 1)
```

如果我们绘制 `resampled` 轨迹，将看到缺失的点是如何填充的。现在我们准备好检测异常了。孤立树（Isolation Trees）通过分区工作，因此我们需要将轨迹转换为特征向量。`TrajDerivatives()` 函数计算点之间的速度和加速度。

```r
derivs <- TrajDerivatives(resampled)

# Print first speeds.
head(derivs$speed)
# [1] 3.640055 2.000000 5.500000 8.225342

# Print accelerations.
head(derivs$acceleration)
# [1] -1.640055 -3.500000 -2.725342 0.000000
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_340_0.png)

图 10.8：原始轨迹（圆形）和通过线性插值填充间隙后的轨迹（交叉）。生成的速度和加速度数量分别为 $n-1$ 和 $n-2，$n$ 是轨迹中的时间步。在训练孤立森林（Isolation Forest）时，所有特征向量需要长度相同；但数据库中的轨迹步骤不同。为了获得固定长度的特征向量，我们将计算速度和加速度的平均值、标准差、最小值和最大值。最后，我们将轨迹和标签（'normal' 或 'abnormal'）组合数据框。

```r
f.meanSpeed <- mean(derivs$speed)
f.sdSpeed <- sd(derivs$speed)
f.minSpeed <- min(derivs$speed)
f.maxSpeed <- max(derivs$speed)
f.meanAcc <- mean(derivs$acceleration)
f.sdAcc <- sd(derivs$acceleration)
f.minAcc <- min(derivs$acceleration)
f.maxAcc <- max(derivs$acceleration)
```

```r
features <- data.frame(id=paste0("id", 1), label=trj$classDescription[1],
                      f.meanSpeed, f.sdSpeed, f.minSpeed, f.maxSpeed,
                      f.meanAcc, f.sdAcc, f.minAcc, f.maxAcc)
```

对每条轨迹进行特征提取，并将结果保存为 .csv 文件 `fishFeatures.csv`，该文件已包含在集中。让我们读取并打印数据集的前几行。

```r
# Read dataset.
dataset <- read.csv("fishFeatures.csv", stringsAsFactors = T)
```

```r
# Print first rows of the dataset.
# id label f.meanSpeed f.sdSpeed f.minSpeed f.maxSpeed f.meanAcc
# 1 id normal 2.623236 2.228456 0.500000 8.225342 -0.053602
# 2 id2 normal 5.984859 3.820270 1.441236 15.101738 -0.0387046
# 3 id3 normal 16.608716 14.502042 0.7071068 46.424670 -1.0019597
# 4 id4 normal 4.808608 4.137387 0.500000 17.204651 -0.2818520
# 5 id5 normal 17.785747 9.927289 0.3354120 44.204818 -0.5375338
# 6 id7 normal 9.848422 6.026229 0.0000000 33.324165 -0.10555561
```

每一行代表一条轨迹。我们可以使用 `table()` 函数来获取 'normal' 和 'abnormal' 情况的计数。

