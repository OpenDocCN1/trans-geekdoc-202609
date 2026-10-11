

## Date[1:3], 格式："2023-08-24" "2022-12-15" "2021-05-03"

### 缺失元素的默认值

```r
make_date(year = 2023, month = 9) # day = 1
# "2023-09-01"

make_date(month = 9, day = 15) # year = 1970
# "1970-09-15"

make_date(year = 2023, day = 15) # month = 1
# "2023-01-15"
```

### 包含单独日期和时间组件的示例数据

```r
datetime_data <- data.frame(
  year = c(2023, 2022, 2021),
  month = c(8, 12, 5),
  day = c(24, 15, 3),
  hour = c(10, 14, 8),
  minute = c(30, 15, 45)
)

# 添加新的 datetime 列
datetime_data <- datetime_data %>%
  mutate(full_datetime = make_datetime(year, month, day, hour, minute))
```

在 `mutate` 内部，我们调用 `lubridate` 包中的 `make_datetime` 函数，将 `year`、`month`、`day`、`hour` 和 `minute` 列合并为一个新的 `full_datetime` 列。

```r
# 显示结果
print(datetime_data)

## year month day hour minute full_datetime
## 2023 8 24 10 30 2023-08-24 10:30:00
## 2022 12 15 14 15 2022-12-15 14:15:00
## 2021 5 3 8 45 2021-05-03 08:45:00
```

## 检索日期和时间组件

`lubridate` 为您提供了一组友好的工具，用于深入挖掘日期或时间的特定元素。假设您正在处理来自智能手表的健身数据。您有一个时间戳，代表 2023 年 8 月 25 日上午 6:30 的一次晨跑。现在，让我们使用 `lubridate` 函数来探索这个时间数据。

```r
# 创建晨跑的时间戳
run_timestamp <- ymd_hm("2023-08-25 06:30")
run_timestamp
## "2023-08-25 06:30:00 UTC"

# 识别年份
year(run_timestamp)
## 2023

# 识别月份
month(run_timestamp)
## 8

# 识别月份中的日期
mday(run_timestamp)
## 25

# 识别年份中的日期
yday(run_timestamp)
## 237

# 识别星期几（星期五，表示为 6）
wday(run_timestamp)
## 6

# 设置 label = TRUE 将星期几显示为有序因子
wday(run_timestamp, label = T)
## Fri
## Levels: Sun < Mon < Tue < Wed < Thu < Fri < Sat
```

## 修改日期和时间组件

虽然在典型的数据分析任务中不太常见，但修改日期和时间组件的功能在清理包含错误日期的数据时显得非常宝贵。让我们看看下面这个 datetime 示例，您有一个代表 2023-09-15 14:30:45 事件的 datetime 对象。您需要将其日期调整为 14 日，时间调整为下午 4:45。

```r
# 创建一个 datetime 对象
event_datetime <- ymd_hms("2023-09-15 14:30:45")

# 显示原始 datetime
event_datetime
## "2023-09-15 14:30:45 UTC"

# 更新多个组件：更改为 2023 年 9 月 14 日 16:45:00
event_datetime <- update(
  event_datetime,
  day = 14,
  hour = 16,
  minute = 45,
  second = 00
)

# 显示更新后的 datetime
event_datetime
## 2023-09-14 16:45:00 UTC
```

## 深入电力生产数据

现在，我们将探索一个包含经济合作与发展组织（OECD）成员国月度电力生产和贸易统计数据，以及少数其他经济体电力生产数据的数据集。该数据集源自国际能源署（IEA）的《月度电力统计 2023》。我们的目的是提取该时间数据中的特定组件。下表描述了 `MonthlyElectricityStatistics` 数据集中每一列的含义：

| 列名 | 描述 |
| --- | --- |
| Country | 国家名称 |
| Time | 日期。代表月份和年份 |
| Balance | 包含描述电力生产和消费状态的各种类别。这些类别包括净电力生产、抽水蓄能用电、输配电损失、计算最终消费、总进口、总出口和其他备注。 |
| Product | 对能源来源和相关数据进行分类。包括电力、各种燃料类型、风能、太阳能等可再生能源。 |
| Value | 该年特定月份的数值 |
| Unit | 单位为 GWh |

**表 5.1：** 月度电力数据集列描述

使用以下代码读取 CSV 文件并了解生成的 DataFrame 结构：

```r
# 读取 CSV 文件
monthly_electricity <- read.csv("MonthlyElectricityStatistics.csv")

# monthly_electricity dataframe 的结构
str(monthly_electricity)

## 'data.frame': 132833 obs. of 6 variables:
## $ Country: chr "Australia" "Australia" "Australia" "Australia" ...
## $ Time : chr "May 2023" "May 2023" "May 2023" "May 2023" ...
## $ Balance: chr "Net Electricity Production" "Net Electricity Production" "Net Electricity Production" "Net Electricity Production" ...
## $ Product: chr "Electricity" "Total Combustible Fuels" "Coal, Peat and Manufactured Gases" "Oil and Petroleum Products" ...
## $ Value : num 22310 15224 10447 386 4118 ...
## $ Unit : chr "GWh" "GWh" "GWh" "GWh" ...

# 显示数据集的前 6 行
head(monthly_electricity)

## Country Time Balance Product Value Unit
## Australia May 2023 Net Electricity Production Electricity 22309.8804 GWh
## Australia May 2023 Net Electricity Production Total Combustible Fuels 15224.3408 GWh
## Australia May 2023 Net Electricity Production Coal, Peat and Manufactured Gases 10446.8998 GWh
## Australia May 2023 Net Electricity Production Oil and Petroleum Products 385.5876 GWh
## Australia May 2023 Net Electricity Production Natural Gas 4117.5758 GWh
## Australia May 2023 Net Electricity Production Combustible Renewables 274.2775 GWh

# Time 列的数据类型
class(monthly_electricity$Time)
## "character"
```

让我们为分析准备 `monthly_electricity` 数据集。我们数据集中的 `Time` 列格式为“月份 年份”（例如，May 2023）。为了有效地处理这些数据，我们要给每个日期添加一个日期组件，具体为 '01'。这一步确保我们拥有完整的日期字符串（01 May 2023），随后可以解析并用于进一步分析。

```r
# 添加日期组件（例如 01）并解析日期
monthly_electricity <- monthly_electricity %>%
  mutate(
    Time = dmy(paste("01", Time))
  )
```

在以下代码中，我们在 `monthly_electricity` 数据集中添加 `Month`、`Year` 和 `Quarter` 列，以进行精确的时间分析。随后，我们专注于 Electricity 产品类别下的印度电力数据，筛选 2021 年及以后的数据。然后我们按季度对这些信息进行分组和汇总，计算总值和平均值。

```r
# 从 Time 中提取不同组件
monthly_electricity <- monthly_electricity %>%
  mutate(
    Month = month(Time),
    Year = year(Time),
    Quarter = quarter(Time, type = "year.quarter")
  )

head(monthly_electricity)

## Country Time Balance Product Value Unit Month
## Australia 2023-05-01 Net Electricity Production Electricity 22309.8804 GWh 5
## Australia 2023-05-01 Net Electricity Production Total Combustible Fuels 15224.3408 GWh 5
## Australia 2023-05-01 Net Electricity Production Coal, Peat and Manufactured Gases 10446.8998 GWh 5
```

