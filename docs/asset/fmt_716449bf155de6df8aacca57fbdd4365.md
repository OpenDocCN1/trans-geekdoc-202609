
```
bcf_table_3 <- bcf_table_2 |>
# succinct way to remove a row which has a single "NA"
na.omit() |>
select(route,
    starts_with("passengers_"),
    starts_with("passenger_tariff_rev")) |>
# change variables to numeric
mutate(passengers_fy2021 = as.numeric(passengers_fy2021),
    passengers_fy2020 = as.numeric(passengers_fy2020),
    passenger_tariff_revenue_fy2021 =
    as.numeric(passenger_tariff_revenue_fy2021),
    passenger_tariff_revenue_fy2020 =
    as.numeric(passenger_tariff_revenue_fy2020))
```

```
bcf_table_3
```

如果我们需要按路线类型创建小计，最好有一个单独的变量来表示。这里就可以使用 `{dplyr}` 中的 `case_when()` 函数。

```
bcf_table_3 <- bcf_table_3 |>
    mutate(route_type = case_when(
    route %in% c("1", "2", "3", "30") ~ "major",
```

## 图 8.9 BC Ferries：表 3。

![](img/b86622d1e9ca82b3cbec45faaffaaf26_136_0.png)

```
route %in% c("10", "11", "28") ~ "northern",
  TRUE ~ "minor"
))
```

`bcf_table_3`

![](img/b86622d1e9ca82b3cbec45faaffaaf26_136_1.png)

## 图 8.10 BC Ferries：表 3，最终。

现在我们可以使用数据整理技能来计算两年之间的百分比变化。让我们看看客运量的变化。

```
bcf_table_3 |>
  group_by(route_type) |>
  summarize(total_fy2021 = sum(passengers_fy2021),
            total_fy2020 = sum(passengers_fy2020)) |>
```

```
mutate(pct_change =
  (total_fy2021 - total_fy2020) / total_fy2020 * 100)
```

```
## # A tibble: 3 x 4
##   route_type total_fy2021 total_fy2020 pct_change
##   <chr>           <dbl>        <dbl>      <dbl>
## 1 major          7203979      13706288     -47.4
## 2 minor          5845280       7870649     -25.7
## 3 northern        34090        100403      -66.0
```

我们的分析：COVID-19 大流行对旅行产生了 *巨大的* 影响。2021 财年涵盖 2020 年 4 月 1 日至 2021 年 3 月 31 日的期间，几乎正好从严格的旅行限制开始实施。尽管在 12 个月期间后期限制开始放宽，但主要路线的旅行量下降了近一半。

# 9 数据来源网络

本章内容：

- 从网络存储库导入数据

## 9.1 引言

互联网上有大量有价值的数据，等待着好奇的数据分析师去发掘其中的洞见。有多种方式可以访问这些数据；在某些情况下，你可以下载 CSV 或 Excel 文件，然后将其读入 R。

但组成 R 社区的才华横溢的人们通过创建包使我们的生活变得轻松得多，这些包允许我们编写 R 脚本直接链接到我们想要的数据。如果访问的数据集会定期更新（例如每周财务报告或每月调查结果），这就特别有价值。

这种与互联网数据源连接的基础是 API（应用程序编程接口）。API 允许两个软件组件进行通信。在数据访问的上下文中，网站会设置 API 来定义数据如何被访问以及如何提供。

通常，API 包需要互联网连接。在某些情况下，API 可能需要请求用户密钥（网站可能用来验证用户或限制请求数量或大小的策略）。

利用 API 的 R 包有两种类型。第一种是专门针对特定数据源的，例如统计机构。除了获取数据外，这些包通常还具有额外的函数，可以为我们完成大量初始数据操作，使其成为 R 中有用的格式。

第二种类型超出了本书的范围，它们允许我们连接到原始数据源。对于这些来源，我们通常需要在使用数据之前进行一些整理。如果你有兴趣了解更多关于在 R 中创建与提供 API 的网站连接的内容，R 包 `{httr2}`(Wickham, 2023) 可能是一个不错的起点。

## 9.2 用于直接连接的 R 包

在本节中，我们将探讨示例，这些示例允许访问英国国家统计局和加拿大统计局托管的数据存储库。还有许多其他工具可用；其中一些列在本书章节末尾。截至撰写时，这些网站都不需要（至少）API 密钥。

### 9.2.1 国家统计局（英国）

我们的第一个示例将是 `{onsr}`，它直接从英国国家统计局下载数据（Vasilopoulos, 2022）。

```
library(onsr)
```

对于此，我们希望获得零售销售的时间序列数据。

我们可能想做的第一件事是探索我们感兴趣领域中有哪些可用内容。`ons_datasets()` 函数提供了当前可用的数据的完整列表。

```
datasets <- ons_datasets()

datasets |>
  select(id, description) |>
  filter(str_detect(id, "retail"))
```

从中我们将选择“按价值和数量计的英国零售销售数据，经季节性调整和未经季节性调整”，其 id 值为“retail-sales-index”。

`ons_ids()` 函数提供了从 `ons_datasets` 函数获得的 id 列的列表。

Another option is the `ons_browse_qmi()` function, which opens the relevant ONS page in your web browser software.

```
ons_browse_qmi(id = "retail-sales-index")
```

Finally, we will use the relevant id value in an `ons_get()` function to retrieve the data.

```
df_retail_sales <- ons_get(id = "retail-sales-index")
```

There are 42,400 rows in this data (as of 2023-06-14), with multiple variables for each month. Your analysis will require further filtering and selecting, but with the `{onsr}` package providing the access to the data, you are well on your way.

### 9.2.2 加拿大统计局

加拿大统计局，加拿大政府的一个部门，提供了一个名为“CANSIM”的社会经济时间序列数据库。发布到数据库中的数据是加拿大统计局定期收集的大部分汇总数据，例如劳动力调查（我们从中获得失业率更新）、消费者价格指数调查（关于通货膨胀）以及从怀孕和出生到预期寿命和死亡的健康相关信息。

包 `{cansim}`（von Bergmann 和 Shkolnik，2021）使用加拿大统计局创建的 API，以便直接下载数百个数据表和数千个单独的时间序列。

```
library(cansim) # access Statistics Canada's CANSIM data repository
```

One of the many tables related to international travel that is published in CANSIM is “Table: 24-10-0050-01 Non-resident visitors entering Canada, by country of residence”¹.

在 CANSIM 中发布的许多与国际旅行相关的表格之一是“表：24-10-0050-01 按居住国划分进入加拿大的非居民访客”¹。

Here’s a screenshot of the table, showing the number of people arriving by their continent of residence.

以下是该表的屏幕截图，显示按居住大陆到达的人数。

¹The webpage for the table, showing the most recently available data, is here: https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=2410005001

Geography: Canada (map)

地理：加拿大（地图）

| 居住国² | 2023年3月 | 2023年4月 | 2023年5月 | 2023年6月 | 2023年7月 |
|---|---:|---:|---:|---:|---:|
| **访客** |  |  |  |  |  |
| 进入加拿大的非居民访客 | 1,382,309 | 1,674,026 | 2,377,181 | 3,332,607 | 4,000,340 |
| 进入加拿大的美利坚合众国居民 | 1,094,111 | 1,300,810 | 1,831,912 | 2,632,723 | 3,132,681 |
| 进入加拿大的除美利坚合众国以外国家的居民 | 288,198 | 373,216 | 545,269 | 699,884 | 867,659 |
| 美洲，除美利坚合众国以外国家 | 74,654 | 92,600 | 90,704 | 116,030 | 141,622 |
| 北美，除美利坚合众国以外国家 | 42,446 | 56,789 | 49,022 | 56,651 | 69,313 |
| 中美洲 | 3,226 | 5,116 | 4,851 | 6,787 | 6,769 |
| 加勒比地区 | 11,203 | 15,742 | 14,952 | 20,830 | 28,585 |
| 南美洲 | 17,779 | 14,953 | 21,879 | 31,762 | 36,955 |
| 美洲，未另行说明³ | 0 | 0 | 0 | 0 | 0 |

**图 9.1** *CANSIM 表 24-10-0050-01.*

This table might be useful if you were developing a marketing campaign and you wanted to understand where tourists are coming from—the biggest markets and the fastest growing. But as shown, it is at too high a level; this is Canada by continent. For our purposes, we need to see specific country, those entering Canada via British Columbia, and a longer time series.

如果您正在开发营销活动并想了解游客来自哪里——最大的市场和增长最快的市场，该表可能很有用。但如图所示，它处于过高的层级；这是按大陆划分的加拿大。对于我们的目的，我们需要查看具体国家、经不列颠哥伦比亚省进入加拿大的人以及更长的时间序列。

We could use the filters and fiddle around making sure we got the right selections and then download the data, but if we have to do that next month it is going to be inefficient. We could also first click on the “download options” button and select “download entire table...” but again, this is not the most efficient way to do this, since there are a few manual steps we have to take and then open the file into R and filter to select the series we want.

我们可以使用过滤器并反复调整以确保获得正确的选择然后下载数据，但如果下个月必须这样做效率会很低。我们也可以先点击“下载选项”按钮并选择“下载整个表...”，但同样，这不是最高效的方式，因为我们必须执行几个手动步骤，然后将文件打开到 R 中并过滤以选择我们想要的系列。

This is where the `{cansim}` package comes in.

这就是 `{cansim}` 包发挥作用的地方。

### 第 1 步：下载数据。

- The `get_cansim()` function takes the table number as the parameter, and connects to CANSIM and downloads the data into an R dataframe.

```
travellers <- get_cansim("24-10-0050-01")
```

We will come back to filtering and variable selection along with working with date fields later, but here’s the code in R using the functions of the `{dplyr}` package to filter for the British Columbia cases during the month of June 2019:

我们稍后会回到过滤和变量选择以及处理日期字段，但以下是使用 `{dplyr}` 包的函数在 R 中过滤 2019 年 6 月不列颠哥伦比亚省案例的代码：

```
travellers_bc <- 
travellers |> 
  filter(GEO == "British Columbia",
         REF_DATE == "2019-06")

glimpse(travellers_bc, width = 65)
```

There are 287 rows, one for each of the categories in the Country of residence variable. It’s important to note that these are not just countries, but the variable also includes subtotals. What if we just want a monthly report on a single continent? One option would be for us to filter the “COUNTRY” variable; here we filter for visitors from Europe.

共有 287 行，每行对应居住国变量中的一个类别。需要注意的是，这些不仅仅是国家，变量还包括小计。如果我们只想要某个大洲的月度报告怎么办？一个选项是我们过滤“COUNTRY”变量；在这里我们过滤来自欧洲的访客。

```
travellers_bc |> 
  filter(`Country of residence` == "Europe")
```

One of the features of CANSIM and other similar tables is that the individual series are given a single identifier. In the case of CANSIM, these are called the “vector numbers”. Scroll to the right on this table, and you’ll see a variable called VECTOR. The vector identifier (sometimes called “the vector number” even though it’s a character string!) for European travellers entering Canada via British Columbia is v1277198032.

CANSIM 和其他类似表格的一个特点是各个系列都有一个唯一标识符。在 CANSIM 的情况下，这些被称为“向量编号”。将此表向右滚动，您会看到一个名为 VECTOR 的变量。经不列颠哥伦比亚省进入加拿大的欧洲旅行者的向量标识符（有时即使它是一个字符字符串也称为“向量编号”！）是 v1277198032。
