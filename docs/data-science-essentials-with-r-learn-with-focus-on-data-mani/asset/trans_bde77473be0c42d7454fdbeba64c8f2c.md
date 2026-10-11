

# 饼图与堆积条形图的对比

饼图长期以来一直是数据可视化的主流工具，但其局限性日益凸显。饼图的主要问题之一在于其倾向于扭曲所代表的实际数值，尤其是在处理微小切片或多个类别时。这种扭曲发生的原因是我们的眼睛不擅长准确判断角度，导致难以比较饼图中不同扇区的大小。因此，受众可能会误解数据，从而得出错误的结论或做出错误的决策。堆积条形图通过将每个类别表示为成比例的矩形来规避这一问题，使观众能更准确地比较不同片段的大小。

堆积条形图的另一大优势在于其处理各类数据类型的通用性。与饼图仅适合展示简单比例不同，堆积条形图既能容纳离散变量，也能容纳连续变量。例如，您可以使用一张堆积条形图，在单个图表中同时展示公司总销售额在不同产品类别和地区间的划分情况。

我们现在将在 `hunger_2021` 数据集中生成一个新列，该列代表各地区遭受饥饿（即营养不良）的人口百分比。随后，我们将使用堆积条形图来可视化这些数据。

```
# 创建新列 "Percentage"
hunger_2021 <- hunger_2021 %>%
  mutate(Percentage = round((Value / sum(Value)) * 100, 1))

# 堆积条形图
ggplot(hunger_2021, aes(x = "", y = Percentage,
  fill = fct_reorder(Region, Percentage))) +
  geom_bar(stat = "identity") +
  geom_text(aes(label = ifelse(Percentage >= 1, paste0(round(Percentage, 0), "%"), "")),
  position = position_stack(vjust = 0.5),
  size = 3, show.legend = FALSE) +
  labs(title = "Undernourished People by Region", fill = "Region",
  x = "", y = "Percentage") +
  scale_fill_brewer(palette = "Set2") +
  theme_bw()
```

下图是堆积条形图的参考示例：

![](images/Figure7.11.png)

图 7.11：堆积条形图

上述代码生成了一个以变量 `Percentage` 为 y 轴的堆积条形图。`Region` 变量用不同颜色填充条形，`fct_reorder` 函数根据百分比值对地区进行排序。`geom_bar()` 用于创建条形，`geom_text()` 用于向条形添加标签。`position_stack` 参数用于调整标签在条形内的位置。

# 可视化关联关系

在接下来的章节中，我们将探讨用于描绘两个变量间关联关系的常用图表。

## 箱线图

箱线图，又称箱须图，提供了集中趋势、离散程度和潜在异常值的图形化表示，特别适用于可视化数值变量与分类变量之间的关系。箱线图的关键组成部分包括：

*   **箱体**：代表四分位距（IQR），跨度从分布的第 25 百分位到第 75 百分位。其长度直观地展示了数据的分散程度。箱体越长表示变异性越大，箱体越短则表明分布越集中。
*   **中位数线**：箱体内绘制的一条粗线标记了中位数，即第 50 百分位。它在箱体内的位置暗示了分布的对称性或偏态。
*   **须线**：从箱体边缘延伸出的线条，通常延伸至最远的非异常值点。它们提供了数据总体范围的概念。
*   **异常值**：绘制在须线之外的单个点，通常定义为距离箱体边缘超过 1.5 倍 IQR 的数值。这些异常值突出了可能与大部分数据显著不同的异常观测值。

### 数据分析中的核心应用

箱线图在以下任务中特别有用：

*   **比较分布**：并排的箱线图展示了不同组别或类别在集中趋势、分散程度和形状上的差异。
*   **识别异常值**：定位可能扭曲结果或揭示意外模式的异常观测值。
*   **可视化偏态**：通过观察中位数在箱体内的位置以及须线的相对长度，可快速判断分布是对称还是偏态。

现在，让我们探索并可视化 2023 年 1 月黄色出租车的行程数据，该数据可通过纽约市出租车和豪华轿车委员会（TLC）获取。该数据集记录了每次出租车行程的多样化详情，如上下客时间、行驶距离和车费金额。数据来源：[https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)。

为进行分析，我们使用了该数据的特定子集，概述如下：

| 列名 | 说明 |
| --- | --- |
| `tpep_pickup_datetime` | 出租车计价器启动的时间戳。 |
| `tpep_dropoff_datetime` | 出租车计价器关闭的时间戳。 |
| `trip_distance` | 行程中记录的行驶距离，由出租车计价器按英里测量。 |
| `RatecodeID` | 行程结束时适用的费率代码。1=标准费率，2=JFK |
| `fare_amount` | 根据时间和距离由计价器计算的车费。 |

表 7.1：黄色出租车行程数据说明

```
cab_rides <- read.csv("cab_rides.csv")

# 转换数据类型
cab_rides$RatecodeID <- as.factor(cab_rides$RatecodeID)

cab_rides <- cab_rides %>% mutate(pickup_date = as_date(tpep_pickup_datetime))

# 创建箱线图以可视化驾驶速度分布
ggplot(cab_rides, aes(x = "", y = speed)) +
  geom_boxplot() +
  labs(
    title = "Driving Speed Distribution",
    x = "",
    y = "Speed (mph)"
  ) +
  theme_bw()
```

![](images/Figure7.12.png)

图 7.12：箱线图

接下来，让我们探索车速如何随一天中的不同时段而变化。为此，我们将添加一个名为 `pickup_timeofday` 的新列。该列将包含每次乘车上客时的时间段信息，从而使我们能够分析驾驶速度在不同时段的变化情况。函数 `time_of_day` 接受单个参数 `x`，代表一天中的某个具体小时。该函数随后使用一系列 `if` 语句来判断给定小时是否落在四个预定义时段之一内：上午（6 点-11 点）、下午（12 点-16 点）、晚上（17 点-21 点）或夜间（22 点-次日 5 点）。根据这些检查的结果，函数返回相应的字符串值以指示时间段。生成的 `pickup_timeofday` 列使用 `factor` 函数转换为有序因子类型。这确保了该列中的值被视为具有定义顺序的分类数据，而非单纯的字符串。`levels` 参数指定类别的顺序，而 `ordered` 参数指示这些类别应被视为有序数据。

```
# 创建计算一天中时间段的函数
time_of_day <- function(x) {
  if (x %in% 6:11) {
    return('Morning')
  } else if (x %in% 12:16) {
    return('Afternoon')
  } else if (x %in% 17:21) {
    return('Evening')
  } else {
    return('Night')
  }
}

# 创建新列 - pickup_timeofday
cab_rides <- cab_rides %>%
  mutate(pickup_timeofday = sapply(pickup_hour, time_of_day))

# 创建 pickup_timeofday，一个有序因子类型
cab_rides$pickup_timeofday <- factor(cab_rides$pickup_timeofday, levels = c("Morning", "Afternoon", "Evening", "Night"), ordered = TRUE)
```

